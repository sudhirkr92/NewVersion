pipeline {
    agent any
    stages {
        stage("Generate Files") {
            steps {
                echo "Generating Java Files from ChatGPT API calls"
	//	sh "git stash"  
	//	sh "git checkout main"
          //      sh "git stash pop" 
		    //sh "git checkout origin/main"
		//sh "chmod -r 755 *"
        	//sh "chmod 755 /var/lib/jenkins/workspace/GetDetails/script/codeconvertor.sh"
                //sh "./script/codeconvertor.sh WebApplication2/WebApplication2/Program.cs"
                 //bat "sh -x ./script/codeconvertor.sh WebApplication2/WebApplication2/Program.cs"
            }
        }

        stage("Commit Generated Files") {
            steps {
                echo "Staging the generated files and commiting in git"
                
                //sh "git add demo1/src/main/java/com/example/demo/Demo1Application.java"
                //sh "git commit -m 'AIGeneratedFiles' || echo 'Commit failed. There is probably nothing to commit.'"
		   //  sh "git commit -m 'AIGeneratedFiles'"
            }
        }

        stage("Push to Repository") {
            steps {
               //withCredentials([gitUsernamePassword(credentialsId: 'PAT_Jenk', gitToolName: 'Default')]) {
		     echo "Pushing to remote GitHub Repo"
	          //    sh "git pull origin main"		
                  //    sh "git push -u origin main"
		      // sh "git push https://github.com/Sakshi-Git1/NewVersion.git HEAD:main"
               // }
            }
        }

        stage("Sync Repository") {
            steps {
                    echo "Sync working directory with remote GitHub Repo"
                    //sh "git pull origin main"
		    //sh "git status"	 
            }
        }
        stage('Build Docker image') {
            steps {
                echo "Building the docker Image based on Dockerfile"
		bat "cd demo1 & dos2unix mvnw & docker build -t sudhirkr92/hackthon-23-team1 ."
            }
        } 

        stage('Push Docker image') {
            environment {
		DOCKERHUB_CREDENTIALS = credentials('sudhirkr92-dockerhub-token')    
            }
            steps {
		 echo "Shiping the Docker Image to DockerHub"    
		 sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'    
		 bat "docker push sudhirkr92/hackthon-23-team1:latest"  
		 bat "docker logout"  
            }
        }
        stage('Deploy to AWS') {
             steps {
                echo "Deploying the Docker Image on AWS -EC2"  
               // build job: "Deploy", wait: true
              }
           }
       }
}
