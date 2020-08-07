---
title: 升级后，新的保留关键字不能用作标识符 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- keywords [SQL Server], after upgrade
- keywords [SQL Server], reserved
- keywords [SQL Server]
ms.assetid: cb242081-54f8-4273-a8ef-52f3751c25ef
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 36f7f8cadcba5e114feee4a3c42de6f40070ce72
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586236"
---
# <a name="after-upgrade-new-reserved-keywords-cannot-be-used-as-identifiers"></a><span data-ttu-id="2f9a1-102">升级后，新的保留关键字不能用作标识符</span><span class="sxs-lookup"><span data-stu-id="2f9a1-102">After upgrade, new reserved keywords cannot be used as identifiers</span></span>
  <span data-ttu-id="2f9a1-103">升级顾问检测到所使用的某些词为保留关键字。</span><span class="sxs-lookup"><span data-stu-id="2f9a1-103">Upgrade Advisor detected the use of words that are reserved keywords.</span></span> <span data-ttu-id="2f9a1-104">保留关键字不能用作标识符或对象名称，除非该名称用分隔符分割。</span><span class="sxs-lookup"><span data-stu-id="2f9a1-104">A reserved keyword cannot be used as an identifier or object name unless the name is delimited.</span></span>  
  
## <a name="component"></a><span data-ttu-id="2f9a1-105">组件</span><span class="sxs-lookup"><span data-stu-id="2f9a1-105">Component</span></span>  
 <span data-ttu-id="2f9a1-106">数据库引擎</span><span class="sxs-lookup"><span data-stu-id="2f9a1-106">Database Engine</span></span>  
  
## <a name="description"></a><span data-ttu-id="2f9a1-107">说明</span><span class="sxs-lookup"><span data-stu-id="2f9a1-107">Description</span></span>  
 <span data-ttu-id="2f9a1-108">在兼容级别 90 或更低级别中，以下词不是保留关键字，因此可以在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本中用作标识符或对象名称。</span><span class="sxs-lookup"><span data-stu-id="2f9a1-108">At compatibility level 90 or lower, the following words are not reserved keywords and can be used as identifiers or object names in [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts.</span></span> <span data-ttu-id="2f9a1-109">在兼容级别 100 中，以下词是完全保留的关键字，因此不应用作标识符或对象名称。</span><span class="sxs-lookup"><span data-stu-id="2f9a1-109">At compatibility level 100, these words are fully reserved keywords and should not be used as identifiers or object names.</span></span>  
  
-   <span data-ttu-id="2f9a1-110">EXTERNAL</span><span class="sxs-lookup"><span data-stu-id="2f9a1-110">EXTERNAL</span></span>  
  
-   <span data-ttu-id="2f9a1-111">MERGE</span><span class="sxs-lookup"><span data-stu-id="2f9a1-111">MERGE</span></span>  
  
-   <span data-ttu-id="2f9a1-112">PIVOT</span><span class="sxs-lookup"><span data-stu-id="2f9a1-112">PIVOT</span></span>  
  
-   <span data-ttu-id="2f9a1-113">REVERT</span><span class="sxs-lookup"><span data-stu-id="2f9a1-113">REVERT</span></span>  
  
-   <span data-ttu-id="2f9a1-114">STOPLIST</span><span class="sxs-lookup"><span data-stu-id="2f9a1-114">STOPLIST</span></span>  
  
-   <span data-ttu-id="2f9a1-115">TABLESAMPLE</span><span class="sxs-lookup"><span data-stu-id="2f9a1-115">TABLESAMPLE</span></span>  
  
-   <span data-ttu-id="2f9a1-116">UNPIVOT</span><span class="sxs-lookup"><span data-stu-id="2f9a1-116">UNPIVOT</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="2f9a1-117">纠正措施</span><span class="sxs-lookup"><span data-stu-id="2f9a1-117">Corrective Action</span></span>  
 <span data-ttu-id="2f9a1-118">建议您重命名该对象。</span><span class="sxs-lookup"><span data-stu-id="2f9a1-118">We recommend that you rename the object.</span></span> <span data-ttu-id="2f9a1-119">如果无法在升级前执行此操作，请使用下列方法之一，直到可以更改该名称为止：</span><span class="sxs-lookup"><span data-stu-id="2f9a1-119">If that cannot be done before upgrading, use one of the following methods until the name can be changed:</span></span>  
  
-   <span data-ttu-id="2f9a1-120">将数据库兼容级别设置保留为 90 或更低。</span><span class="sxs-lookup"><span data-stu-id="2f9a1-120">Retain the database compatibility level setting of 90 or lower.</span></span>  
  
-   <span data-ttu-id="2f9a1-121">使用分隔标识符引用对象。</span><span class="sxs-lookup"><span data-stu-id="2f9a1-121">Refer to the object by using delimited identifiers.</span></span> <span data-ttu-id="2f9a1-122">例如，语句 `CREATE TABLE [MERGE] ([MERGE] int);` 使用方括号分隔对象名称合并。</span><span class="sxs-lookup"><span data-stu-id="2f9a1-122">For example, the statement `CREATE TABLE [MERGE] ([MERGE] int);` uses brackets to delimit the object name MERGE.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="2f9a1-123">外部资源</span><span class="sxs-lookup"><span data-stu-id="2f9a1-123">External Resources</span></span>  
 [<span data-ttu-id="2f9a1-124">保留关键字 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="2f9a1-124">Reserved Keywords &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/reserved-keywords-transact-sql)  
  
 [<span data-ttu-id="2f9a1-125">MERGE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="2f9a1-125">MERGE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/merge-transact-sql)  
  
 [<span data-ttu-id="2f9a1-126">分隔标识符（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="2f9a1-126">Delimited Identifiers (Database Engine)</span></span>](https://go.microsoft.com/fwlink/?LinkId=112509)  
  
 [<span data-ttu-id="2f9a1-127">ALTER DATABASE 兼容级别 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="2f9a1-127">ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)  
  
  
