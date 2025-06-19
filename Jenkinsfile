pipeline {
    agent any
    tools {
        maven ('Maven 3.9.10')
    }
    stages {
        stage ('SCM') {
            steps {
                git url: 'https://github.com/sumaiyas88/spring-petclinic-demo.git',
                    branch: 'main'
            }
        }
        stage ('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
    }
}