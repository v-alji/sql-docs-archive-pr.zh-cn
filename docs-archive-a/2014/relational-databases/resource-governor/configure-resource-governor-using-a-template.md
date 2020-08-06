---
title: 使用模板配置资源调控器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, templates
ms.assetid: f342dec2-d1d6-483e-b44e-98eb7d168b5e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 62edb23cf55a953cb0fef54f002f8eaaa16f58ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590165"
---
# <a name="configure-resource-governor-using-a-template"></a><span data-ttu-id="c4e30-102">使用模板配置 Resource Governor</span><span class="sxs-lookup"><span data-stu-id="c4e30-102">Configure Resource Governor Using a Template</span></span>
  <span data-ttu-id="c4e30-103">您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中提供的模板配置资源调控器。</span><span class="sxs-lookup"><span data-stu-id="c4e30-103">You can configure Resource Governor by using a template that is provided in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="c4e30-104">**开始之前：** [权限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="c4e30-104">**Before you begin:**  [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="c4e30-105">要创建工作负载组，请使用：[模板](#ConfRGTemplate)</span><span class="sxs-lookup"><span data-stu-id="c4e30-105">**To create a workload group, using:**  [a template](#ConfRGTemplate)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c4e30-106">开始之前</span><span class="sxs-lookup"><span data-stu-id="c4e30-106">Before You Begin</span></span>  
 <span data-ttu-id="c4e30-107">使用下列步骤可打开和修改创建资源池和资源池的工作负荷组的模板。</span><span class="sxs-lookup"><span data-stu-id="c4e30-107">Use the following steps to open and modify a template that creates a resource pool and a workload group for the pool.</span></span> <span data-ttu-id="c4e30-108">此外，该模板还可以创建分类器用户定义函数，以将新的连接传送到默认组或用户创建的工作负荷组。</span><span class="sxs-lookup"><span data-stu-id="c4e30-108">In addition, this template enables you to create a classifier user-defined function that routes new connections to either the default group or the workload group that you create.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c4e30-109">权限</span><span class="sxs-lookup"><span data-stu-id="c4e30-109">Permissions</span></span>  
 <span data-ttu-id="c4e30-110">模板中的资源调控器 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句需要 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="c4e30-110">The resource governor [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in the template require CONTROL SERVER permission.</span></span>  
  
##  <a name="configure-resource-governor-using-a-template"></a><a name="ConfRGTemplate"></a> <span data-ttu-id="c4e30-111">使用模板配置资源调控器</span><span class="sxs-lookup"><span data-stu-id="c4e30-111">Configure Resource Governor Using a Template</span></span>  
 <span data-ttu-id="c4e30-112">**使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="c4e30-112">**To configure resource governor by using a template in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span></span>  
  
1.  <span data-ttu-id="c4e30-113">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的“视图”  菜单上，单击“模板资源管理器” 。</span><span class="sxs-lookup"><span data-stu-id="c4e30-113">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **View** menu, click **Template Explorer**.</span></span>  
  
2.  <span data-ttu-id="c4e30-114">在**模板资源管理器**中，展开“资源调控器”，然后双击“配置资源调控器”。</span><span class="sxs-lookup"><span data-stu-id="c4e30-114">In **Template Explorer**, expand **Resource Governor**, and then double-click **Configure Resource Governor**.</span></span>  
  
3.  <span data-ttu-id="c4e30-115">在 **“连接到数据库引擎”** 中，输入所需信息，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="c4e30-115">In **Connect to Database Engine**, enter the required information, and then click **OK**.</span></span> <span data-ttu-id="c4e30-116">查询编辑器中提供模板 Configure Resource Governor.sql。</span><span class="sxs-lookup"><span data-stu-id="c4e30-116">The template Configure Resource Governor.sql is provided in the Query Editor.</span></span> <span data-ttu-id="c4e30-117">使用此模板可创建和配置资源池、工作负荷组和分类器函数。</span><span class="sxs-lookup"><span data-stu-id="c4e30-117">Use this template to create and configure a resource pool, a workload group, and a classifier function.</span></span>  
  
4.  <span data-ttu-id="c4e30-118">若要更改模板中的值，请按 CTRL+SHIFT+M。</span><span class="sxs-lookup"><span data-stu-id="c4e30-118">To change the values in the template, press CTRL+SHIFT+M.</span></span> <span data-ttu-id="c4e30-119">在 **“指定模板参数的值”** 窗口中，输入要使用的值。</span><span class="sxs-lookup"><span data-stu-id="c4e30-119">In the **Specify Values for Template Parameters** window, enter the values that you want to use.</span></span>  
  
5.  <span data-ttu-id="c4e30-120">若要保存对该模板所做的更改，请单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="c4e30-120">To save the changes that you make to the template, click **OK**.</span></span>  
  
6.  <span data-ttu-id="c4e30-121">若要运行查询，请单击 **“执行”** 。</span><span class="sxs-lookup"><span data-stu-id="c4e30-121">To run the query, click **Execute**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4e30-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c4e30-122">See Also</span></span>  
 <span data-ttu-id="c4e30-123">[资源调控器](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="c4e30-123">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="c4e30-124">[启用资源调控器](enable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="c4e30-124">[Enable Resource Governor](enable-resource-governor.md) </span></span>  
 <span data-ttu-id="c4e30-125">[资源调控器资源池](resource-governor-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="c4e30-125">[Resource Governor Resource Pool](resource-governor-resource-pool.md) </span></span>  
 <span data-ttu-id="c4e30-126">[资源调控器工作负荷组](resource-governor-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="c4e30-126">[Resource Governor Workload Group](resource-governor-workload-group.md) </span></span>  
 <span data-ttu-id="c4e30-127">[资源调控器分类器函数](resource-governor-classifier-function.md) </span><span class="sxs-lookup"><span data-stu-id="c4e30-127">[Resource Governor Classifier Function](resource-governor-classifier-function.md) </span></span>  
 <span data-ttu-id="c4e30-128">[查看资源调控器属性](view-resource-governor-properties.md) </span><span class="sxs-lookup"><span data-stu-id="c4e30-128">[View Resource Governor Properties](view-resource-governor-properties.md) </span></span>  
 <span data-ttu-id="c4e30-129">[CREATE RESOURCE POOL (Transact-SQL)](/sql/t-sql/statements/create-resource-pool-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c4e30-129">[CREATE RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql) </span></span>  
 <span data-ttu-id="c4e30-130">[CREATE WORKLOAD GROUP (Transact-SQL)](/sql/t-sql/statements/create-workload-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c4e30-130">[CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-workload-group-transact-sql) </span></span>  
 <span data-ttu-id="c4e30-131">[CREATE FUNCTION (Transact-SQL)](/sql/t-sql/statements/create-function-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c4e30-131">[CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql) </span></span>  
 [<span data-ttu-id="c4e30-132">ALTER RESOURCE GOVERNOR (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c4e30-132">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
