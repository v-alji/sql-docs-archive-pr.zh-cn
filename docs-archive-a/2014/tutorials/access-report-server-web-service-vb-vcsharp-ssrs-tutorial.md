---
title: " (SSRS 教程使用 Visual Basic 或 Visual c # 访问报表服务器 Web 服务) |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- walkthroughs [Reporting Services]
- Reporting Services, Web service
- Web service [Reporting Services], tutorials
ms.assetid: cf688163-4ac0-475b-b6dd-6f2f05b553c6
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 3dc2599b4fafe682d74089d637918e04db9ed219
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691416"
---
# <a name="accessing-the-report-server-web-service-using-visual-basic-or-visual-c-ssrs-tutorial"></a><span data-ttu-id="bb539-102">使用 Visual Basic 或 Visual C# 访问报表服务器 Web 服务（SSRS 教程）</span><span class="sxs-lookup"><span data-stu-id="bb539-102">Accessing the Report Server Web Service Using Visual Basic or Visual C# (SSRS Tutorial)</span></span>
  <span data-ttu-id="bb539-103">以下教程演示如何从使用或创建的应用程序访问报表服务器 Web 服务 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[csprcs](../includes/csprcs-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="bb539-103">The following tutorial shows you how to access the Report Server Web service from an application created with [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] or [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[csprcs](../includes/csprcs-md.md)].</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="bb539-104">学习内容</span><span class="sxs-lookup"><span data-stu-id="bb539-104">What You Will Learn</span></span>  
 <span data-ttu-id="bb539-105">在本教程的课程中，您将完成下列活动：</span><span class="sxs-lookup"><span data-stu-id="bb539-105">During the course of this tutorial, you will complete the following:</span></span>  
  
-   <span data-ttu-id="bb539-106">使用 " [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] 控制台应用程序" 项目模板创建客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="bb539-106">Create a client application using the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] Console Application project template.</span></span>  
  
-   <span data-ttu-id="bb539-107">添加报表服务器 Web 服务的 Web 引用。</span><span class="sxs-lookup"><span data-stu-id="bb539-107">Add a Web reference for the Report Server Web service.</span></span>  
  
-   <span data-ttu-id="bb539-108">编写访问 Web 服务的代码。</span><span class="sxs-lookup"><span data-stu-id="bb539-108">Write code to access the Web service.</span></span>  
  
-   <span data-ttu-id="bb539-109">以调试模式运行控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="bb539-109">Run the console application in debug mode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb539-110">要求</span><span class="sxs-lookup"><span data-stu-id="bb539-110">Requirements</span></span>  
 <span data-ttu-id="bb539-111">若要完成本教程，您必须满足下列要求：</span><span class="sxs-lookup"><span data-stu-id="bb539-111">To complete the tutorial, you must have the following:</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="bb539-112">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bb539-112">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="bb539-113">[!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]或类似 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]兼容的开发工具。</span><span class="sxs-lookup"><span data-stu-id="bb539-113">[!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] or a similar [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-compatible development tool.</span></span>  
  
-   <span data-ttu-id="bb539-114">具有足够的权限，能够访问报表服务器所在计算机中的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 报表服务器 Web 服务。</span><span class="sxs-lookup"><span data-stu-id="bb539-114">Sufficient permissions to be able to access the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Report Server Web service on the computer where your report server is located.</span></span>  
  
-   <span data-ttu-id="bb539-115">报表服务器上已安装了报表。</span><span class="sxs-lookup"><span data-stu-id="bb539-115">A report installed on your report server.</span></span> <span data-ttu-id="bb539-116">本教程使用示例报表 Company Sales。</span><span class="sxs-lookup"><span data-stu-id="bb539-116">This tutorial uses the sample report, Company Sales.</span></span> <span data-ttu-id="bb539-117">有关示例报表的详细信息，请参阅[SQL Server Reporting Services 产品示例](https://go.microsoft.com/fwlink/?LinkId=177889)。</span><span class="sxs-lookup"><span data-stu-id="bb539-117">For more information about sample reports, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bb539-118">安装过程中不会自动安装示例，但是您可以随时安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="bb539-118">The samples are not installed automatically during setup, but you can install them at any time.</span></span> <span data-ttu-id="bb539-119">有关示例的信息，请参阅[SQL Server 产品示例](https://go.microsoft.com/fwlink/?LinkId=182887)。</span><span class="sxs-lookup"><span data-stu-id="bb539-119">For information about samples, see [SQL Server Product Samples](https://go.microsoft.com/fwlink/?LinkId=182887).</span></span>  
  
 <span data-ttu-id="bb539-120">**完成本教程的估计时间：** 60 分钟</span><span class="sxs-lookup"><span data-stu-id="bb539-120">**Estimated time to complete the tutorial:** 60 minutes</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="bb539-121">任务</span><span class="sxs-lookup"><span data-stu-id="bb539-121">Tasks</span></span>  
 [<span data-ttu-id="bb539-122">第 1 课：创建 Web 服务客户端项目</span><span class="sxs-lookup"><span data-stu-id="bb539-122">Lesson 1: Creating the Web Service Client Project</span></span>](../../2014/tutorials/lesson-1-creating-the-web-service-client-project.md)  
  
 [<span data-ttu-id="bb539-123">第 2 课：添加 Web 引用</span><span class="sxs-lookup"><span data-stu-id="bb539-123">Lesson 2: Adding a Web Reference</span></span>](../../2014/tutorials/lesson-2-adding-a-web-reference.md)  
  
 [<span data-ttu-id="bb539-124">第 3 课：访问 Web 服务</span><span class="sxs-lookup"><span data-stu-id="bb539-124">Lesson 3: Accessing the Web Service</span></span>](../../2014/tutorials/lesson-3-accessing-the-web-service.md)  
  
 [<span data-ttu-id="bb539-125">第4课：运行应用程序 &#40;VB-VC&#35;&#41;</span><span class="sxs-lookup"><span data-stu-id="bb539-125">Lesson 4: Running the Application &#40;VB-VC&#35;&#41;</span></span>](../../2014/tutorials/lesson-4-running-the-application-vb-vcsharp.md)  
  
  
