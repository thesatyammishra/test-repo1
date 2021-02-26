pipeline {
    agent any
    tools {
        maven 'maven'
        }
    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'master',
                credentialsId: 'be4829e4-a78c-4a67-a3d0-56e8c1f2c3f4',
                url: 'https://github.com/thesatyammishra/test-repo1.git'
                }
        }
        stage ('Clean') {
            steps {
                sh 'mvn clean'
                }
            }
      stage ('Compile') {
            steps {
                sh 'mvn compile'
                }
            }
	stage ('Install') {
            steps {
                sh 'mvn install'
                }
            }
	stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit '**/target/surefire-reports/*.xml'
                }
            }
        }
	stage ('Package') {
            steps {
                sh 'mvn package'
                }
            } 
        
        
         stage ('Deploy War File') {
                 steps {
                   sh "cp /root/.jenkins/workspace/gamesoflife/gameoflife-web/target/gameoflife.war /home/ec2-user/apache-tomcat-8.5.61/webapps/"
                    }
                }
	 
    }
}
