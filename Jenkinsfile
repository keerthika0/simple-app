pipeline {
    agent any 
    tools {
        maven 'maven3'
    }
    stages {
        stage('stage build') {
            steps {
                sh script: 'mvn clean package'
            }
        }
        stage('build') {
            steps {
                nexusArtifactUploader artifacts: [
                    [
                        artifactId: 'simple-app', 
                        classifier: '', 
                        file: 'target/nexus_sample-2.0.0.war', 
                        type: 'war'
                    ]
                ], 
                credentialsId: 'nexus3', 
                groupId: 'in.javahome', 
                nexusUrl: '10.1.40.43:8082', 
                nexusVersion: 'nexus3', 
                protocol: 'http',
                repository: 'demo', 
                version: '3.0.0'
            }
        }
    }
}
