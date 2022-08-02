pipeline {
   agent any

   stages {

      stage('Check Commit') {
         steps {
          result = sh (script: "git log -1 | grep '\\[build\\]'", returnStatus: true)
           if (result != 0) {
             echo "performing build..."
           } else {
             script {
               throw new Exception("commit not standard")
             }
           }

         }
         post {
             success {
                 script {
                     echo "success"
                 }
             }
             failure {
                 script {
                     echo "failed, not meet commit standard"
                 }
             }
         }
      }

   }
}
