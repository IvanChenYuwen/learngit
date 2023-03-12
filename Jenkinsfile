pipeline{
    agent any
    stages {
        stage("api_autotest"){
            steps{
                bat 'python messages.py'
            }
        }
    }
        post {
          always {
            emailext body: '''<html>
            <h1>Test Mail Yuwen</h1>
            </html>''', subject: 'pipeline email nofify', to: '447330947@qq.com'
          }
    }
}
