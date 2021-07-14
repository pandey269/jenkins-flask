pipeline {
    agent any

    stages('git') {
        stage('clean workspace') {
            steps {
                cleanWs()
                echo 'cleaning workspace..'
            }
        }
        stage('clone repo') {
            steps {
                git branch: 'main', url: 'https://github.com/pandey269/jenkins-first.git'
                echo 'cloning..'
            }
        }
        stage('build') {
    steps {
        sh 'ls -l'
         sh 'python3 mypython.py'
    }
}
    }
    
   
}
