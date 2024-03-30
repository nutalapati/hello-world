pipeline {
    agent any
    stages {
        stage("SCM Code Pull") {
            steps {
                git branch: 'master',                        
                    url: 'https://github.com/nutalapati/hello-world.git'                
                }
            }  
                   
        stage("Build") {
            steps {
                sh "mvn clean"          
                               
            }
        }
        
        stage("copy files") {
            steps {
                ansiblePlaybook become: true,
                    credentialsId: '8bdbf9c4-93b2-4d0f-a32e-364a1ba48d03',
                    disableHostKeyChecking: true, 
                    installation: 'ansible', 
                    inventory: 'hello-world/inventories/dev.inv', 
                    limit: 'jenkinsServer', 
                    playbook: 'hello-world/appDeploy.yml',
                    tags: 'copy_files'
            }
        }
    }    
}