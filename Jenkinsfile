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
            sh 'mvn clean package'
            }
        }
    }
}
