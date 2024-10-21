@Library("Shared") _
pipeline {
    agent { label "vinod" }
    stages {
        stage("hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code") {
            steps {
                script{
                clone("https://github.com/aaqibshaikh-insightful/django-notes-app.git","main")
                }
            }
        }
        stage("Build") {
            steps {
                script{
                docker_build("notes-app","latest","aaqibshaikh20")
                }
            }
        }
        stage("Test") {
            steps {
                echo "This is testing the code"
            }
        }
        stage("Push to Dockerhub") {
            steps {
                script{
                    docker_push("notes-app","latest","aaqibshaikh20")
                }
                }
        }
        stage("Deploy") {
            steps {
                sh "docker compose down && docker compose up -d"
            }
        }
    }
}
