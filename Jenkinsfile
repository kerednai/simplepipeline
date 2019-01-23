pipeline {
    agent any
    stages {
        stage("foo") {
            steps {
                script {
                    env.FILENAME = readFile 'output.txt'
                }
                echo "${env.FILENAME}"
            }
        }
    }
}
