pipeline {
  agent {
    node {
      label 'master'
    }

  }
  stages {
    stage('Stage 1 STAR2') {
      parallel {
        stage('Checkout Smoke Files') {
          steps {
            echo 'Checking out SMokefiles repo'
          }
        }

        stage('Checkout vcpu repo') {
          steps {
            echo 'Checkout vcpu repo'
          }
        }

      }
    }

    stage('Start tests STAR2') {
      agent any
      steps {
        echo 'Starting testin'
      }
    }

  }
}