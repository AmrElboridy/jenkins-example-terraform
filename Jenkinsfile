

pipeline {
    agent none

    stages {           
        stage ('prepare') {
            agent any

            steps {
                script{
                def anr = configFileProvider([configFile(fileId: '942b1831-e7b4-449a-a275-fbab352226b3', variable: 'configFile')]) 
                    {
                             def props = readProperties file: "$configFile"
                             def skip_tests = props['amr']
                                            echo "${skip_tests}"

                            }
           
                }}
        }
        stage('Build') {

            agent any

                     steps {
                                echo 'Hello, '

                                sh '''#!/bin/bash

                                    echo "Hello from bash"
                                    echo "Who I'm $SHELL"
                                '''
            }

        }
    }
}
