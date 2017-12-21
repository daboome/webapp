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
                echo "GIT_COMMIT ${scmVars.GIT_LOCAL_BRANCH}"
                sh "mvn clean package -DwarName=${scmVars.GIT_LOCAL_BRANCH}"
                sh "cp target/${scmVars.GIT_LOCAL_BRANCH}.war ./${scmVars.GIT_LOCAL_BRANCH}.war"
            }
        }
    }
}

