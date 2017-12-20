pipeline {
    agent any
    tools {
        maven 'Maven 3.3.9'
    }
    stages{
        stage('Build'){
            steps {
                echo 'building $BRANCH_NAME'
                sh 'mvn clean package -DwarName=wdw'
                if (env.BRANCH_NAME == 'master') {
                    stage 'Only on master'
                    println 'This happens only on master'
                } else {
                    stage 'Other branches'
                    println "Current branch ${env.BRANCH_NAME}"
                }
            }
        }
    }
}