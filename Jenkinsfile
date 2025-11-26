@Library('Shared') _
pipeline{
    agent Any

    stages{
        stage("hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code"){
            steps{
                script{
                    clone("https://github.com/Avesh-code/django-notes-app.git","main")
                }
            }
        }
        stage("Build"){
            steps{
                script{
                      docker_build("notes-app","latest")
                }
            }
        }
        stage("push to docker hub"){
            steps{
                script{
                    docker_push("notes-app","latest")
                }
            }
        }
        stage("Deploy"){
            steps{
                sh "docker compose down && docker compose up -d"
            }
        }
    }
}
