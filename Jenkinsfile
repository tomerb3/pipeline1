pipeline {
    agent { label "master"}
    stages {
        stage('1') {
            steps {
                script {
                    def tests = [:]
                    for (f in findFiles(glob: '/tmp/files/*.sh')) {
                        tests["${f}"] = {
                            node {
                                stage("${f}") {
                                    echo '${f}'
                                    /tmp/files/${f}
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
