def SWIFT_BRANCH_VERSION = "${env.BRANCH_NAME}".split("-")[1]
def SWIFT_PACKAGE_VERSION = "5.9.2"
def SWIFT_PACKAGE_VERSION_COMPONENTS = SWIFT_PACKAGE_VERSION.split(".")
def SWIFT_PACKAGE_VERSION_BRANCH = SWIFT_PACKAGE_VERSION_COMPONENTS[0] + SWIFT_PACKAGE_VERSION_COMPONENTS[1]

pipeline {
    agent any

    options {
        skipDefaultCheckout()
    }

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
        SWIFT_PACKAGE_VERSION_BRANCH = "${SWIFT_PACKAGE_VERSION_BRANCH}"
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
                sh "echo sh SWIFT_PACKAGE_VERSION_BRANCH: ${SWIFT_PACKAGE_VERSION_BRANCH}"
            }
        }
    }
}
