def prodFilesToRemove = ['.gitignore', 'test.zip', 'test.txt', 'deleteMe.js']
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
        buildZip({buildFor}, devFilesToRemove)
    }


}



def buildZip (buildFor, filesToRemove){

    if (buildFor == "PROD"){
        for(item in filesToRemove){
            sh 'echo removing {item}'
        }
    }

    zip archive: true, dir: '', glob: '', zipFile: 'hackidoo.zip' 

}