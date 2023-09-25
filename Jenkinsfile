pipeline {
    agent any

    stages {
        stage('Checkout SCM') {
            steps {
                // Clone the SimpleTest repository
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://github.com/Mohamed-Ehab1/newlaraveluntitest']]])
            }
        }

        stage('Install Dependencies') {
            steps {
                // Install Composer dependencies
                sh 'composer install'
                
            }
        }

        stage('Unit Tests') {
            steps {
                catchError(buildResult: 'FAILURE', stageResult: 'FAILURE') {
                    sh 'php artisan test'
                }
            
            }
        }
        
        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: '.phpunit.result.cache', followSymlinks: false
            }
        }
    }
}
