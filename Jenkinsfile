node {
    def scmVars = checkout([$class: 'GitSCM', branches: [[name: '/ad5/'], [name: '/ad6/'], [name: '/master']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'LocalBranch', localBranch: "**"]], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/daboome/webapp']]])
    echo "${scmVars.GIT_LOCAL_BRANCH}"

    stage('Build') {
        withMaven {
            maven: 'Maven 3.3.9'
        }
        sh "mvn clean package -DwarName=${scmVars.GIT_LOCAL_BRANCH}"
    }
}
