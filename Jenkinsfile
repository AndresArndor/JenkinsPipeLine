pipeline {
  agent any
  stages {
    stage('Build_Code') {
      steps {
        echo 'Suka, prepare the Build'
	sh 'docker run --name suka --rm -p 8001:80 -v /home/andrew/src:/usr/share/nginx/html:ro -d nginx'
      }
    }
    stage('Build_Verification') {
      steps {
        echo 'Suka, test the site'
	sh 'curl localhost:8001 | grep -i "hello world" && echo "PipeLine has Run Successfully, znachit Suka rabotaet!"'
	sh 'docker stop suka'
	echo 'Suka is going to Production!'
      }
    }  
    stage('Push_to_Testing_Env') {
      steps {
        echo 'Suka, push to production'
      }
    }
  }
}
