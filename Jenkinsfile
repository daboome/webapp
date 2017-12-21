node {
    def scmVars = checkout([$class: 'GitSCM', branches: [[name: '/ad5/'], [name: '/ad6/'], [name: '/master']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'LocalBranch', localBranch: "**"]], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/daboome/webapp']]])
    echo "${scmVars.GIT_LOCAL_BRANCH}"

    tools {
        maven 'Maven 3.3.9'
    }

    stage('Build') {
        sh "mvn clean package -DwarName=${scmVars.GIT_LOCAL_BRANCH}"
    }
}
