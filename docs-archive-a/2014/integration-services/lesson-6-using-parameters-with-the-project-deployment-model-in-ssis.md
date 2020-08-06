---
title: 第6课：对项目部署模型使用参数 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9216f18c-1762-4f2d-8c22-bd0ab7107555
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4bdc6b9dfc019822d6cf1bd9ec7d89ffcc5ea5e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579626"
---
# <a name="lesson-6-using-parameters-with-the-project-deployment-model"></a><span data-ttu-id="fd896-102">第 6 课：对项目部署模型使用参数</span><span class="sxs-lookup"><span data-stu-id="fd896-102">Lesson 6: Using Parameters with the Project Deployment Model</span></span>
  <span data-ttu-id="fd896-103">SQL Server 2012 引入了一个新的部署模型，可用于将您的项目部署到 Integration Services 服务器。</span><span class="sxs-lookup"><span data-stu-id="fd896-103">SQL Server 2012 introduces a new deployment model where you can deploy your projects to the Integration Services server.</span></span> <span data-ttu-id="fd896-104">通过 Integration Services 服务器，您可以管理和运行包，以及为包配置运行时值。</span><span class="sxs-lookup"><span data-stu-id="fd896-104">The Integration Services server enables you to manage and run packages, and to configure runtime values for packages.</span></span>  
  
 <span data-ttu-id="fd896-105">在本课中，您将修改在[第5课：添加包部署模型的包配置](lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md)中创建的包，以使用项目部署模型。</span><span class="sxs-lookup"><span data-stu-id="fd896-105">In this lesson, you will modify the package that you created in [Lesson 5: Adding Package Configurations for the Package Deployment Model](lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md) to use the Project Deployment Model.</span></span> <span data-ttu-id="fd896-106">您将使用一个参数替换该配置值，以便指定示例数据位置。</span><span class="sxs-lookup"><span data-stu-id="fd896-106">You replace the configuration value with a parameter to specify the sample data location.</span></span> <span data-ttu-id="fd896-107">还可以复制本教程附带的已完成的 Lesson 5 包。</span><span class="sxs-lookup"><span data-stu-id="fd896-107">You can also copy the completed Lesson 5 package that is included with the tutorial.</span></span>  
  
 <span data-ttu-id="fd896-108">使用 Integration Services 项目配置向导，您将该项目转换为项目部署模型，并且使用参数而不是配置值来设置 Directory 属性。</span><span class="sxs-lookup"><span data-stu-id="fd896-108">Using the Integration Services Project Configuration Wizard, you will convert the project to the Project Deployment Model and use a Parameter rather than a configuration value to set the Directory property.</span></span> <span data-ttu-id="fd896-109">本课部分介绍了您将现有 SSIS 包转换为新的项目部署模型时要遵循的步骤。</span><span class="sxs-lookup"><span data-stu-id="fd896-109">This lesson partially covers the steps you would follow to convert existing SSIS packages to the new Project Deployment Model.</span></span>  
  
 <span data-ttu-id="fd896-110">再次运行包时，Integration Services 服务使用参数填充变量的值，而变量又会更新 Directory 属性。</span><span class="sxs-lookup"><span data-stu-id="fd896-110">When you run the package again, the Integration Services service uses the parameter to populate the value of the variable, and the variable in turn updates the Directory property.</span></span> <span data-ttu-id="fd896-111">结果，包将遍历该参数值指定的新数据文件夹中的文件，而不是遍历在包配置文件中设置的文件夹。</span><span class="sxs-lookup"><span data-stu-id="fd896-111">As a result, the package iterates through the files in the new data folder specified by the parameter value rather than the folder that was set in the package configuration file.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="fd896-112">本教程需要 **AdventureWorksDW2012** 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="fd896-112">This tutorial requires the **AdventureWorksDW2012** sample database.</span></span> <span data-ttu-id="fd896-113">有关如何安装和部署 **AdventureWorksDW2012**的详细信息，请参阅 [安装 SQL Server 示例和示例数据库的注意事项](https://technet.microsoft.com/library/ms161556%28v=sql.105%29)。</span><span class="sxs-lookup"><span data-stu-id="fd896-113">For more information about how to install and deploy **AdventureWorksDW2012**, see [Considerations for Installing SQL Server Samples and Sample Databases](https://technet.microsoft.com/library/ms161556%28v=sql.105%29).</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="fd896-114">课程任务</span><span class="sxs-lookup"><span data-stu-id="fd896-114">Lesson Tasks</span></span>  
 <span data-ttu-id="fd896-115">本课程包含以下任务：</span><span class="sxs-lookup"><span data-stu-id="fd896-115">This lesson contains the following tasks:</span></span>  
  
1.  [<span data-ttu-id="fd896-116">步骤 1：复制第 5 课包</span><span class="sxs-lookup"><span data-stu-id="fd896-116">Step 1: Copying the Lesson 5 Package</span></span>](lesson-6-1-copying-the-lesson-5-package.md)  
  
2.  [<span data-ttu-id="fd896-117">步骤 2：将项目转换为项目部署模型</span><span class="sxs-lookup"><span data-stu-id="fd896-117">Step 2: Converting the Project to the Project Deployment Model</span></span>](lesson-6-2-converting-the-project-to-the-project-deployment-model.md)  
  
3.  [<span data-ttu-id="fd896-118">步骤 3：测试第 6 课包</span><span class="sxs-lookup"><span data-stu-id="fd896-118">Step 3: Testing the Lesson 6 Package</span></span>](lesson-6-3-testing-the-lesson-6-package.md)  
  
4.  [<span data-ttu-id="fd896-119">步骤 4：部署第 6 课包</span><span class="sxs-lookup"><span data-stu-id="fd896-119">Step 4: Deploying the Lesson 6 Package</span></span>](lesson-6-4-deploying-the-lesson-6-package.md)  
  
## <a name="start-the-lesson"></a><span data-ttu-id="fd896-120">开始课程</span><span class="sxs-lookup"><span data-stu-id="fd896-120">Start the Lesson</span></span>  
 [<span data-ttu-id="fd896-121">步骤 1：复制第 5 课包</span><span class="sxs-lookup"><span data-stu-id="fd896-121">Step 1: Copying the Lesson 5 Package</span></span>](lesson-6-1-copying-the-lesson-5-package.md)  
  
  
