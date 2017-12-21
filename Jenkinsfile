pipeline {
    agent any
    tools {
        maven 'Maven 3.3.9'
    }

    environment {
        checkout([$class: 'GitSCM', branches: [[name: '/ad5/'], [name: '/ad6/'], [name: '/master']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'LocalBranch', localBranch: "**"]], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/daboome/webapp']]])
    }

    stages{
        stage('Build'){
            steps {
                echo "GIT_COMMIT ${env.GIT_LOCAL_BRANCH}"
                sh "mvn clean package -DwarName=${env.GIT_LOCAL_BRANCH}"
                sh "cp target/${env.GIT_LOCAL_BRANCH}.war ./${env.GIT_LOCAL_BRANCH}.war"
            }
        }
    }
}

