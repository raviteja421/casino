pipeline {
    agent {label 'dev'}
    tools {
        maven 'maven'
    }

    stages {
        stage('SCM') {
            steps {
                git branch: 'main', url: 'https://github.com/vamsibyramala/casino.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
                sh 'mvn -v'
            }
        }
        stage('Deploy') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://3.109.55.133:8081/')], contextPath: 'app', war: '**/*.war'
            }
        }
    }
}
