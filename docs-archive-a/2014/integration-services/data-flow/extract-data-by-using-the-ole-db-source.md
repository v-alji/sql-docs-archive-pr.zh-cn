---
title: 使用 OLE DB 源提取数据 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- extracting data [Integration Services]
- sources [Integration Services], OLE DB
- OLE DB source [Integration Services]
ms.assetid: 4ca6eeb5-b60e-4b81-86dd-0674be8ae8d8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 352d62cc66e3f17fb10839086e7ee9c5307f1a17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694053"
---
# <a name="extract-data-by-using-the-ole-db-source"></a><span data-ttu-id="cb239-102">使用 OLE DB 源提取数据</span><span class="sxs-lookup"><span data-stu-id="cb239-102">Extract Data by Using the OLE DB Source</span></span>
  <span data-ttu-id="cb239-103">若要添加并配置 OLE DB 源，包必须已包含至少一个数据流任务。</span><span class="sxs-lookup"><span data-stu-id="cb239-103">To add and configure an OLE DB source, the package must already include at least one Data Flow task.</span></span>  
  
### <a name="to-extract-data-using-an-ole-db-source"></a><span data-ttu-id="cb239-104">使用 OLE DB 源提取数据</span><span class="sxs-lookup"><span data-stu-id="cb239-104">To extract data using an OLE DB Source</span></span>  
  
1.  <span data-ttu-id="cb239-105">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="cb239-105">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="cb239-106">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="cb239-106">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="cb239-107">单击 **“数据流”** 选项卡，然后从 **“工具箱”** 中将 OLE DB 源拖动到设计图面。</span><span class="sxs-lookup"><span data-stu-id="cb239-107">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the OLE DB source to the design surface.</span></span>  
  
4.  <span data-ttu-id="cb239-108">双击此 OLE DB 源。</span><span class="sxs-lookup"><span data-stu-id="cb239-108">Double-click the OLE DB source.</span></span>  
  
5.  <span data-ttu-id="cb239-109">在 **“OLE DB 源编辑器”** 对话框中的 **“连接管理器”** 页上，选择现有的 OLE DB 连接管理器，或单击 **“新建”** 创建新的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="cb239-109">In the **OLE DB Source Editor** dialog box, on the **Connection Manager** page, select an existing OLE DB connection manager or click **New** to create a new connection manager.</span></span> <span data-ttu-id="cb239-110">有关详细信息，请参阅 [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="cb239-110">For more information, see [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md).</span></span>  
  
6.  <span data-ttu-id="cb239-111">选择数据访问方法：</span><span class="sxs-lookup"><span data-stu-id="cb239-111">Select the data access method:</span></span>  
  
    -   <span data-ttu-id="cb239-112">**“表或视图”** 在 OLE DB 连接管理器连接到的数据库中，选择表或视图。</span><span class="sxs-lookup"><span data-stu-id="cb239-112">**Table or view** Select a table or view in the database to which the OLE DB connection manager connects.</span></span>  
  
    -   <span data-ttu-id="cb239-113">**表名变量或视图名变量** 在 OLE DB 连接管理器连接到的数据库中，选择包含表名称或视图名称的用户定义变量。</span><span class="sxs-lookup"><span data-stu-id="cb239-113">**Table name or view name variable** Select the user-defined variable that contains the name of a table or view in the database to which the OLE DB connection manager connects.</span></span>  
  
    -   <span data-ttu-id="cb239-114">**SQL 命令** 键入 SQL 命令或单击 **“生成查询”** ，以使用 **“查询生成器”** 编写 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="cb239-114">**SQL command** Type an SQL command or click **Build Query** to write an SQL command using the **Query Builder**.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="cb239-115">此命令可以包含参数。</span><span class="sxs-lookup"><span data-stu-id="cb239-115">The command can include parameters.</span></span> <span data-ttu-id="cb239-116">有关详细信息，请参阅 [将查询参数映射到数据流组件中的变量](map-query-parameters-to-variables-in-a-data-flow-component.md)</span><span class="sxs-lookup"><span data-stu-id="cb239-116">For more information, see [Map Query Parameters to Variables in a Data Flow Component](map-query-parameters-to-variables-in-a-data-flow-component.md).</span></span>  
  
    -   <span data-ttu-id="cb239-117">**变量中的 SQL 命令** 选择包含 SQL 命令的用户定义变量。</span><span class="sxs-lookup"><span data-stu-id="cb239-117">**SQL command from variable** Select the user-defined variable that contains the SQL command.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="cb239-118">这些变量必须在包含 OLE DB 源的同一个数据流任务的作用域内定义，或在同一个包的作用域内定义；此外，变量的数据类型还必须为字符串。</span><span class="sxs-lookup"><span data-stu-id="cb239-118">The variables must be defined in the scope of the same Data Flow task that contains the OLE DB source, or in the scope of the same package; additionally, the variable must have a string data type.</span></span>  
  
7.  <span data-ttu-id="cb239-119">若要更新外部列和输出列之间的映射，请单击 **“列”** ，并在 **“外部列”** 列表中选择其他列。</span><span class="sxs-lookup"><span data-stu-id="cb239-119">To update the mapping between external and output columns, click **Columns** and select different columns in the **External Column** list.</span></span>  
  
8.  <span data-ttu-id="cb239-120">也可以通过编辑 **“输出列”** 列表中的值来更新输出列的名称。</span><span class="sxs-lookup"><span data-stu-id="cb239-120">Optionally, update the names of output columns by editing values in the **Output Column** list.</span></span>  
  
9. <span data-ttu-id="cb239-121">若要配置错误输出，请单击 **“错误输出”** 。</span><span class="sxs-lookup"><span data-stu-id="cb239-121">To configure the error output, click **Error Output**.</span></span> <span data-ttu-id="cb239-122">有关详细信息，请参阅 [在数据流组件中配置错误输出](../configure-an-error-output-in-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="cb239-122">For more information, see [Configure an Error Output in a Data Flow Component](../configure-an-error-output-in-a-data-flow-component.md).</span></span>  
  
10. <span data-ttu-id="cb239-123">可以单击 **“预览”** ，查看最多 200 行 OLE DB 源所提取的数据。</span><span class="sxs-lookup"><span data-stu-id="cb239-123">You can click **Preview** to view up to 200 rows of the data extracted by the OLE DB source.</span></span>  
  
11. <span data-ttu-id="cb239-124">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="cb239-124">Click **OK**.</span></span>  
  
12. <span data-ttu-id="cb239-125">若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="cb239-125">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb239-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cb239-126">See Also</span></span>  
 <span data-ttu-id="cb239-127">[OLE DB 源](ole-db-source.md) </span><span class="sxs-lookup"><span data-stu-id="cb239-127">[OLE DB Source](ole-db-source.md) </span></span>  
 <span data-ttu-id="cb239-128">[Integration Services 转换](transformations/integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="cb239-128">[Integration Services Transformations](transformations/integration-services-transformations.md) </span></span>  
 <span data-ttu-id="cb239-129">[Integration Services 路径](integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="cb239-129">[Integration Services Paths](integration-services-paths.md) </span></span>  
 [<span data-ttu-id="cb239-130">数据流任务</span><span class="sxs-lookup"><span data-stu-id="cb239-130">Data Flow Task</span></span>](../control-flow/data-flow-task.md)  
  
  
