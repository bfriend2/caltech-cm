pipeline {
  agent any
  stages {
    stage('Git checkout') {
      steps {
        git branch: 'master', url: 'https://github.com/bfriend2/caltech-cm.git'
          }
        }
    stage('Setup Ansible') {
      steps {
        script {
                
          def tfHome = tool name: 'Ansible'
          env.PATH = "${tfHome}:${env.PATH}"
          sh 'ansible --version'
        }
      }
    }
    stage('Deploy Ansible with Jenkins') {
      steps {
        sh "ansible-playbook webserver.yaml --user jenkins --key-file ~/.ssh/student.pem" 
      }
    }
  }
}
