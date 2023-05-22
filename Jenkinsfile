node{
    def app
    
    stage('Clone repository'){
        git 'https://github.com/OuaritHajar/Docker-projet'
        
    }
     stage('Build the image'){
        app = docker.build("hajarouarit/my-app:${env.BUILD_NUMBER}") 
        
    }
    stage('Test image'){
        app.inside{
            sh 'echo "test passed"'
        }
    }
  
    stage('Push the image'){
        withCredentials([usernamePassword(credentialsId: 'DockerHub-id', passwordVariable: 'DOCKER_PASSWORD', usernameVariable: 'DOCKER_USERNAME')]) {
            sh 'docker login -u ${DOCKER_USERNAME} -p ${DOCKER_PASSWORD}'
            sh "docker push hajarouarit/my-app:${env.BUILD_NUMBER}"
        }

    }    
}