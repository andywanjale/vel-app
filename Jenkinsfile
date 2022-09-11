pipeline{
  agent{
       label 'slave'                           
	   }
	stages{
	   stage('clone branch 22q1'){
            steps {
		    sh " sudo rm -rf *"
			sh "sudo git clone https://github.com/andywanjale/vel-app.git -b 22q1"
			}	
         }
        stage('deply on server1'){
		  steps {
          sh "sudo yum remove httpd -y"
          sh "sudo sleep 10"
		  sh "sudo yum install httpd -y"
		  sh "sudo sleep 5"
		  sh "sudo service httpd start"
		  sh "sudo cp -r /home/ec2-user/workspace/assignment-1/vel-app/index.html /var/www/html/"
		  }
		} 
		 stage ('clone branch 22q2'){
            agent{
		        label 'slave2'
				}
             steps{
	      sh " sudo rm -rf *"
	      sh "sudo git clone https://github.com/andywanjale/vel-app.git -b 22q2"
			}	
		}			
	     stage('deply on server2'){
		agent{
		        label 'slave2'
				}
		steps {
           sh "sudo yum remove httpd -y"
           sh "sudo sleep 10"
		   sh "sudo yum install httpd -y"
		   sh "sudo sleep 5"
	       sh "sudo service httpd start"
           sh "sudo cp -r /home/ec2-user/workspace/assignment-1/vel-app/index.html /var/www/html/"
		  }
		}  
         stage ('clone branch 22q3'){
		   agent{
		        label  'slave3'
				}
             steps{
			   sh " sudo rm -rf *"
		       sh "sudo git clone https://github.com/andywanjale/vel-app.git -b 22q3"
			} 
		}			
	     stage('deply on server3'){
		 agent{
		        label 'slave3'
				}
		 steps {
           sh "sudo yum remove httpd -y"
           sh "sudo sleep 10"
		   sh "sudo yum install httpd -y"
		   sh "sudo sleep 5"
		   sh "sudo service httpd start"
		   sh "sudo cp -r /home/ec2-user/workspace/assignment-1/vel-app/index.html /var/www/html/"
		  }
		} 		
  }

}
