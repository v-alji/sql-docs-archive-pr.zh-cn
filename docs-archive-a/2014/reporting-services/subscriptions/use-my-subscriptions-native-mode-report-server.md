---
title: 使用我的订阅 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], My Subscriptions page
- My Subscriptions page [Reporting Services]
ms.assetid: e96623ba-677e-4748-8787-f32bed3b5c12
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f3378a65637ad04151cc517fd9047363af954c31
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692644"
---
# <a name="use-my-subscriptions"></a><span data-ttu-id="2efe6-102">使用我的订阅</span><span class="sxs-lookup"><span data-stu-id="2efe6-102">Use My Subscriptions</span></span>
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]<span data-ttu-id="2efe6-103">报表管理器包含 **"我的订阅"** 页，可将所有订阅组织到一个位置。</span><span class="sxs-lookup"><span data-stu-id="2efe6-103">Report Manager includes a **My Subscriptions** page that organizes all of your subscriptions into one place.</span></span> <span data-ttu-id="2efe6-104">您可以使用“我的订阅”来查看、修改和删除现有订阅。</span><span class="sxs-lookup"><span data-stu-id="2efe6-104">You can use My Subscriptions to view, modify, and delete existing subscriptions.</span></span> <span data-ttu-id="2efe6-105">不过，您不能使用该页来创建订阅。</span><span class="sxs-lookup"><span data-stu-id="2efe6-105">However, you cannot use it to create subscriptions.</span></span>  
  
||  
|-|  
|<span data-ttu-id="2efe6-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 本机模式</span><span class="sxs-lookup"><span data-stu-id="2efe6-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Native mode</span></span>|  
  
 <span data-ttu-id="2efe6-107">在“我的订阅”中，您可以按文件夹、报表、说明、触发器、上次运行时间或状态来对订阅进行排序。</span><span class="sxs-lookup"><span data-stu-id="2efe6-107">Within My Subscriptions, you can sort subscriptions by folder, report, description, trigger, last run, or status.</span></span> <span data-ttu-id="2efe6-108">除了“上次运行时间”是按时间顺序排序之外，其他所有值都是按字母顺序排序的。</span><span class="sxs-lookup"><span data-stu-id="2efe6-108">All values are sorted alphabetically except for Last Run, which is in chronological order.</span></span>  
  
 <span data-ttu-id="2efe6-109">“我的订阅”仅显示您创建的订阅。</span><span class="sxs-lookup"><span data-stu-id="2efe6-109">My Subscriptions shows only the subscriptions that you create.</span></span> <span data-ttu-id="2efe6-110">它不会列出其他用户拥有的订阅（即使您已添加为这些订阅的订阅者），也不会显示数据驱动订阅。</span><span class="sxs-lookup"><span data-stu-id="2efe6-110">It does not list subscriptions that are owned by other users, even if you are added as a subscriber to those subscriptions, nor does it show data-driven subscriptions.</span></span>  
  
 <span data-ttu-id="2efe6-111">您既不能根据名称来搜索订阅，也不能根据触发器信息、状态信息等来搜索订阅。</span><span class="sxs-lookup"><span data-stu-id="2efe6-111">You cannot search for subscriptions by name, nor can you search for subscriptions based on trigger information, status information, and so forth.</span></span> <span data-ttu-id="2efe6-112">有关详细信息，请参阅[创建、修改和删除纯模式下的标准订阅 &#40;Reporting Services&#41;](create-and-manage-subscriptions-for-native-mode-report-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="2efe6-112">For more information, see [Create, Modify, and Delete Standard Subscriptions &#40;Reporting Services in Native Mode&#41;](create-and-manage-subscriptions-for-native-mode-report-servers.md).</span></span>  
  
## <a name="how-to-use-my-subscriptions"></a><span data-ttu-id="2efe6-113">如何使用“我的订阅”</span><span class="sxs-lookup"><span data-stu-id="2efe6-113">How to Use My Subscriptions</span></span>  
 <span data-ttu-id="2efe6-114">可以通过报表管理器使用“我的订阅”。</span><span class="sxs-lookup"><span data-stu-id="2efe6-114">My Subscriptions is available through Report Manager.</span></span> <span data-ttu-id="2efe6-115">若要访问“我的订阅”，请在报表管理器全局工具栏上单击 **“我的订阅”** 。</span><span class="sxs-lookup"><span data-stu-id="2efe6-115">To access My Subscriptions, click **My Subscriptions** on the Report Manager global toolbar.</span></span>  
  
## <a name="use-windows-powershell-to-list-mysubscriptions"></a><span data-ttu-id="2efe6-116">使用 Windows PowerShell 列出 MySubscription</span><span class="sxs-lookup"><span data-stu-id="2efe6-116">Use Windows PowerShell to list MySubscriptions</span></span>  
 <span data-ttu-id="2efe6-117">![PowerShell 相关内容](../media/rs-powershellicon.jpg "PowerShell 相关内容")</span><span class="sxs-lookup"><span data-stu-id="2efe6-117">![PowerShell related content](../media/rs-powershellicon.jpg "PowerShell related content")</span></span>  
  
 <span data-ttu-id="2efe6-118">以下 PowerShell 脚本将返回当前用户的订阅和订阅属性的列表。</span><span class="sxs-lookup"><span data-stu-id="2efe6-118">The following PowerShell script will return the list of subscriptions and subscription properties for the current user.</span></span> <span data-ttu-id="2efe6-119">有关详细信息，请参阅 [ReportingService2010.ListMySubscriptions 方法](https://technet.microsoft.com/library/reportservice2010.reportingservice2010.listmysubscriptions.aspx)。</span><span class="sxs-lookup"><span data-stu-id="2efe6-119">For more information, see [ReportingService2010.ListMySubscriptions Method](https://technet.microsoft.com/library/reportservice2010.reportingservice2010.listmysubscriptions.aspx).</span></span>  
  
```powershell
#server -  all subscriptions of the current user at the given server or site  
$server="[server name]/reportserver"  
$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;  
  
$subscriptions=ListMySubscriptions(ItemPathOrSiteURL)  
$subscriptions | select Path, report, Description, Owner, SubscriptionID, lastexecuted,Status  
#uncomment the following to list all the subscription properties  
#$subscriptions
```  
  
## <a name="see-also"></a><span data-ttu-id="2efe6-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2efe6-120">See Also</span></span>  
 <span data-ttu-id="2efe6-121">[Data-Driven Subscriptions](data-driven-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="2efe6-121">[Data-Driven Subscriptions](data-driven-subscriptions.md) </span></span>  
 <span data-ttu-id="2efe6-122">[订阅和传递 (Reporting Services)](subscriptions-and-delivery-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="2efe6-122">[Subscriptions and Delivery &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md) </span></span>  
 [<span data-ttu-id="2efe6-123">创建和管理本机模式报表服务器的订阅</span><span class="sxs-lookup"><span data-stu-id="2efe6-123">Create and Manage Subscriptions for Native Mode Report Servers</span></span>](../create-manage-subscriptions-native-mode-report-servers.md)  
