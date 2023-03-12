pipeline{
    agent any
    parameters{
         string(name: 'Greeting', defaultValue: 'Hello', description:'How old are you?')   
         text(name: 'Greeting2', defaultValue: 'Hello Again!', description:'How old old are you?')  
         booleanParam(name: 'Greeting3', defaultValue: true, description:'How old are you too?')  
         choice(name: 'Greeting4', choices: ['Hello Again!','1','2'], description:'How are you?')  
         password(name: 'Greeting5', defaultValue: 'secret', description:'secret')  
    }
    environment{
        jobName = "wakaka"
    }
    stages {
        stage("api_autotest"){
            steps{
                echo "Parameters: "
                echo "${params.Greeting}"
                echo "${params.Greeting2}"
                echo "${params.Greeting3}"
                echo "${params.Greeting4}"
                echo "${params.Greeting5}"
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
