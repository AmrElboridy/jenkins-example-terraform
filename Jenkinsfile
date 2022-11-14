

pipeline {
    agent none

    stages {           
        stage ('prepare') {
            agent any

            steps {
                def properties = configFileProvider([configFile(fileId: '942b1831-e7b4-449a-a275-fbab352226b3')]) 
                 echo "Later one" properties.vars
           
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
