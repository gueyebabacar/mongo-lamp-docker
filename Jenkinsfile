node {
    stage('clone') {
       git credentialsId: '47027f88-bad0-4851-acb4-3af3425f95e0', url: 'https://github.com/gueyebabacar/myfarma-docker.git'
    }
     stage('build image') {
            docker.image('api_webserver:latest').withRun('-p 81:80') { c ->
     }
    }
     stage('Test image') {
        sh 'docker ps'
    }
     stage('Connect to container') {
            sh 'docker exec -i api-server cat /etc/*release*'
     }
     stage('Test git installation') {
          sh 'git branch'
     }
}