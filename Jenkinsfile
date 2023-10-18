node {
        lable: 'default'
        if(env.JOB_NAME.contains('DEV')){
            // develop steps:

            php_ut()


        } else if (env.JOB_NAME.contains('STG')){
            //staging steps
            set_env()
            build_image()
            deploy_to stg

        }
    stage('SonarQube Analysis') {
    def scannerHome = tool 'suiiz';
    withSonarQubeEnv() {
      sh "${scannerHome}/bin/sonar-scanner"
    }
    }
}
