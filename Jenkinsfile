node
{
 
 def mavenHome=tool name: "maven-3.9.9"
 stage('checkout'){
     git branch: 'devlopment', url: 'https://github.com/prasaddevopsorg/maven-webapplication-project-kkfunda.git'
 }   
    
 stage('compile'){
     sh "${mavenHome}/bin/mvn clean compile"
 }   
 
 stage('build'){
     sh "${mavenHome}/bin/mvn clean package"
 }
 stage('codequality'){
     sh "${mavenHome}/bin/mvn sonar:sonar "
 }
 
 stage('nexus'){
     sh "${mavenHome}/bin/mvn deploy"
 }
  stage('Deploy to Tomcat') {
        echo "Deploying WAR file using curl..."

        sh """
            curl -u prasad:password \
            --upload-file /var/lib/jenkins/workspace/scripted-pipeline/target/maven-web-application.war \
            "http://3.109.212.211:9000/manager/text/deploy?path=/maven-web-application&update=true"
        """
    }
    
    
    
}
