podTemplate(containers: [
  containerTemplate(
      name: 'maven',
      image: 'maven:3.8.1-jdk-8',
      command: 'sleep',
      args: '30d'
      )
  ],
  
  volumes: [
  persistentVolumeClaim(
      mountPath: '/root/.m2/repository', 
      claimName: 'maven-repo-storage', 
      readOnly: false
      )
  ]) 

{
  node(POD_LABEL) {
    stage('Get a Maven project') {
      git'https://github.com/dlambrig/simple-java-maven-app.git'
'main'	  
      container('maven') {
        sh 'mvn -B -ntp clean package -DskipTests'
      }
    }
  }
}
