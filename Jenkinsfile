node {
    
    // other project stages will come here 
    
    // this could be an array as well
    def containerName = "child07" 
    def profileName = "demo-camel"
    // this need to computed and retrieved from the release util scripts
    def bundleInfo = "mvn:org.workspace7.fuse/camel-jenkins-demo/1.0.1"
    
    stage('Fabric Deploy') {
        sshagent (credentials: ['fabric8-dev']) {
        def exec = """
ssh -o StrictHostKeyChecking=no -p 8101 -l karaf localhost << 'EOF'
source 'http://localhost:3000/gogsadmin/fabric8-pipeline-checks/raw/master/profile_update.karaf'
profile_update $containerName $profileName $bundleInfo
EOF"""
       wrap([$class: 'AnsiColorBuildWrapper', 'colorMapName': 'XTerm']) {
           def fout  = sh script: exec, returnStdout: true
           println fout
           
           if(fout.contains("Error")) {
              currentBuild.result = 'FAIL'
           }
       }
     }
    }
    
}