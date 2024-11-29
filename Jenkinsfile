pipeline {
    agent any
    tools {
        maven 'mvn'
    }
    options {
        skipStagesAfterUnstable()
    }
    stages {
        stage('Check Directory') {
            steps {
                sh 'pwd'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Deliver') { 
            steps {
                sh './scripts/deliver.sh' 
            }
        }
    }
}
