---
title: Track and revoke your documents when you use the RMS sharing application
ms.custom: na
ms.reviewer: na
ms.service: rights-management
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 61f349ce-bdd2-45c1-acc5-bc83937fb187
author: Cabailey
---
# Track and revoke your documents when you use the RMS sharing application
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>After you have protected your documents by using the RMS sharing application, if your organization is using Azure Rights Management rather than Active Directory Rights Management Services, you can track how people are using your protected documents. If necessary, you can also revoke access to these documents when you want to stop sharing them. To do this, you use the <embeddedLabel>document tracking site</embeddedLabel>, which you can access from Windows computers, Mac computers, and even from tablets and phones.</para>
    <alert class="tip">
      <para>Two minute video: <externalLink><linkText>Azure RMS Document Tracking and Revocation</linkText><linkUri>http://channel9.msdn.com/Series/Information-Protection/Azure-RMS-Document-Tracking-and-Revocation</linkUri></externalLink></para>
    </alert>
    <para>When you access this site, sign in to track your documents. Providing your organization has a <externalLink><linkText>subscription that supports document tracking and revocation</linkText><linkUri>https://technet.microsoft.com/dn858608.aspx</linkUri></externalLink> and you are assigned a license for this subscription, you can then see who tried to open the files that you protected and whether they were successful (they were successfully authenticated) or not. Each time they tried to access the document, and their location at the time. In addition: </para>
    <list class="bullet">
      <listItem>
        <para>If you need to stop sharing a document: Click <ui>Revoke access</ui>, note the period of time that the document will continue to be available, and decide whether to let people know that you’re revoking access to the document you previously shared, and provide a customized message.</para>
      </listItem>
      <listItem>
        <para>If you want to export to Excel: Click <ui>Open in Excel</ui>, so that you can then modify the data, and create your own views and graphs.</para>
      </listItem>
      <listItem>
        <para>If you want to configure email notifications: Click <ui>Settings</ui> and select how and whether to be emailed when the document is accessed.</para>
      </listItem>
      <listItem>
        <para>If you have questions or want to provide feedback about the document tracking site: Click the Help icon to access the <externalLink><linkText>FAQ for Document Tracking</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=523977</linkUri></externalLink>.</para>
      </listItem>
    </list>
  </introduction>
  <section expanded="true">
    <title>Using Office to access the document tracking site</title>
    <content>
      <procedure>
        <title/>
        <steps class="bullet">
          <step>
            <content>
              <para>For the Office applications, Word, Excel, and PowerPoint: On the <ui>Home</ui> tab, in the <ui>RMS</ui> group, click <ui>Share Protected</ui>, and then click <ui>Track Usage</ui>.</para>
              <para> </para>
              <mediaLink>
                <image xlink:href="d1280a21-1935-4156-b760-194988cef32c"/>
              </mediaLink>
              <para> </para>
            </content>
          </step>
          <step>
            <content>
              <para>For Outlook: On the <ui>Home</ui> tab, in the <ui> RMS</ui> group, click <ui>Track Usage</ui>:</para>
              <para> </para>
              <mediaLink>
                <image xlink:href="fc86904c-bcde-43a7-8691-de964a3f0085"/>
              </mediaLink>
              <para> </para>
            </content>
          </step>
        </steps>
        <conclusion>
          <content>
            <para>If you do not see these options for RMS, it’s likely that either the RMS sharing application is not installed on your computer, the latest version isn’t installed, or your computer must be restarted to complete the installation. For more information about how to install the sharing application, see <link xlink:href="2bf09690-9dba-43b7-9e0a-0110915d4081">Download and install the Rights Management sharing application</link>.</para>
          </content>
        </conclusion>
      </procedure>
    </content>
    <sections>
      <section expanded="false">
        <title>Other ways to track and revoke your documents</title>
        <content>
          <para>In addition to tracking your documents on Windows computers by using Office applications, you can also use these alternatives:</para>
          <list class="bullet">
            <listItem>
              <para>
                <embeddedLabel>Using a web browser</embeddedLabel>: This method works for all supported devices.</para>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Using File Explorer</embeddedLabel>: This method works for Windows computers.</para>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Using an Outlook email message</embeddedLabel>: This method works for Windows computers. </para>
            </listItem>
          </list>
          <procedure>
            <title>Using a web browser to access the doc tracking site</title>
            <steps class="bullet">
              <step>
                <content>
                  <para>Using a supported browser, go to the <externalLink><linkText>document tracking site</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=529562</linkUri></externalLink>.</para>
                  <para>Supported browsers: We recommend using Internet Explorer that is at least version 10, but you can use any of following browsers to use the document tracking site:</para>
                  <list class="bullet">
                    <listItem>
                      <para>Internet Explorer: At least version 10</para>
                    </listItem>
                    <listItem>
                      <para>Internet Explorer 9 with at least MS12-037: Cumulative Security Update for Internet Explorer: June 12, 2012</para>
                    </listItem>
                    <listItem>
                      <para>Mozilla Firefox: At least version 12</para>
                    </listItem>
                    <listItem>
                      <para>Apple Safari 5: At least version 5</para>
                    </listItem>
                    <listItem>
                      <para>Google Chrome: At least version 18</para>
                    </listItem>
                  </list>
                </content>
              </step>
            </steps>
          </procedure>
          <procedure>
            <title>Using File Explorer to access the doc tracking site</title>
            <steps class="bullet">
              <step>
                <content>
                  <para>Right-click the file, select <ui>Protect with RMS</ui>, and then select <ui>Track Usage</ui>:</para>
                  <mediaLink>
                    <image xlink:href="b87cad5c-8be0-48b6-aadd-097cd6b6ed24"/>
                  </mediaLink>
                </content>
              </step>
            </steps>
          </procedure>
          <procedure>
            <title>Using an Outlook email message to access the doc tracking site</title>
            <steps class="bullet">
              <step>
                <content>
                  <para>In an email message, in the <ui>Message</ui> tab, in the <ui> RMS</ui> group, click <ui>Share Protected</ui>, and then click <ui>Track Usage</ui>:</para>
                  <para> </para>
                  <mediaLink>
                    <image xlink:href="1c479fe1-570d-43c0-ae35-4cba78a04eee"/>
                  </mediaLink>
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
