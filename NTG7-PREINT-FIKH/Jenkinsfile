pipeline {
  agent {
    node {
      label 'master'
    }

  }
  stages {
    stage('Stage 1') {
      parallel {
        stage('Checkout Stage 1') {
          steps {
            echo 'Checking out Stage 1'
          }
        }

        stage('Checkout Stage 2') {
          steps {
            echo 'Checkout Stage 2'
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
