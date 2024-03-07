pipeline {
    agent any

    stages {
         stage('Stage-1 : Clean') { 
            steps {
                sh 'mvn clean'
            }
        }
        stage('Stage-2 : Validate') { 
            steps {
                sh 'mvn validate'
            }
        }
        stage('Stage-3 : Compile') { 
            steps {
                sh 'mvn compile'
            }
        }
        stage('Stage-4 : Test') { 
            steps {
                sh 'mvn test'
            }
        }
        stage('Stage-5 : Install') { 
            steps {
                sh 'mvn install'
            }
        }
        
    }
}
