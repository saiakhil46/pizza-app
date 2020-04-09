pipeline {
    agent any
  
    parameters { 
        string(name: 'image_tag' , defaultValue: "", description: 'Enter image_tag')
        
    }

    stages {
        
        stage('Build Docker Image') {
          
            steps {
                buildName "${params.image_tag}"
                sh "docker build -t saiakhil46/ownkubeproject:${params.image_tag} ."
            }
        }
        stage('Push Docker Image') {
          
            steps {
                
                withCredentials([usernamePassword(credentialsId: 'docker_hub_login', usernameVariable: 'USERNAME', passwordVariable: 'USERPASS')]) {
                sh 'docker login -u $USERNAME -p $USERPASS'
                sh 'docker push saiakhil46/ownkubeproject:${params.image_tag}'

                }
            }
        }
    }
}
