---
title: 创建新的基于策略的管理条件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, creating policy conditions
ms.assetid: 8a612f7e-6c70-49db-a4de-48431e097cc5
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e4fe206c9a82b69101508f6f0a760ca9c1bc423d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587373"
---
# <a name="create-a-new-policy-based-management-condition"></a><span data-ttu-id="0d6d5-102">创建新的基于策略的管理条件</span><span class="sxs-lookup"><span data-stu-id="0d6d5-102">Create a New Policy-Based Management Condition</span></span>
  <span data-ttu-id="0d6d5-103">本主题介绍如何通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中创建基于策略的管理条件。</span><span class="sxs-lookup"><span data-stu-id="0d6d5-103">This topic describes how to create a Policy-based Management condition in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="0d6d5-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="0d6d5-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0d6d5-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="0d6d5-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="0d6d5-106">安全性</span><span class="sxs-lookup"><span data-stu-id="0d6d5-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="0d6d5-107">**若要创建条件，请使用：**</span><span class="sxs-lookup"><span data-stu-id="0d6d5-107">**To create a condition, using:**</span></span>  
  
     [<span data-ttu-id="0d6d5-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0d6d5-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0d6d5-109">开始之前</span><span class="sxs-lookup"><span data-stu-id="0d6d5-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0d6d5-110">Security</span><span class="sxs-lookup"><span data-stu-id="0d6d5-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0d6d5-111">权限</span><span class="sxs-lookup"><span data-stu-id="0d6d5-111">Permissions</span></span>  
 <span data-ttu-id="0d6d5-112">要求具有 msdb 数据库中 PolicyAdministratorRole 角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="0d6d5-112">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="0d6d5-113">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0d6d5-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-condition"></a><span data-ttu-id="0d6d5-114">创建条件</span><span class="sxs-lookup"><span data-stu-id="0d6d5-114">To create a condition</span></span>  
  
1.  <span data-ttu-id="0d6d5-115">在“对象资源管理器”  中，单击加号以展开你要在其中创建基于策略的管理条件的服务器。</span><span class="sxs-lookup"><span data-stu-id="0d6d5-115">In **Object Explorer**, click the plus sign to expand the server where you want to create a Policy-based Management condition.</span></span>  
  
2.  <span data-ttu-id="0d6d5-116">单击加号以便展开 **“管理”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="0d6d5-116">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="0d6d5-117">单击加号以便展开 **“策略管理”** 。</span><span class="sxs-lookup"><span data-stu-id="0d6d5-117">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="0d6d5-118">单击加号以便展开 **“方面”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="0d6d5-118">Click the plus sign to expand the **Facets** folder.</span></span>  
  
5.  <span data-ttu-id="0d6d5-119">右键单击要在其中创建新条件的方面，然后选择“新建条件”  。</span><span class="sxs-lookup"><span data-stu-id="0d6d5-119">Right-click the facet in which you want to create a new condition and select **New Condition**.</span></span>  
  
6.  <span data-ttu-id="0d6d5-120">在 **“创建新条件”** 对话框的 **“名称”** 框中，键入新条件的名称。</span><span class="sxs-lookup"><span data-stu-id="0d6d5-120">In the **Create New Condition** dialog box, in the **Name** box, type the name of the new condition.</span></span>  
  
7.  <span data-ttu-id="0d6d5-121">确认 **“方面”** 列表中的方面正确无误，或者选择一个不同的方面。</span><span class="sxs-lookup"><span data-stu-id="0d6d5-121">Confirm the correct facet in the **Facet** list, or select a different facet.</span></span>  
  
8.  <span data-ttu-id="0d6d5-122">在 **“表达式”** 下，通过在 **“字段”** 框中选择一个方面属性及与其关联的运算符和值，构造条件表达式。</span><span class="sxs-lookup"><span data-stu-id="0d6d5-122">Under **Expression**, construct condition expressions by selecting a facet property in the **Field** box, together with its associated operator and value.</span></span> <span data-ttu-id="0d6d5-123">在添加多个表达式时，可使用 **And** 或 **Or**来联接这些表达式。</span><span class="sxs-lookup"><span data-stu-id="0d6d5-123">When you add multiple expressions, the expressions can be joined by using **And** or **Or**.</span></span> <span data-ttu-id="0d6d5-124">有关此对话框中可用选项的详细信息，请参阅[“创建新条件”或“打开条件”对话框，“常规”页](../../integration-services/general-page-of-integration-services-designers-options.md)、[“创建新条件”或“打开条件”对话框，“说明”页](create-new-condition-or-open-condition-dialog-box-description-page.md)和[“高级编辑(条件)”对话框](advanced-edit-condition-dialog-box.md)。</span><span class="sxs-lookup"><span data-stu-id="0d6d5-124">For more information on the available options in this dialog box, see [Create New Condition or Open Condition Dialog Box, General Page](../../integration-services/general-page-of-integration-services-designers-options.md), [Create New Condition or Open Condition Dialog Box, Description Page](create-new-condition-or-open-condition-dialog-box-description-page.md), and [Advanced Edit &#40;Condition&#41; Dialog Box](advanced-edit-condition-dialog-box.md).</span></span>  
  
9. <span data-ttu-id="0d6d5-125">完成后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="0d6d5-125">When finished, click **OK**.</span></span>  
  
  
