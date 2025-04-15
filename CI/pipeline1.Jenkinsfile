pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Trigger job2'){
            steps {
                echo 'Call job2 ==========================================='
                build job: 'job2',
                    wait: true
            }
        }
    }
}
