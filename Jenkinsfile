pipeline {
    agent any
    stages {
        stage('Compile') {
            steps {
                sh 'mvn clean package -DskipTests=true'
            }
        }
        stage('Unit Tests') {
            steps {
                sh 'mvn test'
            }
        }
         stage('Integration Tests') {
            steps {
                sh 'mvn verify'
            }
        }
    }
    post {
        always {
            junit 'target/surefire-reports/TEST-*.xml'
        }
        failure {
            mail to: 'kiwaczki@gmail.com', subject: 'The Pipeline failed :(', body:'The Pipeline failed :('
        }
    }
}
