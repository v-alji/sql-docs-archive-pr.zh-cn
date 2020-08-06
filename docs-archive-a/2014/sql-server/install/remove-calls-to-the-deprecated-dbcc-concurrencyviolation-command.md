---
title: 删除对不推荐使用的 DBCC CONCURRENCYVIOLATION 命令的调用 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 2cc9f6ff-de36-4e94-bd04-59f5c45c4911
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: cde04ebfc2ea9996d1c9ed233123e5b66f6e81fa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692127"
---
# <a name="remove-calls-to-the-deprecated-dbcc-concurrencyviolation-command"></a><span data-ttu-id="6aa71-102">删除对不推荐使用的 DBCC CONCURRENCYVIOLATION 命令的调用</span><span class="sxs-lookup"><span data-stu-id="6aa71-102">Remove calls to the deprecated DBCC CONCURRENCYVIOLATION command</span></span>
  <span data-ttu-id="6aa71-103">升级顾问检测到使用了 DBCC CONCURRENCYVIOLATION 命令。</span><span class="sxs-lookup"><span data-stu-id="6aa71-103">Upgrade Advisor detected the use of the DBCC CONCURRENCYVIOLATION command.</span></span> <span data-ttu-id="6aa71-104">此命令不再可用。</span><span class="sxs-lookup"><span data-stu-id="6aa71-104">This command is no longer available.</span></span> <span data-ttu-id="6aa71-105">执行此命令返回错误 2526。</span><span class="sxs-lookup"><span data-stu-id="6aa71-105">Executing this command returns error 2526.</span></span>  
  
## <a name="component"></a><span data-ttu-id="6aa71-106">组件</span><span class="sxs-lookup"><span data-stu-id="6aa71-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="6aa71-107">说明</span><span class="sxs-lookup"><span data-stu-id="6aa71-107">Description</span></span>  
 <span data-ttu-id="6aa71-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 没有任何最近版本包括工作负荷调控器；因此该命令已被删除。</span><span class="sxs-lookup"><span data-stu-id="6aa71-108">No recent version of edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] includes a workload governor; therefore the command has been removed.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="6aa71-109">纠正措施</span><span class="sxs-lookup"><span data-stu-id="6aa71-109">Corrective Action</span></span>  
 <span data-ttu-id="6aa71-110">更新应用程序和脚本以删除对这一不推荐使用的命令的引用。</span><span class="sxs-lookup"><span data-stu-id="6aa71-110">Update applications and scripts to remove references to this deprecated command.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="6aa71-111">外部资源</span><span class="sxs-lookup"><span data-stu-id="6aa71-111">External Resources</span></span>  
  
