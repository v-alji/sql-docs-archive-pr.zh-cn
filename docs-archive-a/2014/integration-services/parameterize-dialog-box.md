---
title: "\"参数化\" 对话框 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.parameter.f1
ms.assetid: fac02b6d-d247-447a-8940-e8700c7ac350
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8db19844132402740aec092d6e88f3c9e3864d58
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586781"
---
# <a name="parameterize-dialog-box"></a><span data-ttu-id="09c51-102">Parameterize Dialog Box</span><span class="sxs-lookup"><span data-stu-id="09c51-102">Parameterize Dialog Box</span></span>
  <span data-ttu-id="09c51-103">通过 **“参数化”** 对话框，可以将新参数或现有参数与某个任务的属性相关联。</span><span class="sxs-lookup"><span data-stu-id="09c51-103">The **Parameterize** dialog box enables you to associate a new or an existing parameter with a property of a task.</span></span> <span data-ttu-id="09c51-104">可通过以下方式打开该对话框：在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器中右键单击一个任务或“控制流”选项卡，然后单击“参数化”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="09c51-104">You open the dialog box by right-clicking a task or the Control Flow tab in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer and then by clicking **Parameterize**.</span></span> <span data-ttu-id="09c51-105">以下列表介绍了此对话框中的 UI 元素。</span><span class="sxs-lookup"><span data-stu-id="09c51-105">The following list describes UI elements in the dialog box.</span></span> <span data-ttu-id="09c51-106">有关参数的详细信息，请参阅 [Integration Services (SSIS) 参数](integration-services-ssis-package-and-project-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="09c51-106">For more information about parameters, see [Integration Services &#40;SSIS&#41; Parameters](integration-services-ssis-package-and-project-parameters.md).</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="09c51-107">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="09c51-107">UI element list</span></span>  
 <span data-ttu-id="09c51-108">**属性**</span><span class="sxs-lookup"><span data-stu-id="09c51-108">**Property**</span></span>  
 <span data-ttu-id="09c51-109">选择要与参数相关联的任务属性。</span><span class="sxs-lookup"><span data-stu-id="09c51-109">Select the property of the task that you want to associate with a parameter.</span></span> <span data-ttu-id="09c51-110">此列表包含可参数化的所有属性。</span><span class="sxs-lookup"><span data-stu-id="09c51-110">This list is populated with all the properties that can be parameterized.</span></span>  
  
 <span data-ttu-id="09c51-111">**使用现有参数**</span><span class="sxs-lookup"><span data-stu-id="09c51-111">**Use existing parameter**</span></span>  
 <span data-ttu-id="09c51-112">使用此选项可将任务属性与某个现有参数相关联，从而可以从下拉列表中选择该参数。</span><span class="sxs-lookup"><span data-stu-id="09c51-112">Select this option to associate the property of task with an existing parameter and then select the parameter from drop-down list.</span></span>  
  
 <span data-ttu-id="09c51-113">**不使用参数**</span><span class="sxs-lookup"><span data-stu-id="09c51-113">**Do not use parameter**</span></span>  
 <span data-ttu-id="09c51-114">选择此选项可以删除对参数的引用。</span><span class="sxs-lookup"><span data-stu-id="09c51-114">Select this option to remove a reference to a parameter.</span></span> <span data-ttu-id="09c51-115">不删除该参数。</span><span class="sxs-lookup"><span data-stu-id="09c51-115">The parameter is not deleted.</span></span>  
  
 <span data-ttu-id="09c51-116">**新建参数**</span><span class="sxs-lookup"><span data-stu-id="09c51-116">**Create new parameter**</span></span>  
 <span data-ttu-id="09c51-117">选择此选项可创建要与任务属性相关联的新参数。</span><span class="sxs-lookup"><span data-stu-id="09c51-117">Select this option to create a new parameter that you want to associate with the property of the task.</span></span>  
  
 <span data-ttu-id="09c51-118">**名称**</span><span class="sxs-lookup"><span data-stu-id="09c51-118">**Name**</span></span>  
 <span data-ttu-id="09c51-119">指定要创建的参数的名称。</span><span class="sxs-lookup"><span data-stu-id="09c51-119">Specify the name of the parameter you want to create.</span></span>  
  
 <span data-ttu-id="09c51-120">**说明**</span><span class="sxs-lookup"><span data-stu-id="09c51-120">**Description**</span></span>  
 <span data-ttu-id="09c51-121">指定参数的说明。</span><span class="sxs-lookup"><span data-stu-id="09c51-121">Specify the description for parameter.</span></span>  
  
 <span data-ttu-id="09c51-122">**值**</span><span class="sxs-lookup"><span data-stu-id="09c51-122">**Value**</span></span>  
 <span data-ttu-id="09c51-123">指定参数的默认值。</span><span class="sxs-lookup"><span data-stu-id="09c51-123">Specify the default value for the parameter.</span></span> <span data-ttu-id="09c51-124">这也称作设计默认值，以后在部署时可以覆盖该值。</span><span class="sxs-lookup"><span data-stu-id="09c51-124">This is also known as the design default, which can be overridden later at the deployment time.</span></span>  
  
 <span data-ttu-id="09c51-125">**范围**</span><span class="sxs-lookup"><span data-stu-id="09c51-125">**Scope**</span></span>  
 <span data-ttu-id="09c51-126">通过选择“项目”或“包”选项指定参数的范围。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="09c51-126">Specify the scope of the parameter by selecting either **Project** or **Package** option.</span></span> <span data-ttu-id="09c51-127">项目参数可用于向项目中的一个或多个包提供项目接收的任何外部输入。</span><span class="sxs-lookup"><span data-stu-id="09c51-127">Project parameters are used to supply any external input the project receives to one or more packages in the project.</span></span> <span data-ttu-id="09c51-128">利用包参数，您不必编辑和重新部署包就可以修改包执行。</span><span class="sxs-lookup"><span data-stu-id="09c51-128">Package parameters allow you to modify package execution without having to edit and redeploy the package.</span></span>  
  
 <span data-ttu-id="09c51-129">**光敏**</span><span class="sxs-lookup"><span data-stu-id="09c51-129">**Sensitive**</span></span>  
 <span data-ttu-id="09c51-130">通过选中或清除该复选框，指定参数是否为敏感参数。</span><span class="sxs-lookup"><span data-stu-id="09c51-130">Specify whether the parameter is a sensitive by checking or clearing the check box.</span></span> <span data-ttu-id="09c51-131">敏感参数值在目录中加密，并且在使用 Transact-SQL 或 SQL Server Management Studio 查看时以 NULL 值的形式出现。</span><span class="sxs-lookup"><span data-stu-id="09c51-131">Sensitive parameter values are encrypted in the catalog and appear as a NULL value when viewed with Transact-SQL or SQL Server Management Studio.</span></span>  
  
 <span data-ttu-id="09c51-132">**必需**</span><span class="sxs-lookup"><span data-stu-id="09c51-132">**Required**</span></span>  
 <span data-ttu-id="09c51-133">指定参数是否要求在执行包之前指定设计默认值之外的值。</span><span class="sxs-lookup"><span data-stu-id="09c51-133">Specify whether the parameter requires that a value, other than the design default, is specified before the package can execute.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="09c51-134">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="09c51-134">UI element list</span></span>  
  
