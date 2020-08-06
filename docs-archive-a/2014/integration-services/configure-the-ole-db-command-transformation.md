---
title: 配置 OLE DB 命令转换 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- parameters [Integration Services]
- OLE DB Command transformation
ms.assetid: c800f167-3d2e-4c10-8ba3-a02f1872ccea
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d1714a6b798c6d8256052fd3c16bd86182480bcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692490"
---
# <a name="configure-the-ole-db-command-transformation"></a><span data-ttu-id="15902-102">配置 OLE DB 命令转换</span><span class="sxs-lookup"><span data-stu-id="15902-102">Configure the OLE DB Command Transformation</span></span>
  <span data-ttu-id="15902-103">若要添加和配置 OLE DB 命令转换，包必须已包含至少一个数据流任务和一个源（如平面文件源或 OLE DB 源）。</span><span class="sxs-lookup"><span data-stu-id="15902-103">To add and configure an OLE DB Command transformation, the package must already include at least one Data Flow task and a source such as a Flat File source or an OLE DB source.</span></span> <span data-ttu-id="15902-104">这种转换通常用于运行参数化查询。</span><span class="sxs-lookup"><span data-stu-id="15902-104">This transformation is typically used for running parameterized queries.</span></span>  
  
### <a name="to-configure-the-ole-db-command-transformation"></a><span data-ttu-id="15902-105">配置 OLE DB 命令转换</span><span class="sxs-lookup"><span data-stu-id="15902-105">To configure the OLE DB Command transformation</span></span>  
  
1.  <span data-ttu-id="15902-106">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="15902-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="15902-107">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="15902-107">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="15902-108">单击 **“数据流”** 选项卡，然后从 **“工具箱”** 中将 OLE DB 命令转换拖动到设计图面。</span><span class="sxs-lookup"><span data-stu-id="15902-108">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the OLE DB Command transformation to the design surface.</span></span>  
  
4.  <span data-ttu-id="15902-109">将连接线（绿色或红色箭头）从数据源或前一个转换拖动到 OLE DB 命令转换，从而将 OLE DB 命令转换连接到数据流。</span><span class="sxs-lookup"><span data-stu-id="15902-109">Connect the OLE DB Command transformation to the data flow by dragging a connector-the green or red arrow-from a data source or a previous transformation to the OLE DB Command transformation.</span></span>  
  
5.  <span data-ttu-id="15902-110">右键单击组件，并选择“编辑高级编辑器”或“显示高级编辑器”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="15902-110">Right-click the component and select Edit or Show **Advanced Editor**.</span></span>  
  
6.  <span data-ttu-id="15902-111">在 **“连接管理器”** 选项卡上，从 **“连接管理器”** 列表中选择 OLE DB 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="15902-111">On the **Connection Managers** tab, select an OLE DB connection manager in the **Connection Manager** list.</span></span> <span data-ttu-id="15902-112">有关详细信息，请参阅 [OLE DB Connection Manager](connection-manager/ole-db-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="15902-112">For more information, see [OLE DB Connection Manager](connection-manager/ole-db-connection-manager.md).</span></span>  
  
7.  <span data-ttu-id="15902-113">单击“组件属性”选项卡，并单击“SqlCommand”框中的省略号按钮 (…)\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="15902-113">Click the **Component Properties** tab and click the ellipsis button **(...)** in the **SqlCommand** box.</span></span>  
  
8.  <span data-ttu-id="15902-114">在“字符串值编辑器”中，键入参数化 SQL 语句，并且使用问号 (?) 作为每个参数的参数标记。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="15902-114">In the **String Value Editor**, type the parameterized SQL statement using a question mark (?) as the parameter marker for each parameter.</span></span>  
  
9. <span data-ttu-id="15902-115">单击“刷新”。</span><span class="sxs-lookup"><span data-stu-id="15902-115">Click **Refresh**.</span></span> <span data-ttu-id="15902-116">单击“刷新”时，转换将为 External Columns 集合中的每一个参数都创建一列，并设置 DBParamInfoFlags 属性。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="15902-116">When you click **Refresh**, the transformation creates a column for each parameter in the External Columns collection and sets the DBParamInfoFlags property.</span></span>  
  
10. <span data-ttu-id="15902-117">单击 **“输入属性和输出属性”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="15902-117">Click the **Input and Output Properties** tab.</span></span>  
  
11. <span data-ttu-id="15902-118">展开 **“OLE DB 命令输入”**，再展开 **“外部列”**。</span><span class="sxs-lookup"><span data-stu-id="15902-118">Expand **OLE DB Command Input**, and then expand **External Columns**.</span></span>  
  
12. <span data-ttu-id="15902-119">验证 **“外部列”** 是否为 SQL 语句中的每个参数列出了一列。</span><span class="sxs-lookup"><span data-stu-id="15902-119">Verify that **External Columns** lists a column for each parameter in the SQL statement.</span></span> <span data-ttu-id="15902-120">列的名称是 **Param_0**、 **Param_1**，以此类推。</span><span class="sxs-lookup"><span data-stu-id="15902-120">The column names are **Param_0**, **Param_1**, and so on.</span></span>  
  
     <span data-ttu-id="15902-121">不应更改列名称。</span><span class="sxs-lookup"><span data-stu-id="15902-121">You should not change the column names.</span></span> <span data-ttu-id="15902-122">如果更改列名称， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 会生成有关 OLE DB 命令转换的验证错误。</span><span class="sxs-lookup"><span data-stu-id="15902-122">If you change the column names, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] generates a validation error for the OLE DB Command transformation.</span></span>  
  
     <span data-ttu-id="15902-123">此外，不应更改数据类型。</span><span class="sxs-lookup"><span data-stu-id="15902-123">Also, you should not change the data type.</span></span> <span data-ttu-id="15902-124">每列的 DataType 属性均设置为正确的数据类型。</span><span class="sxs-lookup"><span data-stu-id="15902-124">The DataType property of each column is set to the correct data type.</span></span>  
  
13. <span data-ttu-id="15902-125">如果 **“外部列”** 没有列出任何列，则您必须手动添加这些列。</span><span class="sxs-lookup"><span data-stu-id="15902-125">If **External Columns** lists no columns you must add them manually.</span></span>  
  
    -   <span data-ttu-id="15902-126">对 SQL 语句中的每一个参数，单击一次 **“添加列”** 。</span><span class="sxs-lookup"><span data-stu-id="15902-126">Click **Add Column** one time for each parameter in the SQL statement.</span></span>  
  
    -   <span data-ttu-id="15902-127">将列名更新为 **Param_0**、 **Param_1**，以此类推。</span><span class="sxs-lookup"><span data-stu-id="15902-127">Update the column names to **Param_0**, **Param_1**, and so on.</span></span>  
  
    -   <span data-ttu-id="15902-128">在 DBParamInfoFlags 属性中指定值。</span><span class="sxs-lookup"><span data-stu-id="15902-128">Specify a value in the DBParamInfoFlags property.</span></span> <span data-ttu-id="15902-129">该值必须与 OLE DB DBPARAMFLAGSENUM 枚举中的值相匹配。</span><span class="sxs-lookup"><span data-stu-id="15902-129">The value must match a value in the OLE DB DBPARAMFLAGSENUM enumeration.</span></span> <span data-ttu-id="15902-130">有关详细信息，请参阅 OLE DB 参考文档。</span><span class="sxs-lookup"><span data-stu-id="15902-130">For more information, see the OLE DB reference documentation.</span></span>  
  
    -   <span data-ttu-id="15902-131">指定列的数据类型，并根据该数据类型指定列的代码页、长度、精度和小数位数。</span><span class="sxs-lookup"><span data-stu-id="15902-131">Specify the data type of the column and, depending on the data type, specify the code page, length, precision, and scale of the column.</span></span>  
  
    -   <span data-ttu-id="15902-132">若要删除未使用的参数，请选择 **“外部列”** 中的参数，再单击 **“删除列”**。</span><span class="sxs-lookup"><span data-stu-id="15902-132">To delete an unused parameter, select the parameter in **External Columns**, and then click **Remove Column**.</span></span>  
  
    -   <span data-ttu-id="15902-133">单击 **“列映射”** ，并将 **“可用输入列”** 列表中的列映射到 **“可用目标列”** 列表中的参数。</span><span class="sxs-lookup"><span data-stu-id="15902-133">Click **Column Mappings** and map columns in the **Available Input Columns** list to parameters in the **Available Destination Columns** list.</span></span>  
  
14. <span data-ttu-id="15902-134">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="15902-134">Click **OK**.</span></span>  
  
15. <span data-ttu-id="15902-135">若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存”** 。</span><span class="sxs-lookup"><span data-stu-id="15902-135">To save the updated package, click **Save** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15902-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="15902-136">See Also</span></span>  
 <span data-ttu-id="15902-137">[OLE DB 命令转换](data-flow/transformations/ole-db-command-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="15902-137">[OLE DB Command Transformation](data-flow/transformations/ole-db-command-transformation.md) </span></span>  
 <span data-ttu-id="15902-138">[Integration Services 转换](data-flow/transformations/integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="15902-138">[Integration Services Transformations](data-flow/transformations/integration-services-transformations.md) </span></span>  
 <span data-ttu-id="15902-139">[Integration Services 路径](data-flow/integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="15902-139">[Integration Services Paths](data-flow/integration-services-paths.md) </span></span>  
 [<span data-ttu-id="15902-140">数据流任务</span><span class="sxs-lookup"><span data-stu-id="15902-140">Data Flow Task</span></span>](control-flow/data-flow-task.md)  
  
  
