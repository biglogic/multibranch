pipeline {
    agent any
    parameters {
        booleanParam(name: 'LINUX_X64', defaultValue: true, description: 'Select to build for Linux_X64')
        booleanParam(name: 'WINDOWS_X64', defaultValue: true, description: 'Select to build for Windows_X64')
        booleanParam(name: 'VERSION_BUMP', defaultValue: true, description: 'Enable to version bump on feature branch')
        booleanParam(name: 'Uploadto_PPL', defaultValue: true, description: 'Check this option to upload metadata to PPL.'  )
        string(name: 'CORE_VERSION', defaultValue: '1.2.1-alpha+350.g7fe565.master', description: 'Set core version')
        string(name: 'CORE_BUILD_PATH', defaultValue: 'core/core/1.2.1/pre-release', description: 'Set core build path')
        //invoke qa pipeline
        booleanParam(name: 'RUN_QA_PIPELINE', defaultValue: true, description: 'Enable to run QA pipeline')
    }

     stages {
        stage('Hello_testing') {
            steps {
                script{
                    //   def var1 = currentBuild.getBuildCauses('org.jfrog.hudson.trigger.ArtifactoryCause')[0]?.url
                    //   def var2 = var1.split('/')
                    //   echo "${var2[11]}"
                    //   mail bcc: '', body: "${env.BUILD_URL} has result ${currentBuild.currentResult}", cc: '', from: '', replyTo: '', subject: 'jenkins_jopb', to: 'imatulsingh01@gmail.com'
                    //   emailext mimeType:"test/html", body: env.BUILD_URL, subject: "[Jenkins]-${env.BUILD_URL}-${currentBuild.currentResult}", to: 'imatulsingh01@gmail.com' , replyTo: 'atulsinghtanakpur@gmail.com'
                      def userInput = input id: 'userInput',
                              message: 'Let\'s promote?', 
                              submitterParameter: 'submitter',
                              submitter: 'imatulsingh01',
                              parameters: [
                                [$class: 'BooleanParameterDefinition', defaultValue: 'true', description: 'Select to build for Linux_X64', name: 'LINUX_X64'],
                                [$class: 'BooleanParameterDefinition', defaultValue: 'true', description: 'Select to build for Windows_X64', name: 'WINDOWS_X64'],
                                [$class: 'BooleanParameterDefinition', defaultValue: 'false', description: 'Enable to version bump on feature branch', name: 'VERSION_BUMP'],
                                // [$class: 'BooleanParameterDefinition', defaultValue: 'false', description: 'Check this option to upload metadata to PPL.', name: 'Uploadto_PPL'],
                                [$class: 'StringParameterDefinition', defaultValue: '1.2.1-alpha+350.g7fe565.master', description: 'Set core version', name: 'CORE_VERSION'],
                                [$class: 'StringParameterDefinition', defaultValue: 'core/core/1.2.1/pre-release', description: 'Set core build path', name: 'CORE_BUILD_PATH'],
                                [$class: 'BooleanParameterDefinition', defaultValue: 'false', description: 'Enable to run QA pipeline', name: 'RUN_QA_PIPELINE']]
                    //   properties([pipelineTriggers([upstream('job123')])])          
                            //   parameters: [
                            //     [$class: 'BooleanParameterDefinition', defaultValue: 'true', description: 'Environment', name: 'env'],
                            //     [$class: 'BooleanParameterDefinition', defaultValue: 'true', description: 'Target', name: 'target']]

                    //   echo ("Env: "+userInput['LINUX_X64'])
                    //   echo ("Target: "+userInput['target'])
                    //   LINUX_X64 = userInput['LINUX_X64']
                         WINDOWS_X64 = userInput['WINDOWS_X64']
                         echo "${WINDOWS_X64}"
                    //   params.VERSION_BUMP = userInput['VERSION_BUMP']
                    //   params.Uploadto_PPL = userInput['Uploadto_PPL']
                    //   params.CORE_VERSION = userInput['CORE_VERSION']
                    //   params.CORE_BUILD_PATH = userInput['CORE_BUILD_PATH']
                    //   params.RUN_QA_PIPELINE = userInput['RUN_QA_PIPELINE']
                      
                      
                      
                    //  echo "${env.LINUX_X64}"
                    //   echo ("${env.JOB_NAME}")
                }

            }}
        stage("trigger"){  
                when {
                        expression{
                           return WINDOWS_X64_ == true
                        }
                    }        
                 steps{
                     script{
                           if ( "${WINDOWS_X64}" == true ){
                               sh "echo ${WINDOWS_X64}"
                               artifactoryCause = upStreamBuild.getCause(org.jfrog.hudson.trigger.ArtifactoryCause)
                               echo artifactoryCause
                           }
                           
                     }  
                    // build job: 'job_pera', parameters: [booleanParam(name: 'response', value: "${input}")], wait: "false"    
         }}
        
    }
}
