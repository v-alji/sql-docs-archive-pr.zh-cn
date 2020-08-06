---
title: 通过使用 ODBC 目标来加载数据 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 339ec0a8-922e-48c0-97b3-fc5ee34f95e3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e8bf0b30619c2886df6ddb28858cf98bad858421
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689543"
---
# <a name="load-data-by-using-the-odbc-destination"></a><span data-ttu-id="b1ceb-102">通过使用 ODBC 目标来加载数据</span><span class="sxs-lookup"><span data-stu-id="b1ceb-102">Load Data by Using the ODBC Destination</span></span>
  <span data-ttu-id="b1ceb-103">本过程说明如何使用 ODBC 目标加载数据。</span><span class="sxs-lookup"><span data-stu-id="b1ceb-103">This procedure shows how to load data by using the ODBC destination.</span></span> <span data-ttu-id="b1ceb-104">若要添加和配置 ODBC 目标，包中必须已包含至少一个数据流任务和源。</span><span class="sxs-lookup"><span data-stu-id="b1ceb-104">To add and configure an ODBC destination, the package must already include at least one Data Flow task and source.</span></span>  
  
### <a name="to-load-data-using-an-odbc-destination"></a><span data-ttu-id="b1ceb-105">使用 ODBC 目标加载数据</span><span class="sxs-lookup"><span data-stu-id="b1ceb-105">To load data using an ODBC destination</span></span>  
  
1.  <span data-ttu-id="b1ceb-106">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中，打开所需的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="b1ceb-106">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package you want.</span></span>  
  
2.  <span data-ttu-id="b1ceb-107">单击 **“数据流”** 选项卡，再将 ODBC 目标从 **“工具箱”** 拖动到设计图面。</span><span class="sxs-lookup"><span data-stu-id="b1ceb-107">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the ODBC destination to the design surface.</span></span>  
  
3.  <span data-ttu-id="b1ceb-108">将数据流组件的可用输出拖到 ODBC 目标的输入。</span><span class="sxs-lookup"><span data-stu-id="b1ceb-108">Drag an available output of a data flow component to the input of the ODBC destination.</span></span>  
  
4.  <span data-ttu-id="b1ceb-109">双击此 ODBC 目标。</span><span class="sxs-lookup"><span data-stu-id="b1ceb-109">Double-click the ODBC destination.</span></span>  
  
5.  <span data-ttu-id="b1ceb-110">在 **“ODBC 目标编辑器”** 对话框中的 **“连接管理器”** 页上，选择现有的 ODBC 连接管理器，或单击 **“新建”** 创建新的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="b1ceb-110">In the **ODBC Destination Editor** dialog box, on the **Connection Manager** page, select an existing ODBC connection manager or click **New** to create a new connection manager.</span></span>  
  
6.  <span data-ttu-id="b1ceb-111">选择数据访问方法。</span><span class="sxs-lookup"><span data-stu-id="b1ceb-111">Select the data access method.</span></span>  
  
    -   <span data-ttu-id="b1ceb-112">**表名 - 批处理**：选择此选项可将 ODBC 目标配置为在批处理模式下工作。</span><span class="sxs-lookup"><span data-stu-id="b1ceb-112">**Table Name - Batch**: Select this option to configure the ODBC destination to work in batch mode.</span></span> <span data-ttu-id="b1ceb-113">当您选择此选项时，可以设置 **“批处理大小”** 。</span><span class="sxs-lookup"><span data-stu-id="b1ceb-113">When you select this option, you can set the **Batch size**.</span></span>  
  
    -   <span data-ttu-id="b1ceb-114">**表名 - 逐行**：选择此选项可以将 ODBC 目标配置为一次一行将各行插入目标表中。</span><span class="sxs-lookup"><span data-stu-id="b1ceb-114">**Table Name - Row by Row**: Select this option to configure the ODBC destination to insert each of the rows into the destination table one at a time.</span></span> <span data-ttu-id="b1ceb-115">选择此选项时，数据将一次一行加载到表中。</span><span class="sxs-lookup"><span data-stu-id="b1ceb-115">When you select this option, the data is loaded into the table one row at a time.</span></span>  
  
7.  <span data-ttu-id="b1ceb-116">在 **“表或视图的名称”** 字段中，从列表的数据库中选择某一可用表或视图，或者键入正则表达式以便标识表。该列表仅包含前 1000 个表。</span><span class="sxs-lookup"><span data-stu-id="b1ceb-116">In the **Name of the table or the view** field, select an available table or view from the database from the list or type in a regular expression to identify the table.This list contains the first 1000 tables only.</span></span> <span data-ttu-id="b1ceb-117">如果您的数据库包含超过 1000 个表，则可以键入表名的开头，或者使用 (\*) 通配符输入名称的任何部分以便显示要使用的表。</span><span class="sxs-lookup"><span data-stu-id="b1ceb-117">If your database contains more than 1000 tables, you can type the beginning of a table name or use the (\*) wild card to enter any part of the name to display the table or tables you want to use.</span></span>  
  
8.  <span data-ttu-id="b1ceb-118">可以单击 **“预览”** ，查看在 ODBC 目标中选择的表中的最多 200 行数据。</span><span class="sxs-lookup"><span data-stu-id="b1ceb-118">You can click **Preview** to view up to 200 rows of the data from the table selected in the ODBC destination.</span></span>  
  
9. <span data-ttu-id="b1ceb-119">单击 **“映射”** ，然后将列从一个列表拖动到另一个列表，从而将 **“可用输入列”** 列表中的列映射到 **“可用目标列”** 列表中的列。</span><span class="sxs-lookup"><span data-stu-id="b1ceb-119">Click **Mappings** and then map columns from the **Available Input Columns** list to columns in the **Available Destination Columns** list by dragging columns from one list to another.</span></span>  
  
10. <span data-ttu-id="b1ceb-120">若要配置错误输出，请单击 **“错误输出”** 。</span><span class="sxs-lookup"><span data-stu-id="b1ceb-120">To configure the error output, click **Error Output**.</span></span>  
  
11. <span data-ttu-id="b1ceb-121">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="b1ceb-121">Click **OK**.</span></span>  
  
12. <span data-ttu-id="b1ceb-122">若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="b1ceb-122">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1ceb-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b1ceb-123">See Also</span></span>  
 <span data-ttu-id="b1ceb-124">[ODBC 目标编辑器（“连接管理器”页）](../odbc-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="b1ceb-124">[ODBC Destination Editor &#40;Connection Manager Page&#41;](../odbc-destination-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="b1ceb-125">[ODBC 目标编辑器（“映射”页）](../odbc-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="b1ceb-125">[ODBC Destination Editor &#40;Mappings Page&#41;](../odbc-destination-editor-mappings-page.md) </span></span>  
 [<span data-ttu-id="b1ceb-126">ODBC 源编辑器（“错误输出”页）</span><span class="sxs-lookup"><span data-stu-id="b1ceb-126">ODBC Source Editor &#40;Error Output Page&#41;</span></span>](../odbc-source-editor-error-output-page.md)  
  
  
