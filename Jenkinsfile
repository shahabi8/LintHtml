pipeline {
    agent any
    stages {
      stage('Lint HTML') {
        steps {
          sh 'tidy -q -e *.html'
        }
	  }
      stage('Upload to AWS') {
        steps {
          withAWS(region:'us-east-1',credentials:'udacity1') {
            s3Upload(pathStyleAccessEnabled:true, payloadSigningEnabled: true, file:'Index.html', bucket:'jenkins-upload-aws')
          }
        }
      }
    }
}
