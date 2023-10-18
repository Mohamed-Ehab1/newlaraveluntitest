pipeline {
     agent any
     stages {
         stage('Build') {
             steps {
                 echo 'Building...'
             }
             post {
                 always {
                     jiraSendBuildInfo site: 'suiiz.atlassian.net', branch: 'develop'
                 }
             }
         }
     }
 }

