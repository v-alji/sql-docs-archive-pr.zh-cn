---
title: MSSQLSERVER_1793 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
ms.assetid: 808db1d0-acc1-41d0-9287-8a5455001a02
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 54172adb957c3cbc1dbc221d1cae2a583830a1cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689408"
---
# <a name="mssqlserver_1793"></a><span data-ttu-id="f45bc-102">MSSQLSERVER_1793</span><span class="sxs-lookup"><span data-stu-id="f45bc-102">MSSQLSERVER_1793</span></span>
    
## <a name="details"></a><span data-ttu-id="f45bc-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="f45bc-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f45bc-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="f45bc-104">Product Name</span></span>|<span data-ttu-id="f45bc-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="f45bc-105">SQL Server</span></span>|  
|<span data-ttu-id="f45bc-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="f45bc-106">Event ID</span></span>|<span data-ttu-id="f45bc-107">1793</span><span class="sxs-lookup"><span data-stu-id="f45bc-107">1793</span></span>|  
|<span data-ttu-id="f45bc-108">事件源</span><span class="sxs-lookup"><span data-stu-id="f45bc-108">Event Source</span></span>|<span data-ttu-id="f45bc-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f45bc-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f45bc-110">组件</span><span class="sxs-lookup"><span data-stu-id="f45bc-110">Component</span></span>|<span data-ttu-id="f45bc-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="f45bc-111">SQLEngine</span></span>|  
|<span data-ttu-id="f45bc-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="f45bc-112">Symbolic Name</span></span>|<span data-ttu-id="f45bc-113">FILESTREAM_BASEDATA_NEED_SAME_PARTITION</span><span class="sxs-lookup"><span data-stu-id="f45bc-113">FILESTREAM_BASEDATA_NEED_SAME_PARTITION</span></span>|  
|<span data-ttu-id="f45bc-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="f45bc-114">Message Text</span></span>|<span data-ttu-id="f45bc-115">由于没有为 FILESTREAM 数据指定分区方案，因此无法删除索引“%.\*ls”。</span><span class="sxs-lookup"><span data-stu-id="f45bc-115">Cannot drop index '%.\*ls' since a partition scheme is not specified for FILESTREAM data.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f45bc-116">说明</span><span class="sxs-lookup"><span data-stu-id="f45bc-116">Explanation</span></span>  
 <span data-ttu-id="f45bc-117">当你尝试在包含 FILESTREAM 数据的表上删除聚集索引，并且为基础数据指定了 **MOVE TO** 子句，但没有为 FILESTREAM 数据指定 **FILESTREAM_ON** 子句时，将出现此消息。</span><span class="sxs-lookup"><span data-stu-id="f45bc-117">This message occurs when you try to drop a clustered index on a table that contains FILESTREAM data, and you specify a **MOVE TO** clause for the base data, but you do not specify a **FILESTREAM_ON** clause for the FILESTREAM data.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f45bc-118">用户操作</span><span class="sxs-lookup"><span data-stu-id="f45bc-118">User Action</span></span>  
 <span data-ttu-id="f45bc-119">在删除包含 FILESTREAM 数据的表上的聚集索引时，使用下列选项之一：</span><span class="sxs-lookup"><span data-stu-id="f45bc-119">When dropping a clustered index on a table that contains FILESTREAM data, use one of the following options:</span></span>  
  
-   <span data-ttu-id="f45bc-120">为基础数据指定 **MOVE TO** 子句并且为 FILESTREAM 数据指定 **FILESTREAM_ON** 子句。</span><span class="sxs-lookup"><span data-stu-id="f45bc-120">Specify both a **MOVE TO** clause for the base data and a **FILESTREAM_ON** clause for the FILESTREAM data.</span></span>  
  
-   <span data-ttu-id="f45bc-121">不为基础数据指定 **MOVE TO** 子句，也不为 FILESTREAM 数据指定 **FILESTREAM_ON** 子句。</span><span class="sxs-lookup"><span data-stu-id="f45bc-121">Do not specify either a **MOVE TO** clause for the base data or a **FILESTREAM_ON** clause for the FILESTREAM data.</span></span>  
  
 <span data-ttu-id="f45bc-122">下面的示例失败，因为为基础数据指定了分区方案，但没有为 FILESTREAM 数据指定。</span><span class="sxs-lookup"><span data-stu-id="f45bc-122">The following example fails because a partition scheme is specified for the base data, but is not specified for the FILESTREAM data.</span></span>  
  
```sql  
DROP INDEX [<clustered_index_name>] ON [<table_name>]   
WITH ( ONLINE = OFF, MOVE TO [PRIMARY] )  
GO  
```  
  
 <span data-ttu-id="f45bc-123">下面的示例成功，因为既为基础数据指定了 **MOVE TO** 子句，又为 FILESTREAM 数据指定了 **FILESTREAM_ON** 子句。</span><span class="sxs-lookup"><span data-stu-id="f45bc-123">The following example succeeds because both a **MOVE TO** clause for the base data and a **FILESTREAM_ON** clause for the FILESTREAM data are specified.</span></span>  
  
```sql  
DROP INDEX [<clustered_index_name>] ON [<table_name>]   
WITH ( ONLINE = OFF, MOVE TO [PRIMARY], filestream_on 'default' )  
GO  
```  
  
 <span data-ttu-id="f45bc-124">下面的示例也成功，因为既没有为基础数据指定 **MOVE TO** 子句，也没有为 FILESTREAM 数据指定 **FILESTREAM_ON** 子句。</span><span class="sxs-lookup"><span data-stu-id="f45bc-124">The following example also succeeds because neither a **MOVE TO** clause for the base data nor a **FILESTREAM_ON** clause for the FILESTREAM data is specified.</span></span>  
  
```sql  
DROP INDEX [<clustered_index_name>] ON [<table_name>]   
WITH ( ONLINE = OFF )  
GO  
```  
  
  
