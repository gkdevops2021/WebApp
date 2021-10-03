pipeline {
  agent any
  stages {
    stage('Dev Build') {
      steps {
        echo 'Maven Build Done Locally'
        echo 'Unit tests executed'
      }
    }

    stage('Deploy to QA') {
      steps {
        echo 'Deploy to QA Env...'
        echo 'Notify QA by Email'
      }
    }

    stage('Ui Testing (Smoke)') {
      parallel {
        stage('Ui Testing (Smoke)') {
          steps {
            echo 'Selenium Test (Smoke)'
          }
        }

        stage('API Test') {
          steps {
            echo 'Run API Test'
          }
        }

        stage('Performance Test') {
          steps {
            echo 'Run JMeter Test'
          }
        }

      }
    }

    stage('Deploy to UAT') {
      steps {
        echo 'Deploy to UAT AWS'
        echo 'Notify to users'
      }
    }

    stage('Certify UAT') {
      steps {
        echo 'Manual Approval'
        input(message: 'Do you want to certify', id: '1', ok: 'accept')
      }
    }

    stage('Prod Deploy') {
      steps {
        echo 'Deploy to Prod'
      }
    }

  }
}