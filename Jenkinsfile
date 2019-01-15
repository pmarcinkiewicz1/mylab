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
            }
        }

        stage('build on docker'){
            agent {
                docker  'centos'
            }
            steps{
            unstash "src"
            sh 'python src/script.py'
            }
        }
    }

}