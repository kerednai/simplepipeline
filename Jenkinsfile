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
          def json = new groovy.json.JsonBuilder()
          def root = json.build {
            build_number manager.build.number
            build_timestamp manager.build.timestamp
            build_duration manager.build.duration
            build_url manager.build.url
            build_project_name manager.build.project.name
            build_culprits manager.build.culprits
            build_result result.toString() // get the string representation
          }
          println JsonOutput.prettyPrint(json.toString())
        }

      }
    }
  }
}