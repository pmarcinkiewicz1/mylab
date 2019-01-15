library "lib"

pipeline {
agent none

    stages{

        stage('first'){
            steps {
            echo "First stage"
            trySomething("test")
            }
        }

        stage('second'){
            steps {
            echo "Second stage"
            }
        }
    }

}