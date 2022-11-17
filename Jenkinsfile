pipeline {
    agent any
    
    tools {
        maven 'local_maven'
    }
   
stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Archiving the artifacts'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }

        stage ('Deploy to tomcat server'){

                    steps {
                        deploy adapters: [tomcat9(credentialsId: '5f99f121-7608-4024-8d6a-12bd112e628f', path: '', url: 'http://54.168.233.189:8081/')], contextPath: null, war: '**/*.war'
                    }
     
        }
    }
}
