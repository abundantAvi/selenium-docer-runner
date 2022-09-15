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
                    sh "docker-compose up  PurchaseTest SalesTest InventoryAdjustTest NewContainerTest ShipmentPageTest"
                }
            }
        }
        post{
        always{
        archiveArtifacts artifacts: 'output1/**'
        sh "docker-compose down"
    }
}
}
