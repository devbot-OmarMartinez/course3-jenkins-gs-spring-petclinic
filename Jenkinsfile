pipeline {
    agent any
    tools {dockerTool  "docker" } 
    
    stages {
        stage("build") {
            steps {
                sh "./mvnw package"
            }
        }
        stage("capture"){
            steps{
                archiveArtifacts artifacts: '**/target/*.jar'
                jacoco()
                junit stdioRetention: '', testResults: '**/target/surefire-reports/TEST*.xml'
            }
        }
    }
    
}