pipeline {
    agent any
    
    stages {
        stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                '''
            }
        }
        stage ('Compile Stage') {
            steps {
                withMaven() {
                    sh 'mvn --version'
                    sh 'mvn clean compile'
                }
            }
       
        stage('Results') {
            steps {
                junit 'target/surefire-reports/**/*.xml'
                archive 'target/*.jar'
            }
        }
    }
}
