#!groovy

node {
    // -------------------------------------------------------------------------
    stage('build') {
        checkout scm

        buildVersion = sh(
            script: 'python setup.py --version',
            returnStdout: true
        ).trim()

        // Set build metadata
        currentBuild.displayName = buildVersion + ' on ' + env.BRANCH_NAME

        //sh 'pip install -q tox'
        sh 'tox -e py27'

        // We only push the image to the Docker Hub if we're on master
        if (env.BRANCH_NAME != 'master') {
            return
        }
    }
    // -------------------------------------------------------------------------
    stage('push') {
      echo 'yep'
    }

}
