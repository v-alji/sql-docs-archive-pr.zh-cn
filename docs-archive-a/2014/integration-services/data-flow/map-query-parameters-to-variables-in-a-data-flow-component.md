---
title: 将查询参数映射到数据流组件中的变量 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- queries [Integration Services], parameter mapping
- parameters [Integration Services]
- mapping query parameters to variables [Integration Services]
- variables [Integration Services], mapping parameters to
ms.assetid: 5e26977c-758c-46d6-acf1-4fd9238f0950
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b38940313397c7be7a8bcdbd2bf7f5233583096e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693412"
---
# <a name="map-query-parameters-to-variables-in-a-data-flow-component"></a><span data-ttu-id="675b5-102">将查询参数映射到数据流组件中的变量</span><span class="sxs-lookup"><span data-stu-id="675b5-102">Map Query Parameters to Variables in a Data Flow Component</span></span>
  <span data-ttu-id="675b5-103">当配置 OLE DB 源以使用参数化查询时，可以将参数映射到变量。</span><span class="sxs-lookup"><span data-stu-id="675b5-103">When you configure the OLE DB source to use parameterized queries, you can map the parameters to variables.</span></span>  
  
 <span data-ttu-id="675b5-104">当 OLE DB 源连接到数据源时，OLE DB 源使用参数化查询来筛选数据。</span><span class="sxs-lookup"><span data-stu-id="675b5-104">The OLE DB source uses parameterized queries to filter data when the source connects to a data source.</span></span>  
  
### <a name="to-map-a-query-parameter-to-a-variable"></a><span data-ttu-id="675b5-105">将查询参数映射到变量</span><span class="sxs-lookup"><span data-stu-id="675b5-105">To map a query parameter to a variable</span></span>  
  
1.  <span data-ttu-id="675b5-106">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="675b5-106">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="675b5-107">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="675b5-107">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="675b5-108">单击 **“数据流”** 选项卡，然后从 **“工具箱”** 中将 OLE DB 源拖动到设计图面。</span><span class="sxs-lookup"><span data-stu-id="675b5-108">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the OLE DB source to the design surface.</span></span>  
  
4.  <span data-ttu-id="675b5-109">右键单击 OLE DB 源，再单击“编辑”  。</span><span class="sxs-lookup"><span data-stu-id="675b5-109">Right-click the OLE DB source, and then click **Edit**.</span></span>  
  
5.  <span data-ttu-id="675b5-110">在 **“OLE DB 源编辑器”** 中，选择用于连接到数据源的 OLE DB 连接管理器，或单击 **“新建”** 以创建一个新的 OLE DB 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="675b5-110">In the **OLE DB Source Editor**, select an OLE DB connection manager to use to connect to the data source, or click **New** to create a new OLE DB connection manager.</span></span>  
  
6.  <span data-ttu-id="675b5-111">对于数据访问模式，请选择 **“SQL 命令”** 选项，然后在 **“SQL 命令文本”** 窗格中键入参数化查询。</span><span class="sxs-lookup"><span data-stu-id="675b5-111">Select the **SQL command** option for data access mode, and then type a parameterized query in the **SQL command text** pane.</span></span>  
  
7.  <span data-ttu-id="675b5-112">单击 **“参数”** 。</span><span class="sxs-lookup"><span data-stu-id="675b5-112">Click **Parameters**.</span></span>  
  
8.  <span data-ttu-id="675b5-113">在“设置查询参数”对话框中，将“参数”列表中的每个参数映射到“变量”列表中的某个变量，或单击“\<New variable>”创建新的变量  。</span><span class="sxs-lookup"><span data-stu-id="675b5-113">In the **Set Query Parameters** dialog box, map each parameter in the **Parameters** list to a variable in the **Variables** list, or create a new variable by clicking **\<New variable>**.</span></span> <span data-ttu-id="675b5-114">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="675b5-114">Click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="675b5-115">只有在包作用域内的系统变量和用户定义变量，诸如 Foreach 循环容器这样的父容器或者包含数据流组件的数据流任务，才用于映射。</span><span class="sxs-lookup"><span data-stu-id="675b5-115">Only system variables and user-defined variables that are in the scope of the package, a parent container such as a Foreach Loop, or the Data Flow task that contains the data flow component are available for mapping.</span></span> <span data-ttu-id="675b5-116">变量的数据类型必须与参数所分配的 WHERE 子句的列兼容。</span><span class="sxs-lookup"><span data-stu-id="675b5-116">The variable must have a data type that is compatible with the column in the WHERE clause to which the parameter is assigned.</span></span>  
  
9. <span data-ttu-id="675b5-117">单击 **“预览”** 以查看查询返回的数据（最多 200 行）。</span><span class="sxs-lookup"><span data-stu-id="675b5-117">You can click **Preview** to view up to 200 rows of the data that the query returns.</span></span>  
  
10. <span data-ttu-id="675b5-118">若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="675b5-118">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="675b5-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="675b5-119">See Also</span></span>  
 <span data-ttu-id="675b5-120">[OLE DB 源](ole-db-source.md) </span><span class="sxs-lookup"><span data-stu-id="675b5-120">[OLE DB Source](ole-db-source.md) </span></span>  
 [<span data-ttu-id="675b5-121">查找转换</span><span class="sxs-lookup"><span data-stu-id="675b5-121">Lookup Transformation</span></span>](transformations/lookup-transformation.md)  
  
  
