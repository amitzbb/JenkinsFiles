pipeline {
    agent { node { label 'Dev-Pilot' } }

    stages {
        stage('Parallel Build') {
            steps {
                parallel (
                    "FoxUT" : {
                        bat '''@echo off
                     @echo %date% %time%
                    @echo Fox UT
                    @echo ======
                    "C:\\Program Files (x86)\\NUnit.org\\nunit-console\\nunit3-console.exe" "C:\\Users\\master.I-BRITANNICA\\Fox8\\Fox8\\Dev\\Code\\FoxUT\\bin\\Release\\FoxUT.dll"'''
                    } ,


                    "Old Engine" : {
                        bat '''@echo off
                        @echo %date% %time%
                        @echo Optimization UT
                        @echo ===============
                        "C:\\Program Files (x86)\\NUnit.org\\nunit-console\\nunit3-console.exe" "C:\\Users\\master.I-BRITANNICA\\Fox8\\Fox8\\Dev\\OptimizationServer\\Code\\OptimizationUT\\bin\\OptimizationUT.dll"'''
                    } ,

                    "New Engine" : {
                        bat '''@echo off
                    @echo %date% %time%
                    @echo New Optimization Engine UT
                    @echo ==========================
                    "C:\\Program Files (x86)\\NUnit.org\\nunit-console\\nunit3-console.exe" "C:\\Users\\master.I-BRITANNICA\\Fox8\\Fox8\\Dev\\Optimization\\SchedulerEngine\\UnitTests\\bin\\UnitTests.dll"'''
                    } 
                    
                )
            }
        }

    }

    post {
        success {
            emailext body: '''$DEFAULT_CONTENT
                            The site can be reached at:
                            http://dev-pilot.bks/Login.aspx''', subject: 'Dev-Pilot Unit Tests status', to: 'Innar@Britannica-ks.com;Baraku@Britannica-ks.com'
        }

        failure {
            emailext body: '''$DEFAULT_CONTENT
                            The site can be reached at:
                            http://dev-pilot.bks/Login.aspx''', subject: 'Dev-Pilot Unit Tests status', to: 'amitbl@britannica-ks.com;Baraku@Britannica-ks.com'
        }
    }
}
