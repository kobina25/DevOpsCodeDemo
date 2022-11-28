
pipeline{
    tools{
        jdk 'myjava'
        maven 'mymaven'
    }
	agent none
      stages{
           stage('Checkout'){
               agent any
            //    agent {label 'slave1'}
	    
               steps{
		 echo 'cloning..'
                 git 'https://github.com/kobina25/DevOpsCodeDemo.git'
              }
          }
          stage('Compile'){
              agent {label 'slave1'}
            //   agent {label 'jenkins_slave'}
              steps{
                  echo 'complie the code..'
                  sh 'mvn compile'
	      }
          }
          stage('CodeReview'){
		      agent {label 'slave2'}
              steps{
		    
		  echo 'codeReview'
                  sh 'mvn pmd:pmd'
              }
          }
           stage('UnitTest'){
		       agent {label 'slave1'}
              steps{
	         
                  sh 'mvn test'
              }
          
          }
        
          stage('Package'){
		      agent any
              steps{
		  
                  sh 'mvn package'
              }
          }
	     
          
      }
}
