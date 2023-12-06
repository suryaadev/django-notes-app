pipeline {
    agent any
    stages {
        stage ("clone code"){
            steps {
                echo "Cloning started..."
                git url:"https://github.com/suryaadev/django-notes-app.git", branch:"main"
            }
        }
        stage ("build Image"){
            steps {
                echo "Building image started..."
                sh "docker build -t notes-app ."
            }
        }
        stage ("push to docker hub"){
            steps {
                echo "Docker login started"
                
                withCredentials([usernamePassword(credentialsId:"dockerHub", passwordVariable: "dockerPass", usernameVariable: "dockerUser")]){
                    sh "docker tag notes-app ${env.dockerUser}/notes-app:latest"
                    sh "docker login -u ${env.dockerUser} -p ${env.dockerPass}"
                    sh "docker push ${env.dockerUser}/notes-app:latest"
                }
                
                echo "Docker Hub logged in"
                
                echo "Pushing to docker hub started..."
                
            }
        }
        stage ("Deploy"){
            steps {
                
                echo "Deployment started..."
                //sh "docker run -d -p 8000:8000 kartoos21/notes-app:latest"
                sh "docker-compose down && docker-compose up -d"
            }
        }
    }
}
