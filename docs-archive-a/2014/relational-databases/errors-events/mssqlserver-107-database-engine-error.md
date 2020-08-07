---
title: MSSQLSERVER_107 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 107 (Database Engine error)
ms.assetid: f33f514c-56aa-42e2-841b-e91244da90e2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b9388bbda6f00b1aafd02caee1b6a7b8387564f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589143"
---
# <a name="mssqlserver_107"></a><span data-ttu-id="d97ad-102">MSSQLSERVER_107</span><span class="sxs-lookup"><span data-stu-id="d97ad-102">MSSQLSERVER_107</span></span>
    
## <a name="details"></a><span data-ttu-id="d97ad-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="d97ad-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d97ad-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="d97ad-104">Product Name</span></span>|<span data-ttu-id="d97ad-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d97ad-105">SQL Server</span></span>|  
|<span data-ttu-id="d97ad-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="d97ad-106">Event ID</span></span>|<span data-ttu-id="d97ad-107">107</span><span class="sxs-lookup"><span data-stu-id="d97ad-107">107</span></span>|  
|<span data-ttu-id="d97ad-108">事件源</span><span class="sxs-lookup"><span data-stu-id="d97ad-108">Event Source</span></span>|<span data-ttu-id="d97ad-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d97ad-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d97ad-110">组件</span><span class="sxs-lookup"><span data-stu-id="d97ad-110">Component</span></span>|<span data-ttu-id="d97ad-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="d97ad-111">SQLEngine</span></span>|  
|<span data-ttu-id="d97ad-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="d97ad-112">Symbolic Name</span></span>|<span data-ttu-id="d97ad-113">P_NOCORRMATCH</span><span class="sxs-lookup"><span data-stu-id="d97ad-113">P_NOCORRMATCH</span></span>|  
|<span data-ttu-id="d97ad-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="d97ad-114">Message Text</span></span>|<span data-ttu-id="d97ad-115">列前缀 '%.\*ls' 与查询中使用的表名或别名不匹配。</span><span class="sxs-lookup"><span data-stu-id="d97ad-115">The column prefix '%.\*ls' does not match with a table name or alias name used in the query.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d97ad-116">说明</span><span class="sxs-lookup"><span data-stu-id="d97ad-116">Explanation</span></span>  
 <span data-ttu-id="d97ad-117">用列前缀错误地对该查询的 Select 列表中包含的星号 (\*) 进行了限定。</span><span class="sxs-lookup"><span data-stu-id="d97ad-117">The select list of the query contains an asterisk (\*) that is incorrectly qualified with a column prefix.</span></span> <span data-ttu-id="d97ad-118">在以下情况下可能会返回此错误：</span><span class="sxs-lookup"><span data-stu-id="d97ad-118">This error can be returned under the following conditions:</span></span>  
  
-   <span data-ttu-id="d97ad-119">列前缀与查询中使用的表名或别名不对应。</span><span class="sxs-lookup"><span data-stu-id="d97ad-119">The column prefix does not correspond to any table or alias name used in the query.</span></span> <span data-ttu-id="d97ad-120">例如，下面的语句使用别名 (`T1`) 作为列前缀，但是该别名未在 FROM 子句中定义。</span><span class="sxs-lookup"><span data-stu-id="d97ad-120">For example, the following statement uses an alias name (`T1`) as a column prefix, but the alias is not defined in the FROM clause.</span></span>  
  
    ```  
    SELECT T1.* FROM dbo.ErrorLog;  
    ```  
  
-   <span data-ttu-id="d97ad-121">将表名指定为列前缀，但是在 FROM 子句中提供的是表的别名。</span><span class="sxs-lookup"><span data-stu-id="d97ad-121">A table name is specified as a column prefix when an alias name for the table is supplied in the FROM clause.</span></span> <span data-ttu-id="d97ad-122">例如，下面的语句使用表名 `ErrorLog` 作为列前缀；但是，在该表的 FROM 子句中定义的是别名 (`T1`)。</span><span class="sxs-lookup"><span data-stu-id="d97ad-122">For example, the following statement uses the table name `ErrorLog` as the column prefix; however, the table has an alias (`T1`) defined in the FROM clause.</span></span>  
  
    ```  
    SELECT ErrorLog.* FROM dbo.ErrorLog AS T1;  
    ```  
  
     <span data-ttu-id="d97ad-123">如果已经在 FROM 子句中提供了表的别名，则只能使用该别名作为表列的前缀。</span><span class="sxs-lookup"><span data-stu-id="d97ad-123">If an alias has been provided for a table name in the FROM clause, you can only use the alias to prefix columns from the table.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d97ad-124">用户操作</span><span class="sxs-lookup"><span data-stu-id="d97ad-124">User Action</span></span>  
 <span data-ttu-id="d97ad-125">使列前缀与在查询的 FROM 子句中指定的表名或别名相匹配。</span><span class="sxs-lookup"><span data-stu-id="d97ad-125">Match the column prefixes against the table names or alias names specified in the FROM clause of the query.</span></span> <span data-ttu-id="d97ad-126">例如，可按如下方式更正上面的语句：</span><span class="sxs-lookup"><span data-stu-id="d97ad-126">For example, the statements above can be corrected as follows:</span></span>  
  
```  
SELECT T1.* FROM dbo.ErrorLog AS T1;  
```  
  
 <span data-ttu-id="d97ad-127">或</span><span class="sxs-lookup"><span data-stu-id="d97ad-127">or</span></span>  
  
```  
SELECT ErrorLog.* FROM dbo.ErrorLog;  
```  
  
## <a name="see-also"></a><span data-ttu-id="d97ad-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d97ad-128">See Also</span></span>  
 [<span data-ttu-id="d97ad-129">MSSQLSERVER_4104</span><span class="sxs-lookup"><span data-stu-id="d97ad-129">MSSQLSERVER_4104</span></span>](mssqlserver-4104-database-engine-error.md)  
  
  
