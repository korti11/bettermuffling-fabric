pipeline {
    agent {
        docker {
            image 'gradle:jdk8'
            args '-v dependencies:/home/gradle/.gradle'
        }
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh './gradlew clean build --refresh-dependencies'
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'build/libs/**/*.jar', fingerprint: true
        }
    }

}