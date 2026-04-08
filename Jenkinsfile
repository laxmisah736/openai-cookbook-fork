pipeline {
    agent any

    environment {
        IMAGE_NAME = "openai-cookbook"
        CONTAINER_NAME = "openai-cookbook"
    }

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker rm -f $CONTAINER_NAME || true'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker run -d \
                -p 8888:8888 \
                --name $CONTAINER_NAME \
                -e OPENAI_API_KEY=your_api_key_here \
                $IMAGE_NAME
                '''
            }
        }
    }
}
