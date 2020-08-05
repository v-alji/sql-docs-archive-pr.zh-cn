---
title: 查看 SQL Server 对象的基于策略的管理方面 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, view facets
ms.assetid: 5f423b9f-a6c4-41a7-9d8d-8f4926ce1fb4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9137971a79e9e5a18e0ef5d901184133a4c3eff3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580172"
---
# <a name="view-the-policy-based-management-facets-on-a-sql-server-object"></a><span data-ttu-id="cf843-102">查看 SQL Server 对象的基于策略的管理方面</span><span class="sxs-lookup"><span data-stu-id="cf843-102">View the Policy-Based Management Facets on a SQL Server Object</span></span>
  <span data-ttu-id="cf843-103">本主题介绍如何通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中查看应用到特定 SQL Server 对象的所有基于策略的管理方面。</span><span class="sxs-lookup"><span data-stu-id="cf843-103">This topic describes how to view all of the Policy-Based Management facets applied to a specific SQL Server object in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="cf843-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="cf843-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="cf843-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="cf843-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="cf843-106">安全性</span><span class="sxs-lookup"><span data-stu-id="cf843-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="cf843-107">**若要查看对象的所有方面，请使用：**</span><span class="sxs-lookup"><span data-stu-id="cf843-107">**To view all of the facets in an object, using:**</span></span>  
  
     [<span data-ttu-id="cf843-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="cf843-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="cf843-109">开始之前</span><span class="sxs-lookup"><span data-stu-id="cf843-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="cf843-110">Security</span><span class="sxs-lookup"><span data-stu-id="cf843-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="cf843-111">权限</span><span class="sxs-lookup"><span data-stu-id="cf843-111">Permissions</span></span>  
 <span data-ttu-id="cf843-112">要求具有 msdb 数据库中 PolicyAdministratorRole 角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="cf843-112">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="cf843-113">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="cf843-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-all-of-the-facets-in-an-object"></a><span data-ttu-id="cf843-114">查看对象的所有方面</span><span class="sxs-lookup"><span data-stu-id="cf843-114">To view all of the facets in an object</span></span>  
  
1.  <span data-ttu-id="cf843-115">在对象资源管理器中，右键单击 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例、实例对象、数据库或数据库对象，然后单击“Facet”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="cf843-115">In Object Explorer, right-click an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], instance object, database, or database object, and then click **Facets**.</span></span>  
  
2.  <span data-ttu-id="cf843-116">在 "**查看方面**_object_name_ " 对话框中的 "**方面**" 列表中，选择要查看其属性的方面。</span><span class="sxs-lookup"><span data-stu-id="cf843-116">In the **View Facets -**_object_name_ dialog box, in the **Facet** list, select a facet to view its properties.</span></span> <span data-ttu-id="cf843-117">有关此对话框上可用选项的详细信息，请参阅 [View Facets Dialog Box](view-facets-dialog-box.md)。</span><span class="sxs-lookup"><span data-stu-id="cf843-117">For more information on the available options in this dialog box, see [View Facets Dialog Box](view-facets-dialog-box.md).</span></span>  
  
3.  <span data-ttu-id="cf843-118">完成后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="cf843-118">When finished, click **OK**.</span></span>  
  
  
