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

        stage('second'){
            steps {
            echo "Second stage"
            }
        }
    }

}