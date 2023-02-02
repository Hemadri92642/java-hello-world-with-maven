#!groovy

pipeline {
	agent none
  stages {
  	stage('Maven Install') {
    	agent {
      	docker {
        	image 'maven:3.5.0'
        }
      }
      steps {
      	sh 'mvn clean install'
      }
    }
    stage('Docker Build') {
    	agent any
      steps {
      	sh 'docker build -t java-hello-world-with-maven:latest .'
      }
    }
   stage('display') {
       steps {
             archiveArtifacts artifacts: 'build/' , onlyIfSuccessful: true
  
          }
      }
  }
}
