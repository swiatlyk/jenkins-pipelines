//initiating groovy script, name can be any
def gv

//defining whole pipeline
pipeline {
  agent {
    node {
      label 'master'
      //customWorkspace '/some/other/path'
    }
  }
  //adding/editing environment variables
  environment {
    NEW_VERSION = '1.20.0'
}
  //adding/editing environment variables
  parameters {
        //string(name: 'NAME', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

        //text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

        booleanParam(name: 'RSU present', defaultValue: true, description: 'Is RSU present on bench')

        choice(name: 'Version_to_build', choices: ["1.20", "1.30", "1.40"], description: 'Pick version')

        //password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
	}
  stages {
    //Mandatory stage to load script
    stage("init") {
      steps {
        script {
          gv = load "script.groovy"
        }
      }
    }
    stage('Checkout_app repository') {
      steps {
        //timeout(unit: 'SECONDS', time: 5)
        // echo "Checking out app version ${NEW_VERSION}"
        echo "Checking out app version ${env.Version_to_build}"
        echo "====++++Try to load groovy script++++===="
        //using script by method in script
        script {
          gv.buildApp()
        }
      }
    }

    stage('Run_deploy application') {
      parallel {
        stage('Deploying application') {
          steps {
            echo 'Starting deploying app'
            script {
              gv.deployApp()
            }
          }
        }

        stage('Copy files') {
          steps {
            echo 'Copying files of app'
            script {
              gv.copyFilesToProd()
            }
          }
        }

      }
    }

    stage('Emails') {
      steps {
        echo 'Send letters'
      }
    }

  }
  post { 
    always { 
    echo 'I will always run regardless of the completion status of the Pipeline’s or stage’s run.'
    }
    failure {
      echo 'I will when job will failure'
    }
    success {
      echo 'I will run when job is success'
    }
  }
}
