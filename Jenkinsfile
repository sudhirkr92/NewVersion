pipeline {
    agent any
     stages {
        stage("Generate Files") {
            steps {
		//    echo "Hello world"
		 sh "git pull origin main" 
		sh "git checkout origin/main"
		  sh "chmod 755 *"
                 sh "./codeconvertor.sh WebApplication2/WebApplication2/Program.cs"
            }
        }

        stage("Commit Generated Files") {
            steps {   
		    // echo "Hello world"
		 sh "touch testfile.txt"
		    sh "git add testfile.txt"
		    
            //    sh "git add demo1/src/main/java/com/example/demo/Demo1Application.java"
                sh "git commit -a -m 'aifile'"
            }
        }

        stage("Push to Repository") {
            steps {
		     echo "Hello world"
               withCredentials([gitUsernamePassword(credentialsId: 'PAT_Jenk', gitToolName: 'Default')]) {
				
            //        sh "git pull origin main"
		    sh "git remote"
		       sh "git branch -r"
		       sh "git push -u origin main"
                }
            }
	}

        stage('Build Docker image') {
            steps {
		    echo "Hello world"
                sh "docker build -t sakshidocker12/hackathon_23 ."
            }
        } 
       stage('Push Docker image') {
            environment {
		DOCKERHUB_CREDENTIALS = credentials('sakshidocker12-token')    
            }
            steps {
		sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'    
		 sh "docker push sakshidocker12/hackathon_23:latest"  
		 sh "docker logout"  
            }
        }
        
        }
}
