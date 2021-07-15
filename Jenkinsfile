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
                sh 'python -m virtualenv venv'
                createVirtualEnv 'env'
             
                sh 'pip install flask'
                sh 'ls -l'
        
    }
}
        stage('Test') {
            steps {
                executeIn 'env', 'pip install -r requirements.txt'
                executeIn 'env','python test.py'
               """ sh 'python test.py'"""
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
def createVirtualEnv(String name) {
    sh "virtualenv ${name}"
}
 
def executeIn(String environment, String script) {
    sh "source ${environment}/bin/activate && " + script
}
 
// alternative workaround
env.VENV_PATH = "${JENKINS_HOME}/.virtualenv/${JOB_NAME}/venv"

def virtualEnv(String rebuild){
    withEnv(["PATH+VEX=~/.local/bin"]){
        if(rebuild == "true") {
            sh "rm -rf ${env.VENV_PATH}"
            sh "echo 'rebuild is true'"
        }
        sh returnStatus: true, script: "virtualenv ${env.VENV_PATH}"
    }
}

def runCmd(String pyCmd){
    withEnv(["PATH+VEX=~/.local/bin"]){
        sh returnStatus: true, script: "vex --path=${env.VENV_PATH} ${pyCmd}"
    }
}
