node
{
    def ApplicationName 	=	"PetClinicProject-FortifyScan"
    def ApplicationVersion	=    "1.1"
    def bID		        	=	"PetClinicProject-Fortify Scan"
    def GitRepoURL	       	=	"https://github.com/selvan123/petclinic.git"
    def FailureCriteria		=	"[fortify priority order]:high OR [fortify priority order]:critical"
    def ResultsFile	    	=	"PetClinic.fpr"

    stage('Source Code Download')
    {
        git GitRepoURL
    }
    stage('Fortify Clean')
    {
        fortifyClean addJVMOptions: '', buildID: bID, logFile: '', maxHeap: ''   
    }
    stage('Fortify Update')
    {
        fortifyUpdate proxyPassword: '', proxyURL: '', proxyUsername: '', updateServerURL: 'https://update.fortify.com'
    }
    stage('Fortify Translate')
    {
        fortifyTranslate addJVMOptions: '', buildID: bID, excludeList: '', logFile: '', maxHeap: '', projectScanType: fortifyJava(javaAddOptions: '', javaClasspath: '', javaSrcFiles: 'src/**/*.java', javaVersion: '1.8')
    }
    stage('Fortify Scan')
    {
        fortifyScan addJVMOptions: '', addOptions: '', buildID: bID, customRulepacks: '', logFile: '', maxHeap: '', resultsFile: ResultsFile
    }
    stage('Fortify Upload')
    {
       fortifyUpload appName: ApplicationName, appVersion: ApplicationVersion, failureCriteria: FailureCriteria, filterSet: '', pollingInterval: '', resultsFile: ResultsFile
    }
    
} 
