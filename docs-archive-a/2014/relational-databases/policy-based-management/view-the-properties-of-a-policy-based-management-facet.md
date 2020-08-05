---
title: 查看基于策略的管理方面的属性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, view facet properties
ms.assetid: 022a244c-c2e7-4467-b9a2-c7a27859be22
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ea24ff2768ecaeec426a8689455912d848b54813
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580171"
---
# <a name="view-the-properties-of-a-policy-based-management-facet"></a><span data-ttu-id="b825a-102">查看基于策略的管理方面的属性</span><span class="sxs-lookup"><span data-stu-id="b825a-102">View the Properties of a Policy-Based Management Facet</span></span>
  <span data-ttu-id="b825a-103">本主题介绍如何通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中查看基于策略的管理方面的属性。</span><span class="sxs-lookup"><span data-stu-id="b825a-103">This topic describes how to view the properties of a Policy-Based Management facet in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="b825a-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="b825a-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b825a-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="b825a-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b825a-106">安全性</span><span class="sxs-lookup"><span data-stu-id="b825a-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b825a-107">**若要查看某个方面的属性，请使用：**</span><span class="sxs-lookup"><span data-stu-id="b825a-107">**To view the properties of a facet, using:**</span></span>  
  
     [<span data-ttu-id="b825a-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b825a-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b825a-109">开始之前</span><span class="sxs-lookup"><span data-stu-id="b825a-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b825a-110">Security</span><span class="sxs-lookup"><span data-stu-id="b825a-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b825a-111">权限</span><span class="sxs-lookup"><span data-stu-id="b825a-111">Permissions</span></span>  
 <span data-ttu-id="b825a-112">要求具有 msdb 数据库中 PolicyAdministratorRole 角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="b825a-112">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b825a-113">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b825a-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-properties-of-a-facet"></a><span data-ttu-id="b825a-114">查看方面的属性</span><span class="sxs-lookup"><span data-stu-id="b825a-114">To view the properties of a facet</span></span>  
  
1.  <span data-ttu-id="b825a-115">在 **“对象资源管理器”** 中，单击加号以展开您要查看其属性的方面所在的服务器。</span><span class="sxs-lookup"><span data-stu-id="b825a-115">In **Object Explorer**, click the plus sign to expand the server that contains the facet whose properties you want to view.</span></span>  
  
2.  <span data-ttu-id="b825a-116">单击加号以便展开 **“管理”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="b825a-116">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="b825a-117">单击加号以便展开 **“策略管理”**。</span><span class="sxs-lookup"><span data-stu-id="b825a-117">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="b825a-118">单击加号以便展开 **“方面”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="b825a-118">Click the plus sign to expand the **Facets** folder.</span></span>  
  
5.  <span data-ttu-id="b825a-119">右键单击要查看其属性的方面，然后选择\*\*\*\*“属性”。</span><span class="sxs-lookup"><span data-stu-id="b825a-119">Right-click the facet whose properties you want to view and select **Properties**.</span></span> <span data-ttu-id="b825a-120">有关 "**方面属性-**_facet_name_ " 对话框中的可用选项的详细信息，请参阅 " [facet 属性" 对话框，"常规" 页](../../integration-services/general-page-of-integration-services-designers-options.md)，"[方面属性" 对话框，"依赖策略" 页](facet-properties-dialog-box-dependent-policies-page.md)和["Facet 属性" 对话框，"依赖条件" 页](facet-properties-dialog-box-dependent-conditions-page.md)。</span><span class="sxs-lookup"><span data-stu-id="b825a-120">For more information on the available options in the **Facet Properties -**_facet_name_ dialog box, see [Facet Properties Dialog Box, General Page](../../integration-services/general-page-of-integration-services-designers-options.md), [Facet Properties Dialog Box, Dependent Policies Page](facet-properties-dialog-box-dependent-policies-page.md), and [Facet Properties Dialog Box, Dependent Conditions Page](facet-properties-dialog-box-dependent-conditions-page.md).</span></span>  
  
6.  <span data-ttu-id="b825a-121">完成后，单击“关闭”。</span><span class="sxs-lookup"><span data-stu-id="b825a-121">When finished, click **Close**.</span></span>  
  
  
