pipeline {
    agent any
    options {
        skipStagesAfterUnstable()
    }
    stages {
        stage('Build') {
            steps {
                git branch: 'main', url: 'https://github.com/group5five/CYT300.git'
            }
        }
        stage('Test') {
            steps {
                dependencyCheck additionalArguments: '', odcInstallation: 'CYT300'
            }
        }
        stage('Deploy') {
            steps {
                sshPublisher(publishers: [sshPublisherDesc(configName: 'web-server', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '/var/www/', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '**/*.php')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
            }
        }
    }
}
