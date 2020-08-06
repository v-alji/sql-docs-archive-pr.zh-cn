---
title: 在对象资源管理器中隐藏系统对象 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- hiding system objects
- system objects [SQL Server]
- objects [SQL Server], hiding
- Object Explorer, hiding objects
ms.assetid: c01d8804-838c-4f75-b78c-80e41e4fffdc
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1e039446191154144dd6660fa6e8d3b4b65d1013
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576503"
---
# <a name="hide-system-objects-in-object-explorer"></a><span data-ttu-id="2db0f-102">在对象资源管理器中隐藏系统对象</span><span class="sxs-lookup"><span data-stu-id="2db0f-102">Hide System Objects in Object Explorer</span></span>
  <span data-ttu-id="2db0f-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的对象资源管理器中隐藏系统对象。</span><span class="sxs-lookup"><span data-stu-id="2db0f-103">This topic describes how to hide system objects in Object Explorer in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="2db0f-104">对象资源管理器的“数据库”  节点包含系统对象，如系统数据库。</span><span class="sxs-lookup"><span data-stu-id="2db0f-104">The **Databases** node of Object Explorer contains system objects such as the system databases.</span></span> <span data-ttu-id="2db0f-105">使用“工具”  /“选项”  页可以隐藏系统对象。</span><span class="sxs-lookup"><span data-stu-id="2db0f-105">Use the **Tools**/**Options** pages to hide the system objects.</span></span> <span data-ttu-id="2db0f-106">某些系统对象（如系统函数和系统数据类型）并不受此设置的影响。</span><span class="sxs-lookup"><span data-stu-id="2db0f-106">Some system objects, such as system functions and system data types, are not affected by this setting.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2db0f-107">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2db0f-107">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-hide-system-objects-in-object-explorer"></a><span data-ttu-id="2db0f-108">在对象资源管理器中隐藏系统对象</span><span class="sxs-lookup"><span data-stu-id="2db0f-108">To hide system objects in Object Explorer</span></span>  
  
1.  <span data-ttu-id="2db0f-109">在“工具”  菜单上，单击“选项”  。</span><span class="sxs-lookup"><span data-stu-id="2db0f-109">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="2db0f-110">在“环境”/“启动”  页上，选中“在对象资源管理器中隐藏系统对象”  ，再单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="2db0f-110">On the **Environment/Startup** page, select **Hide system objects in Object Explorer**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="2db0f-111">在“SQL Server Management Studio”  对话框中，单击“确定”  ，确认必须重启 SQL Server Management Studio，以便此更改生效。</span><span class="sxs-lookup"><span data-stu-id="2db0f-111">In the **SQL Server Management Studio** dialog box, click **OK** to acknowledge that SQL Server Management Studio must be restarted for this change to take effect.</span></span>  
  
4.  <span data-ttu-id="2db0f-112">关闭并重新打开 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="2db0f-112">Close and reopen SQL Server Management Studio.</span></span>  
  
  
