pipeline {
  agent { label 'Linux'}
  options {
    skipDefaultCheckout(true)
  }
  props = readProperties(file: 'version.properties')
  stages{
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
        echo "Echo "${props["terraform.version"]}" now .."
      }
    }
  }
  post {
    always {
      cleanWs()
    }
  }
}
