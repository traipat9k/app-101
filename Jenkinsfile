pipeline {
    agent { label 'Jenkins-Agent' }
    stages{
        stage("Cleanup Workspace"){
                steps {
                cleanWs()
                }
        }

        stage("Checkout from SCM"){
                steps {
                    git branch: 'main', credentialsId: 'github', url: 'https://github.com/traipat9k/app-101.git'
                }
        }

        stage("Build Image"){
            steps {
				sh 'docker build -t traipatk/staticsite:1.0 .'
            }

       }

       stage("Push Image"){
           steps {
                withCredentials([usernamePassword(credentialsId: 'docker-hub', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
				sh 'docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD'
				;sh 'docker push traipatk/staticsite:1.0’
           }
       }
    }
}