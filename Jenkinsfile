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
            steps {
            checkout scm
            stash name: "src"
            }
        }

        stage('build'){
            steps {
            unstash "src"
            sh 'pyhon src/script.py'
            }
        }
    }

}