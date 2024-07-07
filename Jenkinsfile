node {
    stage('Git checkout') {
        git 'https://github.com/DiyanPv/DevOps--CICD.git'
    }

    stage("sending Dockerfile to Ansible server via SSH"){
        sshagent(['ansible-project']) {
              sh 'ssh -o StrictHostKeyChecking=no -l ubuntu@54.84.167.89'
}
    }
}
