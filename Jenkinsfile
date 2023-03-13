pipeline{
agent any 
   environment {
     BRANCH_NAME = "${GIT_BRANCH.split("/")[1]}"
     TAG_NAME = sh(returnStdout: true, script: "git describe --tags --abbrev=0").trim()
     IP = "$env.devserver"


  }
        
    stages{
 
        stage('tag-image'){
            steps{
                    configFileProvider([configFile(fileId: '58578323-8c1f-4e10-af01-f5a53496809c', variable: 'MyPropertiesConfig')]) {
                    print "IP = ${IP}"
                    }
                sh 'sudo docker build --build-arg TAG_NAME=$TAG_NAME --build-arg BRANCH_NAME=$BRANCH_NAME -t nginx:$TAG_NAME .'
            }
        }
          stage('test-env-vars'){
            steps{
                script{
                     def props = readProperties file: 'extravars.properties' 
                    env.devserver = props.devserver
                }
                echo "The server is $devserver"
                echo env.$IP
            }
        }
    }
}
