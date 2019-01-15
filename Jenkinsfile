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
            sh 'pyhon src/script.py'
            }
        }
    }

}