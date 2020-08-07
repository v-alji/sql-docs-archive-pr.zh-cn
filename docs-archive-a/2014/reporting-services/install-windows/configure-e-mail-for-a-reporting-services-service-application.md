---
title: " (SharePoint 2010 和 SharePoint 2013) Reporting Services 服务应用程序配置电子邮件 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 38fc34a6-aae7-4dde-9ad2-f1eee0c42a9f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 628122289f8a9d83a307d70a369ab51f8f571c04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588330"
---
# <a name="configure-e-mail-for-a-reporting-services-service-application-sharepoint-2010-and-sharepoint-2013"></a><span data-ttu-id="e0a71-102">为 Reporting Services 服务应用程序配置电子邮件（SharePoint 2010 和 SharePoint 2013）</span><span class="sxs-lookup"><span data-stu-id="e0a71-102">Configure E-mail for a Reporting Services Service Application (SharePoint 2010 and SharePoint 2013)</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="e0a71-103">数据警报功能会在电子邮件中发送警报。</span><span class="sxs-lookup"><span data-stu-id="e0a71-103">data alerting sends alerts in e-mail messages.</span></span> <span data-ttu-id="e0a71-104">若要发送电子邮件，您可能需要配置 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务应用程序，并可能需要修改该服务应用程序的电子邮件传递扩展插件。</span><span class="sxs-lookup"><span data-stu-id="e0a71-104">To send e-mail you may need to configure your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application and you may need to modify the e-mail delivery extension for the service application.</span></span> <span data-ttu-id="e0a71-105">如果您计划将电子邮件传递扩展插件用于 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 订阅功能，则也需要进行电子邮件设置。</span><span class="sxs-lookup"><span data-stu-id="e0a71-105">The e-mail settings are also required if you plan to use the e-mail delivery extension for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] subscription feature.</span></span>  
  
||  
|-|  
|[!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="e0a71-106">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Sharepoint 模式 &#124; sharepoint 2010 和 sharepoint 2013。</span><span class="sxs-lookup"><span data-stu-id="e0a71-106">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode &#124; SharePoint 2010 and SharePoint 2013.</span></span>|  
  
### <a name="to-configure-e-mail-for-the-shared-service"></a><span data-ttu-id="e0a71-107">为共享服务配置电子邮件</span><span class="sxs-lookup"><span data-stu-id="e0a71-107">To configure e-mail for the shared service</span></span>  
  
1.  <span data-ttu-id="e0a71-108">在 SharePoint 管理中心中，单击 **“应用程序管理”**。</span><span class="sxs-lookup"><span data-stu-id="e0a71-108">In SharePoint Central Administration, click the **Application Management**.</span></span>  
  
2.  <span data-ttu-id="e0a71-109">在 **“服务应用程序”** 组中，单击 **“管理服务应用程序”**。</span><span class="sxs-lookup"><span data-stu-id="e0a71-109">In the **Service Applications** group, click **Manage service applications**.</span></span>  
  
3.  <span data-ttu-id="e0a71-110">在 **“名称”** 列表中，单击 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务应用程序的名称。</span><span class="sxs-lookup"><span data-stu-id="e0a71-110">In the **Name** list, click the name of your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span>  
  
4.  <span data-ttu-id="e0a71-111">在“管理 Reporting Services 应用程序”页上，单击“电子邮件设置”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e0a71-111">Click **E-mail Settings** on the **Manage Reporting Services Application** page.</span></span>  
  
5.  <span data-ttu-id="e0a71-112">选择 **“使用 SMTP 服务器”**。</span><span class="sxs-lookup"><span data-stu-id="e0a71-112">Select **Use SMTP server**.</span></span>  
  
6.  <span data-ttu-id="e0a71-113">在 **“出站 SMTP 服务器”** 框中，键入 SMTP 服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="e0a71-113">In the **Outbound SMTP server** box, type the name of an SMTP server.</span></span>  
  
7.  <span data-ttu-id="e0a71-114">在“发件人地址”框中，键入电子邮件地址\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e0a71-114">In the **From address** box, type an e-mail address.</span></span>  
  
     <span data-ttu-id="e0a71-115">此地址为所有警报电子邮件的发件人。</span><span class="sxs-lookup"><span data-stu-id="e0a71-115">This address is the sender of all alert e-mail messages.</span></span>  
  
     <span data-ttu-id="e0a71-116">**“发件人地址”** 中指定的用户帐户必须是您为 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务应用程序配置应用程序池时指定的托管帐户。</span><span class="sxs-lookup"><span data-stu-id="e0a71-116">The account of the user specified in **From address** must be a managed account that you specified when you configured the application pool for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span> <span data-ttu-id="e0a71-117">如果您具有权限，则可以在 SharePoint 管理中心的“服务帐户”页上查看现有托管帐户的列表。</span><span class="sxs-lookup"><span data-stu-id="e0a71-117">If you have permission, you can view a list of existing managed accounts on the Service Accounts page in SharePoint Central Administration.</span></span>  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="ntlm-authentication"></a><span data-ttu-id="e0a71-118">NTLM 身份验证</span><span class="sxs-lookup"><span data-stu-id="e0a71-118">NTLM Authentication</span></span>  
  
1.  <span data-ttu-id="e0a71-119">如果您的电子邮件环境需要 NTLM 身份验证且不允许匿名访问，则需要修改 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务应用程序的电子邮件传递扩展插件配置。</span><span class="sxs-lookup"><span data-stu-id="e0a71-119">If your email environment requires NTLM authentication and does not allow anonymous access, you need to modify the e-mail delivery extension configuration for your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service applications.</span></span> <span data-ttu-id="e0a71-120">将**SMTPAuthenticate**更改为使用值 "2"。</span><span class="sxs-lookup"><span data-stu-id="e0a71-120">Change the **SMTPAuthenticate** to use a value of "2".</span></span> <span data-ttu-id="e0a71-121">无法从用户界面更改此值。</span><span class="sxs-lookup"><span data-stu-id="e0a71-121">This value cannot be changed from the user interface.</span></span> <span data-ttu-id="e0a71-122">以下 PowerShell 脚本示例更新了名为“SSRS_TESTAPPLICATION”的服务应用程序的报表服务器电子邮件传递扩展插件的完全配置。</span><span class="sxs-lookup"><span data-stu-id="e0a71-122">The following PowerShell script example, updates the full configuration for the report server e-mail delivery extension for the service application named "SSRS_TESTAPPLICATION".</span></span> <span data-ttu-id="e0a71-123">请注意，此脚本中列出的某些节点（例如“发件人”地址）也可从用户界面进行设置。</span><span class="sxs-lookup"><span data-stu-id="e0a71-123">Note some of the nodes listed in the script can also be set from the user interface, for example the "From" address.</span></span>  
  
    ```powershell
    $app = Get-SPRSServiceApplication | Where {$_.name -like "SSRS_TESTAPPLICATION *"}  
    $emailCfg = Get-SPRSExtension -Identity $app -ExtensionType "Delivery" -Name "Report Server Email" | Select -ExpandProperty ConfigurationXml
    $emailXml = [xml]$emailCfg
    $emailXml.SelectSingleNode("//SMTPServer").InnerText = "your email server name"  
    $emailXml.SelectSingleNode("//SendUsing").InnerText = "2"  
    $emailXml.SelectSingleNode("//SMTPAuthenticate").InnerText = "2"  
    $emailXml.SelectSingleNode("//From").InnerText = "your FROM email address"  
    Set-SPRSExtension -Identity $app -ExtensionType "Delivery" -Name "Report Server Email" -ExtensionConfiguration $emailXml.OuterXml  
    ```  
  
2.  <span data-ttu-id="e0a71-124">如果需要验证服务应用程序的名称，请运行**get-sprsserviceapplication** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e0a71-124">If you need to verify the name of your service application, run the **Get-SPRSServiceApplication** cmdlet.</span></span>  
  
    ```powershell
    Get-SPRSServiceApplication  
    ```  
  
3.  <span data-ttu-id="e0a71-125">以下示例将返回名为“SSRS_TESTAPPLICATION”的服务应用程序的电子邮件扩展插件的当前值。</span><span class="sxs-lookup"><span data-stu-id="e0a71-125">The following example will return the current values of the e-mail extension for the service application named "SSRS_TESTAPPLICATION".</span></span>  
  
    ```powershell
    $app = get-sprsserviceapplication | Where {$_.name -like "SSRSTEST_APPLICATION*"}  
    Get-SPRSExtension -Identity $app -ExtensionType "Delivery" -Name "Report Server Email" | Select -ExpandProperty ConfigurationXml  
    ```  
  
4.  <span data-ttu-id="e0a71-126">以下示例将使用名为“SSRS_TESTAPPLICATION”的服务应用程序的电子邮件扩展插件的当前值创建名为“emailconfig.txt”的新文件</span><span class="sxs-lookup"><span data-stu-id="e0a71-126">The following example will create a new file named "emailconfig.txt" with the current values of the e-mail extension for the service application named "SSRS_TESTAPPLICATION"</span></span>  
  
    ```powershell
    $app = Get-SPRSServiceApplication | Where {$_.name -like "SSRS_TESTAPPLICATION*"}  
    Get-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" | Select -ExpandProperty ConfigurationXml | Out-File c:\emailconfig.txt  
    ```
