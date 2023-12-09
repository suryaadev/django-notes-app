pipeline {
    agent any
    stages {
        stage("Clone code"){
            steps{
                echo "cloning started"
                git url:"https://github.com/suryaadev/django-notes-app.git", branch: "main"
            }
        }
        stage("build Image"){
            steps{
                echo "Building Image"
                sh "docker build -t noting-app ."                
            }
        }
        stage("push to dockerhub"){
            steps{
                echo "Push to docker Hub"
                withCredentials([usernamePassword(credentialsId:"docker", passwordVariable:"pass", usernameVariable:"user")]){
                    sh "docker tag noting-app ${env.user}/noting-app:latest"
                    sh "docker login -u ${env.user} -p ${env.pass}"
                    sh "docker image push ${env.user}/noting-app:latest"
                }
            }
        }
        stage("Deployment"){
            steps{
                echo "Deployment started..."
                sh "docker-compose down && docker-compose up -d"
            }
        }
    }
}
