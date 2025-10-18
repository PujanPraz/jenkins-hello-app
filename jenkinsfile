@Library("Shared") _

pipeline {
    agent { label "pujan" }
    
    stages{
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Clone"){
            steps{
                echo "This is cloning"
                script {
                    clone("https://github.com/PujanPraz/jenkins-hello-app.git", "main")
                }
            }
        }
        stage("Build"){
            steps{
                echo "This is build"
                script{
                    build("pujanprajapati", "hello-app", "latest")
                }
            }
        }
        stage("Push to dockerhub"){
            steps{
                echo "This is pushing the image to docker hub"
                script{
                    push("hello-app", "latest")
                }
              
            }
        }
        stage("Deploy"){
            steps{
                echo "This is deploying the code"
                sh "docker compose up -d"
            }
        }
    }
}
