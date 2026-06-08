pipeline{
    agent any
    tools{
        maven 'maven'
    }
    stages{
        stage('code'){
            steps{
                git 'https://github.com/Ritesh-Prasad/full-micro-service-project.git'
            }
        }
        stage('Build'){
            steps{
                sh 'mvn compile'
            }
        }
        stage('Test'){
            steps{
                sh 'mvn test'
            }
        }
        stage('Artifacts'){
            steps{
                sh 'mvn package'
            }
        }
        stage('build image'){
            steps{
                sh 'docker build -t netflix2 .'
            }
        }
        stage('Tag & Push'){
            steps{
                withDockerRegistry(credentialsId: 'dockerhub', url: 'https://index.docker.io/v1/') {
                    sh 'docker tag netflix2 riteshprasad07/netflixproject02:v1'
                    sh 'docker push riteshprasad07/netflixproject02:v1'
                }
            }
        }
    }
}
