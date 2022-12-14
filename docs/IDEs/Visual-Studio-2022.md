![Veracode Demo Labs](/images/veracode-demo-labs-banner-wide.png)

[Return to Home](/)  |  [Return to GitHub/Veracode-Demo-Labs](https://github.com/veracode-demo-labs)

# Visual Studio 2022

Open the VeraDemo-DotNet project.

![VSCode](images/VisualStudio-2022/VS-2022-1.png)

Try to build the solution and make sure the project builds properly before proceeding.

## Submit Greenlight IDE Static scan

See more about Greenlight here - [https://docs.veracode.com/r/c_master_greenlight](https://docs.veracode.com/r/c_master_greenlight)

Right-click the Controllers folder and click Scan with Veracode Greenlight.

![VSCode](images/VisualStudio-2022/VS-2022-2.png)

The bottom left shows a messaging stating "Scanning Controllers".
![VSCode](images/VisualStudio-2022/VS-2022-3.png)

SAST results are returned.  Review the results and the remediation details link.
![VSCode](images/VisualStudio-2022/VS-2022-4.png)

## Submit a SAST/SCA Sandbox scan

Click the Veracode Static Scan tab on the bottom, or click Extensions - 
![VSCode](images/VisualStudio-2022/VS-2022-5.png)

A wizard will pop up to help configure the project.
![VSCode](images/VisualStudio-2022/VS-2022-6.png)

Go to the Veracode platform and create a new application profile and a new Sandbox in that profile.

![VSCode](images/VisualStudio-2022/VS-2022-7.png)

The wizard will allow you to select that profile and sandbox.
![VSCode](images/VisualStudio-2022/VS-2022-8.png)

This is the Veracode scan configuration files stored with the project.
![VSCode](images/VisualStudio-2022/VS-2022-9.png)

Run the Package step to create a artifact of the DotNet app for scanning.
![VSCode](images/VisualStudio-2022/VS-2022-10.png)

Click the Run Scan button to submit a SAST/SCA sandbox scan.
![VSCode](images/VisualStudio-2022/VS-2022-11.png)

## Remediate | re-scan | no new flaws
While we wait a few minutes for that to complete, lets fix a SQLi issue and resubmit the scan.  In HomeController.cs, comment out the two bad code sections, and uncomment the two good code sections.
![VSCode](images/VisualStudio-2022/VS-2022-13.png)

Should look like this.
![VSCode](images/VisualStudio-2022/VS-2022-14.png)

Click the V in the toolbar to scan the file with Greenlight. You can monitor the output folder to see it running.
![VSCode](images/VisualStudio-2022/VS-2022-15.png)

You should see the SQLi now removed from the Veracode Greenlight Findings tab.
![VSCode](images/VisualStudio-2022/VS-2022-16.png)

Lets submit another version to the sandbox without the SQLi.  First make sure the existing scan completed (should take a few minutes).
![VSCode](images/VisualStudio-2022/VS-2022-17.png)

Once completed we can submit a new sandbox scan. While you are here, click into the sandbox to review the report.
![VSCode](images/VisualStudio-2022/VS-2022-18.png)

This is the Triage Flaws view.
![VSCode](images/VisualStudio-2022/VS-2022-19.png)

Back to the Veracode Static Anlasys tab we can submit another version to the sandbox.  Click Publish and Package.
![VSCode](images/VisualStudio-2022/VS-2022-20.png)

Then Run Scan.
![VSCode](images/VisualStudio-2022/VS-2022-21.png)

Click Extensions - Veracode Static Analysis - View Results - View Results (Sandbox) to download the findings from our first scan.  The SQLi exists.
![VSCode](images/VisualStudio-2022/VS-2022-24.png)

Once the second sandbox scan completes, download the results again.
![VSCode](images/VisualStudio-2022/VS-2022-25.png)

![VSCode](images/VisualStudio-2022/VS-2022-26.png)

The SQLi is now gone.
![VSCode](images/VisualStudio-2022/VS-2022-27.png)

Visit the sandbox to see two completed scans.
![VSCode](images/VisualStudio-2022/VS-2022-28.png)

Click Results Latest on the left side to see that one issue has been fixed.
![VSCode](images/VisualStudio-2022/VS-2022-29.png)

While you are here, review the Software Composition Analysis page.
![VSCode](images/VisualStudio-2022/VS-2022-30.png)

Next steps would be:
* Remediate or mitigate any issues that violate policy 
* Automate scans via CI/CD to prevent new flaws from being committed.
* Connect bug tracking systems to establish a continuos feedback loop of any issues.  
* Establish a recurring DAST scan.
* Developer training


[Return to Home](/)  |  [Return to GitHub/Veracode-Demo-Labs](https://github.com/veracode-demo-labs)