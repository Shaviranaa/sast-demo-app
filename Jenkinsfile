pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://repository-url'
            }
        }
        stage('Run Bandit') {
            steps {
                sh 'pip install bandit'
                sh 'bandit -r . -f xml -o bandit-report.xml'
            }
        }
        stage('Publish Report') {
            steps {
                recordIssues(
                    tool: Bandit(pattern: 'bandit-report.xml')
                )
            }
        }
    }
}
