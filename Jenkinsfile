pipeline {
    agent any

    stages {
        stage('pull project') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/develop']], extensions: [], userRemoteConfigs: [[credentialsId: '36bff5e1-b3cc-4e9a-8144-c71323d20b1f', url: 'git@github.com:nanfanglr/android-jenkins-sample.git']]])
            }
        }
        stage('build project') {
            steps {
                sh './gradlew clean :app:assembleCertDebug'
            }
        }
        stage('publish project'){
            steps{
                archiveArtifacts artifacts: 'app/build/outputs/apk/cert/debug/*.apk', followSymlinks: false
            }

        }
    }
}
