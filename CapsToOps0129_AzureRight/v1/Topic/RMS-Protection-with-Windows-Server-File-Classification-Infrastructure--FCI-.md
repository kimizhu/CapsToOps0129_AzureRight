---
title: RMS Protection with Windows Server File Classification Infrastructure (FCI)
ms.custom: na
ms.reviewer: na
ms.service: rights-management
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9aa693db-9727-4284-9f64-867681e114c9
author: Cabailey
---
# RMS Protection with Windows Server File Classification Infrastructure (FCI)
<?xml version="1.0" encoding="UTF-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd" xmlns:xlink="http://www.w3.org/1999/xlink">
    <introduction>
        <para>Use this article for instructions and a script to use the Rights Management (RMS) client with the RMS Protection tool to configure File Server Resource Manager and file classification infrastructure (FCI). </para>
    <para>This solutions lets you automatically protect all files in a folder on a file server running Windows Server, or automatically protect files that meet a specific criteria. For example, files that have been classified as containing confidential or sensitive information. This solution uses <link xlink:href="965581c8-be3c-43b4-8145-5cefd29c7636">Azure Rights Management</link> (Azure RMS) to protect the files, so you must have this technology deployed in your organization. </para><alert class="note">
 <para>Although Azure RMS includes a <externalLink><linkText>connector</linkText><linkUri>https://technet.microsoft.com/library/dn375964.aspx</linkUri></externalLink> that supports file classification infrastructure, that solution supports native protection only—for example, Office files. </para>
<para>To support all file types with file classification infrastructure, you must use the Windows PowerShell <embeddedLabel>RMS Protection</embeddedLabel> module, as documented in this article. The RMS Protection cmdlets, like the RMS sharing application, support generic protection as well as native protection, which means that all files can be protected. For more information about these different protection levels, see the <link xlink:href="d9992e30-f3d1-48d5-aedc-4e721f7d7c25#BKMK_LevelsofProtection">Levels of protection – native and generic</link> section in the <link xlink:href="d9992e30-f3d1-48d5-aedc-4e721f7d7c25">Rights Management sharing application administrator guide</link>.</para></alert><para>The instructions that follow are for Windows Server 2012 R2 or Windows Server 2012. If you run other supported versions of Windows, you might need to adapt some of the steps for differences between your operating system version and the one documented in this article.</para></introduction>
    <section>
        <title>Prerequisites for Azure RMS protection with Windows Server FCI</title>
        <content>
            <para>Prerequisites for these instructions: </para>
        <list class="bullet"><listItem><para>On each file server where you will run File Resource Manager with file classification infrastructure:</para><list class="bullet"><listItem><para>You have installed File Server Resource Manager as one of the role services for the File Services role.</para></listItem><listItem><para>You have identified a local folder that contains files to protect with Rights Management. For example, C:\FileShare.</para></listItem><listItem><para>You have installed the RMS Protection tool, including the prerequisites for the tool (such as the RMS client) and for Azure RMS (such as the service principal account). For more information, see <externalLink><linkText>RMS Protection Cmdlets</linkText><linkUri>https://msdn.microsoft.com/library/azure/mt433195.aspx</linkUri></externalLink>.</para></listItem><listItem><para>If you want to change the default level of RMS protection (native or generic) for specific file name extensions, you have edited the registry as described in the <externalLink><linkText>File API configuration</linkText><linkUri>https://msdn.microsoft.com/library/dn197834(v=vs.85).aspx</linkUri></externalLink> page.</para></listItem><listItem><para>You have an Internet connection, with configured computer settings if required for a proxy server. For example: <codeInline>netsh winhttp import proxy source=ie</codeInline></para></listItem></list></listItem><listItem><para>You have configured the additional prerequisites for your Azure Rights Management deployment, as described in <externalLink><linkText>about_RMSProtection_AzureRMS</linkText><linkUri>https://msdn.microsoft.com/library/mt433202.aspx</linkUri></externalLink>. Specifically, you have the following values to connect to Azure RMS by using a service principal:</para><list class="bullet"><listItem><para>BposTenantId</para></listItem><listItem><para>AppPrincipalId</para></listItem><listItem><para>Symmetric key</para></listItem></list></listItem><listItem><para>You have synchronized your on-premises Active Directory user accounts with Azure Active Directory or Office 365, including their email address. This is required for all users that might need to access files after they are protected by FCI and Azure RMS. If you do not  do this step (for example, in a test environment), users might be blocked from accessing these files. If you need more information about this account configuration, see <link xlink:href="afbca2d6-32a7-4bda-8aaf-9f93f5da5abc">Preparing for Azure Rights Management</link>.</para></listItem><listItem><para>You have identified the Rights Management template to use, which will protect the files. Make sure that you know the ID for this template by using the <externalLink><linkText>Get-RMSTemplate</linkText><linkUri>https://msdn.microsoft.com/library/azure/mt433197.aspx</linkUri></externalLink> cmdlet.</para></listItem></list></content>
        
    </section>
    <section>
<title>Instructions to configure File Server Resource Manager FCI for Azure RMS protection </title><content><para>Follow these instructions to automatically protect all files in a folder, by using a Windows PowerShell script as a custom task. Do these procedures in this order:</para><list class="ordered"><listItem><para>Save the Windows PowerShell script</para></listItem><listItem><para>Create a classification property for Rights Management (RMS)</para></listItem><listItem><para>Create a classification rule (Classify for RMS)</para></listItem><listItem><para>Configure the classification schedule</para></listItem><listItem><para>Create a custom file management task (Protect files with RMS)</para></listItem><listItem><para>Test the configuration by manually running the rule and task</para></listItem></list><para>At the end of these instructions, all files in your selected folder will be classified with the custom property of RMS, and these files will then be protected by Rights Management. For a more complex configuration that selectively protects some files and not others, you can then create or use a different classification property and rule, with a file management task that protects just those files.</para><procedure>
<title>Save the Windows PowerShell script</title>
 <steps class="ordered">
        <step><content><para>Expand the <link xlink:href="#BKMK_RMSProtection_Script">Windows PowerShell Script</link> section in this article, and copy its contents. Paste the contents of the script and  name the file <system>RMS-Protect-FCI.ps1</system> on your own computer. </para></content></step>
        <step><content><para>Review the script and make the following changes:</para><list class="bullet"><listItem><para>Search for the following string and replace it with your own AppPrincipalId that you use with the <externalLink><linkText>Set-RMSServerAuthentication</linkText><linkUri>https://msdn.microsoft.com/library/mt433199.aspx</linkUri></externalLink> cmdlet to connect to Azure RMS:</para><code>&lt;enter your AppPrincipalId here&gt;</code><para>For example, the script might look like this:</para><para><codeInline>[Parameter(Mandatory = $false)]
            </codeInline></para><para><codeInline>[Parameter(Mandatory = $false)]
            [string]$AppPrincipalId = "b5e3f76a-b5c2-4c96-a594-a0807f65bba4",</codeInline></para></listItem><listItem><para>Search for the following string and replace it with your own symmetric key that you use with the <externalLink><linkText>Set-RMSServerAuthentication</linkText><linkUri>https://msdn.microsoft.com/library/mt433199.aspx</linkUri></externalLink> cmdlet to connect to Azure RMS:</para><code>&lt;enter your key here&gt;</code><para>For example, the script might look like this:</para><para><codeInline>[Parameter(Mandatory = $false)]
            </codeInline></para><para><codeInline>[string]$SymmetricKey = "zIeMu8zNJ6U377CLtppkhkbl4gjodmYSXUVwAO5ycgA="</codeInline></para></listItem><listItem><para>Search for the following string and replace it with your own BposTenantId (tenant ID) that you use with the <externalLink><linkText>Set-RMSServerAuthentication</linkText><linkUri>https://msdn.microsoft.com/library/mt433199.aspx</linkUri></externalLink> cmdlet to connect to Azure RMS:</para><code>&lt;enter your BposTenantId here&gt;</code><para>For example, the script might look like this:</para><para><codeInline>[Parameter(Mandatory = $false)]
            </codeInline></para><para><codeInline>[string]$BposTenantId = "23976bc6-dcd4-4173-9d96-dad1f48efd42",</codeInline></para></listItem><listItem><para>If your server is running Windows Server 2012, you might have to manually load the RMSProtection module at the beginning of the script. Add the following command (or equivalent if  the "Program Files"  folder is  on a drive other than the  C: drive :</para><code>Import-Module "C:\Program Files\WindowsPowerShell\Modules\RMSProtection\RMSProtection.dll"</code></listItem></list></content></step>
      <step>
 <content><para>Sign the script. If you do not sign the script (more secure), you must configure Windows PowerShell on the servers that run it. For example, run a Windows PowerShell session with the <ui>Run as Administrator</ui> option, and type: <userInput>Set-ExecutionPolicy Unrestricted</userInput>. However, this configuration lets all unsigned scripts run (less secure). </para><para>For more information about signing Windows PowerShell scripts, see <externalLink><linkText>about_Signing</linkText><linkUri>https://technet.microsoft.com/library/hh847874.aspx</linkUri></externalLink> in the PowerShell documentation library.</para></content>
</step><step>
 <content><para>Save the file locally on each file server that will run File Resource Manager with file classification infrastructure. For example, save the file in <system>C:\RMS-Protection</system>. Secure this file by using NTFS permissions so that unauthorized users cannot modify it.</para></content>
</step></steps>
<conclusion><content><para>You're now ready to start configuring File Server Resource Manager.</para></content></conclusion></procedure><procedure>
<title>Create a classification property for Rights Management (RMS)</title>
 <steps class="bullet">
        <step><content><para>In File Server Resource Manager, Classification Management, create a new local property:</para><list class="bullet"><listItem><para><ui>Name</ui>: Type <userInput>RMS</userInput></para></listItem><listItem><para><ui>Description</ui>:   Type <userInput>Rights Management protection</userInput></para></listItem><listItem><para><ui>Property Type</ui>: Select <ui>Yes/No</ui></para></listItem><listItem><para><ui>Value</ui>: Select <ui>Yes</ui></para></listItem></list></content></step>
        
      </steps>
<conclusion><content><para>We can now create a classification rule that uses this property.</para></content></conclusion></procedure><procedure>
<title>Create a classification rule (Classify for RMS)</title>
 <steps class="bullet">
        <step><content><para>Create a new classification rule:</para><list class="bullet"><listItem><para>On the <ui>General</ui> tab:</para><list class="bullet"><listItem><para><ui>Name</ui>: Type<userInput> Classify for RMS</userInput></para></listItem><listItem><para><ui>Enabled</ui>: Keep the default, which is that this checkbox is selected.</para></listItem><listItem><para><ui>Description</ui>: Type <userInput>Classify all files in the &lt;folder name&gt; folder for Rights Management</userInput>. </para><para>Replace <placeholder>&lt;folder name&gt;</placeholder> with your chosen folder name. For example, <ui>Classify all files in the C:\FileShare folder for Rights Management</ui></para></listItem><listItem><para><ui>Scope</ui>: Add your chosen folder. For example, <ui>C:\FileShare</ui>.</para><para>Do not select the checkboxes.</para></listItem></list></listItem><listItem><para>On the <ui>Classification</ui> tab:</para></listItem><listItem><para><ui>Classification method</ui>: Select <ui>Folder Classifier</ui></para></listItem><listItem><para><ui>Property</ui> name: Select <ui>RMS</ui></para></listItem><listItem><para>Property <ui>value</ui>: Select <ui>Yes</ui></para></listItem></list></content></step>
        
      </steps>
<conclusion><content><para>Although you can run the classification rules manually, for ongoing operations, you will want this rule to run on a schedule so that new files will be classified with the RMS property.</para></content></conclusion></procedure><procedure>
<title>Configure the classification schedule</title>
 <steps class="bullet">
        <step><content><para>On the <ui>Automatic Classification</ui> tab:</para><list class="bullet"><listItem><para><ui>Enable fixed schedule</ui>: Select this checkbox.</para></listItem><listItem><para>Configure the schedule for all classification rules to run, which includes our new rule to classify files with the RMS property.</para></listItem><listItem><para><ui>Allow continuous classification for new files</ui>: Select this checkbox so that new files will be classified.</para></listItem><listItem><para>Optional: Make any other changes that you want, such as configuring options for reports and notifications.</para></listItem></list></content></step>
        
      </steps>
<conclusion><content><para>Now you've completed the classification configuration, you're ready to configure a management task to apply the RMS protection to the files.</para></content></conclusion></procedure><procedure>
<title>Create a custom file management task (Protect files with RMS)</title>
 <steps class="bullet">
        <step><content><para>In <ui>File Management Tasks</ui>, create a new file management task:</para><list class="bullet"><listItem><para>On the <ui>General</ui> tab:</para><list class="bullet"><listItem><para><ui>Task name</ui>: Type <userInput>Protect files with RMS</userInput></para></listItem><listItem><para>Keep the <ui>Enable</ui> checkbox selected.</para></listItem><listItem><para><ui>Description</ui>: Type <userInput>Protect files in &lt;folder name&gt; with Rights Management and a template by using a Windows PowerShell script. </userInput></para><para>Replace <placeholder>&lt;folder name&gt;</placeholder> with your chosen folder name. For example, <ui>Protect files in C:\FileShare with Rights Management and a template by using a Windows PowerShell script</ui></para></listItem><listItem><para><ui>Scope</ui>: Select your chosen folder. For example, <ui>C:\FileShare</ui>.</para><para>Do not select the checkboxes.</para></listItem></list></listItem><listItem><para>On the <ui>Action</ui> tab:</para><list class="bullet"><listItem><para><ui>Type</ui>: Select <ui>Custom</ui></para></listItem><listItem><para><ui>Executable</ui>: Specify the following:</para><code>C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe</code><para>If Windows is not on your C: drive, modify this path or browse to this file.</para></listItem><listItem><para><ui>Argument</ui>: Specify the following, supplying your own values for &lt;path&gt; and &lt;template GUID&gt;:</para><code>-Noprofile -Command "&lt;path&gt;\RMS-Protect-FCI.ps1 -File '[Source File Path]' -TemplateID &lt;template GUID&gt; -OwnerMail [Source File Owner Email]"</code><para>For example, if you copied the script to C:\RMS-Protection and the template ID you identified from the prerequisites is e6ee2481-26b9-45e5-b34a-f744eacd53b0, specify the following: </para><para><codeInline>-Noprofile -Command "C:\RMS-Protection\RMS-Protect-FCI.ps1 -File '[Source File Path]' -TemplateID e6ee2481-26b9-45e5-b34a-f744eacd53b0 -OwnerMail [Source File Owner Email]"</codeInline></para><para>In this command, <ui>[Source File Path]</ui> and <ui>[Source File Owner Email]</ui> are both FCI-specific variables, so type these exactly as they appear in the command above. The first one is used by FCI to automatically specify the identified file in the folder, and the second is for FCI to automatically retrieve the email address of the named Owner of the identified file. This command is repeated for each file in the folder, which in our example, is each file in the C:\FileShare folder that additionally, has RMS as a file classification property.</para><alert class="note">
 <para>The<system> -OwnerMail [Source File Owner Email]</system> parameter and value ensures that the original owner of the file is granted the Rights Management owner of the file after it is protected. This ensures that the original file owner has all Rights Management rights to their own files. When files are created by a domain user, the email address is  automatically retrieved from Active Directory by using the user account name in the file's Owner property. To do this, the file server must be in the same domain or trusted domain as the user.</para>
<para>Whenever possible, assign the original owners to protected documents, to ensure that these users continue to have full control over the files that they created. However, if you use the [Source File Owner Email] variable as above, and a file does not have a domain user defined as the owner (for example, a local account was used to create the file, so the owner displays SYSTEM), the script will fail.</para><para>For files that do not have a domain user as owner, you can either copy and save these files yourself as a domain user, so that you become the owner for just these files. Or, if you have permissions, you can manually change the owner.  Or alternatively, you can supply a specific email address (such as your own or a group address for the IT department) instead of the [Source File Owner Email] variable, which means that all files you protect by using this script will use this email address to define the new owner.</para></alert></listItem></list></listItem><listItem><para><ui>Run the command as</ui>: Select <ui>Local System</ui></para></listItem><listItem><para>On the <ui>Condition</ui> tab:</para><list class="bullet"><listItem><para><ui>Property</ui>: Select <ui>RMS</ui> </para></listItem><listItem><para><ui>Operator</ui>: Select <ui>Equal</ui> </para></listItem><listItem><para><ui>Value</ui>: Select <ui>Yes</ui> </para></listItem></list></listItem><listItem><para>On the <ui>Schedule</ui> tab:</para><list class="bullet"><listItem><para><ui>Run at</ui>: Configure your preferred schedule. </para><para>Allow plenty of time for the script to complete. Although this solution  protects all files in the folder, the script runs once for each file, each time. Although this takes longer than protecting all the files at the same time, which the RMS Protection tool supports, this file-by-file configuration for FCI is more powerful. For example, the protected files can have different owners (retain the original owner) when you use the   [Source File Owner Email] variable, and this file-by-file action will be required if you later change the configuration to selectively protect files rather than all files in a folder. </para></listItem><listItem><para><ui>Run continuously on new files</ui>: Select this checkbox.</para></listItem></list></listItem></list></content></step>
        
      </steps>
</procedure><procedure>
<title>Test the configuration by manually running the rule and task</title>
 <steps class="ordered">
        <step><content><para>Run the classification rule: </para><list class="ordered"><listItem><para>Click <ui>Classification Rules</ui> &gt; <ui>Run Classification With All Rules Now</ui></para></listItem><listItem><para>Click <ui>Wait for classification to complete</ui>, and then click <ui>OK</ui>.</para></listItem></list></content></step>
        <step><content><para>Wait for the <ui>Running Classification</ui> dialog box to close and then view the results in the automatically displayed report. You should see <ui>1</ui> for the <ui>Properties</ui> field and the number of files in your folder. Confirm by using File Explorer and checking the properties of files in your chosen folder. On the <ui>Classification</ui> tab, you should see <ui>RMS</ui> as a property name and <ui>Yes</ui> for its <ui>Value</ui>.</para></content></step>
      <step>
 <content><para>Run the file management task: </para><list class="ordered"><listItem><para>Click <ui>File Management Tasks</ui> &gt; <ui>Protect files with RMS</ui>  &gt; <ui>Run File Management Task Now</ui></para></listItem><listItem><para>Click <ui>Wait for the task to complete</ui>, and then click <ui>OK</ui>.</para></listItem></list></content>
</step><step>
 <content><para>Wait for the <ui>Running File Management Task</ui> dialog box to close and then view the results in the automatically displayed report. You should see the number of files that are in your chosen folder in the <ui>Files</ui> field. Confirm that the files in your chosen folder are now protected by RMS. For example, if your chosen folder is C:\FileShare, type the following in a Windows PowerShell session and confirm that no files have a status of <ui>UnProtected</ui>: </para><code>foreach ($file in (Get-ChildItem -Path C:\FileShare -Force | where {!$_.PSIsContainer})) {Get-RMSFileStatus -f $file.PSPath}</code><alert class="tip">
 <para>Some troubleshooting tips:</para><list class="bullet"><listItem><para>If you see <ui>0</ui> in the report, instead of the number of files in your folder, this indicates that the script did not run. First, check the script itself by loading it in Windows PowerShell ISE to validate the script contents and try running it to see if any errors are displayed. With no arguments specified, the script will try to connect and authenticate to Azure RMS.    </para><list class="bullet"><listItem><para>If the script reports that it couldn't connect to Azure RMS, check the values it displays for the service principal account, which you specified in the script.  For more information about how to create this service principal account, see the second prerequisite in <externalLink><linkText>about_RMSProtection_AzureRMS</linkText><linkUri>https://msdn.microsoft.com/library/mt433202.aspx</linkUri></externalLink></para></listItem><listItem><para>If the script reports that it could connect to Azure RMS and your Azure region is outside North America, check that you have edited the registry correctly for this configuration. A good test for this is to run Get-RMSTemplate directly from Windows PowerShell on the server. For more information about the registry edits, see the third prerequisite in <externalLink><linkText>about_RMSProtection_AzureRMS</linkText><linkUri>https://msdn.microsoft.com/library/mt433202.aspx</linkUri></externalLink>.</para></listItem></list></listItem><listItem><para>If the script by itself runs in Windows PowerShell ISE without errors, try running it as follows from a  PowerShell session, specifying a file name to protect and without the -OwnerEmail parameter:</para><code>powershell.exe -Noprofile -Command "&lt;path&gt;\RMS-Protect-FCI.ps1 -File &lt;full path and name of a file&gt;' -TemplateID &lt;template GUID&gt;"</code><list class="bullet"><listItem><para>If the script runs successfully in this Windows PowerShell session, check  your entries for <ui>Executive</ui> and <ui>Argument</ui> in the file management task action.  If you have specified<ui> -OwnerEmail [Source File Owner Email]</ui>, try removing this parameter.  </para><para>If the file management task works successfully without <ui> -OwnerEmail [Source File Owner Email]</ui>, check that the unprotected files have a domain user listed as the file owner, rather than <ui>SYSTEM</ui>.  To do this, use the <ui>Security</ui> tab for the file's properties, and then click <ui>Advanced</ui>. The <ui>Owner</ui> value is displayed immediately after the file <ui>Name</ui>. Also, verify that the file server is in the same domain or a trusted domain to lookup the user's email address from Active Directory Domain Services.</para></listItem></list></listItem><listItem><para>If you see the correct number of files in the report but the files are not protected, try protecting the files manually by using the <externalLink><linkText>Protect-RMSFile</linkText><linkUri>https://msdn.microsoft.com/library/azure/mt433201.aspx</linkUri></externalLink> cmdlet, to see if any errors are displayed.  </para></listItem></list>
</alert></content>
</step></steps>
<conclusion><content><para>When you have confirmed that these tasks run successfully, you can close File Resource Manager. New files will be automatically protected and all files will be protected again when the schedules run. Re-protecting files ensures that any changes to the template are applied to the files.</para></content></conclusion></procedure></content>
<sections><section expanded="false" address="BKMK_RMSProtection_Script">
<title>Windows PowerShell Script for Azure RMS protection by using File Server Resource Manager FCI</title><content><para>This section contains the sample script to copy and edit, as described in the preceding section.</para><para><legacyItalic><legacyBold>Disclaimer</legacyBold>: This sample script is not supported under any Microsoft standard support program or service. This sample
script is provided AS IS without warranty of any kind.</legacyItalic></para><code>&lt;#
.SYNOPSIS 
     Helper script to protect all file types with Azure RMS and FCI.
.DESCRIPTION
     Protect files with Azure RMS and Windows Server FCI, using an RMS template ID.   
#&gt;
param(
            [Parameter(Mandatory = $false)]
            [ValidateScript({ If($_ -eq "") {$true} else { if (Test-Path -Path $_ -PathType Leaf) {$true} else {throw "Can't find file specified"} } })]
            [string]$File,
                               
            [Parameter(Mandatory = $false)]
            [string]$TemplateID,

            [Parameter(Mandatory = $false)]
            [string]$OwnerMail,

            [Parameter(Mandatory = $false)]
            [string]$AppPrincipalId = "&lt;enter your AppPrincipalId here&gt;",

            [Parameter(Mandatory = $false)]
            [string]$SymmetricKey = "&lt;enter your key here&gt;",

            [Parameter(Mandatory = $false)]
            [string]$BposTenantId = "&lt;enter your BposTenantId here&gt;"
) 

# script information
[String] $Script:Version = 'version 1.0' 
[String] $Script:Name = "RMS-Protect-FCI.ps1"

#global working variables
[switch] $Script:isScriptProcess = $False # Controls the script process. If false, the script gracefully stops running.

#**Functions (general helper)***************************************
function Get-ScriptName(){ 
	
	return $MyInvocation.ScriptName.Substring($MyInvocation.ScriptName.LastIndexOf('\') + 1, $MyInvocation.ScriptName.LastIndexOf('.') - $MyInvocation.ScriptName.LastIndexOf('\') - 1)
}

#**Functions (script specific)**************************************

function Check-Module{
	
	param ([String]$Module = $(Throw "Module name not specified"))
    
	[bool]$isResult = $False

	#try to load the module
	if (get-module -list -name $Module) {
		import-module $Module

		if (get-module -name $Module ) {
			
			$isResult = $True
		} else {
			$isResult = $False
		} 

	} else {
			$isResult = $False
	}
	return $isResult
}

function Protect-File ($ffile, $ftemplateId, $fownermail) {
	
    [bool] $returnValue = $false
    try {
        If ($OwnerMail -eq $null -or $OwnerMail -eq "") {
            $protectReturn = Protect-RMSFile -File $ffile -TemplateID $ftemplateId
            $returnValue = $true
            Write-Host ( "Information: " + "Protected File: $ffile with Template: $ftemplateId")
        } else {
            $protectReturn = Protect-RMSFile -File $ffile -TemplateID $ftemplateId -OwnerEmail $fownermail
            $returnValue = $true
            Write-Host ( "Information: " + "Protected File: $ffile with Template: $ftemplateId, set Owner: $fownermail")
        }
    } catch {
        Write-Host ( "ERROR" + "During protection of file: $ffile with Template: $ftemplateId")
            }
    return $returnValue
}

function Set-RMSConnection ($fappId, $fkey, $fbposId) {

	[bool] $returnValue = $false
    try {
               Set-RMSServerAuthentication -AppPrincipalId $fappId -Key $fkey -BposTenantId $fbposId
        Write-Host ("Information: " + "Connected to Azure RMS Service with BposTenantId: $fbposId using AppPrincipalId: $fappId")
        $returnValue = $true
    } catch {
        Write-Host ("ERROR" + "During connection to Azure RMS Service with BposTenantId: $fbposId using AppPrincipalId: $fappId")
        
    }
    return $returnValue
}

#**Main Script (Script)*********************************************
Write-Host ("-== " + $Script:Name + " " + $Version + " ==-")

$Script:isScriptProcess = $True

# Validate Azure RMS connection by checking the module and then connection
if ($Script:isScriptProcess) {
 		if (Check-Module -Module RMSProtection){
    	$Script:isScriptProcess = $True
	} else {
		
		Write-Host ("The RMSProtection module is not loaded") -foregroundcolor "yellow" -backgroundcolor "black"	        
		$Script:isScriptProcess = $False
	}
}

if ($Script:isScriptProcess) {
	#Write-Host ("Try to connect to Azure RMS with AppId: $AppPrincipalId and BPOSID: $BposTenantId" )	
    if (Set-RMSConnection $AppPrincipalId $SymmetricKey $BposTenantId) {
	    Write-Host ("Connected to Azure RMS")
		
    } else {
		Write-Host ("Couldn't connect to Azure RMS") -foregroundcolor "yellow" -backgroundcolor "black"
		$Script:isScriptProcess = $False
	}
}

#  Start working loop
if ($Script:isScriptProcess) {
    if ( !(($File -eq $null) -or ($File -eq "")) ) {
        if (!(Protect-File -ffile $File -ftemplateId $TemplateID -fownermail $OwnerMail)) {
            $Script:isScriptProcess = $False           
        }
    }
}

# Closing
if (!$Script:isScriptProcess) { Write-Host "ERROR occurred during script process" -foregroundcolor "red" -backgroundcolor "black"}
write-host ("-== " + $Script:Name + " " + $Version + "  ==-")
if (!$Script:isScriptProcess) { exit(-1) } else {exit(0)}</code></content>
</section></sections></section><section>
<title>Modifying the instructions to selectively protect files</title><content><para>When you have the preceding instructions working, it's then very easy to modify them for a more sophisticated configuration. For example, protect files by using the same script but only for files that contain personal identifiable information, and perhaps select a template that has more restrictive rights.</para><para>To do this, use one of the built-in classification properties (for example, <ui>Personally Identifiable Information</ui>) or create your own new property. Then create a new rule that uses this property. For example, you might select the <ui>Content Classifier</ui>, choose the <ui>Personally Identifiable Information</ui> property with a value of <ui>High</ui>, and configure the string or expression pattern that identifies the file to be configured for this property (such as the  string "<userInputLocalizable>Date of Birth</userInputLocalizable>"). </para><para>Now all you need to do is create a new file management task that uses the same script but perhaps with a different template, and configure the condition for the classification property that you have just configured. For example, instead of the condition that we configured previously (<ui>RMS</ui> property, <ui>Equal</ui>, <ui>Yes</ui>), select the <ui>Personally Identifiable Information</ui> property with the <ui>Operator</ui> value set to <ui>Equal</ui> and the <ui>Value</ui> of <ui>High</ui>.</para></content>
</section><relatedTopics/>
</developerConceptualDocument>
