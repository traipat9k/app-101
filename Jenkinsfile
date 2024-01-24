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

        stage("Build Application"){
            steps {
				app = docker.build("devops/hello")
            }

       }

       stage("Test Application"){
           steps {
                ;sh "mvn test"
           }
       }
    }
}