pipeline {
    agent any

    environment {
        BRANCH_NAME = "${env.CHANGE_ID}".replaceAll("[^a-zA-Z0-9]", "_")
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    checkout([$class: 'BitbucketSCMSource', id: 'mybitbucket',
                               credentialsId: 'your-credentials-id',
                               traits: [
                                   [$class: 'jenkins.plugins.git.traits.BranchDiscoveryTrait'],
                                   [$class: 'jenkins.plugins.git.traits.CleanBeforeCheckoutTrait'],
                                   [$class: 'jenkins.plugins.git.traits.LocalBranchTrait'],
                                   [$class: 'jenkins.plugins.git.traits.RemoteEndpointTrait'],
                                   [$class: 'jenkins.plugins.git.traits.WipeWorkspaceTrait']
                               ]])
                }
            }
        }

        stage('Build and Test') {
            steps {
                echo "Building and testing..."
            }
        }

        stage('Deploy') {
            when {
                expression { BRANCH_NAME == 'dev' }
            }
            steps {
                echo "Deploying..."
            }
        }
    }
}
