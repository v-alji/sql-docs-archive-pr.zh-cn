---
title: SharePoint 场 (升级顾问) 所需的域帐户 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 90cd6d3e-a271-4cb8-81f2-fc555b2d3cab
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 7d180fbc12a264256156c878916838f7caeec723
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591102"
---
# <a name="domain-accounts-required-for-sharepoint-farm-upgrade-advisor"></a><span data-ttu-id="bbe9b-102">SharePoint 场要求使用域帐户（升级顾问）</span><span class="sxs-lookup"><span data-stu-id="bbe9b-102">Domain accounts required for SharePoint farm (Upgrade Advisor)</span></span>
  <span data-ttu-id="bbe9b-103">为场环境配置的 SharePoint 产品要求您使用域帐户。</span><span class="sxs-lookup"><span data-stu-id="bbe9b-103">SharePoint products that are configured for a farm environment require that you use domain accounts.</span></span>  
  
||  
|-|  
|<span data-ttu-id="bbe9b-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]SharePoint 模式。</span><span class="sxs-lookup"><span data-stu-id="bbe9b-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="bbe9b-105">组件</span><span class="sxs-lookup"><span data-stu-id="bbe9b-105">Component</span></span>  
 [!INCLUDE[ssRS](../../includes/ssrs.md)]  
  
### <a name="description"></a><span data-ttu-id="bbe9b-106">说明</span><span class="sxs-lookup"><span data-stu-id="bbe9b-106">Description</span></span>  
 <span data-ttu-id="bbe9b-107">为场环境配置的 SharePoint 产品要求您使用域帐户来连接服务和数据库。</span><span class="sxs-lookup"><span data-stu-id="bbe9b-107">SharePoint products that are configured for a farm environment require that you use domain accounts for services and database connections.</span></span> <span data-ttu-id="bbe9b-108">这包括您为 Reporting Services 服务帐户指定的帐户。</span><span class="sxs-lookup"><span data-stu-id="bbe9b-108">This includes the account you have specified for the Reporting Services service account.</span></span>  
  
 <span data-ttu-id="bbe9b-109">如果您没有对 Reporting Services 使用域用户帐户，SharePoint 2010 管理中心页及其他位置将会出现问题。</span><span class="sxs-lookup"><span data-stu-id="bbe9b-109">SharePoint 2010 Central Administration pages are one place you will see problems if you are not using a domain user account for Reporting Services.</span></span> <span data-ttu-id="bbe9b-110">当您尝试配置 Reporting Services 集成时，将会看到类似以下内容的错误消息：</span><span class="sxs-lookup"><span data-stu-id="bbe9b-110">When you try to configure Reporting Services integration, you will see an error message similar to the following:</span></span>  
  
 <span data-ttu-id="bbe9b-111">“报表服务器正在内置 NT AUTHORITY\NETWORK SERVICE 帐户下运行，而 SharePoint 场安装不支持它。</span><span class="sxs-lookup"><span data-stu-id="bbe9b-111">"The report server is running under the built-in NT AUTHORITY\NETWORK SERVICE account, which is not supported by a SharePoint farm installation.</span></span> <span data-ttu-id="bbe9b-112">请将 Report Server 重新配置为在域帐户下运行。 "</span><span class="sxs-lookup"><span data-stu-id="bbe9b-112">Please reconfigure the report server to run under a domain account."</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="bbe9b-113">纠正措施</span><span class="sxs-lookup"><span data-stu-id="bbe9b-113">Corrective Action</span></span>  
 <span data-ttu-id="bbe9b-114">对于 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 和以前的版本，请使用 Reporting Services 配置管理器更改分配为 Report Server 服务帐户的帐户。</span><span class="sxs-lookup"><span data-stu-id="bbe9b-114">For [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] and previous versions, use the Reporting Services Configuration Manager to change the account that is assigned as the report server service account.</span></span>  
  
#### <a name="to-change-the-service-account-from-configuration-manager"></a><span data-ttu-id="bbe9b-115">从配置管理器中更改服务帐户</span><span class="sxs-lookup"><span data-stu-id="bbe9b-115">To change the service account from Configuration Manager</span></span>  
  
1.  <span data-ttu-id="bbe9b-116">从 "**开始**" 菜单中，选择 "**所有程序**"，然后单击 " **Microsoft SQL Server 2008 R2**"。</span><span class="sxs-lookup"><span data-stu-id="bbe9b-116">From the **Start** menu, select **All Programs**, and then click **Microsoft SQL Server 2008 R2**.</span></span>  
  
2.  <span data-ttu-id="bbe9b-117">选择 "**配置工具**"，然后单击 " **Reporting Services 配置管理器**"。</span><span class="sxs-lookup"><span data-stu-id="bbe9b-117">Select **Configuration Tools**, and then click **Reporting Services Configuration Manager**.</span></span>  
  
3.  <span data-ttu-id="bbe9b-118">在 Configuration Manager 中，选择 "**服务帐户**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="bbe9b-118">In Configuration Manager, select the **Service Account** tab.</span></span>  
  
4.  <span data-ttu-id="bbe9b-119">选择 "**使用其他帐户**"，然后输入域帐户的凭据。</span><span class="sxs-lookup"><span data-stu-id="bbe9b-119">Select **Use another account** and enter the credentials for a domain account.</span></span>  
  
5.  <span data-ttu-id="bbe9b-120">单击“应用”。</span><span class="sxs-lookup"><span data-stu-id="bbe9b-120">Click **Apply**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbe9b-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bbe9b-121">See Also</span></span>  
 [<span data-ttu-id="bbe9b-122">配置报表服务器服务帐户（SSRS 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="bbe9b-122">Configure the Report Server Service Account &#40;SSRS Configuration Manager&#41;</span></span>](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)  
  
  
