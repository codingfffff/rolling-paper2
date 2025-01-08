node {
    def dockerImage

    stage('Clone repository') {
        git branch: 'main', 
            credentialsId: 'github-access', 
            url: 'https://github.com/codingfffff/rolling-paper2.git'
    }
    
    stage('Build image') {
        dir('docker-project-front') {
            dockerImage = docker.build("seunghunn/node-front:1.0")
        }
    }
    
    stage('Push image') {
        withDockerRegistry([ credentialsId: "docker-access", url: "" ]) {
            dockerImage.push()
        }
    }
}

