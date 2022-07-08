pipeline {
  // agent any
  
    agent {
        docker { 
            image 'sravangcpdocker/terraform:7'
            args '-u root:root'
        }
    }
    /*
    environment {
   ANSIBLE_PRIVATE_KEY=credentials('ansible-key') 
  } */
    stages {
        stage('ansible') {
            steps {
                sh "ansible --version"
                sh "terraform --version"
                //sh "rm -rf *"
                sh "git clone https://github.com/sravan-github/ansible-test.git"
                sh 'ls -l && whoami'
                //sh "cd ansible-test && chmod 777 play.yml && chmod 600 key && ls -ltr"
                //sh 'cd ansible-test && ansible-galaxy collection install -r requirements.yml'
                sh 'cd ansible-test && sudo ansible-playbook -i hosts --private-key=$privatekey play.yml'
                //sh 'cd ansible-test && ansible-playbook -i hosts --private-key=key play.yml'
            }
        }
    }
    post {
        always {
        	cleanWs deleteDirs: true
        }
    }
}
