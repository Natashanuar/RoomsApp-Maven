pipeline{
  agent any
    tools {
      maven 'Maven'
  }
  
  stages {
      
    stage ('Cloning Git') {
      steps {
        git 'https://github.com/Natashanuar/RoomsApp-Maven.git'
     }
    }
    
    stage ('Initialize') {
      steps {
        sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
            ''' 
     }
    }
    
    stage ('Check-Git-Secrets'){
        steps{
        sh 'rm trufflehog || true'
        sh 'docker run gesellix/trufflehog --json https://github.com/Natashanuar/RoomsApp-Maven.git > trufflehog'
        sh 'cat trufflehog'
       }
    }
    
   /* stage ('Software Composition Analysis') {
            steps {
                dependencyCheck additionalArguments: ''' 
                    -o "./" 
                    -s "./"
                    -f "ALL" 
                    --prettyPrint''', odcInstallation: 'dependencycheck'
                dependencyCheckPublisher pattern: 'dependency-check-report.xml'
            }
        }
    /*
  stage ('Software Composition Analysis') {
      steps {
         sh 'rm -r dependency-check* || true' 
         sh 'wget https://github.com/jeremylong/DependencyCheck/releases/download/v6.0.3/dependency-check-6.0.3-release.zip'
         sh 'unzip dependency-check-6.0.3-release.zip'
         sh './dependency-check/bin/dependency-check.sh --scan ./* --enableRetired -f "ALL" '
       }
    }
    
   stage ('SAST') {
      steps {
        withSonarQubeEnv('sonar') {
          sh 'mvn sonar:sonar'
          sh 'cat target/sonar/report-task.txt'
        }
      }
    }
    
    stage ('Build') {
      steps {
        sh 'mvn clean package'
         }
       }
    
    
     /*stage ('Deploy-To-Tomcat') {
            steps {
           //sshagent(['tomcat']) {
             sh 'cp target/*.war /home/tas/prod/apache-tomcat-9.0.41/webapps/webapp.war'

              //  sh 'scp -o StrictHostKeyChecking=no target/*.war ubuntu@35.239.79.249:/home/natasha_1998/prod/apache-tomcat-9.0.41/webapps/webapp.war'
              }      
           }     
     stage ('Deploy-To-Tomcat') {
            steps {
           sshagent(['tomcat']) {
                sh 'scp -o StrictHostKeyChecking=no target/*.war ubuntu@35.239.79.249:/home/natasha_1998/prod/apache-tomcat-9.0.41/webapps/webapp.war'
              }      
           }       
    }
    
     stage ('DAST') {
      steps {
        sshagent(['zap']) {
         sh 'ssh -o  StrictHostKeyChecking=no ubuntu@35.193.155.239 "docker run -t owasp/zap2docker-stable zap-baseline.py -t http://35.225.146.167:8080/shoppingcartapp-web-V2/" || true'
        }
      }
    }*/
  }
}
