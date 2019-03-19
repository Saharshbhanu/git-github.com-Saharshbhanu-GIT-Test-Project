pipeline {
	       agent any  
	       environment { 
	        Jenkinsdemo = 'Jenkins Demo value'
	    }
	       tools {
	        maven 'Maven 3.6.0'
	        jdk 'java 1.8'
	    }
	
	       stages {
	              stage('Pre-Step') {
	                      steps {
	                             echo 'Pre-Step..'
	                             echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
	                             echo "${Jenkinsdemo}"
	                             echo "${PATH}"
	                             bat 'mvn compile'
	                      }
	              }
	              stage('Test') {
	                      steps {
	                             echo 'Testing..'
	                             bat 'mvn test' 
	                      }
	                      post {
	                success {
	                    junit 'target/surefire-reports/**/*.xml' 
	                }
	            }
	              }
	              stage('Build') {
	                      steps {
	                             echo 'Building..'
	                             bat 'mvn -Dmaven.test.failure.ignore=true install'
	                             archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
	                      }
	              }
	              
	              stage('Deploy') {
	                      steps {
	                             echo 'Deploying....'
	                             
	                      }
	              }
	       }
	}


