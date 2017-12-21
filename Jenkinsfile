pipeline {
    agent any
    tools {
        maven 'Maven 3.3.9'
    }

    checkout([$class: 'GitSCM', branches: [[name: '/ad5/'], [name: '/ad6/'], [name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'LocalBranch', localBranch: "**"]], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/daboome/webapp']]])

    stages{
        stage('Build'){
            steps {
                echo 'Building ${env.BRANCH_NAME}'
                echo 'Building ${BRANCH_NAME}'
                sh 'mvn clean package -DwarName=wdw'
            }
        }
    }
}