pipeline {
  agent { label 'Linux'}
  options {
    skipDefaultCheckout(true)
  }
  stages{
    stage('LOAD PROPERTIES FILES') {
        def props = readProperties file: 'version.properties'
        echo "Echo "${props["terraform.version"]}" now .."
    }
    stage('clean workspace') {
      steps {
        cleanWs()
      }
    }
    stage('checkout') {
      steps {
        checkout scm
      }
    }
    stage('terraform') {
      steps {
        sh './terraformw apply -auto-approve -no-color'
      }
    }
  }
  post {
    always {
      cleanWs()
    }
  }
}
