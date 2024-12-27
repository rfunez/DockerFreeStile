pipeline {
    parameters {
      string 'version'
    }
    agent{
        dockerfile {
            filename 'Dockerfile'
            tag ${params.version}
        }  
    }
    stages{
        stage('Checking image'){
            steps{
                sh 'docker image ls | grep ubuntu | grep ${params.version}'
            }
        }
        stage('Running container'){
            steps{
                sh 'docker run --name=ubuntu-${params.version} --hostname=ubuntu -itd ubuntu:${params.version} ubuntu-{params.version}'
            }
        }
        stage('Check container'){
            steps{
                sh 'docker ps | grep ubuntu'
            }
        }
    }
}
