pipeline {
    agent any
    tools {
        maven 'Maven 3.3.9'
    }

    environment {
        scmVars = checkout([$class: 'GitSCM', branches: [[name: '/ad5/'], [name: '/ad6/'], [name: '/master']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'LocalBranch', localBranch: "**"]], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/daboome/webapp']]])
    }

    stages{
        stage('Build'){
            steps {
                echo "GIT_COMMIT ${env.GIT_COMMIT}.indexOf('f')"
                echo "GIT_BRANCH ${env.GIT_BRANCH}"
                sh "mvn clean package -DwarName=${env.GIT_BRANCH}"
                sh "cp target/${env.GIT_BRANCH}.war ./${env.GIT_BRANCH}.war"
            }
        }
    }
}