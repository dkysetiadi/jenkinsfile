pipeline {
    agent {
        any {
           label "lInux && java11"
        }
    }
    stages {
      stage("Build") {
       steps {
        script {
          for (int i = 0; i < 10; i++)
          echo ("Script ${i}")
        }
         echo ("Start Build")
         sh("./mvnw clean compile test-compile")
         echo ("Finish Build")
           }
        }
        stage("Test") {
       steps {
         echo ("Start BUild")
         sh("./mvnw test")
         echo ("FInish Build")
           }
        }
        stage("Deploy") {
       steps {
         echo ("Hello Deploy1")
         echo ("Hello Deploy2")
         echo ("Hello Deploy3")
           }
        }
    }
    post {
  always {
    echo "I will always say Hello again!"
  }
  success {
    echo "Yay, success!"
  }
  failure {
    echo "oh no, failure"
  }
  cleanup {
    echo "Don't care success or error"
  }
}
}