pipeline {
    agent any

    stages{
        stage("git clone"){
            steps {
                git 'https://github.com/Hvanga1431/applogin.git'
            }
        }

        stage("Build"){
            steps{
                sh "mvn clean install"
            }
        }

        stage("test"){
            steps{
                echo "this is for testing"
            }
        }

        stage("publish"){

            steps{
                rtUpload (
                    serverId: "myjfrog",
                    spec: '''{
                        "files":[
                            {
                                "pattern": "target/*.war",
                                "target": "firstrepo"
                            }
                        ]
                    }''',
                )
            }
        }
        
    }
}
