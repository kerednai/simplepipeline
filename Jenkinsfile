pipeline {
  agent any
  stages {
    stage('foo') {
      steps {
        httpRequest(url: 'http://banka.mybluemix.net/loans/v1/quote?loanAmount=9501.64&annualInterestRate=28&termInMonths=36', acceptType: 'APPLICATION_JSON', contentType: 'APPLICATION_JSON', httpMode: 'GET', responseHandle: 'STRING', validResponseCodes: '200', outputFile: 'output.txt')
        script {
          env.FILENAME = readFile 'output.txt'
        }

        echo "${env.FILENAME}"
        httpRequest(url: 'https://postman-echo.com/post', acceptType: 'APPLICATION_JSON', contentType: 'APPLICATION_JSON', httpMode: 'POST', outputFile: 'postmanOutput.txt', requestBody: '${env.FILENAME}', responseHandle: 'STRING', validResponseCodes: '200')
        script {
          env.POSTMANOUT = readFile 'postmanOutput.txt'
        }

        echo '"${env.POSTMxANOUT}"'
      }
    }
  }
}