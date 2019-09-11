pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        echo 'Taking source checkout'
      }
    }
    stage('Build') {
      steps {
        echo 'Preparing Build'
	sh 'docker run --name suka --rm -p 8001:80 -v /home/andrew/src:/usr/share/nginx/html:ro -d nginx'
      }
    }
    stage('Test_Build') {
      steps {
        echo 'Suka blya, test the site'
	sh 'curl localhost:8001 | grep -i "hello world" && echo "PipeLine has Run Successfully!"'
	sh 'docker stop suka'
      }
    }
  }
}
