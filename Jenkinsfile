pipeline{
    agent any
    stages{
        stage("Welcome"){
            steps{
                git 'https://github.com/dgp999/Janarirepo.git'
            }
        }
        stage("Maven Build"){
            steps{
                sh "mvn clean package"
            }
        }
    }
}
