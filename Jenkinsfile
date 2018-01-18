node {
    def apptbloader

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */
        sh 'printenv'
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

    stage('Build images') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */
        echo "Image is built here"
        
    }

    stage('Push images') {
        /* Finally, we'll push the image with two tags:
         * First, the incremental build number from Jenkins
         * Second, the 'latest' tag.
         * Pushing multiple tags is cheap, as all the layers are reused. */
        
        echo "Image would be pushed here."
        /*
        docker.withRegistry('https://registry.hub.docker.com', 'docker-hub') {
            apptbloader.push("${env.BUILD_NUMBER}")
            apptbloader.push("preprod")
            apptbloader.push("latest")
        }
        */
    }
}
