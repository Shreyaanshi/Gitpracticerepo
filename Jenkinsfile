pipeline {
    agent any
        triggers {
                pollSCM('* * * * *')
    }
    stages {
        stage('vcs') {
            steps {
                git branch: "main", url: 'https://github.com/Shreyaanshi/Gitpracticerepo.git'
            }
                }
                 
        stage('Build the Code') {
            steps {
                sh script: 'mvn clean install'

            }
        }
    }
       
    }