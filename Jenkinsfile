node{
    helloworld()
    archiveArtifacts artifacts: '**/*', onlyIfSuccessful: true
    when {
        // Run the pipeline only for pull requests targeting the dev branch
        beforeAgent true
        expression { env.CHANGE_TARGET == 'dev' && env.CHANGE_ID != null }
    }
}