pipeline{
agent any         
    stages{
 

        stage('SCM'){
            steps{
                script {
                                    def propertiesFile = configFileProvider([configFile(fileId: '58578323-8c1f-4e10-af01-f5a53496809c', variable: 'MyPropertiesConfig')]) 
                    {
                             def ips = readProperties file: "$MyPropertiesConfig"
                          //   def skip_tests = props['amr']
                        //   echo "${skip_tests}"
                        print "IP = ${ips['IP']}"
                        echo "IP2 = ${ips['IP']}"

                            }
          env.TAG_NAME2=sh(returnStdout: true, script: "git tag --contains | head -1").trim()
        //   echo "$gitTag + from stage"
          echo "$env.TAG_NAME + from env"
          echo "$env.TAG_NAME2 + from stage"
          echo "$env.BRANCH_NAME + from env branch name"
        }
            }
        }
        stage('tag-image'){
            steps{

                script{
                def propertiesFile = configFileProvider([configFile(fileId: '58578323-8c1f-4e10-af01-f5a53496809c', variable: 'MyPropertiesConfig')]) 
                    {
                             def ips = readProperties file: "$MyPropertiesConfig"
                          //   def skip_tests = props['amr']
                        //   echo "${skip_tests}"
                        print "IP = ${ips['IP']}"
                        echo "IP2 = ${ips['IP']}"

                            }
                      }
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
