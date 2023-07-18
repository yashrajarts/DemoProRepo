pipeline{
    agent any
    
    tools{
        maven 'MAVEN'
    }
    stages{
        stage ('Build'){
            steps{
            bat 'mvn clean package'
            }
            post{
                success{
                    echo "Archiving the Artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage ('Deploy to tomcat server') {
            steps{
                echo "Deployment"
                deploy adapters: [tomcat9(credentialsId: 'e0050683-5390-49d1-a840-65bde1940406', path: '', url: 'http://localhost:8005')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
