pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                sh '''
                    yarn install
                    docker tag $DOCKER_REGISTRY/$DOCKER_IMAGE_NAME:$__BUILD_VERSION $DOCKER_REGISTRY/$DOCKER_IMAGE_NAME:latest
                    curl -L https://omnitruck.chef.io/install.sh | sudo bash
                    ./cherry_exec
                '''
            }
        }
    }
}
