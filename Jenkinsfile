pipeline {
    agent { label "master"}
    stages {
        stage('1') {
            steps {
                script {
                    def tests = [:]
                    for (f in findFiles(glob: '**/*.sh')) {
                        tests["${f}"] = {
                            node {
                                stage("${f}") {
                                    echo 'stg aaa ${f} aaa'
                                     
                                     
                                        
                                    sh("/tmp/script.sh ${f} && sleep 30 ")
                                    
                                 
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
