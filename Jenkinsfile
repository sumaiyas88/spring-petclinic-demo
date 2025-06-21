pipeline {
    agent { label 'java17'}
    options {
        timeout(time: 1, unit: 'HOURS')
    }
    triggers {
        pollSCM('*/5 * * * *')
    }
    tools {
        maven ('Maven-3.9.10')
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
    post {
        success {
            // Publish JUnit test results from XML files (Ant glob pattern)
            junit '**/target/surefire-reports/*.xml'
            // Archive test reports or other artifacts
            archiveArtifacts artifacts: '**/target/surefire-reports/*.xml', 
            fingerprint: true
        }
    }
}
