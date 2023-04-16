pipeline {
    agent any
    stages {
        stage('Build Jar') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }
        stage('Build Image') {
            steps {
                sh "docker build -t='singh24honey/selenium-docker' ."
            }
        }
        stage('Push Image') {
            steps {
                withCredential([usernamePassword(credentialsId: 'dockerhub', passwordVariable: 'pass', usernameVariable: 'user')])

                    sh "docker login --username=${user} --password=${pass}"
                    sh "docker push singh24honey/selenium-docker:latest"
			        }
                }
            }
        }
    