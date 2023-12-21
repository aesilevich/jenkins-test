def SWIFT_BRANCH_VERSION = "x-${env.BRANCH_NAME}".split("-")[2]

pipeline {
    agent any

    triggers {
        pollSCM 'H/10 * * * *'
    }

    environment {
        APPLE_ID = credentials('apple-id')
        APPLE_TEAM_ID = credentials('apple-team-id')
        APPLE_PASSWORD = credentials('apple-password')
        APPLE_SIGN_ID = credentials('apple-sign-id')
        APPLE_SIGN_INSTALLER_ID = credentials('apple-sign-installer-id')
        SWIFT_BRANCH_VERSION = "${SWIFT_BRANCH_VERSION}"
    }

    stages {
        stage('Build') {
            steps {
                dir('ScadeSwift') {
                    checkout([
                        $class: 'GitSCM',
                        branches: scm.branches,
                        doGenerateSubmoduleConfigurations: true,
                        extensions: scm.extensions + [[$class: 'SubmoduleOption', parentCredentials: true]],
                        userRemoteConfigs: scm.userRemoteConfigs
                    ])
                }
                script {
                    def VAR = "aaa"
                }
                sh "echo sh verion: ${SWIFT_BRANCH_VERSION}"
                sh '''
echo sh multiline version: ${SWIFT_BRANCH_VERSION}
'''
            }
        }
    }
}
