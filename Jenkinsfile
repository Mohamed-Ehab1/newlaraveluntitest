node {
    // Call the 'helloworld' library function
    helloworld()

    // Define the 'myPipeline' library function
    def myPipeline = {
        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: '**/*', onlyIfSuccessful: true
            }
        }
    }

    // Use 'when' directive
    when {
        // Run the pipeline only for pull requests targeting the main branch
        beforeAgent true
        expression { env.CHANGE_TARGET == 'main' && env.CHANGE_ID != null }
    }
}