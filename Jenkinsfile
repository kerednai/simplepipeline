pipeline {
  agent any
  stages {
    stage('foo') {
      steps {
        httpRequest(url: 'http://banka.mybluemix.net/loans/v1/quote?loanAmount=9501.64&annualInterestRate=28&termInMonths=36', acceptType: 'APPLICATION_JSON', contentType: 'APPLICATION_JSON', httpMode: 'GET', responseHandle: 'STRING', validResponseCodes: '200', outputFile: 'output.txt')
        script {
          env.FILENAME = readfile 'output.txt'
        }

        echo "${env.FILENAME}"
      }
    }
  }
}