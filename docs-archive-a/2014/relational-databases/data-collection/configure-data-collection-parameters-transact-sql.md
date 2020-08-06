---
title: 配置数据收集参数 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- data collection [SQL Server]
ms.assetid: 850905b6-35d2-4ed1-ab51-de64daa832b2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a8333b47612b4fbd933ef132e886b8125ffb58a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690649"
---
# <a name="configure-data-collection-parameters-transact-sql"></a><span data-ttu-id="a5b6a-102">配置数据收集参数 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a5b6a-102">Configure Data Collection Parameters (Transact-SQL)</span></span>
  <span data-ttu-id="a5b6a-103">在创建自定义收集组之前，必须首先配置数据收集参数。</span><span class="sxs-lookup"><span data-stu-id="a5b6a-103">Before you create a custom collection set, you must first configure data collection parameters.</span></span> <span data-ttu-id="a5b6a-104">使用随数据收集器一起提供的存储过程可实现这一操作。</span><span class="sxs-lookup"><span data-stu-id="a5b6a-104">You can do this by using the stored procedures that are provided with the data collector.</span></span> <span data-ttu-id="a5b6a-105">若要完成此任务，需使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的查询编辑器执行以下过程。</span><span class="sxs-lookup"><span data-stu-id="a5b6a-105">Accomplishing this task involves using Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to carry out the following procedure.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a5b6a-106">数据收集参数只需配置一次。</span><span class="sxs-lookup"><span data-stu-id="a5b6a-106">You only configure data collection parameters once.</span></span> <span data-ttu-id="a5b6a-107">完成配置后, 这些参数将用于您所创建的其他所有收集组。</span><span class="sxs-lookup"><span data-stu-id="a5b6a-107">After configuration, these parameters are used for any additional collection sets that you create.</span></span>  
  
### <a name="configure-data-collection-parameters"></a><span data-ttu-id="a5b6a-108">配置数据收集参数</span><span class="sxs-lookup"><span data-stu-id="a5b6a-108">Configure data collection parameters</span></span>  
  
1.  <span data-ttu-id="a5b6a-109">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，连接至要在其中创建自定义收集组的数据库。</span><span class="sxs-lookup"><span data-stu-id="a5b6a-109">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the database where you want to create a custom collection set.</span></span>  
  
2.  <span data-ttu-id="a5b6a-110">在查询编辑器中发出以下语句：</span><span class="sxs-lookup"><span data-stu-id="a5b6a-110">In Query Editor, issue the following statements.</span></span>  
  
    ```sql  
    USE msdb;  
    EXEC sp_syscollector_set_warehouse_instance_name N'INSTANCE_NAME';-- where instance name is the name of the SQL Server instance  
    EXEC sp_syscollector_set_warehouse_database_name N'MDW';  
    EXEC sp_syscollector_set_cache_directory N'D:\tempdata';  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a5b6a-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a5b6a-111">See Also</span></span>  
 <span data-ttu-id="a5b6a-112">[数据收集](data-collection.md) </span><span class="sxs-lookup"><span data-stu-id="a5b6a-112">[Data Collection](data-collection.md) </span></span>  
 [<span data-ttu-id="a5b6a-113">数据收集器存储过程 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a5b6a-113">Data Collector Stored Procedures &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql)  
  
  
