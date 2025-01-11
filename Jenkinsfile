/*Anshumankr17091996/java-azure-project*/
pipeline {
    agent any

    stages {
        stage('git clone') {
            steps {
              git 'https://github.com/Anshumankr17091996/java-azure-project.git'
            }
        }
        stage('build') {
            steps {
              sh "mvn clean package"
            }
        }
        stage('Build Docker OWN image') {
            steps {
                sh "sudo docker build -t anshumandocker179/javaAzureb51:v1 ."

            }
        }
    
      stage('docker push ') {
     steps {
     withCredentials([string(credentialsId: 'DOCKER_HUB_PWD', variable: 'DOCKER_HUB_PASS_CODE')])  {
    // some block
        sh "sudo docker login -u anshumandocker179 -p $DOCKER_HUB_PASS_CODE"
        }
        sh "sudo docker push anshumandocker179/javaAzureb51:v1"
        }
        }  
          stage('Deploy to docker Env') {
    steps {
         sh "sudo docker rm -f app3" 
    sh "sudo docker run -itd --name app3 -p 9000:8080 anshumandocker179/javaAzureb51:v1" 

}
}
    }
}
