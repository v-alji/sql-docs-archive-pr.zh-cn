---
title: 使用从 RDL 架构生成的类更新报表 (SSRS 教程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- RDL [Reporting Services], generating
- RDL [Reporting Services], tutorials
- RDL [Reporting Services], serializing
ms.assetid: 8f81d48f-7ab9-4ef8-bce0-7d16d9a47fbd
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: f3972b8e1af6d50ccc6f5188c8f671fe333ebce8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578557"
---
# <a name="updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial"></a><span data-ttu-id="26deb-102">使用从 RDL 架构生成的类更新报表（SSRS 教程）</span><span class="sxs-lookup"><span data-stu-id="26deb-102">Updating Reports Using Classes Generated from the RDL Schema (SSRS Tutorial)</span></span>
  <span data-ttu-id="26deb-103">本教程演示了如何使用 XML 架构定义工具 ( # A0) 来生成类，这些类可用于将报表定义文件 ( .rdl 和 .rdlc) 与类进行序列化和反序列化 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] <xref:System.Xml.Serialization.XmlSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="26deb-103">This tutorial illustrates how to use the XML Schema Definition Tool (Xsd.exe) to generate classes that allow you to serialize and deserialize report definition files (.rdl and .rdlc) with the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="26deb-104">学习内容</span><span class="sxs-lookup"><span data-stu-id="26deb-104">What You Will Learn</span></span>  
 <span data-ttu-id="26deb-105">在本教程的课程中，您将完成下列活动：</span><span class="sxs-lookup"><span data-stu-id="26deb-105">During the course of this tutorial, you will complete the following activities:</span></span>  
  
-   <span data-ttu-id="26deb-106">使用 " [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 控制台应用程序" 项目模板创建应用程序。</span><span class="sxs-lookup"><span data-stu-id="26deb-106">Create an application using the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Console Application project template.</span></span>  
  
-   <span data-ttu-id="26deb-107">使用**xsd**工具从报表定义语言 (RDL) 架构生成类。</span><span class="sxs-lookup"><span data-stu-id="26deb-107">Generate classes from the Report Definition Language (RDL) schema using the **xsd** tool.</span></span>  
  
-   <span data-ttu-id="26deb-108">连接到报表服务器并检索报表定义。</span><span class="sxs-lookup"><span data-stu-id="26deb-108">Connect to a report server and retrieve a report definition.</span></span>  
  
-   <span data-ttu-id="26deb-109">编写用于更新报表定义文件的代码。</span><span class="sxs-lookup"><span data-stu-id="26deb-109">Write code to update the report definition file.</span></span>  
  
-   <span data-ttu-id="26deb-110">将更新的报表定义保存回报表服务器。</span><span class="sxs-lookup"><span data-stu-id="26deb-110">Save the updated report definition back to the report server.</span></span>  
  
-   <span data-ttu-id="26deb-111">运行 RDL 架构应用程序 (VB/C#)。</span><span class="sxs-lookup"><span data-stu-id="26deb-111">Run the RDL Schema Application (VB/C#).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="26deb-112">对于没有说明的报表，在本教程中提供的代码示例可能会失败。</span><span class="sxs-lookup"><span data-stu-id="26deb-112">The code samples provided in this tutorial might fail for reports having no description.</span></span> <span data-ttu-id="26deb-113">失败的原因在于：说明属性对于未指定说明的报表不存在。</span><span class="sxs-lookup"><span data-stu-id="26deb-113">The failure is because the description property does not exist for the reports with description not specified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26deb-114">要求</span><span class="sxs-lookup"><span data-stu-id="26deb-114">Requirements</span></span>  
 <span data-ttu-id="26deb-115">若要完成本教程，您必须满足下列要求：</span><span class="sxs-lookup"><span data-stu-id="26deb-115">To complete the tutorial, you must have the following:</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="26deb-116">[!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="26deb-116">[!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="26deb-117">[!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="26deb-117">[!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].</span></span>  
  
-   <span data-ttu-id="26deb-118">拥有足够的权限，能够访问报表服务器所在计算机中的报表服务器 Web 服务并向该服务发布报表。</span><span class="sxs-lookup"><span data-stu-id="26deb-118">Sufficient permissions to be able to access and publish reports to the Report Server Web service on the computer where your report server is located.</span></span>  
  
-   <span data-ttu-id="26deb-119">已将 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 示例数据库安装到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的实例中。</span><span class="sxs-lookup"><span data-stu-id="26deb-119">The [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] sample database installed to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="26deb-120">报表服务器上已安装了报表。</span><span class="sxs-lookup"><span data-stu-id="26deb-120">A report installed on your report server.</span></span> <span data-ttu-id="26deb-121">本教程使用示例报表 Company Sales 2012。</span><span class="sxs-lookup"><span data-stu-id="26deb-121">This tutorial uses the sample report, Company Sales 2012.</span></span> <span data-ttu-id="26deb-122">有关示例报表的详细信息，请参阅[SQL Server Reporting Services 产品示例](https://go.microsoft.com/fwlink/?LinkId=177889)。</span><span class="sxs-lookup"><span data-stu-id="26deb-122">For more information about sample reports, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="26deb-123">安装过程中不会自动安装示例，但是您可以随时安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="26deb-123">The samples are not installed automatically during setup, but you can install them at any time.</span></span> <span data-ttu-id="26deb-124">有关示例的信息，请参阅[SQL Server 产品示例](https://go.microsoft.com/fwlink/?LinkId=182887)。</span><span class="sxs-lookup"><span data-stu-id="26deb-124">For information about samples, see [SQL Server Product Samples](https://go.microsoft.com/fwlink/?LinkId=182887).</span></span>  
  
 <span data-ttu-id="26deb-125">**完成本教程的估计时间：** 30 分钟</span><span class="sxs-lookup"><span data-stu-id="26deb-125">**Estimated time to complete the tutorial:** 30 minutes</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="26deb-126">任务</span><span class="sxs-lookup"><span data-stu-id="26deb-126">Tasks</span></span>  
 [<span data-ttu-id="26deb-127">第 1 课：创建 RDL 架构 Visual Studio 项目</span><span class="sxs-lookup"><span data-stu-id="26deb-127">Lesson 1: Create the RDL Schema Visual Studio Project</span></span>](../../2014/tutorials/lesson-1-create-the-rdl-schema-visual-studio-project.md)  
  
 [<span data-ttu-id="26deb-128">第 2 课：使用 XSD 工具从 RDL 架构生成类</span><span class="sxs-lookup"><span data-stu-id="26deb-128">Lesson 2: Generate Classes from the RDL Schema using the xsd Tool</span></span>](../../2014/tutorials/lesson-2-generate-classes-from-the-rdl-schema-using-the-xsd-tool.md)  
  
 [<span data-ttu-id="26deb-129">第 3 课：从报表服务器加载报表定义</span><span class="sxs-lookup"><span data-stu-id="26deb-129">Lesson 3: Load a Report Definition from the Report Server</span></span>](../../2014/tutorials/lesson-3-load-a-report-definition-from-the-report-server.md)  
  
 [<span data-ttu-id="26deb-130">第 4 课：以编程方式更新报表定义</span><span class="sxs-lookup"><span data-stu-id="26deb-130">Lesson 4: Update the Report Definition Programmatically</span></span>](../../2014/tutorials/lesson-4-update-the-report-definition-programmatically.md)  
  
 [<span data-ttu-id="26deb-131">第 5 课：将报表定义发布到报表服务器</span><span class="sxs-lookup"><span data-stu-id="26deb-131">Lesson 5: Publish the Report Definition to the Report Server</span></span>](../../2014/tutorials/lesson-5-publish-the-report-definition-to-the-report-server.md)  
  
 [<span data-ttu-id="26deb-132">第6课：运行 RDL 架构应用程序 &#40;VB-C&#35;&#41;</span><span class="sxs-lookup"><span data-stu-id="26deb-132">Lesson 6: Run the RDL Schema Application &#40;VB-C&#35;&#41;</span></span>](../../2014/tutorials/lesson-6-run-the-rdl-schema-application-vb-csharp.md)  
  
## <a name="see-also"></a><span data-ttu-id="26deb-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="26deb-133">See Also</span></span>  
 [<span data-ttu-id="26deb-134">报表定义语言 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="26deb-134">Report Definition Language &#40;SSRS&#41;</span></span>](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
