pipeline {
    agent any

    stages('git') {
        stage('clean workspace') {
            steps {
                cleanWs()
                echo 'cleaning workspace..'
            }
        }
        stage('check out scm') {
            steps {
              checkout([$class: 'GitSCM', branches: [[name: 'main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/pandey269/jenkins-flask.git']]])
                echo 'checkout scm'
            }
        }
        stage('build') {
    steps {
        sh 'ls -l'
         sh 'python3 app.py'
    }
}
        stage('Test') {
            steps {
                echo 'Testing...'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
            }
        }
    }
    
   
}
