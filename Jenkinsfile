pipeline {
   agent any


   stages {
       stage('Code Quality') {
           steps {
<<<<<<< HEAD
               echo 'Sonar Analysis is Started'
               sh 'cd webapp && sudo docker run --rm -e SONAR_HOST_URL="http://13.58.184.233:9000" -v ".:/usr/src" -e SONAR_TOKEN="sqb_a872b4cdd803599651c634911e201a9dcf2f3758" sonarsource/sonar-scanner-cli -Dsonar.projectKey=lms-1'
=======
               echo 'sleep 10'
               echo 'Sonar Analysis is Started'
               sh 'cd webapp && sudo docker run --rm -e SONAR_HOST_URL="http://3.139.69.109:9000" -v ".:/usr/src" -e SONAR_TOKEN="sqp_a34ba9048095b33bbf16b7293713c6a020fed71f" sonarsource/sonar-scanner-cli -Dsonar.projectKey=lms-2'
>>>>>>> d186e3d14acd69930152f6b08d2a796a79534e94
               echo 'Sonar Analysis is Completed'
           }
       }
      
       stage('Build LMS') {
           steps {
<<<<<<< HEAD
               echo 'LMS Build is Started'
               sh 'cd webapp && npm install && npm run build'
               echo 'LMS Build is Completed'
=======
               echo 'LMS Build Started'
               sh 'cd webapp && npm install && npm run build'
               echo 'LMS Build Completed'
>>>>>>> d186e3d14acd69930152f6b08d2a796a79534e94
           }
       }
      
       stage('Publish LMS') {
           steps {
               script {
                   def packageJson = readJSON file: 'webapp/package.json'
                   def packageJSONVersion = packageJson.version
                   echo "${packageJSONVersion}"
                   sh "zip webapp/lms-${packageJSONVersion}.zip -r webapp/dist"
<<<<<<< HEAD
                   sh "curl -v -u admin:ManjuAppu@0811 --upload-file webapp/lms-${packageJSONVersion}.zip http://13.58.184.233:8081/repository/lms-1/"
=======
                   sh "curl -v -u admin:ManjuAppu@0811 --upload-file webapp/lms-${packageJSONVersion}.zip http://3.139.69.109:8081/repository/lms-1/"
>>>>>>> d186e3d14acd69930152f6b08d2a796a79534e94
               }
           }
       }
      
       stage('Deploy LMS') {
           steps {
               script {
                def packageJson = readJSON file: 'webapp/package.json'
                   def packageJSONVersion = packageJson.version
                   echo "${packageJSONVersion}"
<<<<<<< HEAD
                   sh "curl -u admin:ManjuAppu@0811 -X GET \'http://13.58.184.233:8081/repository/lms-1/lms-${packageJSONVersion}.zip\' --output lms-'${packageJSONVersion}'.zip"
=======
                   sh "curl -u admin:ManjuAppu@0811 -X GET \'http://3.139.69.109:8081/repository/lms-1/lms-${packageJSONVersion}.zip\' --output lms-'${packageJSONVersion}'.zip"
>>>>>>> d186e3d14acd69930152f6b08d2a796a79534e94
                   sh 'sudo rm -rf /var/www/html/*'
                   sh "sudo unzip -o lms-'${packageJSONVersion}'.zip"
                   sh "sudo cp -r webapp/dist/* /var/www/html"
               }
           }
       }
<<<<<<< HEAD
       stage('Clean Up the Workspace') {
=======
       stage('Clean Up Workspace') {
>>>>>>> d186e3d14acd69930152f6b08d2a796a79534e94
           steps {
                   echo 'Cleaning Work Space'
                   // Install Cleanup Workspace plugin to make below command work
                   cleanWs()
           }
       }
   }
}

