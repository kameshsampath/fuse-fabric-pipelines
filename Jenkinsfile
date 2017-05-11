node {
    
    input "Promote ?"
    
    stage('OSGi List') {
      sshagent (credentials: ['fabric8-dev']) {
         sh 'ssh -o StrictHostKeyChecking=no -p 8101 -l karaf localhost osgi:list'
      }
   }
}