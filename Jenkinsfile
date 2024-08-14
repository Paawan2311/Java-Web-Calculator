node{
def mavenHome = tool name:"Maven"

//this stage is for git clone
stage('checkout git'){
git branch: 'main', url: 'https://github.com/Paawan2311/Java-Web-Calculator.git'
}
//this is for maven build
stage('build'){
sh "$mavenHome/bin/mvn clean package"
}
//upload war to artifact
stage('artifact'){
sh "$mavenHome/bin/mvn deploy"
}

//deploy to tomcat 
stage('deploytom'){
sshagent(['sshtomcat']) {
    sh "scp -o StrictHostKeyChecking=no target/calculator.war ec2-user@52.2.87.166:/opt/apache-tomcat-9.0.93/webapps"
}
}
}//closing
