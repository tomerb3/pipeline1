pipeline {
    agent { label "master"}
    stages {
        stage('first stage') {
            steps{
             sh("/tmp/script2.sh ${VAR1}")
            
            }
        }
        stage('aaa1') {
            steps {
                script11 {
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
