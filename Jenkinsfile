pipeline{
    agent any
        stages{
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
}
post{
    always{
        archiveArtifacts artifacts: 'output/**'
        sh "docker-compose down"
    }
}