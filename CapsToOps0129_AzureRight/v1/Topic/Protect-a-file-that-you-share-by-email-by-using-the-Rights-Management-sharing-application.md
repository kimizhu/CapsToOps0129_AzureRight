---
title: Protect a file that you share by email by using the Rights Management sharing application
ms.custom: na
ms.reviewer: na
ms.service: rights-management
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4c1cd1d3-78dd-4f90-8b37-dcc9205a6736
author: Cabailey
---
# Protect a file that you share by email by using the Rights Management sharing application
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://clixdevr3.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When you protect a file that you share by email, it creates a new version of the original file. The original file remains unprotected and the new version is protected and automatically attached to an email that you then send. </para>
    <para>In some cases (for files that are created by Microsoft Word, Excel, and PowerPoint), the RMS sharing application creates two versions of the file that it attaches to the email message. The second version of the file has a <ui>.ppdf</ui> file name extension and it is a PDF shadow copy of the file. This version of the file ensures that recipients can always read the file, even if they don’t have the same application installed that you used to create it. This is often the case when people read their email on mobile devices, and want to view their email attachments. All they need to open the file, is the RMS sharing application. Then, they can read the attached file, but they won’t be able to change it until they open the other version of the file by using an application that supports RMS.</para>
    <para>If your organization uses Azure RMS, you can keep track of the files that you protect by sharing:</para>
    <list class="bullet">
      <listItem>
        <para>Select an option to receive emails when somebody tries to open these protected attachments. Each time the file is accessed, you will be notified who tried to open the file and when, and whether they were successful (they were successfully authenticated) or not.</para>
      </listItem>
      <listItem>
        <para>Use the documentation tracking site. You can even stop sharing the file, by revoking access to it in the document tracking site. For more information, see <link xlink:href="61f349ce-bdd2-45c1-acc5-bc83937fb187">Track and revoke your documents when you use the RMS sharing application</link>.</para>
      </listItem>
    </list>
  </introduction>
  <section DoNotNumber="false" expanded="true">
    <title>Using Outlook: To protect a file that you share by email</title>
    <content>
      <procedure>
        <title />
        <steps class="ordered">
          <step>
            <content>
              <para>Create your email message and attach the file. Then, on the <ui>Message</ui> tab, in the <ui>RMS</ui> group, click <ui>Share Protected</ui> and then click <ui>Share Protected</ui> again:</para>
              <para>
                <mediaLinkInline>
                  <image xlink:href="b2fcc3b2-4416-401b-b465-1c1962e1e69d" />
                </mediaLinkInline>
              </para>
              <para>If you do not see this button, it’s likely that either the RMS sharing application is not installed on your computer, the latest version isn’t installed, or your computer must be restarted to complete the installation. For more information about how to install the sharing application, see <link xlink:href="2bf09690-9dba-43b7-9e0a-0110915d4081">Download and install the Rights Management sharing application</link>.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Specify the options that you want for this file in the <externalLink><linkText>share protected dialog box</linkText><linkUri>http://technet.microsoft.com/library/dn574738.aspx</linkUri></externalLink>, and then click <ui>Send Now</ui>.</para>
            </content>
          </step>
        </steps>
      </procedure>
    </content>
    <sections>
      <section expanded="false">
        <title>Other ways to protect a file that you share by email</title>
        <content>
          <para>In addition to sharing a protected file by using Outlook, you can also use these alternatives:</para>
          <list class="bullet">
            <listItem>
              <para>From File Explorer: This method works for all files.</para>
            </listItem>
            <listItem>
              <para>From an Office application: This method works for applications that the RMS sharing application supports by using the Office add-in so that you see the <ui>RMS</ui> group on the ribbon.</para>
            </listItem>
          </list>
          <procedure>
            <title>Using File Explorer or an Office application: To protect a file that you share by email</title>
            <steps class="ordered">
              <step>
                <content>
                  <para>Use one of the following options: </para>
                  <list class="bullet">
                    <listItem>
                      <para>For File Explorer: Right-click the file, select <ui>Protect with RMS</ui>, and then select <ui>Share Protected</ui>:</para>
                      <mediaLink>
                        <image xlink:href="c046fc51-6b93-4cb9-a76e-ca4daccc37ee" />
                      </mediaLink>
                    </listItem>
                    <listItem>
                      <para>For the Office applications, Word, Excel, and PowerPoint: Make sure that you have saved the file first. Then, on the <ui>Home</ui> tab, in the <ui>RMS</ui> group, click <ui>Share Protected</ui> and then click <ui>Share Protected</ui> again:</para>
                      <mediaLink>
                        <image xlink:href="78b66704-90d6-4612-8264-b8b3a86db5ce" />
                      </mediaLink>
                    </listItem>
                  </list>
                  <para />
                  <para>If you do not see these options for protection, it’s likely that either the RMS sharing application is not installed on your computer, the latest version isn’t installed, or your computer must be restarted to complete the installation. For more information about how to install the sharing application, see <link xlink:href="2bf09690-9dba-43b7-9e0a-0110915d4081">Download and install the Rights Management sharing application</link>.</para>
                </content>
              </step>
              <step>
                <content>
                  <para>Specify the options that you want for this file in the <externalLink><linkText>share protected dialog box</linkText><linkUri>http://technet.microsoft.com/library/dn574738.aspx</linkUri></externalLink>, and then click <ui>Send</ui>.</para>
                </content>
              </step>
              <step>
                <content>
                  <para>You might quickly see a dialog box to tell you that the file is being protected, and then you see an email message created for you that tells the recipients that the attachments are protected with Microsoft RMS, and that they must sign in. When they click the link to sign in, they see instructions and links to ensure that they can open your protected attachment.</para>
                  <para>Example:</para>
                  <mediaLink>
                    <image xlink:href="4740129b-622e-4323-bb71-5364ac08d041" />
                  </mediaLink>
                  <para />
                  <para>Are you wondering: <link xlink:href="7b91ab30-6363-4929-bcbd-4dfbd05f644a#BKMK_PPDF">What’s the .ppdf file that’s automatically created?</link></para>
                </content>
              </step>
              <step>
                <content>
                  <para>Optional: You can change anything that you want in this email message. For example, you can add to or change the subject or text in the message.</para>
                  <alert class="warning">
                    <para>Although you can add or remove people from this email message, this does not change the permissions for the attachment that you specified in the <ui>share protected</ui> dialog box. If you want to change those permissions, for example, give a new person permissions to open the file, close the email message without saving or sending it, and return to step 1.</para>
                  </alert>
                </content>
              </step>
              <step>
                <content>
                  <para>Send the email message.</para>
                </content>
              </step>
            </steps>
          </procedure>
        </content>
      </section>
    </sections>
  </section>
  <section DoNotNumber="false">
    <title>Examples and other instructions</title>
    <content>
      <para>For examples for how you might use the Rights Management sharing application, and how-to instructions, see the following sections from the Rights Management sharing application user guide:</para>
      <list class="bullet">
        <listItem>
          <para>
            <link xlink:href="eaf6d02c-aa36-4915-856e-49bb71ab1484#BKMK_SharingExamples">Examples for using the RMS sharing application</link>
          </para>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="eaf6d02c-aa36-4915-856e-49bb71ab1484#BKMK_SharingInstructions">What do you want to do?</link>
          </para>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics>
    <link xlink:href="eaf6d02c-aa36-4915-856e-49bb71ab1484">Rights Management sharing application user guide</link>
  </relatedTopics>
</developerConceptualDocument>