pipeline {
    agent {
       node {
         label "linux"
      }
    }
    stages {
        stage('Build') {
            steps {
                echo '<--------------- Building started --------------->'
                sh 'printenv'
                sh 'mvn clean install'
                echo '<------------- Build completed --------------->'
            }
        }

  stage ("Sonar Analysis") {
            environment {
               scannerHome = tool 'sonar'  //scanner name configured for slave 
            }
            steps {
                echo '<--------------- Sonar Analysis started  --------------->'
                withSonarQubeEnv('Sonar') {    
                    //sonarqube server name in master
                    sh "${scannerHome}/bin/sonar-scanner"
                }    
                echo '<--------------- Sonar Analysis stopped  --------------->'
            }   
        }
    }
}

