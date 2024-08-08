pipeline {
   agent any
   


   stages {
       stage('build the docker file') {
           steps {
               sh 'cd webapp && docker build -t manjunathgowda0811/lmsimage:first .'
               
           }
       }
      
       stage('Building the project using DOCKER') {
           steps {
               echo 'LMS Build Started'
               //dockerImage = docker.build registry
               //sh 'cd webapp && docker build -t manjunathgowda0811/lmsimage:first'
               //sh 'docker push manjunathgowda0811/lmsimage:first'
               echo 'lms build completed'
           }
       }
      
       stage('Publish image') {
           steps {
            script{
                   docker.withRegistry( '',registryCredentials ){
                    dockerImage.push()
                   } 
                }
           }
       }
      
       //stage('Deploy LMS') {
           //steps {
               //script {
                //def packageJson = readJSON file: 'webapp/package.json'
                   //def packageJSONVersion = packageJson.version
                   //echo "${packageJSONVersion}"
                   //sh "curl -u admin:ManjuAppu@0811 -X GET \'http://3.139.69.109:8081/repository/lms-1/lms-${packageJSONVersion}.zip\' --output lms-'${packageJSONVersion}'.zip"
                   //sh 'sudo rm -rf /var/www/html/*'
                   //sh "sudo unzip -o lms-'${packageJSONVersion}'.zip"
                   //sh "sudo cp -r webapp/dist/* /var/www/html"
               //}
           //}
       //}
       stage('Clean Up Workspace') {
           steps {
                   echo 'Cleaning Work Space'
                   // Install Cleanup Workspace plugin to make below command work
                   cleanWs()
           }
       }
   }
}

