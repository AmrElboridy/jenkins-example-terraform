pipeline {
  agent { label 'Linux'}
  options {
    skipDefaultCheckout(true)
  }
  stages{
    stage('LOAD PROPERTIES FILES') {
       steps {
        script {
        def props = readProperties file: 'version.properties'
        println("##############")
        println("${props["terraform.version"]}")
        } 
        }
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
