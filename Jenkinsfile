pipeline {
    agent any

    environment{
        CONTAINER_NAME = "nestjs-app"
        IMAGE_NAME = "nesths-image"
        EMAIL= "shaikshaida630gmail.com"
        port = "3000"
    }

    stages {
        stage ('Clone Repo'){
            steps{
                git branch: 'main', url: 'https://github.com/shaikshaida630/CI-CD-Pipeline-Using-Jenkins-Github-Webhook-Ubuntu-AWS-EC2-Docker.git'

            } 

        }
    stage('Build Docket Image'){
        steps{
            sh 'docker build -t $IMAGE_NAME'
        }
    stage('Stop & Remove Previous Container'){
        steps{
            sh '''
            docker stop $CONTAINER_NAME ||
            true
            docker rm $CONTAINER_NAME ||true
            '''
        }
    }

    stage('Docker Container Run'){
        steps{
            sh '''
            docker run -d -p ${PORT}"${PORT}
            --name $CONTAINER_NAME  $IMAGE_NAME
            '''
        }
    }
    stage('Send Email Notification'){
        steps{
            emailtext(
                subject: "NestJS App Depolyed
                Successfully on EC2!"
                body: "Your Nest JS app is Deployed!
                http://16.170.220.222:${PORT}/"
                to: "${EMAIL}"
            )
        }
    }

    }
}