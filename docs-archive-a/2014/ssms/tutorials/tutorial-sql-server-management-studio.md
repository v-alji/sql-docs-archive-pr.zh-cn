---
title: 教程：SQL Server Management Studio | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.tutorialstart.ssms.f1
helpviewer_keywords:
- projects [SQL Server Management Studio], tutorials
- templates [SQL Server], SQL Server Management Studio
- source controls [SQL Server Management Studio], tutorials
- Help [SQL Server], SQL Server Management Studio
- tutorials [SQL Server Management Studio]
- Transact-SQL tutorials
- solutions [SQL Server Management Studio], tutorials
- SQL Server Management Studio [SQL Server], tutorials
- scripts [SQL Server], SQL Server Management Studio
ms.assetid: d2bade70-07cf-4d94-b5d2-88aecb538ed1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8206fea828d6169975dc1d026a22e18e682f71e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590510"
---
# <a name="tutorial-sql-server-management-studio"></a><span data-ttu-id="c5312-102">教程：SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c5312-102">Tutorial: SQL Server Management Studio</span></span>
  <span data-ttu-id="c5312-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 教程向您介绍用于管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 基础结构的集成环境。</span><span class="sxs-lookup"><span data-stu-id="c5312-103">The [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] tutorial introduces you to the integrated environment for managing your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] infrastructure.</span></span> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="c5312-104">提供用于配置、监视和管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的图形界面。</span><span class="sxs-lookup"><span data-stu-id="c5312-104">presents a graphical interface for configuring, monitoring, and administering instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c5312-105">此外，它还允许您部署、监视和升级应用程序使用的数据层组件，如数据库和数据仓库。</span><span class="sxs-lookup"><span data-stu-id="c5312-105">It also allows you to deploy, monitor, and upgrade the data-tier components used by your applications, such as databases and data warehouses.</span></span> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="c5312-106">还提供用于编辑和调试脚本的 [!INCLUDE[tsql](../../includes/tsql-md.md)]、MDX、DMX 和 XML 语言编辑器。</span><span class="sxs-lookup"><span data-stu-id="c5312-106">also provides [!INCLUDE[tsql](../../includes/tsql-md.md)], MDX, DMX, and XML language editors for editing and debugging scripts.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="c5312-107">学习内容</span><span class="sxs-lookup"><span data-stu-id="c5312-107">What You Will Learn</span></span>  
 <span data-ttu-id="c5312-108">本教程将帮助您理解 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中提供的信息以及如何利用这些功能。</span><span class="sxs-lookup"><span data-stu-id="c5312-108">This tutorial will help you understand the presentation of information in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and how to take advantage of the features.</span></span> <span data-ttu-id="c5312-109">请注意，本教程适用于除 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 外所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本随附的 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 的完整安装。</span><span class="sxs-lookup"><span data-stu-id="c5312-109">Note that this tutorial applies to the complete installation of [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] that is included with all editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] except [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span> <span data-ttu-id="c5312-110">针对 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 的基本安装和针对 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 随附的 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 安装的功能与本教程中所示的功能稍有不同。</span><span class="sxs-lookup"><span data-stu-id="c5312-110">Functionality for basic installations of [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and for [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] installations that ship with [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] is slightly different than what is presented in this tutorial.</span></span>  
  
 <span data-ttu-id="c5312-111">熟悉 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 的最好方式是进行实践演练。</span><span class="sxs-lookup"><span data-stu-id="c5312-111">The best way to get acquainted with [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] is through hands-on practice.</span></span> <span data-ttu-id="c5312-112">本教程将讲述如何管理 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 组件以及如何查找常用的功能。</span><span class="sxs-lookup"><span data-stu-id="c5312-112">This tutorial will teach you how to manage the components of [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and how to find the features that you use regularly.</span></span>  
  
 <span data-ttu-id="c5312-113">本教程分为三课：</span><span class="sxs-lookup"><span data-stu-id="c5312-113">This tutorial is divided into three lessons:</span></span>  
  
 [<span data-ttu-id="c5312-114">第 1 课：SQL Server Management Studio 中的基本导航</span><span class="sxs-lookup"><span data-stu-id="c5312-114">Lesson 1: Basic Navigation in SQL Server Management Studio</span></span>](lesson-1-basic-navigation-in-sql-server-management-studio.md)  
 <span data-ttu-id="c5312-115">在本课程中，您将学习如何使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]组件，如何重新配置环境布局以及如何还原默认布局。</span><span class="sxs-lookup"><span data-stu-id="c5312-115">In this lesson you will learn how to use the components of [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], how to reconfigure the environment layout, and how to restore the default layout.</span></span>  
  
 [<span data-ttu-id="c5312-116">第 2 课：编写 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c5312-116">Lesson 2: Writing Transact-SQL</span></span>](lesson-2-writing-transact-sql.md)  
 <span data-ttu-id="c5312-117">在本课程中，您将学习如何打开查询编辑器，如何管理代码以及如何使用查询编辑器的其他新功能。</span><span class="sxs-lookup"><span data-stu-id="c5312-117">In this lesson, you will learn how to open Query Editor, how to manage code, and how to use the other new features of Query Editor.</span></span>  
  
 [<span data-ttu-id="c5312-118">第 3 课：使用模板、解决方案和脚本项目</span><span class="sxs-lookup"><span data-stu-id="c5312-118">Lesson 3: Working with Templates, Solutions, and Script Projects</span></span>](lesson-3-working-with-templates-solutions-and-script-projects.md)  
 <span data-ttu-id="c5312-119">在本课程中，您将学习如何使用模板，以及如何将脚本组织为解决方案和项目。</span><span class="sxs-lookup"><span data-stu-id="c5312-119">In this lesson you will learn how to use templates, and organize scripts into solutions and projects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5312-120">要求</span><span class="sxs-lookup"><span data-stu-id="c5312-120">Requirements</span></span>  
 <span data-ttu-id="c5312-121">本教程面向不熟悉 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]、但熟悉数据库概念和 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语言的经验丰富的数据库管理员和数据库开发人员。</span><span class="sxs-lookup"><span data-stu-id="c5312-121">This tutorial is intended for experienced database administrators and database developers who are not familiar with [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], but who are who are familiar with database concepts and the [!INCLUDE[tsql](../../includes/tsql-md.md)] language.</span></span>  
  
 <span data-ttu-id="c5312-122">若要使用本教程，您的系统必须安装以下组件：</span><span class="sxs-lookup"><span data-stu-id="c5312-122">Your system must have the following installed to use this tutorial:</span></span>  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="c5312-123">或带有 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 示例数据库的更高版本。</span><span class="sxs-lookup"><span data-stu-id="c5312-123">or a later version with the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample databases.</span></span> <span data-ttu-id="c5312-124">为了增强安全性，默认情况下不会安装示例数据库。</span><span class="sxs-lookup"><span data-stu-id="c5312-124">To enhance security, the sample databases are not installed by default.</span></span> <span data-ttu-id="c5312-125">若要安装示例数据库，请参阅 [安装 SQL Server 示例和示例数据库](http://sqlserversamples.codeplex.com)。</span><span class="sxs-lookup"><span data-stu-id="c5312-125">To install the sample databases, see [Installing SQL Server Samples and Sample Databases](http://sqlserversamples.codeplex.com).</span></span>  
  
-   <span data-ttu-id="c5312-126">Internet Explorer 9.0 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="c5312-126">Internet Explorer 9.0 or later.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5312-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c5312-127">See Also</span></span>  
 [<span data-ttu-id="c5312-128">数据库引擎教程</span><span class="sxs-lookup"><span data-stu-id="c5312-128">Database Engine Tutorials</span></span>](../../relational-databases/database-engine-tutorials.md)  
  
  
