git credentialsId: '48f7511a-b0a1-4a90-8d7b-036be497936e', url: 'https://github.com/UST-SEIS665/seis665-03-fall-2018-assignment-11-wygsephi.git'

properties([pipelineTriggers([githubPush()])])

node('linux') {
  stage('Setup'){
    sh 'aws s3 cp s3://seis665-03-asm10/classweb.html ./index.html'
  }
  stage('Build'){
    sh 'docker build -t classweb:1.0 .'
  }
  stage('Test'){
    sh 'docker run -d -p 80:80 --env NGINX_PORT="80" classweb:1.0'
    sh 'curl -s 10.120.1.196'
    }
  }
}
