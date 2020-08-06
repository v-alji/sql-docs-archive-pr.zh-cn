---
title: 向用户和警报管理员授予权限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 166808e1-ada7-48d2-bda8-8f7c017fb3aa
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5bf7f030871287379ce9fb32a1789b95cff0fc0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590580"
---
# <a name="grant-permissions-to-users-and-alerting-administrators"></a><span data-ttu-id="d819e-102">向用户和警报管理员授予权限</span><span class="sxs-lookup"><span data-stu-id="d819e-102">Grant Permissions to Users and Alerting Administrators</span></span>
  <span data-ttu-id="d819e-103">用户和警报管理员必须首先被授予 SharePoint 权限，然后才能创建、编辑、删除和查看数据警报。</span><span class="sxs-lookup"><span data-stu-id="d819e-103">Before users and alerting administrators can create, edit, delete, and view data alerts they must be granted SharePoint permissions.</span></span> <span data-ttu-id="d819e-104">没有用于使用 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 数据警报功能的特殊权限，你将使用内置的 SharePoint 权限。</span><span class="sxs-lookup"><span data-stu-id="d819e-104">There are no special permissions to use with the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] data alerting feature, you use the built-in SharePoint permissions.</span></span>  
  
 <span data-ttu-id="d819e-105">**信息工作者** - 权限必须包括“创建警报”和“查看项”等 SharePoint 权限。</span><span class="sxs-lookup"><span data-stu-id="d819e-105">**Information workers**-Permissions must include the Create Alert and View Items SharePoint permissions.</span></span> <span data-ttu-id="d819e-106">名为“设计”、“参与讨论”、“读取”和“仅查看”的内置 SharePoint 权限级别包括“创建警报”和“查看项”SharePoint 权限。</span><span class="sxs-lookup"><span data-stu-id="d819e-106">The built-in SharePoint permission levels named Design, Contribute, Read, and View Only include the Create Alert and View Items SharePoint permissions.</span></span> <span data-ttu-id="d819e-107">您还可以创建自定义权限级别，该级别具有支持创建、编辑、运行和查看数据警报的用户所需的权限。</span><span class="sxs-lookup"><span data-stu-id="d819e-107">You can also create a custom permission level with the permissions required to support users that create, edit, run, and view data alerts.</span></span>  
  
 <span data-ttu-id="d819e-108">**警报管理员** - 权限必须包括“管理警报”SharePoint 权限。</span><span class="sxs-lookup"><span data-stu-id="d819e-108">**Alerting administrators**-Permissions must include the Manage Alert SharePoint permission.</span></span> <span data-ttu-id="d819e-109">默认情况下，对于使用“工作组网站”站点模板创建的站点，只有“完全控制”权限级别包括此权限。</span><span class="sxs-lookup"><span data-stu-id="d819e-109">By default only the Full Control permission level includes this permission for sites created with the Team Site site template.</span></span> <span data-ttu-id="d819e-110">如果您使用其他站点模板，您将看到不同的默认 SharePoint 组列表。</span><span class="sxs-lookup"><span data-stu-id="d819e-110">If you use other site templates, you will see different lists of default SharePoint groups.</span></span> <span data-ttu-id="d819e-111">您可以将“管理警报”权限添加到内置权限级别之一，或者创建具有支持查看和删除数据警报的警报管理员所需权限的自定义权限级别。</span><span class="sxs-lookup"><span data-stu-id="d819e-111">You can add the Manage Alert permission to one of the built-in permission levels or create a custom permission level with the permission required to support alerting administrators that view and delete data alerts.</span></span>  
  
 <span data-ttu-id="d819e-112">若要了解有关 SharePoint 权限的详细信息，请参阅 [用户权限和权限级别 (SharePoint Server 2010)](https://technet.microsoft.com/library/cc721640.aspx)。</span><span class="sxs-lookup"><span data-stu-id="d819e-112">To learn more about SharePoint permissions, see [User permissions and permission levels (SharePoint Server 2010)](https://technet.microsoft.com/library/cc721640.aspx).</span></span>  
  
### <a name="to-grant-permissions"></a><span data-ttu-id="d819e-113">授予权限</span><span class="sxs-lookup"><span data-stu-id="d819e-113">To grant permissions</span></span>  
  
1.  <span data-ttu-id="d819e-114">转到要授予权限的 SharePoint 站点。</span><span class="sxs-lookup"><span data-stu-id="d819e-114">Go to the SharePoint site to which you want to grant permissions.</span></span>  
  
2.  <span data-ttu-id="d819e-115">在工具栏上，单击 **“网站操作”** ，然后单击 **“网站权限”**。</span><span class="sxs-lookup"><span data-stu-id="d819e-115">On the toolbar, click **Site Actions** and then click **Site Permissions**.</span></span>  
  
     <span data-ttu-id="d819e-116">如果未看到此选项，则表明您没有向他人授予权限所需的足够权限。</span><span class="sxs-lookup"><span data-stu-id="d819e-116">If you do not see this option, you do not sufficient permission to grant permissions to others.</span></span>  
  
3.  <span data-ttu-id="d819e-117">单击“授予权限”  。</span><span class="sxs-lookup"><span data-stu-id="d819e-117">Click **Grant Permissions**.</span></span>  
  
4.  <span data-ttu-id="d819e-118">在“用户/组”中，键入要授予权限的用户名、组名或电子邮件地址\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d819e-118">In **Users/Groups**, type the user names, group names, or e-mail addresses you want grant permission to.</span></span>  
  
5.  <span data-ttu-id="d819e-119">选择 **“向 SharePoint 组添加用户”** 或 **“直接授予用户权限”** 选项。</span><span class="sxs-lookup"><span data-stu-id="d819e-119">Select the **Add users to a SharePoint group** or **Grant users permission directly** option.</span></span> <span data-ttu-id="d819e-120">根据您是选择 **“向 SharePoint 组添加用户”** 还是选择 **“直接授予用户权限”** ，执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="d819e-120">Depending on whether you selected **Add users to a SharePoint group** or **Grant users permissions directly** do one of the following:</span></span>  
  
    -   <span data-ttu-id="d819e-121">如果选择了“向 SharePoint 组添加用户”，则在下拉列表中选择某一权限级别\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d819e-121">If you selected **Add users to a SharePoint group**, select a permission level in the drop-down list.</span></span>  
  
    -   <span data-ttu-id="d819e-122">如果您选择了 **“直接授予用户权限”**，则选择某一权限级别。</span><span class="sxs-lookup"><span data-stu-id="d819e-122">If you selected **Grant users permissions directly**, select a permission level.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d819e-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d819e-123">See Also</span></span>  
 <span data-ttu-id="d819e-124">[为 sharepoint 站点上的报表服务器项设置权限 &#40;Reporting Services 在 SharePoint 集成模式下&#41;](security/set-permissions-for-report-server-items-on-a-sharepoint-site.md) </span><span class="sxs-lookup"><span data-stu-id="d819e-124">[Set Permissions for Report Server Items on a SharePoint Site &#40;Reporting Services in SharePoint Integrated Mode&#41;](security/set-permissions-for-report-server-items-on-a-sharepoint-site.md) </span></span>  
 [<span data-ttu-id="d819e-125">Reporting Services 数据警报</span><span class="sxs-lookup"><span data-stu-id="d819e-125">Reporting Services Data Alerts</span></span>](../ssms/agent/alerts.md)  
  
  
