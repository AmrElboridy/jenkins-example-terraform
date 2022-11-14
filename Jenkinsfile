

pipeline {
    agent none

    stages {           
        stage ('prepare') {
            agent any

            steps {
                script{
                def anr = configFileProvider([configFile(fileId: '942b1831-e7b4-449a-a275-fbab352226b3')]) 
                    {def amro = anr.amr}
                    echo "${amro}"
           
                }}
        }
        stage('Build') {

            agent any

            steps {
                echo anr.aya
            }

        }
    }
}
