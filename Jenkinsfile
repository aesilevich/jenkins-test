def SWIFT_VERSION = '5.9'

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
                    git url: 'git@github.com:FLORG1/ScadeSwift.git', '${env.BRANCH_NAME}'
                }
                sh 'echo VERSION $SWIFT_VERSION'
            }
        }
    }
}
