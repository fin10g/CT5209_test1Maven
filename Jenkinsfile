pipeline {
    agent any

    stages {
        stage('GetProject') {
            steps {
                git branch: 'main', url: 'https://github.com/fin10g/CT5209_test1Maven.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Exec') {
            steps {
                sh 'mvn exec:java'
            }
        }
    }

    post {
        success {
            archiveArtifacts allowEmptyArchive: true,
                    artifacts: '**/ct5209_test1Maven*.jar'
        }
        failure {
            echo 'Build failed!'
        }
    }
}