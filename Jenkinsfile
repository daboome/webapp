pipeline {
    agent any
    tools {
        maven 'Maven 3.3.9'
    }

    environment {
        checkout([$class: 'GitSCM', branches: [[name: '/ad5/'], [name: '/ad6/'], [name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'LocalBranch', localBranch: "**"]], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/daboome/webapp']]])
        foo = 'foovalue'
    }

    stages{
        stage('Build'){
            steps {
                echo 'foo is $foovalue'
                echo 'Commit ${env.GIT_COMMIT}'
                echo 'Commit ${env.GITCOMMIT}'
                echo 'Branch name ${env.GIT_BRANCH}'
                echo 'Branch name ${env.GITBRANCH}'
                sh 'mvn clean package -DwarName=wdw'
            }
        }
    }
}