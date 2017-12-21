pipeline {
    agent any
    tools {
        maven 'Maven 3.3.9'
    }
    stages{
        stage('Build'){
            steps {
                echo 'Building ${env.BRANCH_NAME}'
                sh 'mvn clean package -DwarName=wdw'
            }
        }
    }
}