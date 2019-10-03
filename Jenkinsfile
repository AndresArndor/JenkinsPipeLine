pipeline {
  agent any
  stages {
    stage('Build_Code') {
      steps {
        echo 'Blet, prepare the Build'
	sh 'docker kill blet'
        sh 'cd /tmp/JenkinsPipeLine && git pull'
	sh 'docker run --name blet --rm -p 8001:80 -v /tmp/JenkinsPipeLine/src:/usr/share/nginx/html:ro -d nginx'
      }
    }
    stage('Build_Verification') {
      steps {
        echo 'blet, test the site'
	sh 'curl localhost:8001 | grep -i "hello-world" && echo "PipeLine has Run Successfully, znachit blet rabotaet!"'
	sh 'docker kill blet'
	echo 'blet is able to go to Production!'
      }
    }  
  }
}
