---
title: 更新 OPENXML XPath 表达式以删除不支持的函数 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- OPENXML queries
ms.assetid: b459abaf-8787-4b65-9231-ae30e5469fd0
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 2c64408d6d705654014b6d071012001374a5f486
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586127"
---
# <a name="update-openxml-xpath-expressions-to-remove-unsupported-functions"></a><span data-ttu-id="24e0c-102">更新 OPENXML XPath 表达式以删除不支持的函数</span><span class="sxs-lookup"><span data-stu-id="24e0c-102">Update OPENXML XPath expressions to remove unsupported functions</span></span>
  <span data-ttu-id="24e0c-103">升级顾问检测到使用了 XPath 功能。</span><span class="sxs-lookup"><span data-stu-id="24e0c-103">Upgrade Advisor detected the use of XPath functionality.</span></span> <span data-ttu-id="24e0c-104">升级后，对 OPENXML 功能的 XPath 功能所做的更改可能产生影响。</span><span class="sxs-lookup"><span data-stu-id="24e0c-104">You may be affected by changes in XPath functionality for OPENXML features after you upgrade.</span></span>  
  
## <a name="component"></a><span data-ttu-id="24e0c-105">组件</span><span class="sxs-lookup"><span data-stu-id="24e0c-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="24e0c-106">说明</span><span class="sxs-lookup"><span data-stu-id="24e0c-106">Description</span></span>  
 <span data-ttu-id="24e0c-107">MSXML 3.0 现为基础引擎，用于处理 OPENXML 查询中使用的 XPath 表达式。</span><span class="sxs-lookup"><span data-stu-id="24e0c-107">MSXML 3.0 is now the underlying engine that is used to process XPath expressions that are used within OPENXML queries.</span></span> <span data-ttu-id="24e0c-108">MSXML 3.0 的 XPath 1.0 引擎更为严格，且删除了对以下函数的支持：</span><span class="sxs-lookup"><span data-stu-id="24e0c-108">MSXML 3.0 has a stricter XPath 1.0 engine in which support for the following functions has been removed:</span></span>  
  
-   <span data-ttu-id="24e0c-109">format-number()</span><span class="sxs-lookup"><span data-stu-id="24e0c-109">format-number()</span></span>  
  
-   <span data-ttu-id="24e0c-110">formatNumber()</span><span class="sxs-lookup"><span data-stu-id="24e0c-110">formatNumber()</span></span>  
  
-   <span data-ttu-id="24e0c-111">current()</span><span class="sxs-lookup"><span data-stu-id="24e0c-111">current()</span></span>  
  
-   <span data-ttu-id="24e0c-112">element-available()</span><span class="sxs-lookup"><span data-stu-id="24e0c-112">element-available()</span></span>  
  
-   <span data-ttu-id="24e0c-113">function-available()</span><span class="sxs-lookup"><span data-stu-id="24e0c-113">function-available()</span></span>  
  
-   <span data-ttu-id="24e0c-114">system-property()</span><span class="sxs-lookup"><span data-stu-id="24e0c-114">system-property()</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="24e0c-115">纠正措施</span><span class="sxs-lookup"><span data-stu-id="24e0c-115">Corrective Action</span></span>  
 <span data-ttu-id="24e0c-116">对于 format-number() 和 formatNumber()，可以使用 [!INCLUDE[tsql](../../includes/tsql-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="24e0c-116">In the case of format-number() and formatNumber(), you can use [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="24e0c-117">对于前面列出的其他不支持的函数，没有直接的解决方法。</span><span class="sxs-lookup"><span data-stu-id="24e0c-117">For the other unsupported functions listed earlier, there is no direct workaround.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24e0c-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="24e0c-118">See Also</span></span>  
 <span data-ttu-id="24e0c-119">[数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="24e0c-119">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="24e0c-120">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="24e0c-120">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
