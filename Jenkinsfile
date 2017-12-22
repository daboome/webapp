node {
    def scmVars = checkout([$class: 'GitSCM', branches: [], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'LocalBranch', localBranch: "**"]], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/daboome/webapp']]])
    echo "${scmVars.GIT_LOCAL_BRANCH}"

    stage('Build') {
        withMaven (maven: 'Maven 3.3.9') {
            sh "mvn clean package -DwarName=${scmVars.GIT_LOCAL_BRANCH} && cp target/${scmVars.GIT_LOCAL_BRANCH}.war ./${scmVars.GIT_LOCAL_BRANCH}.war"
        }
    }

    stage('Deploy') {
        if (scmVars.GIT_LOCAL_BRANCH == "ad5" || scmVars.GIT_LOCAL_BRANCH == "ad6") {
            echo "now deploying.... ${scmVars.GIT_LOCAL_BRANCH}"
            sh "curl --upload-file ${scmVars.GIT_LOCAL_BRANCH}.war \"https://jenkins:jenkins@${scmVars.GIT_LOCAL_BRANCH}.kredit24.kz/manager/text/deploy?path=/&udate=true\""
        }
    }
}

