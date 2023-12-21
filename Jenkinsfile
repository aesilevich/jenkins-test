def SWIFT_VERSION = "5.9"
def X_BRANCH_NAME = "x-${env.BRANCH_NAME}"

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
        SWIFT_VERSION = '5.9'
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
                sh 'echo VERSION: $SWIFT_VERSION, BRANCH: ${X_BRANCH_NAME}'
                echo "Echo branch: ${X_BRANCH_NAME}"
            }
        }
    }
}
