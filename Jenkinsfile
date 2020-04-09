pipeline {
    agent any
  
    parameters { 
        string(name: 'image_tag' , defaultValue: "", description: 'Enter image_tag')
        
    }

    stages {
        
        stage('Build Docker Image') {
          
            steps {
                buildName "${params.image_tag}"
                script {
                    app = docker.build(saiakhil46/ownkubeproject)
                }
            }
        }
        stage('Push Docker Image') {
          
            steps {
                
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'docker_hub_login') {
                        app.push("${params.image_tag}")
                        
                    }

                }
            }
        }
    }
}
