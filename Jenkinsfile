node{
    helloworld()
    archiveArtifacts artifacts: '**/*', onlyIfSuccessful: true
    when {
        // Run the pipeline only for pull requests targeting the dev branch
        // ازيك وازى معزيك
        beforeAgent true
        expression { env.CHANGE_TARGET == 'main' && env.CHANGE_ID != null }
    }
}