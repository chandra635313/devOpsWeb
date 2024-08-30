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
                      sh"docker build -t java ."
                      sh"docker run -it -d --name jar -p 8081:8081 java
                    }
                           }
      }
    }
                  
      
