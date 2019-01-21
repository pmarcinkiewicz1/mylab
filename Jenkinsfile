library "lib"

pipeline {
agent none

    stages{

        stage('first'){
            steps {
            echo "First stage"
            trySomething(env.VAR)
            }
        }

        stage('checkout'){
            agent {
                label 'master'
            }

            steps {
            checkout scm
            stash name: "src"
            }
        }

        stage('build'){
             agent {
                label 'master'
            }

            steps {
            unstash "src"
            sh 'python src/script.py'
            sh 'hostname'
            }
        }

        stage('build on docker'){
            agent {
                docker  'centos'
            }
            steps{
            unstash "src"
            sh 'python src/script.py'
            sh 'hostname'
            }
        }
        stage('test'){
             agent {
                label 'master'
            }
            steps {
            script {
              def new_path = checkPath(env.TEST_PATH)
              echo new_path

            if (isTriggered()){
                echo "Variable is set"
            }
            }
        }
        }

        stage('scp'){
             agent {
                label 'master'
            }

            steps {
                runShell(env.ARG1,env.ARG2)
            }
        }
    }

}