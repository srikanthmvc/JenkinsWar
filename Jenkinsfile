node{

   /* def tomcatWeb = 'D:\\Auto_deployment\\apache-tomcat-9.0.30\\apache-tomcat-9.0.30\\webapps' */
   
   def tomcatWeb = 'C:\Program Files\Apache Software Foundation\Tomcat 10.0\webapps'
   
   /* def tomcatBin = 'C:\\apache-tomcat-9.0.55-windows-x64\\apache-tomcat-9.0.55\\bin' */
   
   def tomcatBin = 'C:\Program Files\Apache Software Foundation\Tomcat 10.0\bin'
   
   def tomcatStatus = ''
   stage('SCM Checkout'){
     git 'https://github.com/srikanthmvc/JenkinsWar.git'
   }
   stage('Compile-Package-create-war-file'){
      // Get maven home path
      def MAVEN_HOME =  tool name: 'Maven', type: 'maven'   
      bat "${MAVEN_HOME}/bin/mvn package"
      }
/*   stage ('Stop Tomcat Server') {
               bat ''' @ECHO OFF
               wmic process list brief | find /i "tomcat" > NUL
               IF ERRORLEVEL 1 (
                    echo  Stopped
               ) ELSE (
               echo running
                  "${tomcatBin}\\shutdown.bat"
                  sleep(time:10,unit:"SECONDS") 
               )
'''
   }*/
   stage('Deploy to Tomcat'){
     bat "copy target\\JenkinsWar.war \"${tomcatWeb}\\JenkinsWar.war\""
   }
      stage ('Start Tomcat Server') {
         sleep(time:5,unit:"SECONDS") 
         bat "${tomcatBin}\\startup.bat start"
         sleep(time:200,unit:"SECONDS")
   }
}
