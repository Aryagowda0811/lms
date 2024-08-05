pipeline {
   agent any


   stages {
       stage('Code Quality') {
           steps {
               echo 'sleep 10'
               echo 'Sonar Analysis Started'
               sh 'cd webapp && sudo docker run --rm -e SONAR_HOST_URL="http://18.222.2.22:9000" -v ".:/usr/src" -e SONAR_TOKEN="sqp_a34ba9048095b33bbf16b7293713c6a020fed71f" sonarsource/sonar-scanner-cli -Dsonar.projectKey=lms-2'
               echo 'Sonar Analysis Completed'
           }
       }
      
       stage('Build LMS') {
           steps {
               echo 'LMS Build Started'
               sh 'cd webapp && npm install && npm run build'
               echo 'LMS Build Completed'
           }
       }
      
       stage('Publish LMS') {
           steps {
               script {
                   def packageJson = readJSON file: 'webapp/package.json'
                   def packageJSONVersion = packageJson.version
                   echo "${packageJSONVersion}"
                   sh "zip webapp/lms-${packageJSONVersion}.zip -r webapp/dist"
                   sh "curl -v -u admin:ManjuAppu@0811 --upload-file webapp/lms-${packageJSONVersion}.zip http://18.222.2.22:8081/repository/lms-1/"
               }
           }
       }
      
       stage('Deploy LMS') {
           steps {
               script {
                def packageJson = readJSON file: 'webapp/package.json'
                   def packageJSONVersion = packageJson.version
                   echo "${packageJSONVersion}"
                   sh "curl -u admin:ManjuAppu@0811 -X GET \'http://18.222.2.22:8081/repository/lms-1/lms-${packageJSONVersion}.zip\' --output lms-'${packageJSONVersion}'.zip"
                   sh 'sudo rm -rf /var/www/html/*'
                   sh "sudo unzip -o lms-'${packageJSONVersion}'.zip"
                   sh "sudo cp -r webapp/dist/* /var/www/html"
               }
           }
       }
       stage('Clean Up Workspace') {
           steps {
                   echo 'Cleaning Work Space'
                   // Install Cleanup Workspace plugin to make below command work
                   //cleanWs()
           }
       }
   }
}

