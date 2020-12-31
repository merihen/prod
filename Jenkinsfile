def commit_id
def container_name="containerProd"
pipeline {
    agent any

    stages {
        stage('Preparation') {
            steps {
                checkout scm
            }
        }
        stage('Deploy to QA') {
            steps {
                echo'Deploying'
                //sh "docker stop  ${container_name}"
                //sh "docker rm  ${container_name}"
                sh "docker run -p 8095:8080 -d --name ${container_name} merihen/devopsprod:1.0"
                echo 'deployment complete'
            }
        }
        stage('Push to the docker hub'){
            steps {
                echo 'Connect to docker hub'
                sh 'docker login -u merihen -p SIWARSIWAR '
                sh "docker tag merihen/devopsprod:1.0 merihen/devopsprod:v1.0"
                sh 'docker push merihen/devopsprod:v1.0'
            }
        }
    }
}
