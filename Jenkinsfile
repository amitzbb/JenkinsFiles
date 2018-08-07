pipeline {
    agent { node { label 'Dev-CI01' } }

    stages {
        stage('Parallel UT running') {
            steps {
                parallel (
                    "FoxUT" : {
                        bat '''@echo off
                     @echo %date% %time%
                    @echo Fox UT
                    @echo ======
                    "C:\\Program Files (x86)\\NUnit.org\\nunit-console\\nunit3-console.exe" "C:\\Users\\master.I-BRITANNICA\\Fox8\\Fox8\\Dev\\Code\\FoxUT\\bin\\Release\\FoxUT.dll" --work:"C:\\FoxUT\\FoxUT\\TestATestResult.xml"''' 
                    } ,


                    "Old Engine" : {
                        bat '''@echo off
                        @echo %date% %time%
                        @echo Optimization UT
                        @echo ===============
                        "C:\\Program Files (x86)\\NUnit.org\\nunit-console\\nunit3-console.exe" "C:\\Users\\master.I-BRITANNICA\\Fox8\\Fox8\\Dev\\OptimizationServer\\Code\\OptimizationUT\\bin\\OptimizationUT.dll" --work:"C:\\FoxUT\\OldEngine\\TestATestResult.xml"'''
                    } ,

                    "New Engine" : {
                        bat '''@echo off
                    @echo %date% %time%
                    @echo New Optimization Engine UT
                    @echo ==========================
                    "C:\\Program Files (x86)\\NUnit.org\\nunit-console\\nunit3-console.exe" "C:\\Users\\master.I-BRITANNICA\\Fox8\\Fox8\\Dev\\Optimization\\SchedulerEngine\\UnitTests\\bin\\UnitTests.dll" --work:"C:\\FoxUT\\NewEngine\\TestATestResult.xml"'''
                    } 
                    
                )
            }
        }

    }

    post {
        success {
            emailext body: '''$DEFAULT_CONTENT
                            The site can be reached at:
                            http://dev-pilot.bks/Login.aspx''', subject: 'Dev-Pilot Unit Tests status', to: 'Innar@Britannica-ks.com;Baraku@Britannica-ks.com;amitbl@britannica-ks.com'
        }

        failure {
            emailext body: '''$DEFAULT_CONTENT
                            The site can be reached at:
                            http://dev-pilot.bks/Login.aspx''', subject: 'Dev-Pilot Unit Tests status', to: 'Innar@Britannica-ks.com;Baraku@Britannica-ks.com;amitbl@britannica-ks.com'
        }
    }
}
