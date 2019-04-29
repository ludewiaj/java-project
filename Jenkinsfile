properties([pipelineTriggers([githubPush()])])

node('24aa0f436fb5') {   
  stage('Unit Tests') {
    git 'https://github.com/ludewiaj/java-project.git' 
    sh 'ant -f test.xml -v'
    junit 'reports/result.xml'
  }
  stage('Build') {
   sh 'ant  -f build.xml -v'
  }
  stage('Deploy') {
    sh 'aws s3 cp /workspace/java-pipeline/dist/rectangle-$BUILD_NUMBER.jar s3://assignment-10-jar-bucket/rectangle-$BUILD_NUMBER.jar'
  }
  stage('Report') {
    withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'AWS Keys', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
      sh 'aws cloudformation describe-stack-resources --region us-east-1 --stack-name jenkins'
    }
  }
}

