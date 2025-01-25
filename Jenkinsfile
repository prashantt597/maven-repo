pipeline{
    agent {label 'slave-P1'}
    tools{
        maven 'maven'       
    }
    stages{
        stage('git clone-SCM'){
            steps{
                checkout scm
            }
        }
        stage('Maven_Build'){
            steps{
                sh 'mvn clean package'
            }
        } 
        stage('deploy_Tomcat'){
            steps{
               sshagent(['ec2-user-tommy']) {
                sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@65.2.57.41:/opt/tomcat9/webapps"
               }

               }
            }
        }

    }
