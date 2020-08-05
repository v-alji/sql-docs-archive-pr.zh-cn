---
title: MSSQLSERVER_5242 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5242 (Database Engine error)
ms.assetid: 712b1a10-2f87-41df-a111-1ed9f14102d4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c979d0a788e80cf5c7e1ab9b9a1ca8eccc0eea19
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581248"
---
# <a name="mssqlserver_5242"></a><span data-ttu-id="8db13-102">MSSQLSERVER_5242</span><span class="sxs-lookup"><span data-stu-id="8db13-102">MSSQLSERVER_5242</span></span>
    
## <a name="details"></a><span data-ttu-id="8db13-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="8db13-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8db13-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="8db13-104">Product Name</span></span>|<span data-ttu-id="8db13-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8db13-105">SQL Server</span></span>|  
|<span data-ttu-id="8db13-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="8db13-106">Event ID</span></span>|<span data-ttu-id="8db13-107">5242</span><span class="sxs-lookup"><span data-stu-id="8db13-107">5242</span></span>|  
|<span data-ttu-id="8db13-108">事件源</span><span class="sxs-lookup"><span data-stu-id="8db13-108">Event Source</span></span>|<span data-ttu-id="8db13-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8db13-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8db13-110">组件</span><span class="sxs-lookup"><span data-stu-id="8db13-110">Component</span></span>|<span data-ttu-id="8db13-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="8db13-111">SQLEngine</span></span>|  
|<span data-ttu-id="8db13-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="8db13-112">Symbolic Name</span></span>||  
|<span data-ttu-id="8db13-113">消息正文</span><span class="sxs-lookup"><span data-stu-id="8db13-113">Message Text</span></span>|<span data-ttu-id="8db13-114">在数据库 '%.\*ls'(ID:%d) 中对页 %S_PGID 执行内部操作期间检测到不一致性。</span><span class="sxs-lookup"><span data-stu-id="8db13-114">An inconsistency was detected during an internal operation in database '%.\*ls'(ID:%d) on page %S_PGID.</span></span> <span data-ttu-id="8db13-115">请与技术支持联系。</span><span class="sxs-lookup"><span data-stu-id="8db13-115">Please contact technical support.</span></span> <span data-ttu-id="8db13-116">参考号为 %ld。</span><span class="sxs-lookup"><span data-stu-id="8db13-116">Reference number %ld.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8db13-117">说明</span><span class="sxs-lookup"><span data-stu-id="8db13-117">Explanation</span></span>  
 <span data-ttu-id="8db13-118">在错误消息中引用的数据库页上出现结构不一致性。</span><span class="sxs-lookup"><span data-stu-id="8db13-118">A structural inconsistency occurred on the database page that is referenced in the error message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8db13-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8db13-119">See Also</span></span>  
 <span data-ttu-id="8db13-120">[DBCC CHECKDB &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8db13-120">[DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) </span></span>  
 [<span data-ttu-id="8db13-121">数据库文件和文件组</span><span class="sxs-lookup"><span data-stu-id="8db13-121">Database Files and Filegroups</span></span>](../databases/database-files-and-filegroups.md)  
  
  
