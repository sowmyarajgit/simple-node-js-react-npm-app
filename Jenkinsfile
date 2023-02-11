pipeline { 
  
   agent any

   stages {
   
     stage('Pulling git code') { 
        steps { 
           git credentialsId: 'admin', url: 'https://github.com/sowmyarajgit/simple-node-js-react-npm-app.git'
        }
     }
     
     stage('nodejs build') { 
        steps { 
           sh 'npm install'
        }
      }

       stage ("Sonar Analysis") {
            environment {
               scannerHome = tool 'admin_sonarscanner'
            }
            steps {
                echo '<--------------- Sonar Analysis started  --------------->'
                withSonarQubeEnv('admin_sonarcube') {    
                    sh "${scannerHome}/bin/sonar-scanner"
                echo '<--------------- Sonar Analysis stopped  --------------->'
                }    
               
            }   
        }   
  
   	}

   }
