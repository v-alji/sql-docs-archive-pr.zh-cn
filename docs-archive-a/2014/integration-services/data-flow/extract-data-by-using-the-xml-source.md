---
title: 使用 XML 源提取数据 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- extracting data [Integration Services]
- sources [Integration Services], XML
- XML source [Integration Services]
ms.assetid: 5d5be54c-2b7e-4957-9193-c5ea5c5d6d15
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 57758353c476badfba4cb12a1ef6b5101f16735d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694052"
---
# <a name="extract-data-by-using-the-xml-source"></a><span data-ttu-id="9c378-102">使用 XML 源提取数据</span><span class="sxs-lookup"><span data-stu-id="9c378-102">Extract Data by Using the XML Source</span></span>
  <span data-ttu-id="9c378-103">若要添加和配置 XML 源，包中必须已经包含至少一个数据流任务。</span><span class="sxs-lookup"><span data-stu-id="9c378-103">To add and configure an XML source, the package must already include at least one Data Flow task.</span></span>  
  
### <a name="to-extract-data-using-an-xml-source"></a><span data-ttu-id="9c378-104">使用 XML 源提取数据</span><span class="sxs-lookup"><span data-stu-id="9c378-104">To extract data using an XML source</span></span>  
  
1.  <span data-ttu-id="9c378-105">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="9c378-105">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="9c378-106">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="9c378-106">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="9c378-107">单击 **“数据流”** 选项卡，然后从 **“工具箱”** 把 XML 源拖动到设计图面。</span><span class="sxs-lookup"><span data-stu-id="9c378-107">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the XML source to the design surface.</span></span>  
  
4.  <span data-ttu-id="9c378-108">双击此 XML 源。</span><span class="sxs-lookup"><span data-stu-id="9c378-108">Double-click the XML source.</span></span>  
  
5.  <span data-ttu-id="9c378-109">在 **“XML 源编辑器”** 的 **“连接管理器”** 页上，选择数据访问模式：</span><span class="sxs-lookup"><span data-stu-id="9c378-109">In the **XML Source Editor**, on the **Connection Manager** page, select a data access mode:</span></span>  
  
    -   <span data-ttu-id="9c378-110">对于 **“XML 文件位置”** 访问模式，单击 **“浏览”** 找到包含该 XML 文件的文件夹。</span><span class="sxs-lookup"><span data-stu-id="9c378-110">For the **XML file location** access mode, click **Browse** and locate the folder that contains the XML file.</span></span>  
  
    -   <span data-ttu-id="9c378-111">对于“来自变量的 XML 文件”访问模式，选择包含 XML 文件路径的用户定义变量。 </span><span class="sxs-lookup"><span data-stu-id="9c378-111">For the **XML file from variable** access mode, select the user-defined variable that contains the path of the XML file.</span></span>  
  
    -   <span data-ttu-id="9c378-112">对于“来自变量的 XML 数据”访问模式，选择包含 XML 数据的用户定义变量。 </span><span class="sxs-lookup"><span data-stu-id="9c378-112">For the **XML data from variable** access mode, select the user-defined variable that contains the XML data.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9c378-113">这些变量必须在包含该 XML 源的数据流任务的作用域内定义，或者在包的作用域内定义；此外，变量的数据类型必须为字符串。</span><span class="sxs-lookup"><span data-stu-id="9c378-113">The variables must be defined in the scope of the Data Flow task that contains the XML source, or in the scope of the package; additionally, the variable must have a string data type.</span></span>  
  
6.  <span data-ttu-id="9c378-114">根据需要，也可以选择 **“使用内联架构”** 以指示 XML 文档包含架构信息。</span><span class="sxs-lookup"><span data-stu-id="9c378-114">Optionally, select **Use inline schema** to indicate that the XML document includes schema information.</span></span>  
  
7.  <span data-ttu-id="9c378-115">若要为 XML 文件指定外部 XML 架构定义语言 (XSD) 架构，请执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="9c378-115">To specify an external XML Schema definition language (XSD) schema for the XML file, do one of the following:</span></span>  
  
    -   <span data-ttu-id="9c378-116">单击 **“浏览”** 找到现有的 XSD 文件。</span><span class="sxs-lookup"><span data-stu-id="9c378-116">Click **Browse** to locate an existing XSD file.</span></span>  
  
    -   <span data-ttu-id="9c378-117">单击 **“生成 XSD”** 从 XML 文件创建 XSD。</span><span class="sxs-lookup"><span data-stu-id="9c378-117">Click **Generate XSD** to create an XSD from the XML file.</span></span>  
  
8.  <span data-ttu-id="9c378-118">若要更新输出列的名称，请单击 **“列”** 并在 **“输出列”** 列表中编辑这些值。</span><span class="sxs-lookup"><span data-stu-id="9c378-118">To update the names of output columns, click **Columns** and edit the values in the **Output Column** list.</span></span>  
  
9. <span data-ttu-id="9c378-119">若要配置错误输出，请单击 **“错误输出”** 。</span><span class="sxs-lookup"><span data-stu-id="9c378-119">To configure the error output, click **Error Output**.</span></span> <span data-ttu-id="9c378-120">有关详细信息，请参阅 [在数据流组件中配置错误输出](../configure-an-error-output-in-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="9c378-120">For more information, see [Configure an Error Output in a Data Flow Component](../configure-an-error-output-in-a-data-flow-component.md).</span></span>  
  
10. <span data-ttu-id="9c378-121">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="9c378-121">Click **OK**.</span></span>  
  
11. <span data-ttu-id="9c378-122">若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="9c378-122">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c378-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9c378-123">See Also</span></span>  
 <span data-ttu-id="9c378-124">[XML 源](xml-source.md) </span><span class="sxs-lookup"><span data-stu-id="9c378-124">[XML Source](xml-source.md) </span></span>  
 <span data-ttu-id="9c378-125">[Integration Services 转换](transformations/integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="9c378-125">[Integration Services Transformations](transformations/integration-services-transformations.md) </span></span>  
 <span data-ttu-id="9c378-126">[Integration Services 路径](integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="9c378-126">[Integration Services Paths](integration-services-paths.md) </span></span>  
 [<span data-ttu-id="9c378-127">数据流任务</span><span class="sxs-lookup"><span data-stu-id="9c378-127">Data Flow Task</span></span>](../control-flow/data-flow-task.md)  
  
  
