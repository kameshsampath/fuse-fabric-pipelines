node {
    
    // other project stages will come here 
    
    // this could be an array as well
    def containerName = "child07" 
    def profileName = "demo-camel"
    // this need to computed and retrieved from the release util scripts
    def bundleInfo = "mvn:org.workspace7.fuse/camel-jenkins-demo:1.0.1"
    
    stage('Fabric Deploy') {
        sshagent (credentials: ['fabric8-dev']) {
         def stdOut =  sh(script:"""
            ssh -o StrictHostKeyChecking=no -p 8101 -l karaf localhost <<EOF
            CONTAINER_NAME =  $containerName
            PROFILE_NAME = $profileName
            source http://localhost:3000/gogsadmin/fabric8-pipeline-checks/raw/master/profile_update.karaf 
            profile_update
            'EOF'
        """,returnStdOut: true)
        
        println stdOut
       }
    }
    
}