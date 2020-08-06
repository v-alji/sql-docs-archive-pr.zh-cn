---
title: 通过使用 OLE DB 目标来加载数据 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- loading data
- OLE DB destination [Integration Services]
- destinations [Integration Services], OLE DB
ms.assetid: 78899498-725e-4300-a7af-f983f4ea384b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 43e8d1123ae91d9e68c00fbe3e05c490383afe0c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689541"
---
# <a name="load-data-by-using-the-ole-db-destination"></a><span data-ttu-id="4f1d8-102">通过使用 OLE DB 目标来加载数据</span><span class="sxs-lookup"><span data-stu-id="4f1d8-102">Load Data by Using the OLE DB Destination</span></span>
  <span data-ttu-id="4f1d8-103">若要添加和配置 OLE DB 目标，包中必须已包含至少一个数据流任务和一个源。</span><span class="sxs-lookup"><span data-stu-id="4f1d8-103">To add and configure an OLE DB destination, the package must already include at least one Data Flow task and a source.</span></span>  
  
### <a name="to-load-data-using-an-ole-db-destination"></a><span data-ttu-id="4f1d8-104">使用 OLE DB 目标加载数据</span><span class="sxs-lookup"><span data-stu-id="4f1d8-104">To load data using an OLE DB destination</span></span>  
  
1.  <span data-ttu-id="4f1d8-105">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="4f1d8-105">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="4f1d8-106">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="4f1d8-106">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="4f1d8-107">单击 **“数据流”** 选项卡，然后将 OLE DB 目标从 **“工具箱”** 拖动到设计图面。</span><span class="sxs-lookup"><span data-stu-id="4f1d8-107">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the OLE DB destination to the design surface.</span></span>  
  
4.  <span data-ttu-id="4f1d8-108">将连接线从数据源或前一转换拖到目标，从而将 OLE DB 目标连接到数据流。</span><span class="sxs-lookup"><span data-stu-id="4f1d8-108">Connect the OLE DB destination to the data flow by dragging a connector from a data source or a previous transformation to the destination.</span></span>  
  
5.  <span data-ttu-id="4f1d8-109">双击 OLE DB 目标。</span><span class="sxs-lookup"><span data-stu-id="4f1d8-109">Double-click the OLE DB destination.</span></span>  
  
6.  <span data-ttu-id="4f1d8-110">在 **“OLE DB 目标编辑器”** 对话框中的 **“连接管理器”** 页上，选择现有的 OLE DB 连接管理器，或单击 **“新建”** 创建新的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="4f1d8-110">In the **OLE DB Destination Editor** dialog box, on the **Connection Manager** page, select an existing OLE DB connection manager or click **New** to create a new connection manager.</span></span> <span data-ttu-id="4f1d8-111">有关详细信息，请参阅 [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="4f1d8-111">For more information, see [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md).</span></span>  
  
7.  <span data-ttu-id="4f1d8-112">选择数据访问方法：</span><span class="sxs-lookup"><span data-stu-id="4f1d8-112">Select the data access method:</span></span>  
  
    -   <span data-ttu-id="4f1d8-113">**“表或视图”** 在包含该数据的数据库中选择一个表或视图。</span><span class="sxs-lookup"><span data-stu-id="4f1d8-113">**Table or view** Select a table or view in the database that contains the data.</span></span>  
  
    -   <span data-ttu-id="4f1d8-114">**表或视图 - 快速加载** 选择数据库中包含该数据的表或视图，然后设置快速加载选项：“保留标识”、“保留空值”、“表锁”、“检查约束”、“每批行数”或“最大插入提交大小”。      </span><span class="sxs-lookup"><span data-stu-id="4f1d8-114">**Table or view - fast load** Select a table or view in the database that contains the data, and then set the fast-load options: **Keep identity**, **Keep null**, **Table lock**, **Check constraint**, **Rows per batch**, or **Maximum insert commit size**.</span></span>  
  
    -   <span data-ttu-id="4f1d8-115">**表名变量或视图名变量** 在数据库中选择包含表名称或视图名称的用户定义变量。</span><span class="sxs-lookup"><span data-stu-id="4f1d8-115">**Table name or view name variable** Select the user-defined variable that contains the name of a table or view in the database.</span></span>  
  
    -   <span data-ttu-id="4f1d8-116">**表名变量或视图名变量快速加载** 在包含该数据的数据库中选择包含表名称或视图名称的用户定义变量，然后设置快速加载选项。</span><span class="sxs-lookup"><span data-stu-id="4f1d8-116">**Table name or view name variable fast load** Select the user-defined variable that contains the name of a table or view in the database that contains the data, and then set the fast-load options.</span></span>  
  
    -   <span data-ttu-id="4f1d8-117">**“SQL 命令”** 键入 SQL 命令，或单击 **“生成查询”** 以使用 **查询生成器**编写 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="4f1d8-117">**SQL command** Type an SQL command or click **Build Query** to write an SQL command by using the **Query Builder**.</span></span>  
  
8.  <span data-ttu-id="4f1d8-118">单击 **“映射”** ，然后将列从一个列表拖动到另一个列表，从而将 **“可用输入列”** 列表中的列映射到 **“可用目标列”** 列表中的列。</span><span class="sxs-lookup"><span data-stu-id="4f1d8-118">Click **Mappings** and then map columns from the **Available Input Columns** list to columns in the **Available Destination Columns** list by dragging columns from one list to another.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4f1d8-119">OLE DB 目标会自动映射同名的列。</span><span class="sxs-lookup"><span data-stu-id="4f1d8-119">The OLE DB destination automatically maps same-named columns.</span></span>  
  
9. <span data-ttu-id="4f1d8-120">若要配置错误输出，请单击 **“错误输出”** 。</span><span class="sxs-lookup"><span data-stu-id="4f1d8-120">To configure the error output, click **Error Output**.</span></span> <span data-ttu-id="4f1d8-121">有关详细信息，请参阅 [在数据流组件中配置错误输出](../configure-an-error-output-in-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="4f1d8-121">For more information, see [Configure an Error Output in a Data Flow Component](../configure-an-error-output-in-a-data-flow-component.md).</span></span>  
  
10. <span data-ttu-id="4f1d8-122">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="4f1d8-122">Click **OK**.</span></span>  
  
11. <span data-ttu-id="4f1d8-123">若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="4f1d8-123">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f1d8-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4f1d8-124">See Also</span></span>  
 <span data-ttu-id="4f1d8-125">[OLE DB 目标](ole-db-destination.md) </span><span class="sxs-lookup"><span data-stu-id="4f1d8-125">[OLE DB Destination](ole-db-destination.md) </span></span>  
 <span data-ttu-id="4f1d8-126">[Integration Services 转换](transformations/integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="4f1d8-126">[Integration Services Transformations](transformations/integration-services-transformations.md) </span></span>  
 <span data-ttu-id="4f1d8-127">[Integration Services 路径](integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="4f1d8-127">[Integration Services Paths](integration-services-paths.md) </span></span>  
 [<span data-ttu-id="4f1d8-128">数据流任务</span><span class="sxs-lookup"><span data-stu-id="4f1d8-128">Data Flow Task</span></span>](../control-flow/data-flow-task.md)  
  
  
