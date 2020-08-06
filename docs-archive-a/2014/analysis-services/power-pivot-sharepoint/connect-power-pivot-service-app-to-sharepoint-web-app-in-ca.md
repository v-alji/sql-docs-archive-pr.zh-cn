---
title: 将 PowerPivot 服务应用程序连接到管理中心中的 SharePoint Web 应用程序 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a5da8e29-7ffd-44e7-bf61-344fa5bea8ce
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5fc6dcde4cc2d18c3650adbab0ec71ef5c6265cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589285"
---
# <a name="connect-a-powerpivot-service-application-to-a-sharepoint-web-application-in-central-administration"></a><span data-ttu-id="fc8aa-102">将 PowerPivot 服务应用程序连接到管理中心中的 SharePoint Web 应用程序</span><span class="sxs-lookup"><span data-stu-id="fc8aa-102">Connect a PowerPivot Service Application to a SharePoint Web Application in Central Administration</span></span>
  <span data-ttu-id="fc8aa-103">PowerPivot 服务应用程序可由场中任意数目的 SharePoint Web 应用程序使用。</span><span class="sxs-lookup"><span data-stu-id="fc8aa-103">A PowerPivot service application can be used by any number of SharePoint Web applications in the farm.</span></span> <span data-ttu-id="fc8aa-104">若要使 PowerPivot 服务应用程序可用，请将其添加到服务关联列表中。</span><span class="sxs-lookup"><span data-stu-id="fc8aa-104">To make a PowerPivot service application available, you add it to a service association list.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="fc8aa-105">默认组中必须有一个 PowerPivot 服务应用程序，以确保 PowerPivot 管理面板正确工作。</span><span class="sxs-lookup"><span data-stu-id="fc8aa-105">You must have one PowerPivot service application in the default group to ensure that PowerPivot Management Dashboard works properly.</span></span> <span data-ttu-id="fc8aa-106">不要向默认组添加多个 PowerPivot 服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="fc8aa-106">Do not add more than one PowerPivot service application to the default group.</span></span> <span data-ttu-id="fc8aa-107">添加同一服务应用程序类型的多个条目是不支持的配置并且可能导致错误。</span><span class="sxs-lookup"><span data-stu-id="fc8aa-107">Adding multiple entries of the same service application type is not a supported configuration and might cause errors.</span></span> <span data-ttu-id="fc8aa-108">如果您要创建其他服务应用程序，请将它们添加到自定义列表。</span><span class="sxs-lookup"><span data-stu-id="fc8aa-108">If you are creating additional service applications, add them to custom lists.</span></span>  
  
 <span data-ttu-id="fc8aa-109">本主题包含以下各节：</span><span class="sxs-lookup"><span data-stu-id="fc8aa-109">This topic contains the following sections:</span></span>  
  
 [<span data-ttu-id="fc8aa-110">将 PowerPivot 服务应用程序添加到默认组</span><span class="sxs-lookup"><span data-stu-id="fc8aa-110">Add PowerPivot Services Application to the Default Group</span></span>](#default)  
  
 [<span data-ttu-id="fc8aa-111">将 PowerPivot 服务应用程序添加到自定义服务关联列表</span><span class="sxs-lookup"><span data-stu-id="fc8aa-111">Add PowerPivot Services Application a Custom Service Association List</span></span>](#custom)  
  
##  <a name="add-powerpivot-services-application-to-the-default-group"></a><a name="default"></a><span data-ttu-id="fc8aa-112">将 PowerPivot 服务应用程序添加到默认组</span><span class="sxs-lookup"><span data-stu-id="fc8aa-112">Add PowerPivot Services Application to the Default Group</span></span>  
 <span data-ttu-id="fc8aa-113">服务关联列表是向场中的其他 SharePoint Web 应用程序提供资源的共享服务的列表。</span><span class="sxs-lookup"><span data-stu-id="fc8aa-113">A service association list is a list of shared services that provide resources to other SharePoint Web applications in the farm.</span></span> <span data-ttu-id="fc8aa-114">场有一个默认的服务关联组。</span><span class="sxs-lookup"><span data-stu-id="fc8aa-114">There is one default group of service associations for the farm.</span></span>  
  
 <span data-ttu-id="fc8aa-115">若要将 PowerPivot 服务应用程序添加到该列表中，您既可以在创建应用程序时添加，也可以在之后采用以下步骤添加。</span><span class="sxs-lookup"><span data-stu-id="fc8aa-115">To be on the list, a PowerPivot service application can either be added when you create the application or afterwards by using the following steps.</span></span>  
  
1.  <span data-ttu-id="fc8aa-116">在“管理中心”的 **“应用程序管理”** 中，单击 **“配置服务应用程序关联”**。</span><span class="sxs-lookup"><span data-stu-id="fc8aa-116">In Central Administration, in **Application Management**, click **Configure service application associations**.</span></span>  
  
2.  <span data-ttu-id="fc8aa-117">在“应用程序代理组”中，单击 **“默认值”**。</span><span class="sxs-lookup"><span data-stu-id="fc8aa-117">In Application Proxy Group, click **default**.</span></span>  
  
3.  <span data-ttu-id="fc8aa-118">选中 PowerPivot 服务应用程序旁边的复选框（由类型名称 `PowerPivot Service Application Proxy` 指示）。</span><span class="sxs-lookup"><span data-stu-id="fc8aa-118">Select the checkbox next to the PowerPivot service application (indicated by type name `PowerPivot Service Application Proxy`).</span></span> <span data-ttu-id="fc8aa-119">如果有多个 PowerPivot 服务应用程序，请只选择一个。</span><span class="sxs-lookup"><span data-stu-id="fc8aa-119">If you have more than one PowerPivot service application, choose just one.</span></span>  
  
4.  <span data-ttu-id="fc8aa-120">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="fc8aa-120">Click **OK**.</span></span>  
  
##  <a name="add-powerpivot-services-application-a-custom-service-association-list"></a><a name="custom"></a><span data-ttu-id="fc8aa-121">添加 PowerPivot 服务应用程序自定义服务关联列表</span><span class="sxs-lookup"><span data-stu-id="fc8aa-121">Add PowerPivot Services Application a Custom Service Association List</span></span>  
 <span data-ttu-id="fc8aa-122">默认组可由自定义列表替换。</span><span class="sxs-lookup"><span data-stu-id="fc8aa-122">The default group can be replaced by a custom list.</span></span> <span data-ttu-id="fc8aa-123">自定义列表是专门为单个 SharePoint Web 应用程序创建的。</span><span class="sxs-lookup"><span data-stu-id="fc8aa-123">A custom list is created specifically for a single SharePoint Web application.</span></span> <span data-ttu-id="fc8aa-124">它覆盖默认组，并且仅使用场管理员或服务管理员指定的服务关联来替换它。</span><span class="sxs-lookup"><span data-stu-id="fc8aa-124">It overrides the default group and replaces it with only those service associations that a farm or service administrator specifies.</span></span> <span data-ttu-id="fc8aa-125">如果您创建了多个 PowerPivot 服务应用程序，则必须使用自定义列表指定要使用的应用程序。</span><span class="sxs-lookup"><span data-stu-id="fc8aa-125">If you created multiple PowerPivot service applications, you must use a custom list to specify which one to use.</span></span> <span data-ttu-id="fc8aa-126">自定义列表不能由其他 Web 应用程序重用。</span><span class="sxs-lookup"><span data-stu-id="fc8aa-126">A custom list cannot be reused by other Web applications.</span></span> <span data-ttu-id="fc8aa-127">它仅适用于为其创建的 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="fc8aa-127">It applies only to the Web application for which it was created.</span></span>  
  
1.  <span data-ttu-id="fc8aa-128">在“管理中心”的 **“应用程序管理”** 中，单击 **“管理 Web 应用程序”**。</span><span class="sxs-lookup"><span data-stu-id="fc8aa-128">In Central Administration, in **Application Management**, click **Manage web applications**.</span></span>  
  
2.  <span data-ttu-id="fc8aa-129">选择应用程序（例如 SharePoint -80）。</span><span class="sxs-lookup"><span data-stu-id="fc8aa-129">Select the application (for example, SharePoint -80).</span></span>  
  
3.  <span data-ttu-id="fc8aa-130">在“Web 应用程序”的“管理”中，单击 **“服务连接”**。</span><span class="sxs-lookup"><span data-stu-id="fc8aa-130">In Web Applications, in Manage, click **Service Connections**.</span></span>  
  
4.  <span data-ttu-id="fc8aa-131">在“编辑以下连接组”\*\*\*\* 中，选择“[custom]”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fc8aa-131">In **Edit the following group of connections**, select **[custom]**.</span></span>  
  
5.  <span data-ttu-id="fc8aa-132">选中您要使用的每个服务应用程序连接旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="fc8aa-132">Select the checkbox next to each service application connection you want to use.</span></span> <span data-ttu-id="fc8aa-133">如果您有多个 PowerPivot 服务应用程序（由设置为 `PowerPivot Service Application Proxy` 的类型指示），请确保仅选择一个。</span><span class="sxs-lookup"><span data-stu-id="fc8aa-133">If you have multiple PowerPivot service applications (indicated by Type set to `PowerPivot Service Application Proxy`), be sure to choose only one.</span></span>  
  
6.  <span data-ttu-id="fc8aa-134">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="fc8aa-134">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc8aa-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fc8aa-135">See Also</span></span>  
 <span data-ttu-id="fc8aa-136">[在管理中心中创建和配置 PowerPivot 服务应用程序](create-and-configure-power-pivot-service-application-in-ca.md) </span><span class="sxs-lookup"><span data-stu-id="fc8aa-136">[Create and Configure a PowerPivot Service Application in Central Administration](create-and-configure-power-pivot-service-application-in-ca.md) </span></span>  
 [<span data-ttu-id="fc8aa-137">初始配置 &#40;PowerPivot for SharePoint&#41;</span><span class="sxs-lookup"><span data-stu-id="fc8aa-137">Initial Configuration &#40;PowerPivot for SharePoint&#41;</span></span>](../../sql-server/install/initial-configuration-powerpivot-for-sharepoint.md)  
  
  
