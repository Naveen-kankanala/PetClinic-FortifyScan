node
{
    stage('Git')
    {
        git 'https://github.com/selvan123/petclinic.git'
    }
    stage('Fortify Clean')
    {
        fortifyClean addJVMOptions: '', buildID: 'PetClinicProject-Fortify Scan', logFile: '', maxHeap: ''   
    }
    stage('Fortify Update')
    {
        fortifyUpdate proxyPassword: '', proxyURL: '', proxyUsername: '', updateServerURL: 'https://update.fortify.com'
    }
    stage('Fortify Translate')
    {
        fortifyTranslate addJVMOptions: '', buildID: 'PetClinicProject-Fortify Scan', excludeList: '', logFile: '', maxHeap: '', projectScanType: fortifyJava(javaAddOptions: '', javaClasspath: '', javaSrcFiles: 'src/**/*.java', javaVersion: '1.8')
    }
    stage('Fortify Scan')
    {
        fortifyScan addJVMOptions: '', addOptions: '', buildID: 'PetClinicProject-Fortify Scan', customRulepacks: '', logFile: '', maxHeap: '', resultsFile: 'PetClinic.fpr'
    }
    stage('Fortify Upload')
    {
       fortifyUpload appName: 'PetClinicProject-FortifyScan', appVersion: '1.1', failureCriteria: '', filterSet: '', pollingInterval: '', resultsFile: 'PetClinic.fpr'
    }
    
} 
