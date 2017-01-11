def prodFilesToRemove = ['.gitignore']
def devFilesToRemove = []

node {
    stage('Cloning Project') {
        git 'https://github.com/tmrocha89/hackidoo'
    }
    stage('Unit Tests') {
        sh 'echo "Nothing to test. TDD? nop!"'
    }
    stage('Build a zip file') {
        buildZip('DEV', devFilesToRemove)
    }


}



def buildZip (env, filesToRemove){

    if (env == "PROD"){
        //remove unnecessary files
    }

    zip archive: true, dir: './', glob: 'excludes="**/.gitignore"', zipFile: 'hackidoo.zip' 

}