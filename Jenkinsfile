pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git branch: 'main', url : 'https://github.com/abodojustin/ais-1123-pratice.git'
                sh 'ls -ll'
            }
        }
    }
}