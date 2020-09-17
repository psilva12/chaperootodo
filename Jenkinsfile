pipeline{
        agent any
        stages{
            stage('Install dependecies'){
               steps{
                  sh '''
curl https://get.docker.com | sudo bash
                  sudo curl -L https://github.com/docker/compose/releases/download/1.27.3/docker-compose-$(uname -s)-$(uname -m) -o /usr/local/bin/docker-compose
                  sudo chmod +x /usr/local/bin/docker-compose
                  '''
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
