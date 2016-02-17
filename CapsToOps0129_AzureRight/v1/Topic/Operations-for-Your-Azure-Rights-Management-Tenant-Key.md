---
title: Operations for Your Azure Rights Management Tenant Key
ms.custom: na
ms.reviewer: na
ms.service: rights-management
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1284d0ee-0a72-45ba-a64c-3dcb25846c3d
author: Cabailey
---
# Operations for Your Azure Rights Management Tenant Key
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Depending on your tenant key topology (Microsoft-managed or customer-managed), you have different levels of control and responsibility for your Microsoft Azure Rights Management (Azure RMS) tenant key after it is implemented.</para>
    <para>When you manage your own tenant key, this is often referred to as bring your own key (BYOK). For more information about this scenario and how to choose between the two tenant key topologies, see <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14">Planning and operations for your Azure Rights Management tenant key</link>.</para>
    <para>The following table identifies which operations you can do, depending on the topology that you’ve chosen for your Azure RMS tenant key. </para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Lifecycle operation</para>
          </TD>
          <TD>
            <para>Microsoft-managed (default)</para>
          </TD>
          <TD>
            <para>Customer-managed (BYOK)</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>Revoke your tenant key</para>
          </TD>
          <TD>
            <para>No (automatic)</para>
          </TD>
          <TD>
            <para>No (automatic)</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Re-key your tenant key</para>
          </TD>
          <TD>
            <para>Yes</para>
          </TD>
          <TD>
            <para>Yes</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Backup and recover your tenant key</para>
          </TD>
          <TD>
            <para>No</para>
          </TD>
          <TD>
            <para>Yes</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Export your tenant key</para>
          </TD>
          <TD>
            <para>Yes</para>
          </TD>
          <TD>
            <para>No</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Respond to a breach</para>
          </TD>
          <TD>
            <para>Yes</para>
          </TD>
          <TD>
            <para>Yes</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para/>
    <para>After you have identified which topology you have implemented, use one of the following sections for more information about these operations for your Azure RMS tenant key.</para>
  </introduction>
  <section address="BKMK_MSManagedOperations" expanded="false">
    <title>Microsoft-managed: Tenant key lifecycle operations</title>
    <content>
      <para>If Microsoft manages your tenant key for Azure Rights Management (the default), use the following sections for more information about the lifecycle operations that are relevant to this topology:</para>
      <list class="bullet">
        <listItem>
          <para>
            <link xlink:href="1284d0ee-0a72-45ba-a64c-3dcb25846c3d#BKMK_MSRevoke">Revoke your tenant key</link>
          </para>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="1284d0ee-0a72-45ba-a64c-3dcb25846c3d#BKMK_MSRekey">Re-key your tenant key</link>
          </para>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="1284d0ee-0a72-45ba-a64c-3dcb25846c3d#BKMK_MSBackup">Backup and recover your tenant key</link>
          </para>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="1284d0ee-0a72-45ba-a64c-3dcb25846c3d#BKMK_MSExport">Export your tenant key</link>
          </para>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="1284d0ee-0a72-45ba-a64c-3dcb25846c3d#BKMK_MSBreach">Respond to a breach</link>
          </para>
        </listItem>
      </list>
    </content>
    <sections>
      <section address="BKMK_MSRevoke">
        <title>Revoke your tenant key</title>
        <content>
          <para>When you unsubscribe from Azure RMS, Azure RMS stops using your tenant key and no action is needed from you. </para>
        </content>
      </section>
      <section address="BKMK_MSRekey">
        <title>Re-key your tenant key</title>
        <content>
          <para>Re-keying is also known as rolling your key. Do not re-key your tenant key unless it’s really necessary. Older clients, such as Office 2010, were not designed to handle key changes gracefully. In this scenario, you must clear the RMS state on computers by using Group Policy or an equivalent mechanism. However, there are some legitimate events that may force you to re-key your tenant key. For example:</para>
          <list class="bullet">
            <listItem>
              <para>Your company has split into two or more companies. When you re-key your tenant key, the new company will not have access to new content that your employees publish. They can access the old content if they have a copy of the old tenant key.</para>
            </listItem>
            <listItem>
              <para>You believe the master copy of your tenant key (the copy in your possession) was compromised.</para>
            </listItem>
          </list>
          <para>You can re-key your tenant key by calling Microsoft Customer Support Services (CSS) and proving that you are the tenant administrator.  </para>
          <para>When you re-key your tenant key, new content is protected by using the new tenant key. This happens in a phased manner, so for a period of time, some new content will continue to be protected with the old tenant key. Previously protected content stays protected to your old tenant key. To support this scenario, Azure RMS retains your old tenant key so that it can issue licenses for old content.</para>
        </content>
      </section>
      <section address="BKMK_MSBackup">
        <title>Backup and recover your tenant key</title>
        <content>
          <para>Microsoft is responsible for backing up your tenant key and no action is required from you.</para>
        </content>
      </section>
      <section address="BKMK_MSExport">
        <title>Export your tenant key</title>
        <content>
          <para>You can export your Azure RMS configuration and tenant key by following the instructions in these three steps:</para>
          <procedure>
            <title>Step 1: Initiate export</title>
            <steps class="bullet">
              <step>
                <content>
                  <para>To do this, contact Microsoft Customer Service Support (CSS). You must prove you are an administrator for your Azure RMS tenant.</para>
                </content>
              </step>
            </steps>
          </procedure>
          <procedure>
            <title>Step 2: Wait for verification</title>
            <steps class="bullet">
              <step>
                <content>
                  <para>Microsoft verifies that your request to release your RMS tenant key is legitimate. This process can take up to 3 weeks.</para>
                </content>
              </step>
            </steps>
          </procedure>
          <procedure>
            <title>Step 3: Receive key instructions from CSS</title>
            <steps class="bullet">
              <step>
                <content>
                  <para>Microsoft Customer Support Services (CSS) will send you your Azure RMS configuration and tenant key as encrypted in a password-protected file that has a .tpd file name extension. To do this, CSS first sends you (as the person who initiated the export) a tool by email. You must run the tool from a command prompt as follows:</para>
                  <code>AadrmTpd.exe -createkey
</code>
                  <para>This generates an RSA key pair and saves the public and private halves as files in the current folder. For example: <system>PublicKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt</system>
 and <system>PrivateKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt</system>.</para><para>Respond to the email from CSS, attaching the file that has a name that starts with <system>PublicKey</system>. CSS will next send you a TPD file as an .xml file that is encrypted with your RSA key. Copy this file to the same folder as you ran the AadrmTpd tool originally, and run the tool again, using your file that starts with <system>PrivateKey</system> and the file from CSS. For example:</para>
                  <code>AadrmTpd.exe -key PrivateKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt -target TPD-77172C7B-8E21-48B7-9854-7A4CEAC474D0.xml</code>
                  <para>The output of this command should be two files: One contains the plaintext password for the password-protected TPD, and the other is the password-protected TPD itself. For cross-referencing purposes, both should have the same GUID as the public and private key files from when you ran the AadrmTpd.exe -createkey command:</para>
                  <list class="bullet">
                    <listItem>
                      <para>Password-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt</para>
                    </listItem>
                    <listItem>
                      <para>ExportedTPD-FA29D0FE-5049-4C8E-931B-96C6152B0441.xml</para>
                    </listItem>
                  </list>
                  <para>Backup these files and store them safely to ensure that you can continue to decrypt content that is protected with this tenant key. In addition, if you are migrating to AD RMS, you can import this TPD file (the file that starts with <system>ExportedTDP</system>) to your AD RMS server.</para>
                  <para/>
                </content>
              </step>
            </steps>
          </procedure>
          <procedure>
            <title>Step 4: Ongoing: Protect your tenant key</title>
            <steps class="bullet">
              <step>
                <content>
                  <para>After you receive your tenant key, keep it well-guarded, because if somebody gets access to it, they can decrypt all documents that are protected by using that key. </para>
                  <para>If the reason for exporting your tenant key is because you no longer want to use Azure RMS, as a best practice, now deactivate your RMS tenant. Do not delay doing this after you receive your tenant key because this precaution will help to minimize the consequences if your tenant key is accessed by somebody who should not have it. For instructions, see <link xlink:href="0b1c2064-0d01-45ae-a541-cebd7fd762ad">Deactivating Azure Rights Management</link>.</para>
                </content>
              </step>
            </steps>
          </procedure>
        </content>
      </section>
      <section address="BKMK_MSBreach">
        <title>Respond to a breach</title>
        <content>
          <para>No security system, no matter how strong, is complete without a breach response process. Your tenant key might be compromised or stolen. Even when it’s well protected well, vulnerabilities might be found in current generation HSM technology or current key lengths and algorithms. </para>
          <para>Microsoft has a dedicated team to respond to security incidents in its products and services. As soon as there is a credible report of an incident, this team engages to investigate the scope, root cause, and mitigations. If this incident affects your assets, then Microsoft will notify your Azure RMS tenant administrators by email by using the address that you supplied when you subscribed. </para>
          <para>If you have a breach, the best action that you or Microsoft can take depends on the scope of the breach; Microsoft will work with you through this process. The following table shows some typical situations and the likely response, although the exact response will depend on all the information that is revealed during the investigation. </para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>Incident description</para>
                </TD>
                <TD>
                  <para>Likely response</para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>Your tenant key is leaked.</para>
                </TD>
                <TD>
                  <para>Re-key your tenant key. See the <link xlink:href="1284d0ee-0a72-45ba-a64c-3dcb25846c3d#BKMK_MSRekey">Re-key your tenant key</link> section in this topic.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>An unauthorized individual or malware got rights to use your tenant key but the key itself did not leak.</para>
                </TD>
                <TD>
                  <para>Re-keying your tenant key does not help here and requires root-cause analysis. If a process or software bug was responsible for the unauthorized individual to get access, that situation must be resolved.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Vulnerability discovered in the RSA algorithm, or key length, or brute-force attacks become computationally feasible.</para>
                </TD>
                <TD>
                  <para>Microsoft must update the Azure RMS to support new algorithms and longer key lengths that are resilient, and instruct all customers to renew their tenant keys.</para>
                </TD>
              </tr>
            </tbody>
          </table>
        </content>
      </section>
    </sections>
  </section>
  <section address="BKMK_BYOKManagedOperations" expanded="false">
    <title>Customer-managed: Tenant key lifecycle operations</title>
    <content>
      <para>If you manage your tenant key for Azure Rights Management (the bring your own key, or BYOK, scenario), use the following sections for more information about the lifecycle operations that are relevant to this topology:</para>
      <list class="bullet">
        <listItem>
          <para>
            <link xlink:href="1284d0ee-0a72-45ba-a64c-3dcb25846c3d#BKMK_BYOKRevoke">Revoke your tenant key</link>
          </para>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="1284d0ee-0a72-45ba-a64c-3dcb25846c3d#BKMK_BYOKRekey">Re-key your tenant key</link>
          </para>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="1284d0ee-0a72-45ba-a64c-3dcb25846c3d#BKMK_BYOKBackup">Backup and recover your tenant key</link>
          </para>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="1284d0ee-0a72-45ba-a64c-3dcb25846c3d#BKMK_BYOKExport">Export your tenant key</link>
          </para>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="1284d0ee-0a72-45ba-a64c-3dcb25846c3d#BKMK_BYOKBreach">Respond to a breach</link>
          </para>
        </listItem>
      </list>
    </content>
    <sections>
      <section address="BKMK_BYOKRevoke">
        <title>Revoke your tenant key</title>
        <content>
          <para>When you unsubscribe from Azure RMS, Azure RMS stops using your tenant key and no action is needed from you. </para>
        </content>
      </section>
      <section address="BKMK_BYOKRekey">
        <title>Re-key your tenant key</title>
        <content>
          <para>Re-keying is also known as rolling your key. Do not re-key your tenant key unless it’s really necessary. Older clients, such as Office 2010, were not designed to handle key changes gracefully. In this scenario, you must clear the RMS state on computers by using Group Policy or an equivalent mechanism. However, there are some legitimate events that may force you to re-key your tenant key. For example:</para>
          <list class="bullet">
            <listItem>
              <para>Your company has split into two or more companies. When you re-key your tenant key, the new company will not have access to new content that your employees publish. They can access the old content if they have a copy of the old tenant key.</para>
            </listItem>
            <listItem>
              <para>You believe the master copy of your tenant key (the copy in your possession) was compromised.</para>
            </listItem>
          </list>
          <para>When you re-key your tenant key, new content is protected by using the new tenant key. This happens in a phased manner, so for a period of time, some new content will continue to be protected with the old tenant key. Previously protected content stays protected to your old tenant key. To support this scenario, Azure RMS retains your old tenant key so that it can issue licenses for old content.</para>
          <para>To re-key your tenant key, generate and create a new key over the Internet or in person, by using the procedures in the <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_ImplementBYOK">Implementing bring your own key (BYOK)</link> section from the <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14">Planning and operations for your Azure Rights Management tenant key</link> topic.</para>
        </content>
      </section>
      <section address="BKMK_BYOKBackup">
        <title>Backup and recover your tenant key</title>
        <content>
          <para>You are responsible for backing up your tenant key. If you generated your tenant key in a Thales HSM, to back up the key, just back up the Tokenized Key file, the World file, and the Administrator Cards.</para>
          <para>If you transferred your key by following the procedures in the <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_ImplementBYOK">Implementing bring your own key (BYOK)</link> section from the <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14">Planning and operations for your Azure Rights Management tenant key</link> topic, Azure RMS will persist the Tokenized Key File, to protect against failure of any Azure RMS nodes. However, do not consider this to be a full backup. For example, if you ever need a plaintext copy of your key to use outside a Thales HSM, Azure RMS will not be able to retrieve it for you because it only has a non-recoverable copy.</para>
        </content>
      </section>
      <section address="BKMK_BYOKExport">
        <title>Export your tenant key</title>
        <content>
          <para>If you use BYOK, you cannot export your tenant key from Azure RMS. The copy in Azure RMS is non-recoverable. If you want to delete this key so it can no longer be used, contact Microsoft Customer Service Support (CSS). </para>
        </content>
      </section>
      <section address="BKMK_BYOKBreach">
        <title>Respond to a breach</title>
        <content>
          <para>No security system, no matter how strong, is complete without a breach response process. Your tenant key might be compromised or stolen. Even when it’s well protected well, vulnerabilities might be found in current generation HSM technology or current key lengths and algorithms. </para>
          <para>Microsoft has a dedicated team to respond to security incidents in its products and services. As soon as there is a credible report of an incident, this team engages to investigate the scope, root cause, and mitigations. If this incident affects your assets, then Microsoft will notify your Azure RMS tenant administrators by email by using the address that you supplied when you subscribed. </para>
          <para>If you have a breach, the best action that you or Microsoft can take  depends on the scope of the breach; Microsoft will work with you through this process. The following table shows some typical situations and the likely response, although the exact response will depend on all the information that is revealed during the investigation. </para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>Incident description</para>
                </TD>
                <TD>
                  <para>Likely response</para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>Your tenant key is leaked.</para>
                </TD>
                <TD>
                  <para>Re-key your tenant key. See the <link xlink:href="1284d0ee-0a72-45ba-a64c-3dcb25846c3d#BKMK_BYOKRekey">Re-key your tenant key</link> section in this topic.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>An unauthorized individual or malware got rights to use your tenant key but the key itself did not leak.</para>
                </TD>
                <TD>
                  <para>Re-keying your tenant key does not help here and requires root-cause analysis. If a process or software bug was responsible for the unauthorized individual to get access, that situation must be resolved.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Vulnerability discovered in the current-generation HSM technology.</para>
                </TD>
                <TD>
                  <para>Microsoft must update the HSMs. If there is reason to believe that the vulnerability exposed keys, then Microsoft will instruct all customers to renew their tenant keys.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Vulnerability discovered in the RSA algorithm, or key length, or brute-force attacks become computationally feasible.</para>
                </TD>
                <TD>
                  <para>Microsoft must update the Azure RMS to support new algorithms and longer key lengths that are resilient, and instruct all customers to renew their tenant keys.</para>
                </TD>
              </tr>
            </tbody>
          </table>
        </content>
      </section>
    </sections>
  </section>
  <relatedTopics>
    <link xlink:href="18564e4a-9364-4ed2-8f17-89d24fc0d878">Using Azure Rights Management</link>
  </relatedTopics>
</developerConceptualDocument>
