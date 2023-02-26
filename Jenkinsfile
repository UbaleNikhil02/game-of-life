pipeline {
  agent {
    node {
      label 'built-in'
      customWorkspace "/home/ubalenikhil7866/project/"
    }
  }
  stages {
    stage('clone') {
      steps { 
        sh "rm -rf game-of-life"
        sh 'git clone "https://github.com/UbaleNikhil02/game-of-life.git"'
      }
    }
    stage('compilation') { 
      agent {
        node {  
          label "built-in" 
          customWorkspace "/home/ubalenikhil7866/project/game-of-life" 
        }
      }
       steps {
         sh "mvn clean install"
       }
    }   
    stage('docker build and publish') { 
      steps {
	    dir("/home/ubalenikhil7866/project/game-of-life/gameoflife-web") {
          sh "docker build -t nikhil ."
          sh "docker tag nikhil:latest nikhil02/nikhil:2.0"
          sh "docker login -u nikhil02 -p dckr_pat_f3fFguBXrvziR9KTutAHr-VZgqU"
          sh "docker push nikhil02/nikhil:2.0"
        }
	  }
    }
    stage ("deploy") {
      steps {
        dir("/home/ubalenikhil7866/project/game-of-life/gameoflife-web") {
	      sh "docker build -t nikhil ." 
	      sh "docker run -itdp 9090:8080 nikhil"
	    }
	  }
    }	    
  }
}
