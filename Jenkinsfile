

pipeline {
    agent none

    stages {           
        stage ('prepare') {
            agent any

            steps {
                script{
                def anr = configFileProvider([configFile(fileId: 'f15e9453-75b4-49da-8fc4-18ebb38e6e07', variable: 'configFile')]) 
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
                    echo "z"
            }

        }
    }
}
