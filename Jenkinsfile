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
            writeFile file: 'result.txt', text: "Test: job ${env.JOB_BASE_NAME}, result: ${currentBuild.currentResult}"
            emailext body: '''<html>
            <h1>Test Mail Yuwen</h1>
            </html>''', subject: "job ${env.JOB_BASE_NAME}, result: ${currentBuild.currentResult}", to: '447330947@qq.com'
          }
    }
}
