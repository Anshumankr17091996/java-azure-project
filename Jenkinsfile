pipeline {
    agent any

    stages {
        stage('git clone') {
            steps {
              git 'https://github.com/Kumarbgm16/java-azure-project.git'
            }
        }
        stage('build') {
            steps {
              sh "mvn clean package"
            }
        }
        stage('Build Docker OWN image') {
            steps {
                sh "sudo docker build -t saidevops16/javasantab51:latest ."

            }
        }
    
      stage('docker push ') {
     steps {
     withCredentials([string(credentialsId: 'DOCKER_HUB_PWD', variable: 'DOCKER_HUB_PASS_CODE')])  {
    // some block
        sh "sudo docker login -u saidevops16 -p $DOCKER_HUB_PASS_CODE"
        }
        sh "sudo docker push saidevops16/javasantab51:latest"
        }
        }  
          stage('Deploy to docker Env') {
    steps {
         sh "sudo docker rm -f app3" 
    sh "sudo docker run -itd --name app3 -p 9000:8080 saidevops16/javasantab51:latest" 

}
}
    }
}
