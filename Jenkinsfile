pipeline{
    agent any

    stages{
        stage{'Build'}{
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