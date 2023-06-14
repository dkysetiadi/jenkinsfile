pipeline {
    agent {
        any {
            label "lInux && java11"
        }
    }
    
    stages {
        stage('Hello') {
            steps {
                echo ('Hello Pipeline')
            }
        }
    }
}