---
title: 使用 SQL Server 目标大容量加载数据 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server destination
- loading data
- destinations [Integration Services], SQL Server
- inserting data
- bulk load [Integration Services]
ms.assetid: 8f982f85-a82e-4e2d-9cd8-cd2f85402d8e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 92ed530ae849f7a4ce123cded421ac0cd0c411ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585916"
---
# <a name="bulk-load-data-by-using-the-sql-server-destination"></a><span data-ttu-id="a7b34-102">使用 SQL Server 目标大容量加载数据</span><span class="sxs-lookup"><span data-stu-id="a7b34-102">Bulk Load Data by Using the SQL Server Destination</span></span>
  <span data-ttu-id="a7b34-103">若要添加并配置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目标，则包必须已包含至少一个数据流任务和一个数据源。</span><span class="sxs-lookup"><span data-stu-id="a7b34-103">To add and configure a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, the package must already include at least one Data Flow task and a data source.</span></span>  
  
### <a name="to-load-data-using-a-sql-server-destination"></a><span data-ttu-id="a7b34-104">使用 SQL Server 目标加载数据</span><span class="sxs-lookup"><span data-stu-id="a7b34-104">To load data using a SQL Server destination</span></span>  
  
1.  <span data-ttu-id="a7b34-105">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="a7b34-105">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="a7b34-106">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="a7b34-106">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="a7b34-107">单击 **“数据流”** 选项卡，再将 **目标从**“工具箱” [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 拖动到设计图面。</span><span class="sxs-lookup"><span data-stu-id="a7b34-107">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination to the design surface.</span></span>  
  
4.  <span data-ttu-id="a7b34-108">将连接线拖到目标，从而将目标连接到数据流中的源或前一转换。</span><span class="sxs-lookup"><span data-stu-id="a7b34-108">Connect the destination to a source or a previous transformation in the data flow by dragging a connector to the destination.</span></span>  
  
5.  <span data-ttu-id="a7b34-109">双击此目标。</span><span class="sxs-lookup"><span data-stu-id="a7b34-109">Double-click the destination.</span></span>  
  
6.  <span data-ttu-id="a7b34-110">在 **“SQL Server 目标编辑器”** 中的 **“连接管理器”** 页上，选择一个现有的 OLE DB 连接管理器或单击 **“新建”** 创建新的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="a7b34-110">In the **SQL Server Destination Editor**, on the **Connection Manager** page, select an existing OLE DB connection manager or click **New** to create a new connection manager.</span></span> <span data-ttu-id="a7b34-111">有关详细信息，请参阅 [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="a7b34-111">For more information, see [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md).</span></span>  
  
7.  <span data-ttu-id="a7b34-112">若要指定把数据加载到其中的表或视图，请执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="a7b34-112">To specify the table or view into which to load the data, do one of the following:</span></span>  
  
    -   <span data-ttu-id="a7b34-113">选择一个现有的表或视图。</span><span class="sxs-lookup"><span data-stu-id="a7b34-113">Select an existing table or view.</span></span>  
  
    -   <span data-ttu-id="a7b34-114">单击“新建”  ，并在“创建表”  对话框中写入创建表或视图的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="a7b34-114">Click **New**, and in the **Create Table** dialog boxwrite an SQL statement that creates a table or view.</span></span>  
  
        > [!NOTE]  
        >  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="a7b34-115">将基于连接数据源生成一个默认的 CREATE TABLE 语句。</span><span class="sxs-lookup"><span data-stu-id="a7b34-115">generates a default CREATE TABLE statement based on the connected data source.</span></span> <span data-ttu-id="a7b34-116">即使源表包含一个已声明了 FILESTREAM 属性的列，此默认 CREATE TABLE 语句也不会包含 FILESTREAM 属性。</span><span class="sxs-lookup"><span data-stu-id="a7b34-116">This default CREATE TABLE statement will not include the FILESTREAM attribute even if the source table includes a column with the FILESTREAM attribute declared.</span></span> <span data-ttu-id="a7b34-117">若要运行具有 FILESTREAM 属性的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 组件，首先要在目标数据库上实现 FILESTREAM 存储。</span><span class="sxs-lookup"><span data-stu-id="a7b34-117">To run an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] component with the FILESTREAM attribute, first implement FILESTREAM storage on the destination database.</span></span> <span data-ttu-id="a7b34-118">然后在 **“创建表”** 对话框中将 FILESTREAM 属性添加到 CREATE TABLE 语句中。</span><span class="sxs-lookup"><span data-stu-id="a7b34-118">Then, add the FILESTREAM attribute to the CREATE TABLE statement in the **Create Table** dialog box.</span></span> <span data-ttu-id="a7b34-119">有关详细信息，请参阅[二进制大型对象 (Blob) 数据 (SQL Server)](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="a7b34-119">For more information, see [Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md).</span></span>  
  
8.  <span data-ttu-id="a7b34-120">单击 **“映射”** ，并将列从一个列表拖动到另一个列表，从而将 **“可用输入列”** 列表中的列映射到 **“可用目标列”** 列表中的列。</span><span class="sxs-lookup"><span data-stu-id="a7b34-120">Click **Mappings** and map columns from the **Available Input Columns** list to columns in the **Available Destination Columns** list by dragging columns from one list to another.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a7b34-121">目标自动映射名称相同的列。</span><span class="sxs-lookup"><span data-stu-id="a7b34-121">The destination automatically maps same-named columns.</span></span>  
  
9. <span data-ttu-id="a7b34-122">单击 **“高级”** ，并设置大容量加载选项： **“保留标识”** 、 **“保留空值”** 、 **“表锁”** 、 **“检查约束”** 和 **“激发触发器”** 。</span><span class="sxs-lookup"><span data-stu-id="a7b34-122">Click **Advanced** and set the bulk load options: **Keep identity**, **Keep nulls**, **Table lock**, **Check constraints**, and **Fire triggers**.</span></span>  
  
     <span data-ttu-id="a7b34-123">也可以指定要插入的第一个和最后一个输入行、在插入操作停止前可以出现的最大错误数以及插入据以排序的列。</span><span class="sxs-lookup"><span data-stu-id="a7b34-123">Optionally, specify the first and last input rows to insert, the maximum number of errors that can occur before the insert operation stops, and the columns on which the insert is sorted.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a7b34-124">排序顺序由列所列出的顺序确定。</span><span class="sxs-lookup"><span data-stu-id="a7b34-124">The sort order is determined by the order in which the columns are listed.</span></span>  
  
10. <span data-ttu-id="a7b34-125">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="a7b34-125">Click **OK**.</span></span>  
  
11. <span data-ttu-id="a7b34-126">若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="a7b34-126">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7b34-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a7b34-127">See Also</span></span>  
 <span data-ttu-id="a7b34-128">[SQL Server Destination](sql-server-destination.md) </span><span class="sxs-lookup"><span data-stu-id="a7b34-128">[SQL Server Destination](sql-server-destination.md) </span></span>  
 <span data-ttu-id="a7b34-129">[Integration Services 转换](transformations/integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="a7b34-129">[Integration Services Transformations](transformations/integration-services-transformations.md) </span></span>  
 <span data-ttu-id="a7b34-130">[Integration Services 路径](integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="a7b34-130">[Integration Services Paths](integration-services-paths.md) </span></span>  
 [<span data-ttu-id="a7b34-131">数据流任务</span><span class="sxs-lookup"><span data-stu-id="a7b34-131">Data Flow Task</span></span>](../control-flow/data-flow-task.md)  
  
  
