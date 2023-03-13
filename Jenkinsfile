pipeline{
agent any  
    stages{
        stage('tag-image'){
            steps{
                    def propertiesFile = configFileProvider([configFile(fileId: '58578323-8c1f-4e10-af01-f5a53496809c', variable: 'MyPropertiesConfig')]) {
                        def ips = readProperties file: "$MyPropertiesConfig"
                        print "IP = ${ips['IP']}"
                    }
                sh 'sudo docker build --build-arg TAG_NAME=$TAG_NAME --build-arg BRANCH_NAME=$BRANCH_NAME -t nginx:$TAG_NAME .'
            }
        }

    }
}
