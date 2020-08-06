---
title: 步骤 2：将项目转换为项目部署模型 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 80964293-f1f5-4da7-b1fb-00ab8c30c1c5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1a7b879b2bea4afd58a48cdfc6f0890353fe6758
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578301"
---
# <a name="step-2-converting-the-project-to-the-project-deployment-model"></a><span data-ttu-id="4f629-102">步骤 2：将项目转换为项目部署模型</span><span class="sxs-lookup"><span data-stu-id="4f629-102">Step 2: Converting the Project to the Project Deployment Model</span></span>
  <span data-ttu-id="4f629-103">在本任务中，你将使用 Integration Services 项目转换向导将项目转换为项目部署模型。</span><span class="sxs-lookup"><span data-stu-id="4f629-103">In this task, you will use the Integration Services Project Conversion Wizard to convert the project to the Project Deployment Model.</span></span>  
  
### <a name="converting-the-project-to-the-project-deployment-model"></a><span data-ttu-id="4f629-104">将项目转换为项目部署模型</span><span class="sxs-lookup"><span data-stu-id="4f629-104">Converting the Project to the Project Deployment Model</span></span>  
  
1.  <span data-ttu-id="4f629-105">在“项目”菜单上，单击“转换为项目部署模型”。</span><span class="sxs-lookup"><span data-stu-id="4f629-105">On the Project Menu, click Convert to Project Deployment Model.</span></span>  
  
2.  <span data-ttu-id="4f629-106">在 Integration Services 项目转换向导简介页面上，检查步骤，然后单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="4f629-106">On the Integration Services Project Conversion Wizard Introduction page, review the steps then click Next.</span></span>  
  
3.  <span data-ttu-id="4f629-107">在“选择包”页面上的“包”列表中，清除所有复选框（除了 Lesson 6.dtsx），然后单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="4f629-107">On the Select Packages page, in the Packages list, clear all checkboxes except Lesson 6.dtsx then click Next.</span></span>  
  
4.  <span data-ttu-id="4f629-108">在“指定项目属性”页面上，单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="4f629-108">On the Specify Project Properties page, click Next.</span></span>  
  
5.  <span data-ttu-id="4f629-109">在“更新执行包任务”页面上，单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="4f629-109">On the Update Execute Package Task page click Next.</span></span>  
  
6.  <span data-ttu-id="4f629-110">在“选择配置”页面上，确保在“配置”列表中选择 Lesson 6.dtsx 包，然后单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="4f629-110">On the Select Configurations page, make sure the Lesson 6.dtsx package is selected in the Configurations list, then click Next.</span></span>  
  
7.  <span data-ttu-id="4f629-111">在“创建参数”页面上，确保在“配置属性”列表中选择 Lesson 6.dtsx 包，并且“范围”设置为“包”，然后单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="4f629-111">On the Create Parameters page make sure the Lesson 6.dtsx package is selected, and the Scope is set to Package, in the Configuration Properties List, then Click Next.</span></span>  
  
8.  <span data-ttu-id="4f629-112">在“配置参数”页面上，对于变量和配置值验证“名称”和“值”的值是否为第 5 课中指定的相同名称和值，然后单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="4f629-112">On the Configure Parameters page verify that the values for Name and Value are the same name and value specified in Lesson 5 for the variable and configuration value, then click Next.</span></span>  
  
9. <span data-ttu-id="4f629-113">在“检查”页面上的“摘要”窗格中，请注意向导使用了配置文件中的信息来设置“要转换的属性”。</span><span class="sxs-lookup"><span data-stu-id="4f629-113">On the Review page, in the Summary pane, notice that the wizard has used the information from the configuration file to set the Properties to be converted.</span></span>  
  
10. <span data-ttu-id="4f629-114">单击“转换”。</span><span class="sxs-lookup"><span data-stu-id="4f629-114">Click Convert.</span></span>  
  
     <span data-ttu-id="4f629-115">转换完成时会显示一条消息，警告在 Visual Studio 中保存项目之前不会保存更改。</span><span class="sxs-lookup"><span data-stu-id="4f629-115">When the conversion completes a message is displayed warning that the changes are not saved until the project is saved in Visual Studio.</span></span> <span data-ttu-id="4f629-116">在警告对话框中单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="4f629-116">Click OK on the warning dialog.</span></span>  
  
11. <span data-ttu-id="4f629-117">在 Integration Services 项目转换向导上单击“关闭”。</span><span class="sxs-lookup"><span data-stu-id="4f629-117">On the Integration Services Project Conversion Wizard click Close.</span></span>  
  
12. <span data-ttu-id="4f629-118">在 SQL Server Data Tools 中，单击“文件”菜单，然后单击“保存”以保存转换的包。</span><span class="sxs-lookup"><span data-stu-id="4f629-118">In SQL Server Data Tools, click the File menu, then click Save to save the converted package.</span></span>  
  
13. <span data-ttu-id="4f629-119">单击“参数”选项卡，然后验证包现在是否包含用于 VarFolderName 的参数，以及值是否为第 5 课配置文件中为 New Sample Data 文件夹指定的相同路径。</span><span class="sxs-lookup"><span data-stu-id="4f629-119">Click the Parameters Tab and verify that the package now contains a parameter for VarFolderName and that the value is the same path specified for the New Sample Data folder from the Lesson 5 configuration file.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="4f629-120">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="4f629-120">Next Task in Lesson</span></span>  
 [<span data-ttu-id="4f629-121">步骤 3：测试第 6 课包</span><span class="sxs-lookup"><span data-stu-id="4f629-121">Step 3: Testing the Lesson 6 Package</span></span>](lesson-6-3-testing-the-lesson-6-package.md)  
  
  
