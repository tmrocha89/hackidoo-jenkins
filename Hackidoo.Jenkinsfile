def prodFilesToRemove = ['.gitignore']
def devFilesToRemove = []

node {
    stage('Cloning Project') {
        git 'https://github.com/tmrocha89/hackidoo'
    }
    stage('Unit Tests') {
        sh 'echo "Nothing to test. TDD? nop!"'
    }
    stage('Add Random Files') {
        touch file: 'test.zip', timestamp: 0
        touch file: 'test.txt', timestamp: 0
        touch file: 'deleteMe.js', timestamp: 0
    }
    stage('Build a zip file') {
        buildZip('DEV', devFilesToRemove)
    }


}



def buildZip (env, filesToRemove){

    if (env == "PROD"){
        //remove unnecessary files
    }

    zip archive: true, dir: '', glob: '', zipFile: 'hackidoo.zip' 

}