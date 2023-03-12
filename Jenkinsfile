pipeline{
    agent any
    parameters{
         string(name: 'Greeting', defaultValue: 'Hello', description:'How old are you?')   
    }
    environment{
        jobName = "wakaka"
    }
    stages {
        stage("api_autotest"){
            steps{
                echo "${params.Greeting}"
                bat 'python messages.py'
            }
        }
    }
        post {
          always {
            writeFile file: 'result.txt', text: "Test: job ${env.JOB_BASE_NAME}, result: ${currentBuild.currentResult}"
            writeFile file: 'result2.txt', text: "job ${env.jobName}"
            emailext body: '''<html>
            <h1>Test Mail Yuwen</h1>
            </html>''', subject: "job ${env.JOB_BASE_NAME}, result: ${currentBuild.currentResult}", to: '447330947@qq.com'
          }
    }
}
