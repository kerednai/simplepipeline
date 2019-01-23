pipeline {
  agent any
  stages {
    stage('Stage1') {
      steps {
        httpRequest(url: 'http://banka.mybluemix.net/loans/v1/quote?loanAmount=20000&annualInterestRate=0.9&termInMonths=52', acceptType: 'APPLICATION_JSON', contentType: 'APPLICATION_JSON', httpMode: 'GET', outputFile: 'outputFile')
        script{
          def myVar = readFile 'outputFile'
          println $myVar
        }        
      }
    }
  }
}
