@Library("Shared") _
pipeline {
    
    agent { label "vinod"}

    stages {
        
        stage("hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage('Code') {
            steps {
                script{
                    clone( "https://github.com/Manish2408/django-notes-app.git","main")
                }
            }
        }
        stage('Build') {
            steps {
                script{
                    docker_build("notes-app","latest","manishrlmra")
                }
            }
        }
        stage('Push to dockerhub') {
            steps {
                script{
                    docker_push("notes-app","latest","manishrlmra")
                }
            }
        }
        
        stage('Deploy') {
            steps {
                echo "This is deploy stage"
                sh "docker compose down && docker compose up -d "
            }
        }
            
}
}


