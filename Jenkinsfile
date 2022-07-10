pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                sh '''
                    yarn install
                    docker tag $DOCKER_REGISTRY/$DOCKER_IMAGE_NAME:$__BUILD_VERSION $DOCKER_REGISTRY/$DOCKER_IMAGE_NAME:latest
                    ./cherry_exec
                '''
            }
        }
        stage('test') {
            steps {
                sh '''
                    jq -r .name package.json
                '''
        }
    }
}
