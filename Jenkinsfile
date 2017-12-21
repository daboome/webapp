pipeline {
    agent any
    tools {
        maven 'Maven 3.3.9'
    }

    environment {
        def scmVars = checkout([$class: 'GitSCM', branches: [[name: '/ad5/'], [name: '/ad6/'], [name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'LocalBranch', localBranch: "**"]], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/daboome/webapp']]])
    }

    stages{
        stage('Build'){
            steps {
                echo 'Commit ${scmVars.GIT_COMMIT}'
                echo 'Branch name ${scmVars.GIT_BRANCH}'
                sh 'mvn clean package -DwarName=wdw'
            }
        }
    }
}