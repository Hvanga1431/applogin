pipeline {
    agent {label "H555"}

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

        stage("deploy"){
            steps{
                sh "ansible-playbook -i myhosts java.yml"
            }
        }
        
    }
} 
