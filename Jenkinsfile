pipeline {
    agent any
    stages {
       stage('Checkout source code') {
        environment {
        // 'This value is exported to all commands in this stage'
        l = sh 'source ./scripts/env.sh'

        AWESOME_BUILD = "${env.GIT_UR}"
         }
          steps{
              echo "$AWESOME_BUILD"
              echo "$l"
                    
          }
         
    }
         
        stage("build") {
            steps {
                script {
                    if (fileExists('build.sbt')) {
                           sh './scripts/sbt.sh'
                      } else if(fileExists('pom.xml') && !fileExists('build.sbt')){
                           sh './scripts/mvn.sh'
                          }
                       else {
                           echo "The repo does not contain build.sbt or pom.xml"
                       }   
                    
                }
            }
        }
    }
  }
