---
title: MSSQLSERVER_2570 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2570 (Database Engine error)
ms.assetid: 29800aa9-81aa-4371-992c-487dbb617f46
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 79137d0f70c05c6aa7b758f7e073d152681a14b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687911"
---
# <a name="mssqlserver_2570"></a><span data-ttu-id="3cb79-102">MSSQLSERVER_2570</span><span class="sxs-lookup"><span data-stu-id="3cb79-102">MSSQLSERVER_2570</span></span>
    
## <a name="details"></a><span data-ttu-id="3cb79-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="3cb79-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3cb79-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="3cb79-104">Product Name</span></span>|<span data-ttu-id="3cb79-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="3cb79-105">SQL Server</span></span>|  
|<span data-ttu-id="3cb79-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="3cb79-106">Event ID</span></span>|<span data-ttu-id="3cb79-107">2570</span><span class="sxs-lookup"><span data-stu-id="3cb79-107">2570</span></span>|  
|<span data-ttu-id="3cb79-108">事件源</span><span class="sxs-lookup"><span data-stu-id="3cb79-108">Event Source</span></span>|<span data-ttu-id="3cb79-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="3cb79-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="3cb79-110">组件</span><span class="sxs-lookup"><span data-stu-id="3cb79-110">Component</span></span>|<span data-ttu-id="3cb79-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="3cb79-111">SQLEngine</span></span>|  
|<span data-ttu-id="3cb79-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="3cb79-112">Symbolic Name</span></span>|<span data-ttu-id="3cb79-113">DBCC_COLUMN_VALUE_OUT_OF_RANGE</span><span class="sxs-lookup"><span data-stu-id="3cb79-113">DBCC_COLUMN_VALUE_OUT_OF_RANGE</span></span>|  
|<span data-ttu-id="3cb79-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="3cb79-114">Message Text</span></span>|<span data-ttu-id="3cb79-115">页 P_ID，槽 S_ID 位于对象 ID O_ID，索引 ID I_ID，分区 ID PN_ID，分配单元 ID A_ID (类型为 "TYPE")中。</span><span class="sxs-lookup"><span data-stu-id="3cb79-115">Page P_ID, slot S_ID in object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE).</span></span> <span data-ttu-id="3cb79-116">列 "COLUMN_NAME" 的值超出了数据类型 "DATATYPE" 的范围。</span><span class="sxs-lookup"><span data-stu-id="3cb79-116">Column COLUMN_NAME value is out of range for data type "DATATYPE".</span></span> <span data-ttu-id="3cb79-117">请将该列更新为合法的值。</span><span class="sxs-lookup"><span data-stu-id="3cb79-117">Update column to a legal value.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3cb79-118">说明</span><span class="sxs-lookup"><span data-stu-id="3cb79-118">Explanation</span></span>  
 <span data-ttu-id="3cb79-119">指定列中包含的列值超出了列数据类型可能的值范围。</span><span class="sxs-lookup"><span data-stu-id="3cb79-119">The column value that is contained in the specified column is outside the range of possible values for the column data type.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3cb79-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="3cb79-120">User Action</span></span>  
 <span data-ttu-id="3cb79-121">该错误不可修复。</span><span class="sxs-lookup"><span data-stu-id="3cb79-121">The error is not repairable.</span></span> <span data-ttu-id="3cb79-122">将该列更新为列的数据类型范围内的值并再次运行该命令。</span><span class="sxs-lookup"><span data-stu-id="3cb79-122">Update the column to a value within the range for the data type of the column and run the command again.</span></span>  <span data-ttu-id="3cb79-123">有关详细信息，请参阅此知识库文章 [923247](https://support.microsoft.com/kb/923247)。</span><span class="sxs-lookup"><span data-stu-id="3cb79-123">For more information, see this KB article [923247](https://support.microsoft.com/kb/923247).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cb79-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3cb79-124">See Also</span></span>  
 <span data-ttu-id="3cb79-125">[UPDATE (Transact-SQL)](/sql/t-sql/queries/update-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3cb79-125">[UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql) </span></span>  
 [<span data-ttu-id="3cb79-126">数据类型 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="3cb79-126">Data Types &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/data-types-transact-sql)  
  
  
