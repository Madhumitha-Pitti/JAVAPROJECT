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
        stage('Stage-6 : Verify') { 
            steps {
                sh 'mvn verify '
            }
        }
          stage('Stage-7 : Package') { 
            steps {
                sh 'mvn package '
            }
        }
         stage('Stage-0 : Static Code Analysis Using SonarQube') { 
            steps {
                sh 'mvn clean verify sonar:sonar -DskipTests'
            }
        }  
        stage('Upload'){
steps{
rtUpload (
serverId:"Artifactory" ,
spec: '''{
"files": [
{
"pattern": "*.war",
"target": "libs-snapshot-local"
}
]
}''',
)
}
}
stage ('Publish build info') {
steps {
rtPublishBuildInfo (
serverId: "Artifactory"
)
}
} 
        stage('Stage-9 : Deployment - Deploy a Artifact devops-3.0.0-SNAPSHOT.war file to Tomcat Server') { 
            steps {
                sh 'curl -u admin:redhat@123 -T target/**.war "http://54.254.154.100:8080/manager/text/deploy?path=/madhu&update=true"'
            }
        }
    }
}
