pipeline {
    agent any
	tools {
  	    maven "Maven"
	    jdk "Java 11"
	}
	
    stages {
        stage('Clone the repo') {
            
            steps {
                echo'Clona el repo'
		   
		    git url: 'https://github.com/craygoza/termometer.git'
		        
		    //git url: 'https://github.com/gabobriceno83/maven-hello-world.git'
            }
        }
		stage('Maven Build') {
            steps {
		    //bat 'mvn -version'
		    //bat 'mvn clean install'
		    
		    bat 'mvn clean package'
		    //bat 'mvn install'
		    //bat "mvn -Dmaven.test.failure.ignore= true clean package" 
                //echo 'Maven Build' 
            }
        }
		stage('Unit Test') {
            steps {
                echo 'Unit Test' 
            }
	 }

	   	stage('SonarQube Test') {
            steps {
                echo 'SonarQube Test' 
            }
	 }
	    
	    	stage('Deploy') {
            steps {
                echo 'Process Deploy'
   	    }
	}
    }
	 post 
	{
	  always 
	   {
	     
	    emailext(attachLog: true, body:'El archivo adjunto corresponde al log de ejecucion', subject: "Estatus de Ejecucion del Pipeline - "+env.JOB_NAME+" : "+currentBuild.currentResult, to: 'gaboxi83@gmail.com')	        
	  }
     }
}

 
