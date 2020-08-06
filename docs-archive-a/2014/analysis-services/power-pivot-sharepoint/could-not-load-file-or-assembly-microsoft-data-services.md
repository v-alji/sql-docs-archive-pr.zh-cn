---
title: 未能加载文件或程序集 &#39;Microsoft.analysisservices.sharepoint.integration.dll&#39; |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 6e350b67-5e18-4b90-8fb7-a0109cbb27b7
author: minewiskan
ms.author: owend
ms.openlocfilehash: b7ba75bdbd8e25f98d11d822c22fa7881352ad88
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589284"
---
# <a name="could-not-load-file-or-assembly-39microsoftanalysisservicessharepointintegration39"></a><span data-ttu-id="7b4bd-102">未能加载文件或程序集 &#39;Microsoft.analysisservices.sharepoint.integration.dll&#39;</span><span class="sxs-lookup"><span data-stu-id="7b4bd-102">Could not load file or assembly &#39;Microsoft.AnalysisServices.SharePoint.Integration&#39;</span></span>
  <span data-ttu-id="7b4bd-103">在具有 PowerPivot for SharePoint 的 SharePoint 2010 环境中，如果用于 PowerPivot 的应用程序级别的解决方案未正确部署，将发生此错误。</span><span class="sxs-lookup"><span data-stu-id="7b4bd-103">In SharePoint 2010 environments that have PowerPivot for SharePoint, this error will occur if the application-level solution for PowerPivot did not deploy correctly.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7b4bd-104">详细信息</span><span class="sxs-lookup"><span data-stu-id="7b4bd-104">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7b4bd-105">适用于</span><span class="sxs-lookup"><span data-stu-id="7b4bd-105">Applies to</span></span>|<span data-ttu-id="7b4bd-106">PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="7b4bd-106">PowerPivot for SharePoint</span></span>|  
|<span data-ttu-id="7b4bd-107">产品版本</span><span class="sxs-lookup"><span data-stu-id="7b4bd-107">Product Version</span></span>|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<span data-ttu-id="7b4bd-108">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b4bd-108">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|<span data-ttu-id="7b4bd-109">原因</span><span class="sxs-lookup"><span data-stu-id="7b4bd-109">Cause</span></span>|<span data-ttu-id="7b4bd-110">Powerpivotwebapp 解决方案未部署或者未正确部署。</span><span class="sxs-lookup"><span data-stu-id="7b4bd-110">Powerpivotwebapp solution is not deployed or did not deploy correctly.</span></span>|  
|<span data-ttu-id="7b4bd-111">消息正文</span><span class="sxs-lookup"><span data-stu-id="7b4bd-111">Message Text</span></span>|<span data-ttu-id="7b4bd-112">无法加载文件或程序集“Microsoft.AnalysisServices.SharePoint.Integration”</span><span class="sxs-lookup"><span data-stu-id="7b4bd-112">Could not load file or assembly 'Microsoft.AnalysisServices.SharePoint.Integration'</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7b4bd-113">说明</span><span class="sxs-lookup"><span data-stu-id="7b4bd-113">Explanation</span></span>  
 <span data-ttu-id="7b4bd-114">PowerPivot for SharePoint 使用解决方案包在 SharePoint 服务器上部署其功能。</span><span class="sxs-lookup"><span data-stu-id="7b4bd-114">PowerPivot for SharePoint uses solution packages to deploy its features on a SharePoint server.</span></span> <span data-ttu-id="7b4bd-115">解决方案之一未正确部署。</span><span class="sxs-lookup"><span data-stu-id="7b4bd-115">One of the solutions is not deployed correctly.</span></span> <span data-ttu-id="7b4bd-116">因此，只要您尝试在 SharePoint 站点上打开 PowerPivot 库或者其他 PowerPivot 应用程序页，就会出现此错误。</span><span class="sxs-lookup"><span data-stu-id="7b4bd-116">As a result, this error appears whenever you try to open PowerPivot Gallery or other PowerPivot application pages on a SharePoint site.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7b4bd-117">用户操作</span><span class="sxs-lookup"><span data-stu-id="7b4bd-117">User Action</span></span>  
 <span data-ttu-id="7b4bd-118">部署解决方案包。</span><span class="sxs-lookup"><span data-stu-id="7b4bd-118">Deploy the solution package.</span></span>  
  
1.  <span data-ttu-id="7b4bd-119">在管理中心的“系统设置”中，单击 **“管理场解决方案”**。</span><span class="sxs-lookup"><span data-stu-id="7b4bd-119">In Central Administration, in System Settings, click **Manage farm solutions**.</span></span>  
  
2.  <span data-ttu-id="7b4bd-120">单击 **“Powerpivotwebapp”**。</span><span class="sxs-lookup"><span data-stu-id="7b4bd-120">Click **Powerpivotwebapp**.</span></span>  
  
3.  <span data-ttu-id="7b4bd-121">单击 **“部署解决方案”**。</span><span class="sxs-lookup"><span data-stu-id="7b4bd-121">Click **Deploy Solution**.</span></span>  
  
4.  <span data-ttu-id="7b4bd-122">选择发生了此错误的 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="7b4bd-122">Choose the web application for which this error is occurring.</span></span> <span data-ttu-id="7b4bd-123">如果存在多个 Web 应用程序，则为所有这些应用程序都重新部署解决方案。</span><span class="sxs-lookup"><span data-stu-id="7b4bd-123">If there is more than one web application, redeploy the solution for all of hem.</span></span>  
  
5.  <span data-ttu-id="7b4bd-124">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="7b4bd-124">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b4bd-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7b4bd-125">See Also</span></span>  
 [<span data-ttu-id="7b4bd-126">将 PowerPivot 解决方案部署到 SharePoint</span><span class="sxs-lookup"><span data-stu-id="7b4bd-126">Deploy PowerPivot Solutions to SharePoint</span></span>](deploy-power-pivot-solutions-to-sharepoint.md)  
  
  
