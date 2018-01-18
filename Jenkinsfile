node {
    def apptbloader

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace 

        checkout([$class: 'GitSCM', 
                  branches: [[name: '*/master']],
                  doGenerateSubmoduleConfigurations: false,
                  extensions: [[$class: 'SubmoduleOption',
                                disableSubmodules: false,
                                parentCredentials: true,
                                recursiveSubmodules: true,
                                reference: '',
                                trackingSubmodules: true]], 
                  submoduleCfg: [],
                  userRemoteConfigs: [[credentialsId: 'github-auro', 
                                       url: 'https://github.com/']]])
                                       /*
        echo "Branch: " env.BRANCH_NAME

    }

    stage('Build images') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */

        apptbloader = docker.build("aurotfp/secsvc_treasury")
        
    }

    stage('Push images') {
        /* Finally, we'll push the image with two tags:
         * First, the incremental build number from Jenkins
         * Second, the 'latest' tag.
         * Pushing multiple tags is cheap, as all the layers are reused. */
        docker.withRegistry('https://registry.hub.docker.com', 'docker-hub') {
            apptbloader.push("${env.BUILD_NUMBER}")
            apptbloader.push("preprod")
            apptbloader.push("latest")
        }
    }
}
