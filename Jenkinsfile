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
            publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: '', reportFiles: 'index.html', reportName: 'HTML Report', reportTitles: '', useWrapperFileDirectly: true])
          always {
            emailext body: '''<html>
            <h1>Test Mail Yuwen</h1>
            </html>''', subject: 'pipeline email nofify', to: '447330947@qq.com'
          }
    }
}
