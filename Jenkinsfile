pipeline{
        agent any
        stages{
            stage('Install dependecies'){
               steps{
<<<<<<< HEAD
                  sh '''
curl https://get.docker.com | sudo bash
                  sudo curl -L https://github.com/docker/compose/releases/download/1.27.3/docker-compose-$(uname -s)-$(uname -m) -o /usr/local/bin/docker-compose
                  sudo chmod +x /usr/local/bin/docker-compose
                  '''
=======
                  sh "curl https://get.docker.com | sudo bash"
                  sh "sudo curl -L https://github.com/docker/compose/releases/download/1.27.3/docker-compose-$(uname -s)-$(uname -m)" && "-o /usr/local/bin/docker-compose"
                  sh "sudo chmod +x /usr/local/bin/docker-compose"
>>>>>>> e4867ea1a43df2d10353f93f9d00b680f11fc6b3
               }
            }
            stage('Build Image'){
                steps{
                    sh "sudo docker build -t chaperoo ."
                }
            }
            stage('Clean'){
                steps{
                    sh label: '', script: '''if [ "$(sudo docker ps -aq -f name=chaptodo)" ]; then
                        sudo docker rm -f chaptodo
                    fi'''
                    }
                }
            stage('Run Container'){
                steps{
                    sh "sudo docker-compose up -d"
                    sh "sudo docker run -d --name chaptodo -p 80:80 chaperoo"
                }
            }
        }    
}
