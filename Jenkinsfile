pipeline {
    agent any
    
    tools {
        maven 'myMaven'
    }
    stages {
        stage('CloneRepository') {
            steps {
                git 'https://github.com/habdulr1/DevOpsClassCodes.git'
            }
        }
        stage('DevCompile') {
            steps {
                sh 'mvn compile'
            }
        }
        stage('CodeReview') {
            steps {
                sh 'mvn pmd:pmd'
            }
            post {
                success {
                    recordIssues sourceCodeRetention: 'LAST_BUILD', tools: [pmdParser(pattern: 'target/pmd.xml')]
                }
            }
        }
    }
}
