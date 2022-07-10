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
                    python3 /var/lib/jenkins/workspace/mandalore/test.py
                    aws ecr get-login --no-include-email --region=us-east-1 --registry-ids=${AWS_ACCOUNT}
                '''
            }
        }
    }
}
