pipeline{
    agent any
  
    stages{
        stage("Git Checkout"){
            steps{
                git credentialsId: 'shaik', url: 'https://github.com/srinivas-charlie/konsole-maven-.git'
            }
        }
        stage("Maven Build"){
            steps{
                sh "mvn clean package"
            }
        }
        stage{"deploy-dev"}{
            steps{
                 deploy adapters: [tomcat8(credentialsId: 'tomcat', path: '', url: 'http://localhost:1997/')], contextPath: null, war: 'target/*.war'

            }

        }
    }
}
