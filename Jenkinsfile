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
                                    ./${f}
                                 
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
