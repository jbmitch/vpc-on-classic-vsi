---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-07"

keywords: add ssh key, delete ssh key, ssh key, manage ssh key, virtual server instance, instance, virtual server

subcollection: vpc-on-classic-vsi

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# Managing SSH keys
{: #managing-ssh-keys}

To access {{site.data.keyword.vsi_is_full}} instances, you must have an SSH key available to use. You can add and delete SSH keys in {{site.data.keyword.cloud_notm}} console and by using the CLI. 
{:shortdesc}

Managing keys by using the {{site.data.keyword.cloud_notm}} console or CLI has no effect on keys in instances that are already created. (For an existing Linux instance, you can edit keys directly in the `~/.ssh/` directory of the instance.)

## Before you begin
{: #prereq-ssh-key-available}

To create a virtual server instance, you must have an SSH key uploaded and available so that you can connect to your instance after it's provisioned.

For more information about locating or generating an SSH key, see [SSH keys](/docs/vpc-on-classic-vsi?topic=vpc-on-classic-vsi-ssh-keys#ssh-keys).
{: tip}

## Managing SSH keys with IBM Cloud console
{: #managing-ssh-keys-with-ibm-cloud-console}

When you provision a virtual server, you can select from available SSH keys or upload a new one. You cannot generate SSH keys in {{site.data.keyword.cloud_notm}} console.


You can manage and delete SSH keys by using the {{site.data.keyword.cloud_notm}} console.
1. In [{{site.data.keyword.cloud_notm}} console ![External link icon](../icons/launch-glyph.svg "External link icon")](https://console.cloud.ibm.com/vpc), navigate to **Menu icon ![Menu icon](../icons/icon_hamburger.svg) > VPC Infrastructure > Compute > SSH keys**.
2. From here, you can add or delete an SSH key. 

To add an SSH key with the IBM Cloud console:

1. Click the **Add SSH Key** link to display the SSH key creation dialog.
2. Enter a name for your SSH key.
3. Choose a specific resource group, if necessary.
4. Then select your region from the drop down list.

  You will only be shown a list of available regions for your specific resource group.
  {: note}
  
5. Locate your SSH key by looking for a file called id_rsa.pub under an .ssh directory under your home directory, for example, `/Users/<USERNAME>/.ssh/id_rsa.pub`. 

  There may be two files of the same file name in this directory. The "public" SSH key, contains the extension `.pub`, and the contents begin with `ssh-rsa` and end with your email address.
  {: tip}
  
 6. Paste the entire contents of the SSH file into the **Public key** space on the form.
 7. Click **Add SSH key** to create the your SSH key in the IBM Cloud console. It now displas in **VPC Infrastructure > Compute > SSH keys**.

## Managing SSH keys by using the CLI
{: #managing-ssh-keys-by-using-the-cli}

You can also manage your SSH keys by using the CLI.

| Action           | Command                     | What happens next |
| ---------------- | --------------------------- | ----------------- |
| Create SSH key   | `ibmcloud is key-create`    | After you create an SSH key, it is added to the list of keys. |
| View key details | `ibmcloud is key`           | You can view the name of the key and the ID of the key. |
| List keys        | `ibmcloud is keys`          | You can view all of your existing SSH keys. |
| Update key       | `ibmcloud is key-update`    | After you update an existing key, the key is renamed immediately. |
| Delete key       | `ibmcloud is key-delete`    | After you remove an SSH key, it can no longer be used when you provision a new instance or when you perform an OS reload on an existing instance. However, the key is still available on any instances that you have provisioned with it, and you can use it to log in. |
{: caption="Table 1. SSH key actions" caption-side="top"}
