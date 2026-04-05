pipeline {
    // add your slave label name
    agent { label 'my-slave-1'}
    tools{
        maven 'mvn'
    }
    stages {
        stage ('Checkout_SCM') {

            steps {
          	   checkout scm  
            }
        }

        stage ('Maven_Build') {

            steps {
               sh 'mvn clean package'
            }
        }
        
        stage ('Deploy_Tomcat') {

            steps {
	      sshagent(['My-tomcat-server']) {
              sh "scp -o StrictHostKeyChecking=no  target/maven-web-application.war  ec2-user@100.48.20.152:/opt/tomcat11/webapps"
	      }
         }
        }
        
    }
}
