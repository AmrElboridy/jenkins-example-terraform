properties = null

def loadProperties() {
    node {
        checkout scm
        properties = readProperties file: 'version.properties'
        echo "Immediate one ${properties.repo}"
    }
}

pipeline {
    agent none

    stages {           
        stage ('prepare') {
            agent any

            steps {
                script {
                    loadProperties()
                    echo "Later one ${properties.version}"
                }
            }
        }
        stage('Build') {

            agent any

            steps {
                echo properties.version
            }

        }
    }
}
