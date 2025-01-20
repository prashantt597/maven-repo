pipeline {
    // add your slave label name
    agent { label 'Slave-L1'}
    tools{
        maven 'Apache Maven 3.9.9'
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
	      sshagent(['ec2-user-tommy']) {
              sh "scp -o StrictHostKeyChecking=no  target/maven-web-application.war  ec2-user@3.108.54.10:/opt/tomcat9/webapps"
	      }
         }
        }
        
    }
}

