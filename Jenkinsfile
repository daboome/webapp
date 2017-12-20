pipeline {
    agent any
    tools {
        maven 'Maven 3.3.9'
    }
    stages{
        stage('Build'){
            steps {
                echo 'building'
                sh 'mvn clean package -DwarName=${env.BRANCH_NAME}'
            }
        }
    }
}