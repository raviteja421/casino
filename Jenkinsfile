pipeline {
    agent any

    tools {
        maven "maven"
    }

    stages {
        stage('SCM') {
            steps {
                git branch: 'main', url: 'https://github.com/vamsibyramala/casino.git'
            }
        }
        stage('build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage ('deploy') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://13.233.145.22:8080/')], contextPath: 'newapp', war: '**/*.war'
            }
        }
    }
}
