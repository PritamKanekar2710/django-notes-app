@Library("Shared") _
pipeline{ 
    
    agent { label "vinod"} 

    stages{ 
        stage("Code"){ 
            steps{
                script{
                    clone("https://github.com/PritamKanekar2710/django-notes-app.git","main")
                }
            } 
        } 
        stage("Build"){ 
            steps{
                script{
                    docker_build("notes-app","latest","pritamkanekar")
                }
            } 
        } 
        stage("Push to DockerHub"){ 
            steps{ 
                script{
                    docker_push("notes-app","latest","pritamkanekar")
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
