![Veracode Demo Labs](/images/veracode-demo-labs-banner-wide.png)

[Return to Home](/)  |  [Return to GitHub/Veracode-Demo-Labs](https://github.com/veracode-demo-labs)

# IntelliJ

Begin by ensuring the project builds.
![IntelliJ](images/IntelliJ/IntelliJ-1.png)

Pull up the terminal using ALT+F12 or from the main menu, select View | Tool Windows | Terminal 

![IntelliJ](images/IntelliJ/IntelliJ-1.2.png)

Type in "cd app"
then "mvn clean install"
This will create verademo.war in the target folder.
![IntelliJ](images/IntelliJ/IntelliJ-1.3.png)

## Submit Scan with Greenlight

See more about Greenlight here - [https://docs.veracode.com/r/c_master_greenlight](https://docs.veracode.com/r/c_master_greenlight)

Right click on the main folder and click Veracode Greenlight to submit a scan.
![IntelliJ](images/IntelliJ/IntelliJ-2.png)

Review results and organize by Severity.
![IntelliJ](images/IntelliJ/IntelliJ-3.png)

## Submit SAST/SCA sandbox scan

In the platform create an application profile and a sandbox.
![IntelliJ](images/IntelliJ/IntelliJ-6.png)

From IntelliJ, click Veracode - Upload and Scan
![IntelliJ](images/IntelliJ/IntelliJ-5.png)

Cancel out of the first screen so you can properly set the application profile and sandbox.
![IntelliJ](images/IntelliJ/IntelliJ-7.png)

Add the verademo.war file to the upload
![IntelliJ](images/IntelliJ/IntelliJ-8.png)


![IntelliJ](images/IntelliJ/IntelliJ-9.png)

Submit the scan
![IntelliJ](images/IntelliJ/IntelliJ-10.png)

## Remediate | re-scan | no new flaws
While we wait a few minutes for that to complete, lets fix a SQLi issue and resubmit the scan.  In UserController.java, comment out the two bad code sections, and uncomment the two good code sections.

Locate the SQLi on line 170.
![IntelliJ](images/IntelliJ/IntelliJ-11.png)

Should look like...
![IntelliJ](images/IntelliJ/IntelliJ-12.png)

Should look like...
![IntelliJ](images/IntelliJ/IntelliJ-13.png)

Save the file and submit a Greenlight scan.
![IntelliJ](images/IntelliJ/IntelliJ-14.png)

The issue is now gone.
![IntelliJ](images/IntelliJ/IntelliJ-15.png)

Open the Terminal to recompile the project using "mvn clean install".
![IntelliJ](images/IntelliJ/IntelliJ-16.png)

Submit another sandbox scan - Scan 2.
![IntelliJ](images/IntelliJ/IntelliJ-17.png)

Download results from Scan 1.
![IntelliJ](images/IntelliJ/IntelliJ-18.png)

The SQLi exists.
![IntelliJ](images/IntelliJ/IntelliJ-19.png)

Download results from Scan 2.
![IntelliJ](images/IntelliJ/IntelliJ-20.png)

The flaw is gone.
![IntelliJ](images/IntelliJ/IntelliJ-21.png)

The reporting shows 3 issue fixed.  Two other issues were resolved while fixing the SQLi.

![IntelliJ](images/IntelliJ/IntelliJ-22.png)

Next steps would be:
* Remediate or mitigate any issues that violate policy 
* Automate scans via CI/CD to prevent new flaws from being committed.
* Connect bug tracking systems to establish a continuos feedback loop of any issues.  
* Establish a recurring DAST scan.
* Developer training


[Return to Home](/)  |  [Return to GitHub/Veracode-Demo-Labs](https://github.com/veracode-demo-labs)