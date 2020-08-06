---
title: 将收集项添加到收集组中 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- collection items [SQL Server]
- collection sets [SQL Server], adding items
ms.assetid: 9fe6454e-8c0e-4b50-937b-d9871b20fd13
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0b21508761bdfbaf8918242b074f78203c1bcaed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591384"
---
# <a name="add-a-collection-item-to-a-collection-set-transact-sql"></a><span data-ttu-id="f1f27-102">将收集项添加到收集组中 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f1f27-102">Add a Collection Item to a Collection Set (Transact-SQL)</span></span>
  <span data-ttu-id="f1f27-103">可以使用随数据收集器一起提供的存储过程将收集项添加到现有收集组中。</span><span class="sxs-lookup"><span data-stu-id="f1f27-103">You can add a collection item to an existing collection set using the stored procedures that are provided with the data collector.</span></span>  
  
 <span data-ttu-id="f1f27-104">使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的查询编辑器执行以下步骤。</span><span class="sxs-lookup"><span data-stu-id="f1f27-104">Carry out the following steps using Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
### <a name="add-a-collection-item-to-a-collection-set"></a><span data-ttu-id="f1f27-105">将收集项添加到收集组中</span><span class="sxs-lookup"><span data-stu-id="f1f27-105">Add a collection item to a collection set</span></span>  
  
1.  <span data-ttu-id="f1f27-106">通过运行 **sp_syscollector_stop_collection_set** 存储过程停止要向其中添加收集项的收集组。</span><span class="sxs-lookup"><span data-stu-id="f1f27-106">Stop the collection set that you want to add the item to by running the **sp_syscollector_stop_collection_set** stored procedure.</span></span> <span data-ttu-id="f1f27-107">例如，若要停止名为“Test Collection Set”的收集组，请运行下列语句：</span><span class="sxs-lookup"><span data-stu-id="f1f27-107">For example, to stop a collection set that is named "Test Collection Set", run the following statements:</span></span>  
  
    ```sql  
    USE msdb  
    DECLARE @csid int  
    SELECT @csid = collection_set_id  
    FROM syscollector_collection_sets  
    WHERE name = 'Test Collection Set'  
    SELECT @csid  
    EXEC dbo.sp_syscollector_stop_collection_set @collection_set_id = @csid  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="f1f27-108">还可以通过使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的对象资源管理器来停止收集组。</span><span class="sxs-lookup"><span data-stu-id="f1f27-108">You can also stop the collection set by using Object Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="f1f27-109">有关详细信息，请参阅 [启动或停止收集组](start-or-stop-a-collection-set.md)。</span><span class="sxs-lookup"><span data-stu-id="f1f27-109">For more information, see [Start or Stop a Collection Set](start-or-stop-a-collection-set.md).</span></span>  
  
2.  <span data-ttu-id="f1f27-110">声明要向其中添加收集项的收集组。</span><span class="sxs-lookup"><span data-stu-id="f1f27-110">Declare the collection set that you want to add the collection item to.</span></span> <span data-ttu-id="f1f27-111">下面的代码提供了一个演示如何声明收集组 ID 的示例。</span><span class="sxs-lookup"><span data-stu-id="f1f27-111">The following code provides an example of how to declare the collection set ID.</span></span>  
  
    ```sql  
    DECLARE @collection_set_id_1 int  
    SELECT @collection_set_id_1 = collection_set_id FROM [msdb].[dbo].[syscollector_collection_sets]  
    WHERE name = N'Test Collection Set'; -- name of collection set  
    ```  
  
3.  <span data-ttu-id="f1f27-112">声明收集器类型。</span><span class="sxs-lookup"><span data-stu-id="f1f27-112">Declare the collector type.</span></span> <span data-ttu-id="f1f27-113">下面的代码提供了一个演示如何声明一般 T-SQL 查询收集器类型的示例。</span><span class="sxs-lookup"><span data-stu-id="f1f27-113">The following code provides an example of how to declare the Generic T-SQL Query collector type.</span></span>  
  
    ```sql  
    DECLARE @collector_type_uid_1 uniqueidentifier  
    SELECT @collector_type_uid_1 = collector_type_uid FROM [msdb].[dbo].[syscollector_collector_types]   
       WHERE name = N'Generic T-SQL Query Collector Type';  
    ```  
  
     <span data-ttu-id="f1f27-114">可以运行下面的代码以获取已安装收集器类型的列表：</span><span class="sxs-lookup"><span data-stu-id="f1f27-114">You can run the following code to obtain a list of the installed collector types:</span></span>  
  
    ```sql  
    USE msdb  
    SELECT * from syscollector_collector_types  
    GO  
    ```  
  
4.  <span data-ttu-id="f1f27-115">运行 **sp_syscollector_create_collection_item** 存储过程来创建收集项。</span><span class="sxs-lookup"><span data-stu-id="f1f27-115">Run the **sp_syscollector_create_collection_item** stored procedure to create the collection item.</span></span> <span data-ttu-id="f1f27-116">必须声明收集项的架构，以便它映射到所需收集器类型要求的架构。</span><span class="sxs-lookup"><span data-stu-id="f1f27-116">You must declare the schema for the collection item so that it maps to the required schema for the desired collector type.</span></span> <span data-ttu-id="f1f27-117">下面的示例使用一般 T-SQL 查询输入架构。</span><span class="sxs-lookup"><span data-stu-id="f1f27-117">The following example uses the Generic T-SQL Query input schema.</span></span>  
  
    ```sql  
    DECLARE @collection_item_id int;  
    EXEC [msdb].[dbo].[sp_syscollector_create_collection_item]   
    @name=N'OS Wait Stats', --name of collection item  
    @parameters=N'  
    <ns:TSQLQueryCollector xmlns:ns="DataCollectorType">  
     <Query>  
      <Value>select * from sys.dm_os_wait_stats</Value>  
      <OutputTable>os_wait_stats</OutputTable>  
    </Query>  
    </ns:TSQLQueryCollector>',  
    @collection_item_id = @collection_item_id OUTPUT,  
    @frequency = 60,  
    @collection_set_id = @collection_set_id_1, --- Provides the collection set ID number  
    @collector_type_uid = @collector_type_uid_1 -- Provides the collector type UID  
    SELECT @collection_item_id     
    ```  
  
5.  <span data-ttu-id="f1f27-118">在启动已更新的收集组之前，运行以下查询来验证新的收集项是否已创建：</span><span class="sxs-lookup"><span data-stu-id="f1f27-118">Before starting the updated collection set, run the following query to verify that the new collection item has been created:</span></span>  
  
    ```xaml  
    USE msdb  
    SELECT * from syscollector_collection_sets  
    SELECT * from syscollector_collection_items  
    GO  
    ```  
  
     <span data-ttu-id="f1f27-119">收集组和它们的收集项都显示在 **“结果”** 选项卡中。</span><span class="sxs-lookup"><span data-stu-id="f1f27-119">The collection sets and their collection items are displayed in the **Results** tab.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1f27-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f1f27-120">See Also</span></span>  
 <span data-ttu-id="f1f27-121">[创建使用一般 T-SQL 查询收集器类型的自定义收集组 (Transact-SQL)](create-custom-collection-set-generic-t-sql-query-collector-type.md) </span><span class="sxs-lookup"><span data-stu-id="f1f27-121">[Create a Custom Collection Set That Uses the Generic T-SQL Query Collector Type &#40;Transact-SQL&#41;](create-custom-collection-set-generic-t-sql-query-collector-type.md) </span></span>  
 [<span data-ttu-id="f1f27-122">数据收集器存储过程 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f1f27-122">Data Collector Stored Procedures &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql)  
  
  
