pipeline{
    agent any
        stages{
            stage("Pull latest image"){
                steps{
                    sh "docker pull aviraj047/selenium-docker"
                }
            }
            stage("Start Grid"){
                steps{
                    sh "docker-compose up -d hub chrome firefox"
                }
            }
            stage("Run Test"){
                steps{
                    sh "docker-compose up  PurchaseTest SalesTest"
                }
            }
        }
        post{
        always{
        archiveArtifacts artifacts: 'output/**'
        sh "docker-compose down"
    }
}
}
