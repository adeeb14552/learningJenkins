pipeline {
    agent { 
        node {
            label 'docker-python-agent'
            }
      }
    triggers {
    	pollSCM '* * * * *'
    }  
    stages {
        stage('Build') {
            steps {
                echo "Building.."
                sh '''
                cd myapp
                python3 -m venv env
                source env/bin/activate
                pip install -r requirements.txt
                '''
            }
        }
        stage('Test') {
            steps {
                echo "Testing.."
                sh '''
                cd myapp
                source env/bin/activate
                python3 hello.py
                python3 hello.py --name=Adeeb
                '''
            }
        }
        stage('Deliver') {
            steps {
                echo 'Deliver..'
                sh '''
                echo "doing delivery stuff..."
                '''
            }
        }
    }
}
