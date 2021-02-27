pipeline {
  agent {
    node {
      label 'master'
    }

  }
  parameters {
        string(name: 'NAME', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
	      choice(name: 'CHOICE 2', choices: ['One', 'Two', 'Three'], description: 'Pick something')

        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
	}
  stages {
    stage('Checkout_smokefiles') {
      steps {
        echo 'Checking out SMoke Files'
      }
    }

    stage('Copy_smokefiles') {
      agent any
      steps {
        echo 'Copy Smoke Files'
      }
    }

    stage('Check_SmokeTests_list_parameters') {
      steps {
        echo 'SmokeTests.exe --listparameters'
      }
    }

    stage('Checkout_TTCL') {
      steps {
        echo 'Checking out TTCL'
      }
    }

    stage('Checkout_vcpu_source_NTG7') {
      steps {
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
}
