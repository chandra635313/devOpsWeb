pipeline{
    agent any
    tools{
        maven 'local_maven'
    }
    stages{
        stage ('Build'){
            steps{
                sh 'mvn clean package'
            }
            post{
                success{
                    echo "Archiving the Artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
                 stage ("Deploy to Staging"){
                    steps {
                      sh 'docker rm -f \$(docker ps -aq)'
 
                         sh"docker rmi -f \$(docker images -aq)"
                      sh"docker build -t java ."
                      sh '''
docker run -it -d --name jar -p 8081:8080 java
'''
                    }
                           }
      }
    }
                  
      
