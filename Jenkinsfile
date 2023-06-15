pipeline {
  agent any
    environment {
      AUTHOR = "Dicky Setiadi"
      EMAIL = "dkysetiadi@gmail.com"
      APP = credentials("dicky")
    }
    options {
                disableConcurrentBuilds()
                timeout(time: 10, unit: 'SECONDS')
            }
    }
    stages {
      stage("Prepare") {
       steps {
          echo("Author ${AUTHOR}")
          echo("Email ${EMAIL}")
          echo("Start Job : ${env.JOB_NAME}")
          echo("Start Build : ${env.BUILD_NUMBER}")
          echo("Branch Name : ${env.BRANCH_NAME}")
          echo("APP USer : ${APP_USR}")
          sh('echo "APP Password : $APP_PSW" > "rahasia.txt"')
           }
        }
        stage("Test") {
       steps {

        script {
          def data = [
            "Name": "Dicky Setiadi"
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
