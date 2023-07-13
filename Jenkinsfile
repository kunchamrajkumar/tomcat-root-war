node {

  stage ('checkout'){
           git branch: 'master', credentialsId: 'git_creds', url: 'https://github.com/kunchamrajkumar/tomcat-root-war.git'
 
         }

   stage ('build'){ 
        withMaven(globalMavenSettingsConfig: '', jdk: 'java', maven: 'maven', mavenSettingsConfig: '', traceability: true) {
    sh 'mvn clean package'
           }
   
   }
   stage ('deploy'){
        
           
     deploy adapters: [tomcat9(credentialsId: 'tomcatID', path: '', url: 'http://44.201.79.229:8081/')], contextPath: null, war: '**/*.war'
   }

}
