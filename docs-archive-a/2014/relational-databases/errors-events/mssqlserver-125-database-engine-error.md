---
title: MSSQLSERVER_125 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "125"
helpviewer_keywords:
- 125 (Database Engine error)
ms.assetid: 0f58338d-2ea0-48b8-8a20-c438b0940433
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 59c732d80ccfafc8f242bb1c42fe60e3dea81f19
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586744"
---
# <a name="mssqlserver_125"></a><span data-ttu-id="9aade-102">MSSQLSERVER_125</span><span class="sxs-lookup"><span data-stu-id="9aade-102">MSSQLSERVER_125</span></span>
    
## <a name="details"></a><span data-ttu-id="9aade-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="9aade-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9aade-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="9aade-104">Product Name</span></span>|<span data-ttu-id="9aade-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="9aade-105">SQL Server</span></span>|  
|<span data-ttu-id="9aade-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="9aade-106">Event ID</span></span>|<span data-ttu-id="9aade-107">125</span><span class="sxs-lookup"><span data-stu-id="9aade-107">125</span></span>|  
|<span data-ttu-id="9aade-108">事件源</span><span class="sxs-lookup"><span data-stu-id="9aade-108">Event Source</span></span>|<span data-ttu-id="9aade-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="9aade-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="9aade-110">组件</span><span class="sxs-lookup"><span data-stu-id="9aade-110">Component</span></span>|<span data-ttu-id="9aade-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="9aade-111">SQLEngine</span></span>|  
|<span data-ttu-id="9aade-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="9aade-112">Symbolic Name</span></span>||  
|<span data-ttu-id="9aade-113">消息正文</span><span class="sxs-lookup"><span data-stu-id="9aade-113">Message Text</span></span>|<span data-ttu-id="9aade-114">Case 表达式只能嵌套到 %d 层。</span><span class="sxs-lookup"><span data-stu-id="9aade-114">Case expressions may only be nested to level %d.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9aade-115">说明</span><span class="sxs-lookup"><span data-stu-id="9aade-115">Explanation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9aade-116">仅允许在 CASE 表达式中嵌套 10 个级别。</span><span class="sxs-lookup"><span data-stu-id="9aade-116">allows for only 10 levels of nesting in CASE expressions.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9aade-117">用户操作</span><span class="sxs-lookup"><span data-stu-id="9aade-117">User Action</span></span>  
 <span data-ttu-id="9aade-118">将 CASE 语句的级别减少到 10 级或更低的级数。</span><span class="sxs-lookup"><span data-stu-id="9aade-118">Reduce the level of CASE statements to 10 or less.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9aade-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9aade-119">See Also</span></span>  
 [<span data-ttu-id="9aade-120">CASE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9aade-120">CASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/case-transact-sql)  
  
  
