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
        
        script {
          def data = [
            "firstname" : "Dicky"
            "lastname" : "Setiadi"
          ] 
          writeJSON(file: "data.json", json: data)
        }
         echo ("Start Test")
         sh("./mvnw test")
         echo ("FInish Test")
           }
        }
        stage("Deploy") {
       steps {
         echo ("Start Deploy")
         echo ("Finish Deploy")
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