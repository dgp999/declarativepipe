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
                sh "mv target/*.war target/myweb.war"
            }
        }
        stage("Deploy"){
            steps{
            sshagent(['Newone']){
                sh """
                scp -o StrictHostKeyChecking=no target/myweb.war ec2-user@172.31.6.240:/opt/tomcat9/webapps/'
                ssh ec2-user@172.31.6.240 /opt/tomcat9/bin ./shutdown.sh
                ssh ec2-user@172.31.6.240 /opt/tomcat9/bin ./startup.sh
                """
            }
        }
    }
}
