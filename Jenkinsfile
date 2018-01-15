pipeline {
 agent  {
label 'master' 
} 
  stages{
   stage ("Unit tests") {
   steps{
    sh 'ant -f test.xml -v'
     junit 'report/result.xml'
	}
     }
   stage('build') {
       steps {
        sh 'ant -f build.xml -v'
           }
        }
    stage ('deploy') {
      steps {
       sh "cp dist/rectangle_${env.MAJOR_VERSION}.${env.BUILD_NUMBER}.jar /var/www/html/rectangles/all/"
}
}
}
  post {
   always {
 archiveArtifacts artifacts: 'dist/*.jar' , fingerprint:true 
          }
      }
}
