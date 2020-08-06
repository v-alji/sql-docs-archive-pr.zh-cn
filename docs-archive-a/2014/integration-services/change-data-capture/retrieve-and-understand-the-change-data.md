---
title: 检索和了解变更数据 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],retrieving data
ms.assetid: af366697-6942-42bb-aea5-18fdef018965
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 62f60bf4a79c39b4f0cb7d1ba8fb3f52680a1f11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691332"
---
# <a name="retrieve-and-understand-the-change-data"></a><span data-ttu-id="abea6-102">检索和了解变更数据</span><span class="sxs-lookup"><span data-stu-id="abea6-102">Retrieve and Understand the Change Data</span></span>
  <span data-ttu-id="abea6-103">在用于执行变更数据增量加载的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包的数据流中，第一个任务是运行查询以检索变更数据。</span><span class="sxs-lookup"><span data-stu-id="abea6-103">In the data flow of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that performs an incremental load of change data, the first task is to run the query that retrieves the change data.</span></span> <span data-ttu-id="abea6-104">在数据流任务中在源组件内执行此查询。</span><span class="sxs-lookup"><span data-stu-id="abea6-104">You execute this query inside a source component in a Data Flow task.</span></span> <span data-ttu-id="abea6-105">然后，使用下游转换和目标将变更数据应用到目标。</span><span class="sxs-lookup"><span data-stu-id="abea6-105">You can then use downstream transformations and destinations to apply the change data to your destination.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="abea6-106">在创建用于执行变更数据增量加载的包的过程中，第三步是创建包含表值函数的查询。</span><span class="sxs-lookup"><span data-stu-id="abea6-106">The creation of a query that contains a table-valued function is the third step in the process of creating a package that performs an incremental load of change data.</span></span> <span data-ttu-id="abea6-107">有关此查询的详细信息，请参阅 [创建函数以检索变更数据](create-the-function-to-retrieve-the-change-data.md)。</span><span class="sxs-lookup"><span data-stu-id="abea6-107">For more information about this query, see, [Create the Function to Retrieve the Change Data](create-the-function-to-retrieve-the-change-data.md).</span></span> <span data-ttu-id="abea6-108">有关创建用于执行变更数据增量加载的包的完整过程的说明，请参阅[变更数据捕获 (SSIS)](change-data-capture-ssis.md)。</span><span class="sxs-lookup"><span data-stu-id="abea6-108">For a description of the overall process for creating a package that performs an incremental load of change data, see [Change Data Capture &#40;SSIS&#41;](change-data-capture-ssis.md).</span></span>  
  
## <a name="adding-the-data-flow-task"></a><span data-ttu-id="abea6-109">添加数据流任务</span><span class="sxs-lookup"><span data-stu-id="abea6-109">Adding the Data Flow Task</span></span>  
 <span data-ttu-id="abea6-110">在包的数据流中，您将检索变更数据，根据所发生的变更的类型分隔行，然后将变更应用到目标。</span><span class="sxs-lookup"><span data-stu-id="abea6-110">In the data flow of the package, you retrieve the change data, separate the rows based on the type of change that occurred, and then apply the changes to the destination.</span></span>  
  
#### <a name="to-add-a-data-flow-task-to-the-package"></a><span data-ttu-id="abea6-111">向包添加数据流任务</span><span class="sxs-lookup"><span data-stu-id="abea6-111">To add a Data Flow task to the package</span></span>  
  
1.  <span data-ttu-id="abea6-112">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中的 **“控制流”** 选项卡上，添加数据流任务。</span><span class="sxs-lookup"><span data-stu-id="abea6-112">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], on the **Control Flow** tab, add a Data Flow task.</span></span>  
  
2.  <span data-ttu-id="abea6-113">将准备查询字符串的前一任务连接到数据流任务。</span><span class="sxs-lookup"><span data-stu-id="abea6-113">Connect the preceding task that prepared the query string to the Data Flow task.</span></span>  
  
## <a name="configuring-the-source-component-to-query-for-changes"></a><span data-ttu-id="abea6-114">配置源组件以查询变更</span><span class="sxs-lookup"><span data-stu-id="abea6-114">Configuring the Source Component to Query for Changes</span></span>  
 <span data-ttu-id="abea6-115">源组件使用已准备好并存储在变量中的查询字符串来调用用于检索已变更数据的表值函数。</span><span class="sxs-lookup"><span data-stu-id="abea6-115">The source component uses the query string that was prepared and stored in a variable to calls the table-valued function that retrieves the changed data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="abea6-116">有关已准备好并存储在变量中的查询字符串的详细信息，请参阅 [准备查询变更数据](prepare-to-query-for-the-change-data.md)。</span><span class="sxs-lookup"><span data-stu-id="abea6-116">For more information about the query string that was prepared and stored in a variable, see [Prepare to Query for the Change Data](prepare-to-query-for-the-change-data.md).</span></span> <span data-ttu-id="abea6-117">有关用于检索变更数据的表值函数的详细信息，请参阅 [创建函数以检索变更数据](create-the-function-to-retrieve-the-change-data.md)。</span><span class="sxs-lookup"><span data-stu-id="abea6-117">For more information about the table-valued function that retrieves the change data, see [Create the Function to Retrieve the Change Data](create-the-function-to-retrieve-the-change-data.md).</span></span>  
  
#### <a name="to-configure-an-ole-db-source-to-retrieve-the-change-data"></a><span data-ttu-id="abea6-118">配置 OLE DB 源以检索变更数据</span><span class="sxs-lookup"><span data-stu-id="abea6-118">To configure an OLE DB source to retrieve the change data</span></span>  
  
1.  <span data-ttu-id="abea6-119">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中的 **“数据流”** 选项卡上，添加 OLE DB 源。</span><span class="sxs-lookup"><span data-stu-id="abea6-119">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], on the **Data Flow** tab, add an OLE DB source.</span></span>  
  
2.  <span data-ttu-id="abea6-120">在 **“OLE DB 源编辑器”** 的 **“连接管理器”** 页上，选择下列选项：</span><span class="sxs-lookup"><span data-stu-id="abea6-120">In the **OLE DB Source Editor**, on the **Connection Manager** page, select the following options:</span></span>  
  
    1.  <span data-ttu-id="abea6-121">配置到源数据库的有效连接。</span><span class="sxs-lookup"><span data-stu-id="abea6-121">Configure a valid connection to the source database.</span></span>  
  
    2.  <span data-ttu-id="abea6-122">对于 **“数据访问模式”** ，选择 **“变量中的 SQL 命令”** 。</span><span class="sxs-lookup"><span data-stu-id="abea6-122">For **Data access mode**, select **SQL command from variable**.</span></span>  
  
    3.  <span data-ttu-id="abea6-123">对于 **“变量名称”** ，选择 **“User::SqlDataQuery”** 。</span><span class="sxs-lookup"><span data-stu-id="abea6-123">For **Variable name**, select **User::SqlDataQuery**.</span></span>  
  
3.  <span data-ttu-id="abea6-124">在 **“OLE DB 源编辑器”** 中的 **“列”** 页上，确保所需的所有列都映射到输出列。</span><span class="sxs-lookup"><span data-stu-id="abea6-124">In the **OLE DB Source Editor**, on the **Columns** page, make sure that all the columns that you want are mapped to output columns.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="abea6-125">下一步</span><span class="sxs-lookup"><span data-stu-id="abea6-125">Next Step</span></span>  
 <span data-ttu-id="abea6-126">在配置了用于检索变更数据的 OLE DB 源之后，下一步就是开始设计包中的数据流。</span><span class="sxs-lookup"><span data-stu-id="abea6-126">After you have configured an OLE DB source to retrieve the change data, the next step is to start designing the data flow in the package.</span></span>  
  
 <span data-ttu-id="abea6-127">**下一个主题：** [处理插入、更新和删除](process-inserts-updates-and-deletes.md)</span><span class="sxs-lookup"><span data-stu-id="abea6-127">**Next topic:** [Process Inserts, Updates, and Deletes](process-inserts-updates-and-deletes.md)</span></span>  
  
  
