pipeline {
	  agent any
	   stages {
		     stage('CHECKOUT SCM') {
		           steps {
		           checkoutScm 'git','https://github.com/keer0322/oodle.git',''
		          }
		      }
            stage('CODE COMPILE') {
                 steps {
               sh "cd ${WORKSPACE}/ && ${tool 'MAVEN'}/bin/mvn org.talend:ci.builder:6.4.1:generate -f pom.xml -Dcommandline.workspace=${WORKSPACE}/ -Dcommandline.host=localhost -Dcommandline.port=8002 -Dcommandline.user=admin@company.com"+
               }
             }
            stage('CODE BUILD') {
                 steps {
                  sh "cd ${WORKSPACE}/ && ${tool 'MAVEN'}/bin/mvn package -f pom.xml -Dcommandline.workspace=${WORKSPACE}/ -Dcommandline.host=localhost -Dcommandline.port=8002 -Dcommandline.user=admin@company.com -DprojectsTargetDirectory=${WORKSPACE}/target"
                 }
                }
            stage('PUBLISH ARTIFACTS') {
                 steps {
                   sh "cd ${WORKSPACE}/ && ${tool 'MAVEN'}/bin/mvn deploy -fn -e" 
                 }
                }
              }
      }
