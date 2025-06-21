pipeline {
    agent { label 'java17'}
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
        always {
            // Publish JUnit test results from XML files (Ant glob pattern)
            jUnit '**/target/surefire-reports/*.xml'
            // Archive test reports or other artifacts
            archiveArtifacts artifacts: '**/target/surefire-reports/*.xml', 
            fingerprint: true
        }
    }
}
