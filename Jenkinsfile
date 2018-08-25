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
                                    echo '${f}'
                                     
                                     
                                        
                                        sh('cd /tmp && ./script.sh kk1')
                                    
                                 
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
