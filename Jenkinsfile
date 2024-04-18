pipeline{
    agent any
    tools{
        maven 'local_maven'
    }
    stages{
        stage ('Build'){
            steps{
                bat 'mvn clean package'
            }
            post{
                success{
                    echo "Archiving the Artifacts"
                    archiveArtifacts artifacts: '/target/.war'
                }
            }
        }
        stage ('Deploy to tomcat server'){
            steps{
                deploy adapters: [tomcat7(credentialsId: 'c40dbad7-b07b-4996-98fb-4dd30ee7f44a', path: '', url: 'http://localhost:8181/')], contextPath: null, war: '**/.war'
            }
        }
    }
}
