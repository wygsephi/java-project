properties([pipelineTriggers([githubPush()])])

node('linux') {
  stage('Unit Tests'){
    git 'https://github.com/wygsephi/java-project.git'
    sh 'ant -f test.xml -v'
    junit 'reports/result.xml'
  }
  stage('Build'){
    sh 'ant -f build.xml -v'
  }
  stage('Deploy'){
    sh 'sudo aws s3 cp s3://seis665-03-asm10/rectangle-2.jar build.xml'
  }
  stage('Report'){
    withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: '28b3c933-f5a1-4396-afd2-5d892f86afe0', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
    // some block
      sh 'aws cloudformation describe-stack-resources --region us-east-1 --stack-name jenkins665'
    }
  }
}
