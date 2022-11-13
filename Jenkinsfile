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
       echo "Echo "${props["terraform.version"]}" now .."
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
