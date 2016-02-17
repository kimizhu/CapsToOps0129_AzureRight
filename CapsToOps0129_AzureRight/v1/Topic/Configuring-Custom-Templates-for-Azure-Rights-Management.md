---
title: Configuring Custom Templates for Azure Rights Management
ms.custom: na
ms.reviewer: na
ms.service: rights-management
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1775d8d0-9a59-42c8-914f-ce285b71ac1c
author: Cabailey
---
# Configuring Custom Templates for Azure Rights Management
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>After you have activated Azure Rights Management (Azure RMS), users are automatically able to use two default templates that make it easy for them to apply policies to sensitive files that restrict access to authorized users in your organization. These two templates have the following rights policy restrictions: </para>
    <list class="bullet">
      <listItem>
        <para>Read-only viewing for the protected content</para>
        <list class="bullet">
          <listItem>
            <para>Display name: <ui>&lt;organization name&gt; - Confidential View Only</ui></para>
          </listItem>
          <listItem>
            <para>Specific permission: View Content</para>
          </listItem>
        </list>
      </listItem>
      <listItem>
        <para>Read or Modify permissions for the protected content</para>
        <list class="bullet">
          <listItem>
            <para>Display name: <ui>&lt;organization name&gt; - Confidential</ui></para>
          </listItem>
          <listItem>
            <para>Specific permissions: View Content, Save File, Edit Content, View Assigned Rights, Allow Macros, Forward, Reply, Reply All</para>
          </listItem>
        </list>
      </listItem>
    </list>
    <para>In addition, the <externalLink><linkText>RMS sharing application</linkText><linkUri>http://technet.microsoft.com/library/dn339006.aspx</linkUri></externalLink> lets users define their own set of permissions. And, for the Outlook client and Outlook Web Access, users can select the <ui>Do Not Forward</ui> option for email messages.</para>
    <para>For many organizations, the default templates might be sufficient. But if you want to create your own custom rights policy templates, you can do so. Reasons for creating a custom template include the following:</para>
    <list class="bullet">
      <listItem>
        <para>You want a template to grant rights to a subset of users in the organization rather than all users. </para>
      </listItem>
      <listItem>
        <para>You want only a subset of users to be able to see and select a template (departmental template) from applications, rather than all users in the organization see and can select the template.</para>
      </listItem>
      <listItem>
        <para>You want to define a custom right for a template, such as View and Edit, but not Copy and Print.</para>
      </listItem>
      <listItem>
        <para>You want to configure additional options in a template that include an expiration date and whether the content can be accessed without an Internet connection.</para>
      </listItem>
    </list>
    <para>For users to be able to select a custom template that contains settings such as these, you must first create a custom template, configure it, and then publish it. </para>
    <para>Use the following sections to help you configure and use custom templates:</para>
    <list class="bullet">
      <listItem>
        <para>
          <link xlink:href="1775d8d0-9a59-42c8-914f-ce285b71ac1c#BKMK_HowToConfigureCustomTemplates">How to create, configure, and publish a custom template</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="1775d8d0-9a59-42c8-914f-ce285b71ac1c#BKMK_HowToCopyTemplates">How to copy a template</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="1775d8d0-9a59-42c8-914f-ce285b71ac1c#BKMK_HowToArchiveTemplates">How to remove (archive) templates</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="1775d8d0-9a59-42c8-914f-ce285b71ac1c#BKMK_RefreshingTemplates">Refreshing templates for users</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="1775d8d0-9a59-42c8-914f-ce285b71ac1c#BKMK_PowerShellTemplates">Windows PowerShell reference</link>
        </para>
      </listItem>
    </list>
  </introduction>
  <section address="BKMK_HowToConfigureCustomTemplates">
    <title>How to create, configure, and publish a custom template</title>
    <content>
      <para>You create and manage custom templates in the Azure classic portal. You can do this directly from the Azure classic portal, or you can sign in to the Office 365 admin center, and choose the <ui>advanced features</ui> for Rights Management, which then redirects you to the Azure classic portal.</para>
      <para>Use the following procedures to create, configure, and publish custom templates for Rights Management.</para>
      <procedure>
        <title>To create a custom template</title>
        <steps class="ordered">
          <step>
            <content>
              <para>Depending on whether you sign in to the Office 365 admin center, or the Azure classic portal, do one of the following:</para>
              <list class="bullet">
                <listItem>
                  <para>From the <externalLink><linkText>Office 365 admin center</linkText><linkUri>https://<?Comment CB: 10353 2015-01-22T14:50:00Z  Id='0?>portal.office.com<?CommentEnd Id='0'
    ?>/</linkUri></externalLink>:</para>
                  <list class="ordered">
                    <listItem>
                      <para>In the left pane, click <ui>service settings</ui>.</para>
                    </listItem>
                    <listItem>
                      <para>From the <ui>service settings</ui> page, click <ui>rights management</ui>.</para>
                    </listItem>
                    <listItem>
                      <para>In the <ui>Protect your information</ui> section, click <ui>Manage</ui>.</para>
                    </listItem>
                    <listItem>
                      <para>In the <ui>rights management</ui> section, click <ui>advanced features</ui>.</para>
                      <alert class="note">
                        <para>If you haven’t activated Rights Management, first click <ui>activate</ui> and confirm your action. For more information, see <link xlink:href="f8707e01-b239-4d1a-a1ea-0d1cf9a8d214">Activating Azure Rights Management</link>.</para>
                        <para>If you haven’t clicked <ui>advanced features</ui> before, after Rights Management is activated, follow the on-screen instructions to get a free Azure subscription that’s required to access the Azure classic portal.</para>
                      </alert>
                    <para>Clicking <ui>advanced features</ui> loads the Azure classic portal, where you can manage <ui>RIGHTS MANAGEMENT</ui> for your organization's Azure Active Directory.</para></listItem>
                  </list>
                </listItem>
                <listItem>
                  <para>From the <externalLink><linkText>Azure classic portal</linkText><linkUri>http://go.microsoft.com/fwlink/p/?LinkID=275081</linkUri></externalLink>:</para>
                  <list class="ordered">
                    <listItem>
                      <para>In the left pane, click <ui>ACTIVE DIRECTORY</ui>.</para>
                    </listItem>
                    <listItem>
                      <para>From the <ui>active directory</ui> page, click <ui>RIGHTS MANAGEMENT</ui>.</para>
                    </listItem>
                    <listItem>
                      <para>Select the directory to manage for Rights Management.</para>
                    </listItem>
                    <listItem>
                      <para>If you have not already activated Rights Management, click <ui>ACTIVATE</ui> and confirm your action.</para>
                      <alert class="note">
                        <para>For more information, see <link xlink:href="f8707e01-b239-4d1a-a1ea-0d1cf9a8d214">Activating Azure Rights Management</link>.</para>
                      </alert>
                    </listItem>
                  </list>
                </listItem>
              </list>
            </content>
          </step>
          <step>
            <content>
              <para>Create a new template: </para>
              <list class="bullet">
                <listItem>
                  <para>In the Azure classic portal, from the <ui>Get started with Rights Management</ui> quick start page, click <ui><?Comment CB: 251951 2015-01-22T14:50:00Z  Id='1?>Create a new rights policy template<?CommentEnd Id='1'
    ?></ui>. </para>
                <para>If you do not immediately see this page after following the instructions for Office 365, use the navigation instructions, above,  for the Azure classic portal.   </para></listItem>
              </list>
            </content>
          </step>
          <step>
            <content>
              <para>On the <ui>Add a new rights policy template</ui> page, choose a language in which you will type the template name and description that users will see (you can add more languages later). Then type a unique name and a description, and click the Complete button.</para>
            </content>
          </step>
        </steps>
        <conclusion>
          <content>
            <para>From the <ui>Get started with Rights Management</ui> quick start page, now click <ui>Manage your rights policy templates</ui>. You will see your newly created template added to the list of templates, with a status of <ui>Archived</ui>. At this stage, the template is created but not configured, and is not visible to users.</para>
          </content>
        </conclusion>
      </procedure>
      <procedure>
        <title>To configure and publish a custom template</title>
        <steps class="ordered">
          <step>
            <content>
              <para>Select your newly created template from the <ui>TEMPLATES</ui> page in the Azure classic portal.</para>
            </content>
          </step>
          <step>
            <content>
              <para>From the <ui>Your template has been added</ui> quick start page, click <ui>Get started</ui> from step 1, <ui>Configure rights for users and groups,</ui> then click <ui>GET STARTED NOW</ui> or <ui>ADD</ui>, and then select the users and groups who will have rights to use the content that is protected by the new template. </para>
              <alert class="note">
                <para>The users or groups that you select must have an email address. In a production environment, this will nearly always be the case but in a simple testing environment, you might need to add email addresses to user accounts or groups.</para>
              </alert><para>As a best practice, use groups rather than users, which simplifies management of the templates. If you have Active Directory on-premises and are synchronizing to Azure AD, you can use mail-enabled groups that are either security groups or distribution groups. However, if you want to grant rights to all users in the organization, it will be more efficient to copy one of the default templates rather than specify multiple groups. For more information, see the <link xlink:href="1775d8d0-9a59-42c8-914f-ce285b71ac1c#BKMK_HowToCopyTemplates">How to copy a template</link> section in this topic.</para>
              <alert class="tip">
                <para>You can later add users from outside your organization to the template by using the <externalLink><linkText>Windows PowerShell module for Azure Rights Management</linkText><linkUri>https://technet.microsoft.com/library/jj585012.aspx</linkUri></externalLink> and using one of the following methods:</para>
                <list class="bullet"><listItem><para><embeddedLabel>Use a rights definition object to update a template</embeddedLabel>:    Specify the external email addresses and their rights in a rights definition object, which you then use to update your template. You specify the rights definition object by using the <externalLink><linkText>New-AadrmRightsDefinition</linkText><linkUri>https://msdn.microsoft.com/library/azure/dn727080.aspx</linkUri></externalLink> cmdlet to create a variable and then supply this variable to the  -RightsDefinition parameter with the <externalLink><linkText>Set-AadrmTemplateProperty</linkText><linkUri>https://msdn.microsoft.com/library/azure/dn727076.aspx</linkUri></externalLink> cmdlet to modify an existing template. However, if you're adding these users to an existing template, you will also need to define rights definition objects for the existing groups in the templates and not just the new, external users.</para></listItem><listItem><para><embeddedLabel>Export, edit, and import the updated template</embeddedLabel>:Use the <externalLink><linkText>Export-AadrmTemplate</linkText><linkUri>https://msdn.microsoft.com/library/azure/dn727078.aspx</linkUri></externalLink> cmdlet to export the template to a file that you can edit to add the external email addresses of these users and their rights to the existing groups and rights. Then use the <externalLink><linkText>Import-AadrmTemplate</linkText><linkUri>https://msdn.microsoft.com/library/azure/dn727077.aspx</linkUri></externalLink> cmdlet to import this change back into Azure RMS. </para></listItem></list>
              </alert>
            </content>
          </step>
          <step>
            <content>
              <para>Click the Next button, and then assign one of the listed rights to your selected users and groups.</para>
              <para>
                <?Comment CB: Short term fix forTlapka’sfeedback 2015-01-22T14:50:00Z  Id='2?>Use the displayed description for more information about each right (and for custom rights). More detailed  information is also available in <link xlink:href="97ddde38-b91b-42a5-8eb4-3ce6ce15393d">Configuring Usage Rights for Azure Rights Management</link>. However, applications that support RMS might vary in how they implement these rights. Consult their documentation and do your own testing with the applications that users use to check the behavior before you deploy the template for users. To make this template visible to only administrators for this testing, make this template a departmental template (step 6).<?CommentEnd Id='2'
    ?></para>
            </content>
          </step>
          <step>
            <content>
              <para>If you selected <ui>Custom</ui>, click the Next button, and then select those custom rights.</para>
              <para>Although you can use any combination of the individual rights available, in some applications, some rights might have dependencies on other individual rights. <?Comment CB: 251951 2015-01-22T14:50:00Z  Id='3?>When this is the case, the dependent rights are automatically selected for you. <?CommentEnd Id='3'
    ?></para>
              <alert class="tip">
                <para>Consider adding the <ui>Copy and Extract Content</ui> right and grant this to selected administrators or personnel in other roles that have responsibilities for information recovery. Granting this right lets them remove protection if needed, from files and emails that will be protected by using this template. This ability to remove protection at the template level provides more fine-grained control than using the super user feature.</para>
              </alert>
            </content>
          </step>
          <step>
            <content>
              <para>Click the Complete button.</para>
            </content>
          </step>
          <step>
            <content>
              <para>If you want the template to be visible to only a subset of users when they see a list of templates in applications: Click <ui>SCOPE</ui> to configure this as a departmental template, and click <ui>GET STARTED NOW</ui>. Otherwise, go to step 9.</para>
              <para>More information about departmental templates: By default, all users in your Azure directory see all the published templates and they can then select them from applications when they want to protect content. If you want specific users only to see some of the published templates, you must scope the templates to these users. Then, only these users will be able to select these templates. Other users that you do not specify will not see the templates and therefore, cannot select them. This technique can make choosing the correct template easier for users, especially when you create templates that are designed to be used by specific groups or departments. Users then see only the templates that are designed for them.</para>
              <para>For example, you’ve created a template for the Human Resources department that applies the Read-only permission to members of the Finance department. So that only members of the Human Resources department can apply this template when they use the Rights Management sharing application, you scope the template to the email-enabled group named HumanResources. Then, only members of this group see and can apply this template.</para>
            </content>
          </step>
          <step>
            <content>
              <para>On the <ui>TEMPLATE VISIBILITY</ui> page, select the users and groups who will be able to see and select the template from the RMS-enlightened applications. As before, as a best practice, use groups rather than users, and the groups or users you select must have an email address.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Click the Next button, and decide whether you need to configure application compatibility for your departmental template. If you do, click <ui>APPLICATION COMPATIBILITY</ui>, select the check box, and click <ui>Complete</ui>.</para>
              <para>Why might you need to configure application compatibility? Not all applications can support departmental templates. To do so, the application must first authenticate with the RMS service before downloading the templates. If the authentication process does not occur, by default, none of the departmental templates are downloaded. You can override this behavior by specifying that all the departmental templates should download, by configuring application compatibility and selecting the <ui>Show this template to all users when the applications do not support user identity</ui> check box.</para>
              <para>For example, if you do not configure application compatibility for the departmental template in our Human Resources example, only users in the Human Resources department see the departmental template when they use the RMS sharing application, but no users see the departmental template when they use Outlook Web Access (OWA) from Exchange Server 2013 because Exchange OWA and Exchange ActiveSync do not currently support departmental templates. If you override this default behavior by configuring application compatibility, only users in the Human Resources department see the departmental template when they use the RMS sharing application, but all users see the departmental template when they use Outlook Web Access (OWA). If users use OWA or Exchange ActiveSync from Exchange Online, either all users will see the departmental templates or no users will see the department templates, based on the template status (archival or published) in Exchange Online.</para>
              <para>Office 2016 natively supports departmental templates, and so does Office 2013 with the latest  Office updates (<externalLink><linkText>KB 3054853</linkText><linkUri>https://support.microsoft.com/kb/3054853</linkUri></externalLink>).</para><alert class="note">
                <para> If you have applications that don’t yet natively support departmental templates, you can use a custom RMS template download script or other tools to deploy these templates to the local RMS client folder. Then, these applications will correctly display the departmental templates to only the users and groups that you selected for the template scope: 

</para>
                <list class="bullet">
                  <listItem>
                    <para>For Office 2010, the client folder is <system>%localappdata%\Microsoft\DRM\Templates</system>.</para>
                  </listItem>
                  <listItem>
                    <para>From a client computer that has downloaded all the templates, you can copy and then paste the template files to other computers.</para>
                  </listItem>
                </list>
              <para> </para><para>You can <externalLink><linkText>download the custom RMS template script from the Microsoft Connect site</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=524506</linkUri></externalLink>. If you see an error when you click this link, you probably haven't registered on Microsoft Connect.   To register:</para><list class="ordered"><listItem><para>Go to the <externalLink><linkText>Microsoft Connect site</linkText><linkUri>http://www.connect.microsoft.com</linkUri></externalLink> and sign in with your Microsoft Account.</para></listItem><listItem><para>Click <ui>Directory</ui>, and select the <ui>View Connect products currently not accepting feedback</ui> category.</para></listItem><listItem><para>Search for <userInput>Rights Management Services</userInput>, and for the <ui>Microsoft RMS Enterprise Features</ui> program, click <ui>Join</ui>.</para></listItem></list></alert>
            </content>
          </step>
          <step>
            <content>
              <para>Click <ui>CONFIGURE</ui> and add additional languages that users use, together with the name and description of this template in that language. When you have multi-language users, it’s important to add each language that they use, and supply a name and description in that language. Users will then see the name and description of the template in the same language as their client operating system, which ensures they understand the policy applied to a document or email message. If there is no match with their client operating system, the name and description that they see falls back to the language and description that you defined when you first created the template.</para>
              <para>Then check whether you want to make any changes to the following settings:</para>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Setting</para>
                    </TD>
                    <TD>
                      <para>More information</para>
                    </TD>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <TD>
                      <para>
                        <ui>content expiration</ui>
                      </para>
                    </TD>
                    <TD>
                      <para>Define a date or number of days for this template when files that are protected by the template should not open. You can specify a date or specify a number of days starting from the time that the protection is applied to the file. </para>
                    <para>When you specify a date, it is effective midnight, in your current time zone.</para></TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>
                        <ui>offline access</ui>
                      </para>
                    </TD>
                    <TD>
                      <para>Use this setting to balance any security requirements that you have against the requirement that users must be able to open protected files when they don’t have an Internet connection.</para>
                      <para>If you specify that content is not available without an Internet connection or that content is only available for a specified number of days, when that threshold is reached, users must be re-authenticated and their access is logged. When this happens, if their credentials are not cached, users are prompted to sign in before they can open the file. </para>
                      <para>In addition to re-authentication, the policy and the user group membership is re-evaluated. This means that users could experience different access results for the same file if there are changes in the policy or group membership from when they last accessed the file. </para>
                    </TD>
                  </tr>
                </tbody>
              </table>
            </content>
          </step>
          <step>
            <content>
              <para>When you are confident that the template is configured appropriately for your users, click <ui>PUBLISH</ui> to make the template visible for users, and then click <ui>SAVE</ui>.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Click the Back button in the classic portal to return to the <ui>TEMPLATES</ui> page, where your template now has an updated status of <ui>Published</ui>.</para>
            </content>
          </step>
        </steps>
        <conclusion>
          <content>
            <para>To make any changes to your template, select it, and then use the quick start steps again. Or, select one of the following options:</para>
            <list class="bullet">
              <listItem>
                <para>To add more users and groups, and define the rights for those users and groups: Click <ui>RIGHTS</ui>, then click <ui>ADD</ui>.</para>
              </listItem>
              <listItem>
                <para>To remove users or groups that you previously selected: Click <ui>RIGHTS</ui>, select the user or group from the list, and then click <ui>DELETE</ui>.</para>
              </listItem>
              <listItem>
                <para>To change which users can see the templates to select them from applications: Click <ui>SCOPE</ui>, then click <ui>ADD</ui> or <ui>DELETE</ui>, or <ui>APPLICATION COMPATIBILITY</ui>.</para>
              </listItem>
              <listItem>
                <para>To make the template no longer visible to all users: Click <ui>CONFIGURE</ui>, click <ui>ARCHIVE</ui>, and then click <ui>SAVE</ui>.</para>
              </listItem>
              <listItem>
                <para>To make other configuration changes: Click <ui>CONFIGURE</ui>, make your changes, and then click <ui>SAVE</ui>.</para>
              </listItem>
            </list>
            <alert class="warning">
              <para>When you make changes to a template that was previously saved, clients will not see those changes to the template until templates are refreshed on their computers. For more information, see the <link xlink:href="1775d8d0-9a59-42c8-914f-ce285b71ac1c#BKMK_RefreshingTemplates">Refreshing templates for users</link> section in this topic.</para>
            </alert>
          </content>
        </conclusion>
      </procedure>
    </content>
  </section>
  <section address="BKMK_HowToCopyTemplates">
    <?Comment CB: 251951 2015-01-22T14:50:00Z  Id='4?>
    <title>How to copy a template<?CommentEnd Id='4'
    ?></title>
    <content>
      <para>If you want to create a new template that has very similar settings to an existing template, select the original template on the <ui>TEMPLATES</ui> page, click <ui>COPY</ui>, specify a unique name, and make the changes that you need.</para>
      <alert class="important">
        <para>When you copy a template, the <ui>Published</ui> or <ui>Archived</ui> status is also copied. So if you copy a published template, its immediate status will be published, unless you change it.</para>
      </alert>
      <para>You can copy custom templates and the default templates. As a best practice, copy one of the default templates instead of creating a new custom template if you want the template to grant rights to all users in your organization. This method means that you don’t have to create or select multiple groups to specify all users. In this scenario however, be sure to specify a new name and description for the copied template for additional languages.</para>
    </content>
  </section>
  <section address="BKMK_HowToArchiveTemplates">
    <title>How to remove (archive) templates</title>
    <content>
      <para>The default templates cannot be deleted, but they can be archived so that users do not see them.</para>
      <para>Similarly, if you have published a custom template and no longer want users to be able to see it, you can edit the template and choose <ui>ARCHIVE</ui> and <ui>SAVE</ui> from the <ui>CONFIGURE</ui> page. Or, you can select it from the <ui>TEMPLATES</ui> page and select <ui>ARCHIVE</ui>. </para>
      <para>Because you cannot edit the default templates, to archive these templates, you must use the <ui>ARCHIVE</ui> option from the <ui>TEMPLATES</ui> page. You cannot archive the Outlook <ui>Do Not Forward</ui> option.</para>
      <procedure>
        <title>To remove a default template</title>
        <steps class="bullet">
          <step>
            <content>
              <para>From the <ui>TEMPLATES</ui> page, select the default template, and click <ui>ARCHIVE</ui>.</para>
            </content>
          </step>
        </steps>
        <conclusion>
          <content>
            <para>The status changes from <ui>Published</ui> to <ui>Archived</ui>. If you change your mind, select the template and click <ui>PUBLISH</ui>.</para>
          </content>
        </conclusion>
      </procedure>
    </content>
  </section>
  <section address="BKMK_RefreshingTemplates">
    <title>Refreshing templates for users</title>
    <content>
      <para>When you use Azure RMS, templates are automatically downloaded to client computers so that users can select them from their applications. However, you might need to take additional steps if you make changes to the templates:</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Application or service</para>
            </TD>
            <TD>
              <para>How templates are refreshed after changes</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>Exchange Online</para>
            </TD>
            <TD>
              <para>Manual configuration required to refresh templates.</para>
              <para>For the configuration steps, expand the following section, <link xlink:href="1775d8d0-9a59-42c8-914f-ce285b71ac1c#BKMK_ExchangeOnlineTemplatesUpdate">Exchange Online only: How to configure Exchange to download changed custom templates</link>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Office 365</para>
            </TD>
            <TD>
              <para>Automatically refreshed  – no additional steps required.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Office 2016 and Office 2013</para>
            <para>RMS sharing application for Windows</para></TD>
            <TD>
              <para>Automatically refreshed – on a schedule: </para>
              <para>For these later versions of Office: The default refresh interval  is every 7 days.</para><para>For the RMS sharing application for Windows: Starting with version 1.0.1784.0, the default refresh interval is every 1 day. Prior versions have a default refresh interval of every 7 days. </para><para> </para><para>To force a refresh sooner than this schedule, expand the following section, <link xlink:href="#BKMK_Office2013ForceUpdate">Office 2016,  Office 2013, and RMS sharing application for Windows: How to force a refresh for a changed custom template</link>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Office 2010</para>
            </TD>
            <TD>
              <para>Refreshed when users log on.</para>
              <para>To force a refresh, ask or force users to log off and log back on again. Or, see the following section, <link xlink:href="#BKMK_Office2010ForceUpdate">Office 2010 only: How to force a refresh for a changed custom template</link>.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>For mobile devices that use the RMS sharing application, templates are automatically downloaded (and refreshed if necessary) without additional configuration required. </para>
    </content>
    <sections>
      <section address="BKMK_ExchangeOnlineTemplatesUpdate" expanded="false">
        <title>Exchange Online only: How to configure Exchange to download changed custom templates</title>
        <content>
          <para>If you have already configured Information Rights Management (IRM) for Exchange Online, custom templates will not download for users until you make the following changes by using Windows PowerShell in Exchange Online. </para>
          <alert class="note">
            <para>For more information about how to use Windows PowerShell in Exchange Online, see <externalLink><linkText>Using PowerShell with Exchange Online</linkText><linkUri>https://technet.microsoft.com/library/jj200677(v=exchg.160).aspx</linkUri></externalLink>.</para>
          </alert>
          <para>You must do this procedure each time you change a template.</para>
          <procedure>
            <title>To update templates for Exchange Online</title>
            <steps class="ordered">
              <step>
                <content>
                  <para>Using Windows PowerShell in Exchange Online, connect to the service:</para>
                <list class="ordered"><listItem><para>Supply your Office 365 user name and password:</para><code>$Cred = Get-Credential</code></listItem><listItem><para>Connect to the Exchange Online service by running the following two commands:</para><code>$Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell/ -Credential $Cred -Authentication Basic –AllowRedirection</code><code>Import-PSSession $Session</code></listItem></list></content>
              </step>
              <step>
                <content>
                  <para>Use the <externalLink><linkText>Import-RMSTrustedPublishingDomain</linkText><linkUri>http://technet.microsoft.com/library/jj200724(v=exchg.160).aspx</linkUri></externalLink> cmdlet to re-import your trusted publishing domain (TPD) from Azure RMS:</para>
                  <?Comment CB: 252105 2015-01-22T14:50:00Z  Id='5?>
                  <code>Import-RMSTrustedPublishingDomain -Name "&lt;TPD name&gt;" -RefreshTemplates -RMSOnline<?CommentEnd Id='5'
    ?></code>
                  <para>For example, if your TPD name is <ui>RMS Online - 1</ui> (a typical name for many organizations), enter: <userInput>Import-RMSTrustedPublishingDomain -Name "RMS Online - 1" -RefreshTemplates -RMSOnline</userInput></para>
                  <?Comment CB: 252105 2015-01-22T14:50:00Z  Id='6?>
                  <alert class="note">
                    <para>To verify your TPD name, you can use the <externalLink><linkText>Get-RMSTrustedPublishingDomain</linkText><linkUri>http://technet.microsoft.com/library/jj200707(v=exchg.160).aspx</linkUri></externalLink> cmdlet.</para>
                  </alert>
                </content>
              </step>
              <step>
                <content>
                  <para>To confirm that the templates have imported successfully, wait a few minutes and then run the <externalLink><linkText>Get-RMSTemplate</linkText><linkUri>http://technet.microsoft.com/library/dd297960(v=exchg.160).aspx</linkUri></externalLink> cmdlet and set the Type to All.<?CommentEnd Id='6'
    ?> For example:</para>
                  <code>Get-RMSTemplate -TrustedPublishingDomain "RMS Online - 1" -Type All
</code>
                <alert class="tip">
 <para>It's useful to keep a copy of the output so that you can easily copy the template names or GUIDs if you later archive a template. </para>
</alert></content>
              </step>
              <step>
                <content>
                  <para>For each imported template that you want to be available in the Outlook Web App, you must use the <externalLink><linkText>Set-RMSTemplate</linkText><linkUri>http://technet.microsoft.com/library/hh529923(v=exchg.160).aspx</linkUri></externalLink> cmdlet and set the Type to Distributed:</para>
                  <code>Set-RMSTemplate -Identity "&lt;name  or GUID of the template&gt;" -Type Distributed</code>
                <para>Because Outlook Web Access caches the UI for 24 hours, users might not see the new template for up to a day.</para></content>
              </step>
            </steps>
          </procedure>
          <para>In addition, if you archive a template (custom or default) and use Exchange Online with Office 365, users will continue to see the archived templates if they use the Outlook Web App or mobile devices that use the Exchange ActiveSync Protocol. </para>
          <para>So that users no longer see these templates, connect to the service by using Windows PowerShell in Exchange Online, and then use the <externalLink><linkText>Set-RMSTemplate</linkText><linkUri>http://technet.microsoft.com/library/hh529923(v=exchg.160).aspx</linkUri></externalLink> cmdlet by running the following command: </para>
          <code>Set-RMSTemplate -Identity "&lt;name or GUID of the template&gt;" -Type Archived</code>
        </content>
      </section>
      <section expanded="false" address="BKMK_Office2013ForceUpdate">
        <title>Office 2016,  Office 2013, and RMS sharing application for Windows: How to force a refresh for a changed custom template</title>
        <content>
          <para>By editing the registry on the computers running Office 2016, Office 2013, or the Rights Management (RMS) sharing application for Windows, you can change the automatic schedule so that changed templates are refreshed on computers more frequently than their default value. You can also force an immediate refresh by deleting the existing data in a registry value.</para>
          <alert class="warning">
            <para>If you use the Registry Editor incorrectly, you might cause serious problems that might require you to reinstall the operating system. Microsoft cannot guarantee that you can solve problems that result from using the Registry Editor incorrectly. Use the Registry Editor at your own risk.</para>
          </alert>
          <procedure>
            <title>To change the automatic schedule</title>
            <steps class="ordered">
              <step>
                <content>
                  <para>Using a registry editor, create and set one of the following registry values:</para>
                  <list class="bullet"><listItem><para>To set an update frequency in days (minimum of 1 day):  Create a new registry value named <ui>TemplateUpdateFrequency</ui> and define an integer value for the data, which specifies the frequency in days to download any changes to a downloaded template. Use the following table to locate the registry path to create this new registry value. </para><table>
                    <thead>
                      <tr>
                        <TD>
                          <para>Registry path</para>
                        </TD>
                        <TD>
                          <para>Type</para>
                        </TD>
                        <TD>
                          <para>Value</para>
                        </TD>
                      </tr>
                    </thead>
                    <tbody>
                      <tr>
                        <TD>
                          <para>HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC</para>
                        </TD>
                        <TD>
                          <para>REG_DWORD</para>
                        </TD>
                        <TD>
                          <para>TemplateUpdateFrequency</para>
                        </TD>
                      </tr>
                    </tbody>
                  </table>
                </listItem><listItem><para>To set an update frequency in seconds (minimum of 1 second):  Create a new registry value named <ui>TemplateUpdateFrequencyInSeconds</ui> and define an integer value for the data, which specifies the frequency in seconds to download any changes to a downloaded template. Use the following table to locate the registry path to create this new registry value. </para><table>
                    <thead>
                      <tr>
                        <TD>
                          <para>Registry path</para>
                        </TD>
                        <TD>
                          <para>Type</para>
                        </TD>
                        <TD>
                          <para>Value</para>
                        </TD>
                      </tr>
                    </thead>
                    <tbody>
                      <tr>
                        <TD>
                          <para>HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC</para>
                        </TD>
                        <TD>
                          <para>REG_DWORD</para>
                        </TD>
                        <TD>
                          <para>TemplateUpdateFrequencyInSeconds</para>
                        </TD>
                      </tr>
                    </tbody>
                  </table></listItem></list><para>Make sure that you create and set one of these registry values, not both. If both are present, <system>TemplateUpdateFrequency</system> is ignored.</para></content>
              </step>
              <step>
                <content>
                  <para>If you want to force an immediate refresh of the templates, go to the next procedure. Otherwise, restart your Office applications and instances of File Explorer now.</para>
                </content>
              </step>
            </steps>
          </procedure>
          <procedure>
            <title>To force an immediate refresh</title>
            <steps class="ordered">
              <step>
                <content>
                  <para>Using a registry editor, delete the data for the <ui>LastUpdatedTime</ui> value. For example, the data might display <ui>2015-04-20T15:52</ui>; delete 2015-04-20T15:52 so that no data is displayed. Use the following table to locate the registry path to delete this registry value data.</para>
                  <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                    <thead>
                      <tr>
                        <TD>
                          <para>Registry path</para>
                        </TD>
                        <TD>
                          <para>Type</para>
                        </TD>
                        <TD>
                          <para>Value</para>
                        </TD>
                      </tr>
                    </thead>
                    <tbody>
                      <tr>
                        <TD>
                          <para>HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\&lt;MicrosoftRMS_FQDN&gt;\Template</para>
                        </TD>
                        <TD>
                          <para>REG_SZ</para>
                        </TD>
                        <TD>
                          <para>LastUpdatedTime</para>
                        </TD>
                      </tr>
                    </tbody>
                  </table>
                  <alert class="tip">
                    <para>In the registry path, <placeholder>&lt;MicrosoftRMS_FQDN&gt;</placeholder> refers to your Microsoft RMS service FQDN. If you want to verify this value:</para>
                    <list class="ordered">
                      <listItem>
                        <para>Run the <externalLink><linkText>Get-AadrmConfiguration</linkText><linkUri>https://msdn.microsoft.com/library/windowsazure/dn629410.aspx</linkUri></externalLink> cmdlet for Azure RMS. If you haven’t already installed the Windows PowerShell module for Azure RMS, see <link xlink:href="0d665ed6-b1de-4d63-854a-bc57c1c49844">Installing Windows PowerShell for Azure Rights Management</link>.</para>
                      </listItem>
                      <listItem>
                        <para>From the output, identify the <ui>LicensingIntranetDistributionPointUrl</ui> value. </para>
                        <para>For example: <ui>LicensingIntranetDistributionPointUrl   : https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing</ui></para>
                      </listItem>
                      <listItem>
                        <para>From the value, remove <ui>https://</ui> and <ui>/_wmcs/licensing</ui> from this string. The remaining value is your Microsoft RMS service FQDN. In our example, the Microsoft RMS service FQDN would be the following value:</para>
                        <para>
                          <ui>5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com</ui>
                        </para>
                      </listItem>
                    </list>
                  </alert>
                </content>
              </step>
              <step>
 <content><para>Delete the following folder and all files it contains: <system>%localappdata%\Microsoft\MSIPC\Templates</system></para></content>
</step><step>
                <content>
                  <para>Restart your Office applications and instances of File Explorer.</para>
                </content>
              </step>
            </steps>
          </procedure>
        </content>
      </section>
    <section expanded="false" address="BKMK_Office2010ForceUpdate">
        <title>Office 2010 only: How to force a refresh for a changed custom template</title>
        <content>
          <para>By editing the registry on the computers running Office 2010, you can set a value so that changed templates are refreshed on computers without waiting for users to log off and back on. You can also force an immediate refresh by deleting the existing data in a registry value.</para>
          <alert class="warning">
            <para>If you use the Registry Editor incorrectly, you might cause serious problems that might require you to reinstall the operating system. Microsoft cannot guarantee that you can solve problems that result from using the Registry Editor incorrectly. Use the Registry Editor at your own risk.</para>
          </alert>
          <procedure>
            <title>To change the update frequency</title>
            <steps class="ordered">
              <step>
                <content>
                  <para>Using a registry editor, create a new registry value named <ui>UpdateFrequency</ui> and define an integer value for the data, which specifies the frequency in days to download any changes to a downloaded template. Use the following table to locate the registry path to create this new registry value.</para>
                  <table>
                    <thead>
                      <tr>
                        <TD>
                          <para>Registry path</para>
                        </TD>
                        <TD>
                          <para>Type</para>
                        </TD>
                        <TD>
                          <para>Value</para>
                        </TD>
                      </tr>
                    </thead>
                    <tbody>
                      <tr>
                        <TD>
                          <para>HKEY_CURRENT_USER\Software\Microsoft\MSDRM\TemplateManagement</para>
                        </TD>
                        <TD>
                          <para>REG_DWORD</para>
                        </TD>
                        <TD>
                          <para>UpdateFrequency</para>
                        </TD>
                      </tr>
                    </tbody>
                  </table>
                </content>
              </step>
              <step>
                <content>
                  <para>If you want to force an immediate refresh of the templates, go to the next procedure. Otherwise, restart your Office applications now.</para>
                </content>
              </step>
            </steps>
          </procedure>
          <procedure>
            <title>To force an immediate refresh</title>
            <steps class="ordered">
              <step>
                <content>
                  <para>Using a registry editor, delete the data for the <ui>LastUpdatedTime</ui> value. For example, the data might display <ui>2015-04-20T15:52</ui>; delete 2015-04-20T15:52 so that no data is displayed. Use the following table to locate the registry path to delete this registry value data.</para>
                  <table>
                    <thead>
                      <tr>
                        <TD>
                          <para>Registry path</para>
                        </TD>
                        <TD>
                          <para>Type</para>
                        </TD>
                        <TD>
                          <para>Value</para>
                        </TD>
                      </tr>
                    </thead>
                    <tbody>
                      <tr>
                        <TD>
                          <para>HKEY_CURRENT_USER\Software\Microsoft\MSDRM\TemplateManagement</para>
                        </TD>
                        <TD>
                          <para>REG_SZ</para>
                        </TD>
                        <TD>
                          <para>lastUpdatedTime</para>
                        </TD>
                      </tr>
                    </tbody>
                  </table>
                  
                </content>
              </step>
              <step>
 <content><para>Delete the following folder and all files it contains: <system>%localappdata%\Microsoft\MSIPC\Templates</system></para></content>
</step><step>
                <content>
                  <para>Restart your Office applications.</para>
                </content>
              </step>
            </steps>
          </procedure>
        </content>
      </section></sections>
  </section>
  <section address="BKMK_PowerShellTemplates">
    <title>Windows PowerShell reference</title>
    <content>
      <para>Everything that you can do in the Azure classic portal to create and manage templates, you can do from the command line, by using Windows PowerShell. In addition, you can export and import templates, so that you can copy templates between tenants or perform bulk edits of complex properties in templates, such as multilingual names and descriptions. </para>
      <para>You can also use export and import to back up and restore your custom templates, As a best practice, regularly back up your custom templates, so that if you make a change that was not intended, you can easily revert to a previous version.  </para><alert class="important">
        <para>To use Windows PowerShell to create and manage Azure RMS rights policy templates, you must have at least version 2.0.0.0 of the <externalLink><linkText>Windows PowerShell module for Azure RMS</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=257721</linkUri></externalLink>. </para>
        <para>If you have previously installed this Windows PowerShell module, run the following command in a PowerShell window to check the version number: <codeInline>(Get-Module aadrm -ListAvailable).Version</codeInline></para>
      </alert>
      <para>For installation instructions, see <link xlink:href="0d665ed6-b1de-4d63-854a-bc57c1c49844">Installing Windows PowerShell for Azure Rights Management</link>.</para>
      <para>The cmdlets that support creating and managing templates:</para>
      <list class="bullet">
        <listItem>
          <para>
            <externalLink>
              <linkText>Add-AadrmTemplate</linkText>
              <linkUri>https://msdn.microsoft.com/library/azure/dn727075.aspx</linkUri>
            </externalLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <externalLink>
              <linkText>Export-AadrmTemplate</linkText>
              <linkUri>https://msdn.microsoft.com/library/azure/dn727078.aspx</linkUri>
            </externalLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <externalLink>
              <linkText>Get-AadrmTemplate</linkText>
              <linkUri>https://msdn.microsoft.com/library/azure/dn727079.aspx</linkUri>
            </externalLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <externalLink>
              <linkText>Get-AadrmTemplateProperty</linkText>
              <linkUri>https://msdn.microsoft.com/library/azure/dn727081.aspx</linkUri>
            </externalLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <externalLink>
              <linkText>Import-AadrmTemplate</linkText>
              <linkUri>https://msdn.microsoft.com/library/azure/dn727077.aspx</linkUri>
            </externalLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <externalLink>
              <linkText>New-AadrmRightsDefinition</linkText>
              <linkUri>https://msdn.microsoft.com/library/azure/dn727080.aspx</linkUri>
            </externalLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <externalLink>
              <linkText>Remove-AadrmTemplate</linkText>
              <linkUri>https://msdn.microsoft.com/library/azure/dn727082.aspx</linkUri>
            </externalLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <externalLink>
              <linkText>Set-AadrmTemplateProperty</linkText>
              <linkUri>https://msdn.microsoft.com/library/azure/dn727076.aspx</linkUri>
            </externalLink>
          </para>
        </listItem>
      </list>
    </content>
  </section>
  <section>
    <title>Next steps</title>
    <content>
      <para>After you’ve configured custom templates for Azure Rights Management, use the <link xlink:href="086600c2-c5d8-47ec-a4c0-c782e1797486">Azure Rights Management Deployment Roadmap</link> to check whether there are other configuration steps that you might want to do before you roll out <token>aad_rightsmanagement_1</token> to users and administrators. If there are no other configuration steps that you need to do, see <link xlink:href="18564e4a-9364-4ed2-8f17-89d24fc0d878">Using Azure Rights Management</link> for operational guidance to support a successful deployment for your organization.</para>
    </content>
  </section>
  <relatedTopics>
    <link xlink:href="206a0bfe-0912-4e0e-aa15-484b000b264c">Configuring Azure Rights Management</link>
  </relatedTopics>
</developerConceptualDocument>
