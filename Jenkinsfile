pipeline{
    agent any    
    environment {
        DISABLE_AUTH = 'true'
        DB_ENGINE = 'sqlite'
    }
    
    stages{
        def testvar
        stage ('Clone Repo') {
            steps{
                sh 'echo branch: $BRANCH_NAME'
                checkout([$class: 'GitSCM',
                    branches: [[name: '**']],
                    doGenerateSubmoduleConfigurations: false,
                    extensions: [[$class: 'SubmoduleOption',
                        disableSubmodules: false,
                        parentCredentials: false,
                        recursiveSubmodules: true,
                        reference: '',
                        trackingSubmodules: true]],
                    submoduleCfg: [],
                    userRemoteConfigs: [[credentialsId: '4698f43c-8701-446a-a74b-d3e3eb0c4179',
                        url: 'https://github.com/rbuhl/pythread.git']]]
                )
            }
        }   

        stage('Build') {
            steps {
                sh 'printenv'
            }
        }
    }
    
}
