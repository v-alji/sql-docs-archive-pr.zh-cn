---
title: 第5课：添加包部署模型的包配置 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 1c10dd54-67cb-4b63-9e4d-aa6ff0452ecb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ee03d624ac7144cf6aef0829bcb7835fe5af9c53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688027"
---
# <a name="lesson-5-adding-package-configurations-for-the-package-deployment-model"></a><span data-ttu-id="df75f-102">第 5 课： 添加包部署模型的包配置</span><span class="sxs-lookup"><span data-stu-id="df75f-102">Lesson 5: Adding Package Configurations for the Package Deployment Model</span></span>
  <span data-ttu-id="df75f-103">包配置允许您从开发环境的外部设置运行时属性和变量。</span><span class="sxs-lookup"><span data-stu-id="df75f-103">Package configurations let you set run-time properties and variables from outside of the development environment.</span></span> <span data-ttu-id="df75f-104">配置允许您开发灵活且易于部署和分发的包。</span><span class="sxs-lookup"><span data-stu-id="df75f-104">Configurations allow you to develop packages that are flexible and easy to both deploy and distribute.</span></span> [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="df75f-105">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 提供了以下配置类型：</span><span class="sxs-lookup"><span data-stu-id="df75f-105">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] offers the following configuration types:</span></span>  
  
-   <span data-ttu-id="df75f-106">XML 配置文件</span><span class="sxs-lookup"><span data-stu-id="df75f-106">XML configuration file</span></span>  
  
-   <span data-ttu-id="df75f-107">环境变量</span><span class="sxs-lookup"><span data-stu-id="df75f-107">Environment variable</span></span>  
  
-   <span data-ttu-id="df75f-108">注册表项</span><span class="sxs-lookup"><span data-stu-id="df75f-108">Registry entry</span></span>  
  
-   <span data-ttu-id="df75f-109">父包变量</span><span class="sxs-lookup"><span data-stu-id="df75f-109">Parent package variable</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="df75f-110">表</span><span class="sxs-lookup"><span data-stu-id="df75f-110">table</span></span>  
  
 <span data-ttu-id="df75f-111">在本课中，将修改在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 中创建的简单 [ssISnoversion](lesson-4-add-error-flow-redirection-with-ssis.md) 包，以便使用包部署模型并利用包配置。</span><span class="sxs-lookup"><span data-stu-id="df75f-111">In this lesson, you will modify the simple [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package that you created in [Lesson 4: Adding Error Flow Redirection](lesson-4-add-error-flow-redirection-with-ssis.md) to use the Package Deployment Model and take advantage of package configurations.</span></span> <span data-ttu-id="df75f-112">还可以复制本教程中附带的已完成的 Lesson 4 包。</span><span class="sxs-lookup"><span data-stu-id="df75f-112">You can also copy the completed Lesson 4 package that is included with the tutorial.</span></span> <span data-ttu-id="df75f-113">使用包配置向导，将创建一个 XML 配置，以便通过使用映射到 Directory 属性的包级别变量来更新 Foreach 循环容器的 `Directory` 属性。</span><span class="sxs-lookup"><span data-stu-id="df75f-113">Using the Package Configuration Wizard, you will create an XML configuration that updates the `Directory` property of the Foreach Loop container by using a package-level variable mapped to the Directory property.</span></span> <span data-ttu-id="df75f-114">在创建配置文件之后，将从开发环境的外部修改该变量的值，并将修改后的属性指向新的示例数据文件夹。</span><span class="sxs-lookup"><span data-stu-id="df75f-114">Once you have created the configuration file, you will modify the value of the variable from outside of the development environment and point the modified property to a new sample data folder.</span></span> <span data-ttu-id="df75f-115">再次运行包时，配置文件将填充变量的值，而变量将更新 `Directory` 属性。</span><span class="sxs-lookup"><span data-stu-id="df75f-115">When you run the package again, the configuration file populates the value of the variable, and the variable in turn updates the `Directory` property.</span></span> <span data-ttu-id="df75f-116">结果，包将迭代遍历新数据文件夹中的文件，而不是迭代遍历在该包中硬编码的原始文件夹中的文件。</span><span class="sxs-lookup"><span data-stu-id="df75f-116">As a result, the package iterates through the files in the new data folder, rather than iterating through the files in the original folder that was hard-coded in the package.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="df75f-117">本教程需要 **AdventureWorksDW2012** 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="df75f-117">This tutorial requires the **AdventureWorksDW2012** sample database.</span></span> <span data-ttu-id="df75f-118">有关如何安装和部署 **AdventureWorksDW2012**的详细信息，请参阅 [CodePlex 上的 Reporting Services 产品示例](https://go.microsoft.com/fwlink/?LinkID=526910)。</span><span class="sxs-lookup"><span data-stu-id="df75f-118">For more information about how to install and deploy **AdventureWorksDW2012**, see [Reporting Services Product Samples on CodePlex](https://go.microsoft.com/fwlink/?LinkID=526910).</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="df75f-119">课程任务</span><span class="sxs-lookup"><span data-stu-id="df75f-119">Lesson Tasks</span></span>  
 <span data-ttu-id="df75f-120">本课程包含以下任务：</span><span class="sxs-lookup"><span data-stu-id="df75f-120">This lesson contains the following tasks:</span></span>  
  
-   [<span data-ttu-id="df75f-121">步骤 1：复制 Lesson 4 包</span><span class="sxs-lookup"><span data-stu-id="df75f-121">Step 1: Copying the Lesson 4 Package</span></span>](lesson-5-1-copying-the-lesson-4-package.md)  
  
-   [<span data-ttu-id="df75f-122">步骤 2：启用和配置包配置</span><span class="sxs-lookup"><span data-stu-id="df75f-122">Step 2: Enabling and Configuring Package Configurations</span></span>](lesson-5-2-enabling-and-configuring-package-configurations.md)  
  
-   [<span data-ttu-id="df75f-123">步骤 3：修改目录属性配置值</span><span class="sxs-lookup"><span data-stu-id="df75f-123">Step 3: Modifying the Directory Property Configuration Value</span></span>](lesson-5-3-modifying-the-directory-property-configuration-value.md)  
  
-   [<span data-ttu-id="df75f-124">步骤 4：测试第 5 课教程包</span><span class="sxs-lookup"><span data-stu-id="df75f-124">Step 4: Testing the Lesson 5 Tutorial Package</span></span>](lesson-5-4-testing-the-lesson-5-tutorial-package.md)  
  
## <a name="start-the-lesson"></a><span data-ttu-id="df75f-125">开始课程</span><span class="sxs-lookup"><span data-stu-id="df75f-125">Start the Lesson</span></span>  
  
-   [<span data-ttu-id="df75f-126">步骤 1：复制 Lesson 4 包</span><span class="sxs-lookup"><span data-stu-id="df75f-126">Step 1: Copying the Lesson 4 Package</span></span>](lesson-5-1-copying-the-lesson-4-package.md)  
  
  
