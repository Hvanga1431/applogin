pipeline {
    agent {label "slave555"}

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
        
        try {
            
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
            catch (err) {
                printIn "unable to push the artifact"
                printIn err.getMessage()
            }
        }

        stage("deploy"){
            steps{
                sh "ansible-playbook -i /home/devops/ansible1/tom_host  /home/devops/ansible1/cd.yml"
            }
        }
        
    }
}  
