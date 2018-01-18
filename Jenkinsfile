pipeline{
    agent any
    
    environment {
        DISABLE_AUTH = 'true'
        DB_ENGINE = 'sqlite'
    }
    
    stages{
        stage ('Clone Repo') {
            steps{
                sh 'echo branch: $BRANCH_NAME'
                checkout([
                    $class: 'GitSCM',
                    branches: scm.branches,
                    doGenerateSubmoduleConfigurations: false,
                    extensions: [[$class: 'SubmoduleOption',
                                           disableSubmodules: false,
                                           parentCredentials: true,
                                           recursiveSubmodules: true,
                                           reference: '',
                                          trackingSubmodules: true]],
                             submoduleCfg: [],,
                    userRemoteConfigs: scm.userRemoteConfigs
                ])
            }
        }   

        stage('Build') {
            steps {
                sh 'printenv'
            }
        }
    }
    
}
