pipeline {
  agent any
  stages {
    stage('foo') {
      steps {
        httpRequest(url: 'http://banka.mybluemix.net/loans/v1/quote?loanAmount=9501.64&annualInterestRate=28&termInMonths=36', acceptType: 'APPLICATION_JSON', contentType: 'APPLICATION_JSON', httpMode: 'GET', responseHandle: 'STRING', validResponseCodes: '200', outputFile: 'body.json')
        script {
          env.requestBody = readFile 'body.json'
        }

        echo "${env.requestBody}"
        httpRequest(url: 'https://postman-echo.com/post', acceptType: 'APPLICATION_JSON', contentType: 'APPLICATION_JSON', httpMode: 'POST', outputFile: 'postmanOutput.txt', requestBody: "${env.requestBody}", responseHandle: 'STRING', validResponseCodes: '200')
        script {
          env.POSTMANOUT = readFile 'postmanOutput.txt'
        }

        echo "${env.POSTMANOUT}"
        script {
          sampleMap = [color:'Blue', shape:'Circle']
          data = readJSON text: ${sampleMap}
          writeJSON(file: 'message1.json', json: data, pretty: 4)
        }

      }
    }
  }
}