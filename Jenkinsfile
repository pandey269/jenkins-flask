/*def createVirtualEnv(String name) {
     sh 'python -m virtualenv venv'
    sh 'venv ${name}'
    echo 'enviroment craeted...'
}
def executeIn(String environment, String script) {
    sh "source ${environment}/bin/activate && " + script
}*/
 
// alternative workaround
//env.VENV_PATH = "${JENKINS_HOME}/.virtualenv/${JOB_NAME}/venv"
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
               
               // createVirtualEnv 'env'
                 sh 'pip install virtualenv'
               //  sh 'virtualenv myproject'
                 sh 'virtualenv .myproject source myproject/venv/bin/activate '
                 //sh 'source virtualenv/bin/activate' 
                // echo 'all done..'
                /* sh 'python -m virtualenv venv'
               sh 'venv env'
              echo 'enviroment craeted...'
             
                sh 'pip install flask'
                //sh 'ls -l'*/
        
    }
}
        stage('Test') {
            steps {
               // executeIn 'env', 'pip install -r requirements.txt'
                //executeIn 'env','python test.py'
          
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



