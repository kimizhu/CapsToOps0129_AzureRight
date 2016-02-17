---
title: Rights Management sharing application administrator guide
ms.custom: na
ms.reviewer: na
ms.service: rights-management
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d9992e30-f3d1-48d5-aedc-4e721f7d7c25
author: Cabailey
---
# Rights Management sharing application administrator guide
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Use the following information if you are responsible for the Microsoft Rights Management sharing application on an enterprise network, or if you want more technical information than is in the <link xlink:href="eaf6d02c-aa36-4915-856e-49bb71ab1484">Microsoft Rights Management sharing application User's Guide</link> or <externalLink><linkText>FAQ for Microsoft Rights Management Sharing Application for Windows</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=303971</linkUri></externalLink>:</para>
    <list class="bullet">
      <listItem>
        <para>
          <link xlink:href="d9992e30-f3d1-48d5-aedc-4e721f7d7c25#BKMK_ScriptedInstall">Automatic deployment for the Microsoft Rights Management sharing application</link>
        </para>
        <list class="bullet">
          <listItem>
            <para>
              <link xlink:href="d9992e30-f3d1-48d5-aedc-4e721f7d7c25#BKMK_verifyscripted">Verifying installation success</link>
            </para>
          </listItem>
          <listItem>
            <para>
              <link xlink:href="d9992e30-f3d1-48d5-aedc-4e721f7d7c25#BKMK_uninstallscripted">Uninstall commands </link>
            </para>
          </listItem>
          <listItem>
            <para>
              <link xlink:href="d9992e30-f3d1-48d5-aedc-4e721f7d7c25#BKMK_SuppressAutomaticUpdates">Suppressing automatic updates</link>
            </para>
          </listItem>
          <listItem><para><link xlink:href="#BKMK_DocumentTracking">Azure RMS only: Configuring document tracking</link></para></listItem><listItem>
            <para>
              <link xlink:href="d9992e30-f3d1-48d5-aedc-4e721f7d7c25#BKMK_FederatedDomains">AD RMS only: Support for multiple email domains within your organization </link>
            </para>
          </listItem>
        </list>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="d9992e30-f3d1-48d5-aedc-4e721f7d7c25#BKMK_AdminOverview">Technical overview for the Microsoft Rights Management sharing application </link>
        </para>
        <list class="bullet">
          <listItem>
            <para>
              <link xlink:href="d9992e30-f3d1-48d5-aedc-4e721f7d7c25#BKMK_LevelsofProtection">Levels of protection – native and generic</link>
            </para>
          </listItem>
          <listItem>
            <para>
              <link xlink:href="d9992e30-f3d1-48d5-aedc-4e721f7d7c25#BKMK_SupportFileTypes">Supported file types and file name extensions</link>
            </para>
          </listItem>
          <listItem>
            <para>
              <link xlink:href="d9992e30-f3d1-48d5-aedc-4e721f7d7c25#BKMK_ChangeDefaultProtection">Changing the default protection level of files</link>
            </para>
          </listItem>
        </list>
      </listItem>
    </list>
    <alert class="tip">
      <para>If you are new to the RMS sharing app, or looking for more information, see <externalLink><linkText>How RMS protects all file types – by using the RMS sharing app</linkText><linkUri>https://curah.microsoft.com/191031/how-rms-protects-all-file-types-by-using-the-rms-sharing-app</linkUri></externalLink>.</para>
    </alert>
  <para>The RMS sharing application is best suited to work with Azure RMS, because this deployment configuration supports sending protected attachments to users in another organization, and options such as email notifications and document tracking with revocation.  However, with some limitations, it also works with the on-premises version, AD RMS. For a comprehensive comparison of features that are supported by Azure RMS and AD RMS, see <externalLink><linkText>Comparing Azure Rights Management and AD RMS</linkText><linkUri>https://technet.microsoft.com/library/jj739831.aspx</linkUri></externalLink>. If you have AD RMS and want to migrate to Azure RMS, see <externalLink><linkText>Migrating from AD RMS to Azure Rights Management</linkText><linkUri>https://technet.microsoft.com/library/dn858447.aspx</linkUri></externalLink>.</para></introduction>
  <section DoNotNumber="false" address="BKMK_ScriptedInstall">
    <title>Automatic deployment for the Microsoft Rights Management sharing application</title>
    <content>
      <para/>
      <para>The Windows version of the RMS sharing application supports a scripted installation, which makes it suitable for enterprise deployments. </para>
      <para>The only prerequisites for installations are that the computers run a minimum version of Windows 7 Service Pack 1, <?Comment CB: 9333 2015-02-13T09:52:00Z  Id='0?>and that the Microsoft Framework, minimum version 4.0 is installed. If you need to install the Microsoft .NET Framework 4.0, you can <externalLink><linkText>download it for installation from the Microsoft Download Center</linkText><linkUri>http://www.microsoft.com/download/details.aspx?id=17718</linkUri></externalLink>.<?CommentEnd Id='0'
    ?></para>
      <procedure>
        <title>To download the RMS sharing application for automatic deployment</title>
        <steps class="ordered">
          <step>
            <content>
              <para>Go to the <externalLink><linkText>Microsoft Rights Management sharing application for Windows</linkText><linkUri>http://www.microsoft.com/download/details.aspx?id=40857</linkUri></externalLink> page in the Microsoft Download Center, and click <ui>Download</ui>.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Select and download the files that you need. There are two client installation packages: one for Windows 64-bit (Microsoft Rights Management sharing application x64.zip), and another for Windows 32-bit (Microsoft Rights Management sharing application x86.zip).</para>
            </content>
          </step>
          <step>
            <content>
              <para>Extract the files from the compressed installation packages, for example, by double-clicking them. Then copy the extracted files to a network location that client computers can access.</para>
            </content>
          </step>
        </steps>
      </procedure>
      <para>The setup packages for the RMS sharing application supports different deployment scenarios and includes the following:</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Description</para>
            </TD>
            <TD>
              <para>Deployment scenario</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          
          <tr>
            <TD>
              <para>Microsoft Online Sign-In Assistant</para>
            </TD>
            <TD>
              <para>Office 2010 and Azure RMS</para><para> Office 2013 and Azure RMS if you have not installed the <externalLink><linkText>June 9, 2015, update for Office 2013</linkText><linkUri>https://support.microsoft.com/kb/3054853</linkUri></externalLink> (KB3054853) </para>
              
            <?xm-deletion_mark author="" time="20150930T150439-0800" data="&lt;maml:para xmlns:maml=&quot;http://ddue.schemas.microsoft.com/authoring/2003/5&quot;&gt;For Office 2013, the Sign-In Assistant is not needed if you have installed the &lt;maml:externalLink&gt;&lt;maml:linkText&gt;June 9, 2015, update for Office 2013&lt;/maml:linkText&gt;&lt;maml:linkUri&gt;https://support.microsoft.com/kb/3054853&lt;/maml:linkUri&gt;&lt;/maml:externalLink&gt; (KB3054853). &lt;/maml:para&gt;"?></TD>
          </tr>
          <tr>
            <TD>
              <para>Hotfix for Office (KB 2596501)</para>
            </TD>
            <TD>
              <para>Office 2010 and Azure RMS</para><para>Office 2010 and Active Directory RMS</para>
              
            </TD>
          </tr><tr>
            <TD>
              <para>Hotfix to enable the AD RMS Client 1.0 to work with Azure RMS (KB 2843630)</para>
            </TD>
            <TD>
              <para>Office 2010 and Azure RMS</para><para>Office 2010 and Active Directory RMS</para>
              
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AD RMS Client and the RMS sharing application</para>
            </TD>
            <TD>
              <para>Office 2016 or Office 2013 and Azure RMS or Active Directory RMS</para><para>Office 2010 and Azure RMS </para><para>Office 2010 and Active Directory RMS</para><para>RMS sharing application and Office add-in only</para>
              
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Office add-in for the ribbon</para>
            </TD>
            <TD>
              <para>Office 2016 or Office 2013 and Azure RMS or Active Directory RMS</para><para>Office 2010 and Azure RMS</para><para>Office 2010 and Active Directory RMS</para>
              <para>RMS sharing application and Office add-in only</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Azure Active Directory Rights Management preparation tool</para>
            </TD>
            <TD>
              <para>Office 2010 and Azure RMS</para>
              
            </TD>
          </tr>
        </tbody>
      </table>
      <para/>
      <para>Use the following procedures to identify the commands required to deploy the RMS sharing application for these deployment scenarios:</para>
      <list class="bullet">
        <listItem>
          <para>
            <embeddedLabel>Office 2016 or Office 2013 and Azure RMS or Active Directory RMS</embeddedLabel>
          </para>
          <para>Your users are running Office 2016 or Office 2013, your organization uses Azure RMS or Active Directory RMS, and users collaborate with other organizations who use Azure RMS or Active Directory RMS. </para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Office 2010 and Azure RMS</embeddedLabel>
          </para>
          <para>Your users are running Office 2010, your organization uses Azure RMS, and users collaborate with other organizations who use Azure RMS or Active Directory RMS.</para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Office 2010 and Active Directory RMS</embeddedLabel>
          </para>
          <para>Your users are running Office 2010, your organization uses AD RMS, and users collaborate with other organizations who use Azure RMS.</para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>RMS sharing application and Office add-in only</embeddedLabel>
          </para>
          <para>Your users are running Office 2016, Office 2013, or Office 2010, your organization uses AD RMS, and users do not need to collaborate with other organizations who use Azure RMS. This installation lets you install just the sharing application and Office add-in.</para>
        </listItem>
      </list>
      <alert class="note">
        <?Comment CB: 251446 2015-02-13T09:52:00Z  Id='2?>
        <para>In these scenarios, if your organization is running AD RMS, your users can receive protected content from other organizations who use Azure RMS, but your users cannot send protected content to users in an organization that uses Azure RMS. However, if your organization is running Azure RMS, your users can send and receive protected content from other organizations.<?CommentEnd Id='2'
    ?></para>
      </alert>
      <para>To complete the installation for each procedure, the computer must restart. You can initiate an automatic restart by using a command such as shutdown /i.</para>
      <procedure expanded="false">
        <title>To deploy the RMS sharing application for Office 2016 or Office 2013 and Azure RMS or Active Directory RMS</title>
        <steps class="bullet">
          <step>
            <content>
              <para>On each computer on which you want to install the RMS sharing application and related components, run the following command with elevated privileges:</para>
              <code>setup.exe /s</code>
            </content>
          </step>
        </steps>
        <conclusion>
          <content>
            <para>To verify success, see the <link xlink:href="d9992e30-f3d1-48d5-aedc-4e721f7d7c25#BKMK_verifyscripted">Verifying installation success</link> section in this topic.</para>
          </content>
        </conclusion>
      </procedure>
      <procedure expanded="false">
        <title>To deploy the RMS sharing application for Office 2010 and Azure RMS</title>
        <steps class="ordered">
          <step>
            <content>
              <para>You must be the global administrator for your Office 365 or Azure Active Directory tenant so that you can get your organization’s certification service URL by running the Azure Active Directory Rights Management preparation tool. You need run this tool only once, on a single computer. You will use the certification service URL when you install the RMS sharing application on each computer:</para>
              <list class="ordered">
                <listItem>
                  <para>Log in to a computer by using a local administrator account.</para>
                </listItem>
                <?xm-insertion_mark_start author="" time="20150930T150239-0800"?><listItem><para>On that computer, <externalLink><linkText>download and install the Microsoft Online Sign In Assistant</linkText><linkUri>http://www.microsoft.com/download/details.aspx?id=28177</linkUri></externalLink>.</para></listItem><?xm-insertion_mark_end?><listItem>
                  <para>Run the following command to see displayed on the screen the certification service URL, which you can then copy and save for the next step:</para>
                  <list class="bullet">
                    <listItem>
                      <para>For <?xm-deletion_mark author="" time="20150930T150337-0800" data="Windows 10, "?>Windows 8.1 and Windows 8, 64-bit:</para>
                      <code>x64\aadrmprep.exe /findCertificationUrl /logfile "&lt;log file path and name&gt;"</code>
                    </listItem>
                    <listItem>
                      <para>For <?xm-deletion_mark author="" time="20150930T150345-0800" data="Windows 10, "?>Windows 8.1 and  Windows 8, 32-bit:</para>
                      <code>X86\aadrmprep.exe /findCertificationUrl /logfile "&lt;log file path and name&gt;"</code>
                    </listItem>
                    <listItem>
                      <para>For Windows 7, 64-bit:</para>
                      <code>x64\win7\aadrmprep.exe /findCertificationUrl /logfile "&lt;log file path and name&gt;"</code>
                    </listItem>
                  </list>
                  <alert class="note">
                    <para>This command might prompt you to enter your credentials for Azure. If the computer is not joined to a domain, you will be prompted. If the computer is joined to a domain, the tool might be able to use cached credentials.</para>
                  </alert>
                </listItem>
              </list>
            </content>
          </step>
          <step>
            <content>
              <para>On each computer on which you will install the RMS sharing application, run the following command with elevated privileges:</para>
              <code>setup.exe /s /configureO2010Admin /certificationUrl &lt;certification_url&gt;</code>
            </content>
          </step>
          <step>
            <content>
              <para>On each computer on which you will install the RMS sharing application, users must run the following command (does not need elevated privileges). There are different ways to achieve this, including asking users to run the command (for example, a link in an email message or a link on the help desk portal) or you can add it to their logon script:</para>
              <code>bin\RMSSetup.exe /configureO2010Only</code>
            </content>
          </step>
        </steps>
        <conclusion>
          <content>
            <para>To verify success, see the <link xlink:href="d9992e30-f3d1-48d5-aedc-4e721f7d7c25#BKMK_verifyscripted">Verifying installation success</link> section in this topic.</para>
          </content>
        </conclusion>
      </procedure>
      <procedure expanded="false">
        <title>To deploy the RMS sharing application for Office 2010 and Active Directory RMS</title>
        <steps class="ordered">
          <step>
            <content>
              <para>On each computer on which you will install the RMS sharing application, run the following command with elevated privileges:</para>
              <code>setup.exe /s /configureO2010Admin</code>
            </content>
          </step>
          <step>
            <content>
              <para>On each computer on which you will install the RMS sharing application, users must run the following command (does not need elevated privileges). There are different ways to achieve this, including asking users to run the command (for example, a link in an email message or a link on the help desk portal) or you can add it to their logon script:</para>
              <list class="bullet">
                <listItem>
                  <para>For Windows 10, Windows 8.1  and Windows 8, 64-bit:</para>
                  <code>x64\aadrmprep.exe /configureO2010</code>
                </listItem>
                <listItem>
                  <para>For Windows 10, Windows 8.1 and Windows 8, 32-bit:</para>
                  <code>X86\aadrmprep.exe /configureO2010</code>
                </listItem>
                <listItem>
                  <para>For Windows 7, 64-bit:</para>
                  <code>x64\win7\aadrmpep.exe /configureO2010</code>
                </listItem>
              </list>
            </content>
          </step>
        </steps>
        <conclusion>
          <content>
            <para>To verify success, see the <link xlink:href="d9992e30-f3d1-48d5-aedc-4e721f7d7c25#BKMK_verifyscripted">Verifying installation success</link> section in this topic.</para>
          </content>
        </conclusion>
      </procedure>
      <procedure expanded="false">
        <title>To install the RMS sharing application and Office add-in only</title>
        <steps class="ordered">
          <step>
            <content>
              <para>Install the AD RMS Client and the RMS sharing application by using the following command:</para>
              <list class="bullet">
                <listItem>
                  <para>For 64-bit Windows: </para>
                  <code>x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "&lt;log file path and name&gt;"</code>
                </listItem>
                <listItem>
                  <para>For 32-bit Windows: </para>
                  <code>X86\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "&lt;log file path and name&gt;"</code>
                </listItem>
              </list>
              <para/>
              <para>For example: <codeInline>\\server5\apps\rms\x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "C:\Log files\ipviewerinstall.log"</codeInline></para>
            </content>
          </step>
          <step>
            <content>
              <para>Install the Office add-in by using the following commands:</para>
              <list class="bullet">
                <listItem>
                  <para>For 64-bit version of Office: </para>
                  <code>msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "&lt;log file path and name&gt;"</code>
                </listItem>
                <listItem>
                  <para>For 32-bit version of Office: </para>
                  <code>msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x86\Setup.msi" /L*v "&lt;log file path and name&gt;"</code>
                </listItem>
              </list>
              <para/>
              <para>For example: <codeInline>\\server5\apps\rms\msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "C:\Log files\rmsofficeinstall.log"</codeInline>
</para>
            </content>
          </step>
        </steps>
        <conclusion>
          <content>
            <para>To verify success, see the <link xlink:href="d9992e30-f3d1-48d5-aedc-4e721f7d7c25#BKMK_verifyscripted">Verifying installation success</link> section in this topic.</para>
          </content>
        </conclusion>
      </procedure>
    </content>
    <sections>
      <section address="BKMK_verifyscripted">
        <title>Verifying installation success</title>
        <content>
          <para>You can use the installation log files to verify a successful installation. </para>
          <procedure expanded="false">
            <title>To verify installation success for the RMS sharing application for Office 2016 or Office 2013 and Azure RMS or Active Directory RMS</title>
            <steps class="bullet">
              <step>
                <content>
                  <para>To verify success of the Setup.exe command, on each computer, search for the installation log file <ui>RMInstaller.log</ui> in the <placeholder>%temp%\RMS_installer_&lt;guid&gt;</placeholder> folder, and then identify the exit code.</para>
                  <para>A successful installation has an exit code of 0 and any other number indicates a failed installation.</para>
                  <para>Example log file name: <ui>C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0\RMInstaller.log</ui> </para>
                </content>
              </step>
            </steps>
          </procedure>
          <procedure expanded="false">
            <title>To verify installation success for the RMS sharing application for Office 2010 and Azure RMS</title>
            <steps class="ordered">
              <step>
                <content>
                  <para>To verify success of the Setup.exe command, on each computer, search for the installation log file <ui>RMInstaller.log</ui> in the <placeholder>%temp%\RMS_installer_&lt;guid&gt;</placeholder> folder, and then identify the exit code.</para>
                  <para>A successful installation has an exit code of 0 and any other number indicates a failed installation.</para>
                  <para>Example log file name: <ui>C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0</ui> </para>
                </content>
              </step>
              <step>
                <content>
                  <para>To verify success for the RMSSetup.exe command, the user should have the following files created in their <placeholder>%localappdata%\microsoft\drm</placeholder> folder:</para>
                  <list class="bullet">
                    <listItem>
                      <para>CERT-Machine-2048.drm</para>
                    </listItem>
                    <listItem>
                      <para>CERT-Machine.drm</para>
                    </listItem>
                    <listItem>
                      <para>CLC-*.drm</para>
                    </listItem>
                    <listItem>
                      <para>GIC-*.drm</para>
                    </listItem>
                  </list>
                  <para/>
                  <para>Example of a CLC-*.drm file: </para>
                  <para>
                    <ui>CLC-alice@isvtenant999.onmicrosoft.com-{1b9cfccf;k5b11;k4a10;kac15;k29b2b6980f4c}.drm</ui>
                  </para>
                </content>
              </step>
            </steps>
          </procedure>
          <procedure expanded="false">
            <title>To verify installation success for the RMS sharing application for Office 2010 and Active Directory RMS</title>
            <steps class="ordered">
              <step>
                <content>
                  <para>To verify success of the Setup.exe command, on each computer, search for the installation log file in the <placeholder>%temp%\RMS_installer_&lt;guid&gt;</placeholder> folder, and identify the exit code.</para>
                  <para>A successful installation has an exit code of 0 and any other number indicates a failed installation.</para>
                  <para>Example log file name: <ui>C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0</ui> </para>
                </content>
              </step>
              <step>
                <content>
                  <para>To verify success of the aadrmprep.exe command, on each computer, search for the following text in the installation log file: <ui>aadrmprep.exe exited with status SUCCESS</ui></para>
                  <alert class="note">
                    <para>Sometimes, this installation can run twice; the first occurrence fails and the second is successful.</para>
                  </alert>
                  <para>If you want to manually check the registry changes that this tool makes, they are as follows:</para>
                  <list class="bullet">
                    <listItem>
                      <para>[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\Federation]</para>
                      <para>"FederationHomeRealm"="urn:HostedRmsOnlineService:Certification"</para>
                    </listItem>
                    <listItem>
                      <para>[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\Federation]</para>
                      <para>"FederationHomeRealm"="urn:HostedRmsOnlineService:Certification"</para>
                    </listItem>
                    <listItem>
                      <para>[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\Activation]</para>
                      <para>@="&lt;certification url&gt;"
</para>
                    </listItem>
                    <listItem>
                      <para>[HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\14.0\Common\DRM] 
</para>
                      <para>DefaultUser="&lt;default_user&gt;"</para>
                    </listItem>
                  </list>
                </content>
              </step>
            </steps>
          </procedure>
          <procedure expanded="false">
            <title>To verify installation success for the RMS sharing application and Office add-in only</title>
            <steps class="ordered">
              <step>
                <content>
                  <para>To verify success of the Setup_ipviewer.exe command, search for the following text in the installation log file: <ui>Installation success or error status: 0</ui></para>
                  <para/>
                  <para>Example lines from a successful installation:  </para>
                  <para>
                    <ui>MSI (s) (F0:B8) [14:19:57:854]: Product: Active Directory Rights Management Services Client 2.1 -- Installation completed successfully.</ui>
                  </para>
                  <para>
                    <ui>MSI (s) (F0:B8) [14:19:57:854]: Windows Installer installed the product. Product Name: Active Directory Rights Management Services Client 2.1. Product Version: 1.0.1179.1. Product Language: 1033. Manufacturer: Microsoft Corporation. Installation success or error status: 0.</ui>
                  </para>
                </content>
              </step>
              <step>
                <content>
                  <para>To verify success of the Office add-in, on each computer, search for the following text in the installation log file: <ui>Installation success or error status: 0</ui></para>
                  <para/>
                  <para>Example lines from a successful installation:  </para>
                  <para>
                    <ui>MSI (s) (9C:88) [18:49:04:007]: Product: Microsoft RMS Office Addins -- Installation completed successfully.</ui>
                  </para>
                  <para>
                    <ui>MSI (s) (9C:88) [18:49:04:007]: Windows Installer installed the product. Product Name: Microsoft RMS Office Addins. Product Version: 1.0.7. Product Language: 1033. Manufacturer: Microsoft. Installation success or error status: 0.</ui>
                  </para>
                </content>
              </step>
            </steps>
          </procedure>
        </content>
      </section>
      <section address="BKMK_uninstallscripted">
        <title>Uninstall commands </title>
        <content>
          <para>Not all of the installation commands that are required for these deployments support an uninstallation command. You can uninstall the AD RMS client and the sharing application, and you can uninstall the Office add-in. Use the following commands to uninstall these elements.</para>
          <procedure expanded="false">
            <title>To uninstall the AD RMS Client and the RMS sharing application</title>
            <steps class="bullet">
              <step>
                <content>
                  <para>Use the following commands:</para>
                  <list class="bullet">
                    <listItem>
                      <para>For 64-bit Windows: </para>
                      <code>x64\setup_ipviewer.exe /uninstall /quiet</code>
                    </listItem>
                    <listItem>
                      <para>For 32-bit Windows: </para>
                      <code>x86\setup_ipviewer.exe /uninstall /quiet</code>
                    </listItem>
                  </list>
                </content>
              </step>
            </steps>
          </procedure>
          <procedure expanded="false">
            <title>To uninstall the Office add-in</title>
            <steps class="bullet">
              <step>
                <content>
                  <para>Use the following commands:</para>
                  <list class="bullet">
                    <listItem>
                      <para>For 64-bit version of Office: </para>
                      <code>msiexec /x \x64\Setup[64].msi /quiet</code>
                    </listItem>
                    <listItem>
                      <para>For 32-bit version of Office: </para>
                      <code>msiexec /x \x86\Setup.msi /quiet</code>
                    </listItem>
                  </list>
                </content>
              </step>
            </steps>
          </procedure>
        </content>
      </section>
      <section address="BKMK_SuppressAutomaticUpdates">
        <title>
          <?Comment CB: 251538 2015-02-13T09:52:00Z  Id='3?>Suppressing automatic updates<?CommentEnd Id='3'
    ?></title>
        <content>
          <para>By default, users are notified if there is a later version of the RMS sharing application, and prompted to download it. You can suppress this notification by making the following registry edit:</para>
          <list class="ordered">
            <listItem>
              <para>Navigate to <ui>HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC</ui> and if not already present, create a new key named <ui>RmsSharingApp</ui>. </para>
            </listItem>
            <listItem>
              <para>Select <ui>RmsSharingApp</ui>, create a new DWORD Value of <ui>AllowUpdatePrompt</ui>, and set the value to <ui>0</ui>.</para>
            </listItem>
          </list>
          <para>Because the RMS sharing application is not supported by WSUS, you can use the following technique to test any new versions of the RMS sharing application before deploying it to all users:</para>
          <list class="ordered">
            <listItem>
              <para>On all users’ computers, run a script to suppress automatic updates. On the computers that administrators use to test new versions, do not run this script. </para>
            </listItem>
            <listItem>
              <para>When a new version is available, administrators download it and test it.</para>
            </listItem>
            <listItem>
              <para>When testing is complete and any issues resolved, deploy the latest version to all users by using the automatic deployment instructions in this guide.</para>
            </listItem>
          </list>
        </content>
      </section>
      <section address="BKMK_DocumentTracking">
<title>Azure RMS only: Configuring document tracking</title><content><para>If you have a <externalLink><linkText>subscription that supports document tracking</linkText><linkUri>https://technet.microsoft.com/en-us/dn858608</linkUri></externalLink>, the document tracking site is enabled by default for all users in your organization.  Document tracking shows information such as email addresses of the people who attempted to access protected documents that users shared, when these people tried to access them, and their location. If displaying this information is prohibited in your organization because of privacy requirements, you can disable access to the document tracking site by using the  <externalLink><linkText>Disable-AadrmDocumentTrackingFeature</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=623032</linkUri></externalLink> cmdlet. You can re-enable access to the site at any time, by using the <externalLink><linkText>Enable-AadrmDocumentTrackingFeature</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=623037</linkUri></externalLink>, and you can check whether access is currently enabled or disabled by using <externalLink><linkText>Get-AadrmDocumentTrackingFeature</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=623037</linkUri></externalLink>.</para> <para>To run these cmdlets, you must have at least version <embeddedLabel>2.3.0.0</embeddedLabel> of the Azure RMS module for Windows PowerShell.  For installation instructions, see <externalLink><linkText>Installing Windows PowerShell for Azure Rights Management</linkText><linkUri>https://technet.microsoft.com/library/jj585012.aspx</linkUri></externalLink>.</para><alert class="tip"><para>If you have previously downloaded and installed the module, check the version number by running: <codeInline>(Get-Module aadrm –ListAvailable).Version</codeInline>
</para></alert><para>The following URLs are used for document tracking and must be allowed (for example, add them to your Trusted Sites if you're using Internet Explorer with Enhanced Security): </para><list class="bullet"><listItem><para>https://*.azurerms.com</para></listItem><listItem><para>https://ecn.dev.virtualearth.net</para><alert class="note"><para>This URL is for Bing maps.</para></alert></listItem><listItem><para>https://*.microsoftonline.com</para></listItem><listItem><para>https://*.microsoftonline-p.com</para></listItem></list></content>
</section><section address="BKMK_FederatedDomains">
        <title>AD RMS only: Support for multiple email domains within your organization </title>
        <content>
          <para>If you use AD RMS and users in your organization have multiple email domains, perhaps as a result of a merger or acquisition, you must make the following registry edit:</para>
          <list class="ordered">
            <listItem>
              <para>Navigate to <ui>HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC</ui> and if not already present, create a new key named <ui>RmsSharingApp</ui>. </para>
            </listItem>
            <listItem>
              <para>Select <ui>RmsSharingApp</ui>, create a new Multi-String Value named <ui>FederatedDomains</ui>, and then add the domains and all the subdomains that your organization uses. Wildcards are not supported.</para>
              <para>For example: The company Coho Vineyard &amp; Winery has a standard email domain of <embeddedLabel>cohovineyardandwinery.com</embeddedLabel>, but as a result of mergers, they also use the email domains <embeddedLabel>cohowinery.com</embeddedLabel>, <embeddedLabel>eastcoast.cohowinery.com</embeddedLabel>, and <embeddedLabel>cohovineyard</embeddedLabel>. For the <ui>FederatedDomains</ui> value data, the administrator enters: <userInput>cohowinery.com; eastcoast.cohowinery.com; cohovineyard</userInput></para>
            </listItem>
          </list>
          <para>If you do not make this registry change, users might not be able to consume content that has been protected by other users in their organization. This registry edit is not needed if you use Azure RMS.</para>
        </content>
      </section>
    </sections>
  </section>
  <section DoNotNumber="false" address="BKMK_AdminOverview">
    <title>Technical overview for the Microsoft Rights Management sharing application </title>
    <content>
      <para>The Microsoft Rights Management sharing application is an optional downloadable application for Microsoft Windows and other platforms that provides the following:</para>
      <list class="bullet">
        <listItem>
          <para>Protection of a single file or bulk protection of multiple files as well as all files within a selected folder.</para>
        </listItem>
        <listItem>
          <para>Full support for protection of any type of file and a built-in viewer for commonly used text and image file types.</para>
        </listItem>
        <listItem>
          <para>Generic protection for files that do not support RMS protection.</para>
        </listItem>
        <listItem>
          <para>Full interoperability with files protected using Office Information Rights Management (IRM). </para>
        </listItem>
        <listItem>
          <para>Full interoperability with PDF files protected using SharePoint, FCI, and supported PDF authoring tools.</para>
        </listItem>
      </list>
      <para>The Microsoft Rights Management sharing application uses the new <externalLink><linkText>AD RMS Client 2.1 runtime</linkText><linkUri>http://www.microsoft.com/download/details.aspx?id=38396</linkUri></externalLink>. By using the functionality of AD RMS 2.1, the Microsoft Rights Management sharing application provides end users a simple protection and consumption experience.</para>
      <para>With the October 2013 release of RMS, you can natively protect documents by using Office 2010 and send them to people in another company, who can then consume them by using Azure RMS. In addition, with this release, if you use AD RMS in Cryptographic Mode 2, you can use RMS for individuals and consume content from people in another company that uses Azure RMS. For more information about Cryptographic Mode 2, see <externalLink><linkText>AD RMS Cryptographic Modes</linkText><linkUri>http://technet.microsoft.com/library/hh867439(v=ws.10).aspx</linkUri></externalLink>.</para>
    </content>
    <sections>
      <section DoNotNumber="false" address="BKMK_LevelsofProtection">
        <title>Levels of protection – native and generic</title>
        <content>
          <para>Microsoft Rights Management sharing application supports protection at two different levels, as described in the following table.</para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>Type of protection</para>
                </TD>
                <TD>
                  <para>Native</para>
                </TD>
                <TD>
                  <para>Generic</para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>Description</para>
                </TD>
                <TD>
                  <para>For text, image, Microsoft Office (Word, Excel, PowerPoint) files, .pdf files, and other application file types that support AD RMS, native protection provides a strong level of protection that includes both encryption and enforcement of rights (permissions).</para>
                </TD>
                <TD>
                  <para>For all other applications and file types, generic protection provides a level of protection that includes both file encapsulation using the .pfile file type and authentication to verify if a user is authorized to open the file.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Protection</para>
                </TD>
                <TD>
                  <para>Files are fully encrypted and protection is enforced in the following ways:</para>
                  <para>Before protected content is rendered, successful authentication must occur for those who receive the file through email or are given access to it through file or share permissions.</para><para>Additionally, usage rights and policy set by the content owner when files are protected are fully enforced when the content is rendered in either IP Viewer (for protected text and image files) or the associated application (for all other supported file types).</para>
                </TD>
                <TD>
                  <para>File protection is enforced in the following ways:</para>
                  <para>Before protected content is rendered, successful authentication must occur for those who are authorized to open the file and given access to it. If authorization fails, the file does not open.</para><para>Usage rights and policy set by the content owner are displayed to inform authorized users of the intended usage policy.</para><para>Audit logging of authorized users opening and accessing files occurs, however, no usage rights are enforced by non-supporting applications.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Default for file types</para>
                </TD>
                <TD>
                  <para>This is the default level of protection for the following file types:</para>
                  <para>Text and image files </para><para>Microsoft Office (Word, Excel, PowerPoint) files </para><para>Portable document format (.pdf)</para><para> </para>
                  <para>For more information, see the following section, <link xlink:href="d9992e30-f3d1-48d5-aedc-4e721f7d7c25#BKMK_SupportFileTypes">Supported file types and file name extensions</link>.</para>
                </TD>
                <TD>
                  <para>This is the default protection for all other file types (such as .vsdx, .rtf, and so on) that are not supported by full protection.</para>
                </TD>
              </tr>
            </tbody>
          </table>
          <para/>
          <para>You can change the default protection level that the RMS sharing application applies. You can change the default level of native to generic, from generic to native, and even prevent the RMS sharing application from applying protection. For more information, see the <link xlink:href="d9992e30-f3d1-48d5-aedc-4e721f7d7c25#BKMK_ChangeDefaultProtection">Changing the default protection level of files</link> section in this topic.</para>
        </content>
      </section>
      <section address="BKMK_SupportFileTypes" DoNotNumber="false">
        <title>Supported file types and file name extensions</title>
        <content>
          <para>The following table lists file types that are natively supported by Microsoft Rights Management sharing application. For these file types, the original file name extension is changed when native protected is applied, and these files become read-only. </para>
          <para>In addition, when the RMS sharing application natively protects a Word, Excel, or PowerPoint file that users protect by sharing, this action automatically creates a second file that is a copy of the original with the same file name but with a <ui>.ppdf</ui> file name extension ¹. This version of the file ensures that recipients who install the RMS sharing application can always open the file that has native protection applied.</para>
          <para>For files that are generically protected, the original file name extension is always changed to .pfile.</para>
          <alert class="warning">
            <para>If you have firewalls, web proxies, or security software that inspect and take action according to file name extensions, you might need to reconfigure these to support these new file name extensions.</para>
          </alert>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>Original file name extension</para>
                </TD>
                <TD>
                  <para>RMS-protected file name extension</para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>.txt</para>
                </TD>
                <TD>
                  <para>.ptxt</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>.xml</para>
                </TD>
                <TD>
                  <para>.pxml</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>.jpg</para>
                </TD>
                <TD>
                  <para>.pjpg</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>.jpeg</para>
                </TD>
                <TD>
                  <para>.ppng</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>.pdf</para>
                </TD>
                <TD>
                  <para>.ppdf</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>.png</para>
                </TD>
                <TD>
                  <para>.ppng</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>.tif</para>
                </TD>
                <TD>
                  <para>.ptif</para>
                </TD>
              </tr><tr>
                <TD>
                  <para>.tiff</para>
                </TD>
                <TD>
                  <para>.ptiff</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>.bmp</para>
                </TD>
                <TD>
                  <para>.pbmp</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>.gif</para>
                </TD>
                <TD>
                  <para>.pgif</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>.giff</para>
                </TD>
                <TD>
                  <para>.pgiff</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>.jpe</para>
                </TD>
                <TD>
                  <para>.pjpe</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>.jfif</para>
                </TD>
                <TD>
                  <para>.pjfif</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>.jif</para>
                </TD>
                <TD>
                  <para>.pjif</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>.jt</para>
                </TD>
                <TD>
                  <para>.pjt<?CommentEnd Id='5'
    ?></para>
                </TD>
              </tr>
            </tbody>
          </table>
          <para>¹ PDF Rendering Powered by Foxit. Copyright © 2003–2014 by Foxit Corporation.</para>
          <para>The following table lists the file types that the Microsoft Rights Management sharing application natively supports in Microsoft Office 2016,  Office 2013, and Office 2010. For these files, the file name extension remains the same after the file is protected by RMS. </para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>File types supported by Office</para>
                </TD>
                <TD>
                  <para>File types supported by Office</para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>.doc </para>
                  <para>.docm</para>
                  <para>.docx</para>
                  <para>.dot</para>
                  <para>.dotm</para>
                  <para>.dotx</para>
                  <para>.potm</para>
                  <para>.potx</para>
                  <para>.pps</para>
                  <para>.ppsm</para>
                  <para>.ppsx</para>
                  <para>.ppt</para>
                  <para>.pptm</para>
                </TD>
                <TD>
                  <para>.pptx</para>
                  <para>.thmx</para>
                  <para>.xla</para>
                  <para>.xlam</para>
                  <para>.xls</para>
                  <para>.xlsb</para>
                  <para>.xlt</para>
                  <para>.xlsm</para>
                  <para>.xlsx</para>
                  <para>.xltm</para>
                  <para>.xltx</para>
                  <para>.xps</para>
                </TD>
              </tr>
            </tbody>
          </table>
        </content>
      </section>
      <section address="BKMK_ChangeDefaultProtection">
        <title>
          <?Comment CB: 251538 2015-02-13T09:52:00Z  Id='9?>Changing the default protection level of files<?CommentEnd Id='9'
    ?></title>
        <content>
          <para>You can change how the RMS sharing application protects files by editing the registry. For example, you can force files that support native protection to be generically protected by the RMS sharing application.</para>
          <para>Reasons for why you might want to do this:</para>
          <list class="bullet">
            <listItem>
              <para>To ensure that all users can open the file from their mobile devices.</para>
            </listItem>
            <listItem>
              <para>To ensure that all users can open the file if they don’t have an application that supports native protection.</para>
            </listItem>
            <listItem>
              <para>To accommodate security systems that take action on files by their file name extension and can be reconfigured to accommodate the .pfile file name extension but cannot be reconfigured to accommodate multiple file name extensions for native protection.</para>
            </listItem>
          </list>
          <para>Similarly, you can force the RMS sharing application to apply native protection to files that by default, would have generic protection applied. This might be appropriate if you have an application that supports the RMS APIs – for example, a line-of-business application written by your internal developers or an application purchased from an independent software vendor (ISV).</para>
          <para>You can also force the RMS sharing application to block the protection of files (not apply native protection or generic protection). For example, this might be required if you have an automated application or service that must be able to open a specific file to process its contents. When you block protection for a file type, users cannot use the RMS sharing application to protect a file that has that file type. When they try, they see a message that the administrator has prevented protection and they must cancel their action to protect the file.</para>
          <para>To configure the RMS sharing application to apply generic protection to all files that by default, would have native protection applied, make the following registry edits:</para>
          <list class="ordered">
            <listItem>
              <para>
                <ui>HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection</ui>: Create a new key named <ui>*</ui>. </para>
              <para>This setting denotes files with any file name extension.</para>
            </listItem>
            <listItem>
              <para>In the newly added key of <ui>HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection\*</ui>, create a new string value (REG_SZ) named <ui>Encryption</ui> that has the data value of <ui>Pfile</ui>.  </para>
              <para>This setting results in the RMS sharing application applying generic protection.</para>
            </listItem>
          </list>
          <para>These two settings result in the RMS sharing application applying generic protection to all files that have a file name extension. If this is your goal, no further configuration is required. However, you can define exceptions for specific file types, so that they are still natively protected. To do this, you must make three additional registry edits for each file type:</para>
          <list class="ordered">
            <listItem>
              <para>
                <ui>HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection</ui>: Add a new key that has the name of the file name extension (without the preceding period). </para>
              <para>For example, for files that have a .docx file name extension, create a key named <ui>DOCX</ui>.</para>
            </listItem>
            <listItem>
              <para>In the newly added file type key (for example, <ui>HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection\DOCX</ui>), create a new DWORD Value named <ui>AllowPFILEEncryption</ui> that has a value of <ui>0</ui>.</para>
            </listItem>
            <listItem>
              <para>In the newly added file type key (for example, <ui>HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection\DOCX</ui>), create a new String Value named <ui>Encryption</ui> that has a value of <ui>Native</ui>.</para>
            </listItem>
          </list>
          <para>As a result of these settings, all files are generically protected except files that have a .docx file name extension, which are natively protected by the RMS sharing application. </para>
          <para>Repeat these three steps for other file types that you want to define as exceptions because they support native protection and you do not want them to be generically protected by the RMS sharing application.</para>
          <para>You can make similar registry edits for other scenarios by changing the value of the <ui>Encryption</ui> string that supports the following values: </para>
          <list class="bullet">
            <listItem>
              <para>
                <ui>Pfile</ui>: Generic protection</para>
            </listItem>
            <listItem>
              <para>
                <ui>Native</ui>: Native protection</para>
            </listItem>
            <listItem>
              <para>
                <ui>Off</ui>: Block protection</para>
            </listItem>
          </list>
        </content>
      </section>
    </sections>
  </section>
  <relatedTopics>
    <link xlink:href="eaf6d02c-aa36-4915-856e-49bb71ab1484">Rights Management sharing application user guide</link>
    
  </relatedTopics>
</developerConceptualDocument>
