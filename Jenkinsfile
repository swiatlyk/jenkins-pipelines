pipeline {
  agent {
    node {
      label 'master'
      //customWorkspace '/some/other/path'
    }

  }
  parameters {
        string(name: 'NAME', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')

        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
	}
  stages {
    stage('Checkout_smokefiles') {
      steps {
        timeout(unit: 'SECONDS', time: 5)
        echo 'Checking out SMoke Files'
      }
    }

    stage('Copy_smokefiles') {
      agent any
      steps {
        timeout(unit: 'SECONDS', time: 5)
        echo 'Copy Smoke Files'
      }
    }

    stage('Check_SmokeTests_list_parameters') {
      steps {
        timeout(unit: 'SECONDS', time: 5)
        echo 'SmokeTests.exe --listparameters'
      }
    }

    stage('Checkout_TTCL') {
      steps {
        timeout(unit: 'SECONDS', time: 5)
        echo 'Checking out TTCL'
      }
    }

    stage('Checkout_vcpu_source_NTG7') {
      steps {
        timeout(unit: 'SECONDS', time: 5)
        echo 'Checkout VCPU source'
      }
    }

    stage('Run_vcpuupdate_and_smoketests') {
      parallel {
        stage('Run_vcpuupdate_and_smoketests') {
          steps {
            echo 'Starting flashing and testing'
          }
        }

        stage('run_vcpuupdate') {
          steps {
            echo 'Flashing vcpu'
          }
        }

        stage('run_smoketests') {
          steps {
            echo 'Starting SmokeTests.exe'
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
  // post { 
  //   always { 
  //   echo 'I will always run regardless of the completion status of the Pipeline’s or stage’s run.'
  //   }
  // }
}
