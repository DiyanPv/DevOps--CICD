node {
    stage('Git checkout') {
        git 'https://github.com/DiyanPv/DevOps--CICD.git'
    }

    stage('sending Dockerfile to Ansible server via SSH') {
        sshagent(['ansible-project']) {
            //connect to ansible server
            sh 'ssh -o StrictHostKeyChecking=no -l ubuntu@54.84.167.89'
            //once build is done, copy files from jenkins to ansible server
            sh 'scp /var/lib/jenkins/workspace/pipeline-demo/* ubuntu@54.84.167.89:/home/ubuntu/'
        }
    }

    stage(
        sshagent(['ansible-project']) {
            //connect to Ansible server and go to /home/ubuntu/ directory
            sh 'ssh -o StrictHostKeyChecking=no -l ubuntu@54.84.167.89 "cd /home/ubuntu/"'
            //build image with docker
            sh 'ssh -o StrictHostKeyChecking=no ubuntu@54.84.167.89 "docker image build -t $JOB_NAME:v1.$BUILD_ID ."'
        }
    )
}
