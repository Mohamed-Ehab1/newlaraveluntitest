node {
    // Call the 'helloworld' library function
    helloworld()

    // Check if it's a pull request targeting the main branch
    def isPullRequestToMain = env.CHANGE_TARGET == 'main' && env.CHANGE_ID != null

    // Run the Archive Artifacts stage only if it's a pull request to main
    if (isPullRequestToMain) {
        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: '**/*', onlyIfSuccessful: true
            }
        }
    }
}
