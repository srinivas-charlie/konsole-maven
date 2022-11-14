pipeline{
    agent any

    stages{
<<<<<<< HEAD
        stage{"git checkout"}{
            steps{
                git credentialsId: 'javahome2', url: 'https://github.com/srinivas-charlie/konsole-maven.git'
            }
        }
        stage{"Maven Build"}{
=======
        stage{'Build'}{
>>>>>>> 97a7a238acc87d86529b28f28657a11f6f28ea08
            steps{
                sh 'mvn clean package'
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
                deploy adapters: [tomcat8(credentialsId: '5f5388fd-9100-4db2-8ec8-b8dcb9b40656', path: '', url: 'http://192.168.43.26:1997')], contextPath: 'local', war: '**/*.war'

            }

        }
    }
} 