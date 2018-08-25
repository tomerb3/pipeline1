pipeline {
    agent { label "master"}
    stages {        
            steps {      
                       
                
                
                script {
                    def tests = [:]
                    for (f in findFiles(glob: '**/*.action')) {
                        tests["${f}"] = {
                            node {
                                stage("${f}") {
                                    echo 'stg aaa ${f} aaa'
                                     
                                     
                                        
                                    sh("/tmp/script.sh ${f}")
                                    
                                 
                                }
                            }
                        }
                    }
                    parallel tests
                }
            }
        }       
    }
}
