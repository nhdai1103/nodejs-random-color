pipeline {
    agent any
    stages {
        // stage('Checkout') {
        //     steps {
        //         git 'https://github.com/nhdai1103/nodejs-random-color.git'
        //     }
        // }

        stage('Build') {
            steps {
                sh 'docker build -t nodejs-random-color:${BUILD_ID} .'
            }
        }
        stage('Upload image to ECR') {
            steps {
                sh 'aws ecr get-login-password --region ap-southeast-1 | docker login --username AWS --password-stdin 115372766015.dkr.ecr.ap-southeast-1.amazonaws.com'
                sh 'docker tag nodejs-random-color:${BUILD_ID} 115372766015.dkr.ecr.ap-southeast-1.amazonaws.com/nodejs-random-color:${BUILD_ID}'
                sh 'docker push 115372766015.dkr.ecr.ap-southeast-1.amazonaws.com/nodejs-random-color:${BUILD_ID}'
            }
        }
    }
}
