/* groovylint-disable-next-line CompileStatic */
pipeline {
    agent any
    environment {
        IMAGE_NAME = 'ais-website'
        IMAGE_TAG = 'v1'
        PREFIX_IMAGE = 'abodojustin'

        DOCKERHUB_CREDENTIALS = credentials('DOCKERHUB_KEY')
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
        
        stage('Test Acceptance') {
            steps {
                script {
                    sh '''
                        docker run -d --name $IMAGE_NAME -p 80:80 $PREFIX_IMAGE/$IMAGE_NAME:$IMAGE_TAG
                        sleep 20
                    '''
                }
            }
        }
        
        stage('Test Conteneur') {
            steps {
                script {
                    sh '''
                        curl http://15.188.87.165 | grep -q "Dimension"
                    '''
                }
            }
        }
        
        stage('Delete Conteneur') {
            steps {
                script {
                    sh '''
                        docker stop $IMAGE_NAME
                        docker rm $IMAGE_NAME
                    '''
                }
            }
        }
    }
}