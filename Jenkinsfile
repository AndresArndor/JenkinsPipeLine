pipeline {
  agent any
  stages {
    stage('Build_Code') {
      steps {
        echo 'Suka, prepare the Build'
        sh 'if [ -d !=/tmp/JenkinsPipeLine ] ; then git clone https://github.com/AndresArndor/JenkinsPipeLine.git /tmp/JenkinsPipeLine; else cd /tmp/JenkinsPipeLine && git pull; fi'
	sh 'docker run --name blet --rm -p 8001:80 -v /tmp/JenkinsPipeLine/src:/usr/share/nginx/html:ro -d nginx'
      }
    }
    stage('Build_Verification') {
      steps {
        echo 'blet, test the site'
	sh 'curl localhost:8001 | grep -i "hello world" && echo "PipeLine has Run Successfully, znachit blet rabotaet!"'
	sh 'docker stop blet'
	echo 'blet is going to Production!'
      }
    }  
    stage('Push_to_Test_Env') {
      steps {
        echo 'blet, we are going to kubernetes'
      }
    }
  }
}
