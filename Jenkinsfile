pipeline {
    agent any 
    stages {
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
                sh ' whoami '
                sh 'ls -la'
                sh ' chmod u+x deliver.sh'
                sh ' ./deliver.sh'
            }
        }
    }
}