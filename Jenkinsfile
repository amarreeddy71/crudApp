pipeline {
    agent any
        stages {
            stage('Build') {
                steps {
                    sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
                    }
                }
            stage('Docker') {
                steps {
                    dockerfile {
                        filename 'Dockerfile'
                        }
                    }
                }             
            }
    }
