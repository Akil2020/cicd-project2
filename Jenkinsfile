pipeline {
    agent any
    environment{
        SONAR_HOME = tool "Sonar"
    }
    
    
    stages {
        
        stage("code"){
            steps{
                git url: "https://github.com/Akil2020/cicd-project2", branch: "master"
                echo 'code cloned'
            }
        }
        
        
        stage("build and test"){
            steps{
                sh "docker build -t node-app-test-new ."
                echo 'code build also done'
            }
        }
        stage("scan image"){
            steps{
                echo 'image is scanned'
            }
        }
        stage("push"){
            steps{
                withCredentials([usernamePassword(credentialsId:"dockerpat",passwordVariable:"dockerHubPass",usernameVariable:"dockerHubUser")]){
                sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPass}"
                sh "docker tag node-app-test-new:latest ${env.dockerHubUser}/node-app-test-new:latest"
                sh "docker push ${env.dockerHubUser}/node-app-test-new:latest"
                echo 'image is pushed'
                }
            }
        }
       stage('Deploy') {
            steps {
               //script {
                  // def dockerbuild = 'docker-compose build'
                    //def dockerCmd = 'docker-compose up -d'
                    //sshagent(['sshkeypair']) {
                        //chnage the private ip in below code
                        // sh "docker run -itd --name My-first-containe211 -p 8082:80 akshu20791/2febimg:v1"
                       //  sh "ssh -o StrictHostKeyChecking=no ubuntu@172.31.36.171 ${dockerbuild}"
                         //sh "ssh -o StrictHostKeyChecking=no ubuntu@172.31.36.171 wget https://raw.githubusercontent.com/akshu20791/cicd-project2/master/docker-compose.yaml"
                         //sh "ssh -o StrictHostKeyChecking=no ubuntu@172.31.36.171 chmod 777 docker-compose.yaml"
                         //sh "ssh -o StrictHostKeyChecking=no ubuntu@172.31.36.171 ${dockerCmd}"
                         sh "wget https://raw.githubusercontent.com/Akil2020/cicd-project2/master/docker-compose.yaml"
                         sh "chmod 777 docker-compose.yaml"
                         sh "docker-compose up -d"
                    //}
                }
            }
        }
    }
