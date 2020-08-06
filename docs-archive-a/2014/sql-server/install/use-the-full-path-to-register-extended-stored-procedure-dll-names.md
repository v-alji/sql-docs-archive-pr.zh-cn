---
title: 使用完整路径注册扩展存储过程 DLL 名称 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- registering DLL names
- extended stored procedures [SQL Server], registering
- DLL names [SQL Server]
- full path DLL name registration [SQL Server]
ms.assetid: f648d57c-af32-4c71-9882-47b6766f3c2b
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 5ec4ef3fc2e0f2c4834ffa7479a00562ae15d07f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689705"
---
# <a name="use-the-full-path-to-register-extended-stored-procedure-dll-names"></a><span data-ttu-id="c70da-102">使用完整路径注册扩展存储过程 DLL 名称</span><span class="sxs-lookup"><span data-stu-id="c70da-102">Use the full path to register extended stored procedure DLL names</span></span>
  <span data-ttu-id="c70da-103">先前未用 DLL 名称的完整路径注册的扩展存储过程在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中可能无法运行。</span><span class="sxs-lookup"><span data-stu-id="c70da-103">Extended stored procedures that were previously registered without the full path for the DLL name may not work in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="component"></a><span data-ttu-id="c70da-104">组件</span><span class="sxs-lookup"><span data-stu-id="c70da-104">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="c70da-105">说明</span><span class="sxs-lookup"><span data-stu-id="c70da-105">Description</span></span>  
 <span data-ttu-id="c70da-106">升级后，先前未用 DLL 名称的完整路径注册的扩展存储过程可能无法运行。</span><span class="sxs-lookup"><span data-stu-id="c70da-106">Extended stored procedures that were previously registered without the full path for the DLL name may not work after you upgrade.</span></span> <span data-ttu-id="c70da-107">这是因为在升级过程中未将旧的 BINN 目录添加到新路径中。</span><span class="sxs-lookup"><span data-stu-id="c70da-107">This is because the old BINN directory is not added to the new path during the upgrade process.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c70da-108">可能无法找到这些扩展存储过程。</span><span class="sxs-lookup"><span data-stu-id="c70da-108">may not be able to locate the extended stored procedures.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="c70da-109">纠正措施</span><span class="sxs-lookup"><span data-stu-id="c70da-109">Corrective Action</span></span>  
 <span data-ttu-id="c70da-110">升级之前，请对每个未使用完整路径名注册的扩展存储过程执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="c70da-110">Before you upgrade, follow these steps for each extended stored procedure that was not registered with a full path name:</span></span>  
  
1.  <span data-ttu-id="c70da-111">运行 sp_dropextendedproc 删除扩展存储过程。</span><span class="sxs-lookup"><span data-stu-id="c70da-111">Run sp_dropextendedproc to remove the extended stored procedure.</span></span>  
  
2.  <span data-ttu-id="c70da-112">运行 sp_addextendedproc，使用完整路径名注册扩展存储过程。</span><span class="sxs-lookup"><span data-stu-id="c70da-112">Run sp_addextendedproc to register the extended stored procedure with the full path name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c70da-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c70da-113">See Also</span></span>  
 <span data-ttu-id="c70da-114">[数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="c70da-114">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="c70da-115">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="c70da-115">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
