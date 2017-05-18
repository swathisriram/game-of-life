node("docker") {
    docker.withRegistry('registry', 'swathisriramf') {
    
        git url: "https://github.com/wakaleo/game-of-life.git", credentialsId: 'swathisriram'
    
        sh "git rev-parse HEAD > .git/commit-id"
        def commit_id = readFile('.git/commit-id').trim()
        println commit_id
    
        stage "build"
        def app = docker.build "game-of-life"
    
        stage "publish"
        app.push 'master'
        app.push "${commit_id}"
    }
}
