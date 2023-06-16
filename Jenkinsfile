pipeline {
  agent any
    environment {
      AUTHOR = "Dicky Setiadi"
      EMAIL = "dkysetiadi@gmail.com"
      APP = credentials("dicky")
    }

    triggers {
        cron('*/5 * * * *')
    }

    parameters {
        string(name: 'NAME', defaultValue: 'Mr Dicky', description: 'What is your name?')

        text(name: 'DESCRIPTION', defaultValue: 'Description', description: 'Tell me about your description')

        booleanParam(name: 'DEPLOY', defaultValue: false, description: 'Need to Deploy')

        choice(name: 'SOSIAL_MEDIA', choices: ['Instagram', 'Facebook', 'Twittwr'], description: 'Pick something')

        password(name: 'PASSWORD', defaultValue: '', description: 'Enter a password')
    }

    options {
        disableConcurrentBuilds()
        timeout(time: 3, unit: 'MINUTES') 
    }

    stages {

      stage('Parameters') {
            steps {
                echo "Hello ${params.NAME}"

                echo "Description: ${params.DESCRIPTION}"

                echo "Deploy: ${params.DEPLOY}"

                echo "Sosial Media: ${params.SOSIAL_MEDIA}"

                echo "Password: ${params.PASSWORD}"
            }
        }

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
        input {
                message "Can we deploy?"
                ok "Yes, we should."
                submitter "Dicky"
                parameters {
                    string(name: 'PERSON', defaultValue: 'Dicky', description: 'We will deploy to?')
                }
            }
       steps {
         echo "Hello, ${PERSON}, nice to meet you."
           }
        }
        stage('Release') {
            when {
                expression  {
                  return params.DEPLOY
                }
            }
            steps {
                echo ('Deploying')
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