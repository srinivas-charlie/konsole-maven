pipeline{
    agent any
         environment{
        PATH = "/opt/maven/bin:$PATH"
         }

    stages{
        stage{"git checkout"}{
            steps{
                git credentialsId: 'shaik', url: 'https://github.com/srinivas-charlie/konsole-maven-.git'
            }
        }
        stage{'Build'}{
            steps{
                sh 'mvn clean sonar:sonar deploy'
            }
            post{
                success{
                    echo "Archiving the Artifact"
                    archiveArtifacts artfacts: '**/target/*.war'
                }
            }

        }
        stage{'Deploy to tomcat server'}{
            steps{
                deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://localhost:1997/')], contextPath: null, war: 'target/*.war'

            }

        }
    }
} 
