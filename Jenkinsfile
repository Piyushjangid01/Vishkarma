pipeline {
    agent any

    triggers {
        pollSCM('* * * * *')
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Piyushjangid01/Vishkarma.git'
            }
        }
        
        
          stage('Deploy to Netlify') {
            steps {
                sh 'curl -X POST https://api.netlify.com/build_hooks/689802d8b420bdb97a195cbb'
            }
        } 
    }

     post {
        success {
            mail to: 'piyushjangid7417@gmail.com',
                 subject: "Jenkins Build #${env.BUILD_NUMBER} Successful",
                 body: """
Build Successful

Project: deploy to netlify
Build Number: ${env.BUILD_NUMBER}
View Build Log: ${env.BUILD_URL}console
view webiste: https://vishwakrma-furnituresheopur.netlify.app/
"""
        }

        failure {
            mail to: 'piyushjangid7417@gmail.com',
                 subject: "Jenkins Build #${env.BUILD_NUMBER} Failed",
                 body: """
Build Failed

Project: deploy to netlify
Build Number: ${env.BUILD_NUMBER}
View Build Log: ${env.BUILD_URL}console
view webiste: https://vishwakrma-furnituresheopur.netlify.app/
"""
        }
    }
}