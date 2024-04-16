/* groovylint-disable-next-line CompileStatic */
pipeline {
    agent any
    environment {
        IMAGE_NAME = 'ais-website'
        IMAGE_TAG = 'v1'
        PREFIX_IMAGE = 'abodojustin'
    }

    stages {
        stage('Clone') {
            steps {
                script {
                    '''
                        git branch: 'main', url : 'https://github.com/abodojustin/ais-1123-pratice.git'
                    '''
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    sh '''
                        docker build -t $PREFIX_IMAGE/$IMAGE_NAME:$IMAGE_TAG .
                    '''
                }
            }
        }
    }
}