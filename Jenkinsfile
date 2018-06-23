#!groovy
import jenkins.*
import jenkins.model.*
import hudson.*
import hudson.model.*
import hudson.EnvVars
 
//@Library('DSG_PIPELINE') _
 

 

//import java.sql.DriverManager
//import jenkins.model.*
//jenkins = Jenkins.instance

//DriverManager.registerDriver(new com.mysql.jdbc.Driver())



//Drop table if it already exists
//sql.execute('drop TABLE users')

node {
    
 
    currentBuild.result = 'SUCCESS'

    try {

        def ciEnv = "code1"

        stage('Prepare') {

       // \\slackSend message: "${env.JOB_NAME} - #${env.BUILD_NUMBER} Started... (<${env.BUILD_URL}|Open>)"

        checkout([
            $class: 'GitSCM',
            branches: [[name: '*/master']],
            doGenerateSubmoduleConfigurations: false,
            extensions: [],
            submoduleCfg: [],
            userRemoteConfigs: [[
                url: 'https://github.com/tomerb3/pipeline1.git'
            ]]
        ])

        stage("git-checkout") {

            if ("${REV_VER}" != 'master') {

                sh "git checkout ${REV_VER}"

            }
        }

    //    sh '${JENKINS_HOME}/workspace/it-build-tools/src/scripts/it-build-ctl init --ecr-login'

        }

        stage('run script a1') {

            sh '${JENKINS_HOME}/workspace/pipe1/scr1.sh ${REV_VER}'

        }

        stage('mysql 1') {

           

           ansiColor('xterm') {
        // Just some echoes to show the ANSI color.
        stage "\u001B[31mI'm Red\u001B[0m Now not"
         
        }

        stage('Build-Containers') {

         //   sh '${JENKINS_HOME}/workspace/it-build-tools/src/scripts/it-build-ctl build-containers'

        }

        stage('Publish-Containers') {

        //    sh '${JENKINS_HOME}/workspace/it-build-tools/src/scripts/it-build-ctl publish-containers'

        }

        stage('Gather-Results') {
     //       archive 'target/**.rpm'
        }

        stage('Cleanup'){
            echo 'prune and cleanup'
         //   sh 'docker system prune --force'
            //sh 'rm -rf dist/builds'
        }

        stage((ciEnv ? ("Diagnose on " + ciEnv) : "Skip Diagnostics")) {

            if (ciEnv) {

             //   build job: "seeded.env." + ciEnv + ".diagnostics"

            } else {

            //    sh 'echo "WARNING: CI Environment Not Defined - Skipping..."'

            }

        }

    } catch (err) {

        currentBuild.result = "FAILURE"

        throw err

    } finally {

       // slackSend message: "${env.JOB_NAME} - #${env.BUILD_NUMBER} ${currentBuild.result} after ${currentBuild.durationString.replace(' and counting', '')} (<${env.BUILD_URL}|Open>)",
         //   color: ((currentBuild.result == "FAILURE")?"danger":"good")

    }

}

