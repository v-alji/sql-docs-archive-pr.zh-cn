---
title: 使用 XMLA 创建数据挖掘查询 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- content queries [DMX]
ms.assetid: 8f6b6008-006c-4792-9bd1-64c30dc3fd41
author: minewiskan
ms.author: owend
ms.openlocfilehash: d0e85b17db0781671fab0874706f12fdac95b30b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590448"
---
# <a name="create-a-data-mining-query-by-using-xmla"></a><span data-ttu-id="e22ff-102">使用 XMLA 创建数据挖掘查询</span><span class="sxs-lookup"><span data-stu-id="e22ff-102">Create a Data Mining Query by Using XMLA</span></span>
  <span data-ttu-id="e22ff-103">可以使用 AMO、DMX 或 XML/A 创建针对数据挖掘对象的各种查询。</span><span class="sxs-lookup"><span data-stu-id="e22ff-103">You can create a variety of queries against data mining objects by using AMO, DMX, or XML/A.</span></span>  
  
 <span data-ttu-id="e22ff-104">XML 用于 Analysis Services 服务器和所有客户端之间的通信。</span><span class="sxs-lookup"><span data-stu-id="e22ff-104">XML is used for communication between the Analysis Services server and all clients.</span></span> <span data-ttu-id="e22ff-105">因此，尽管使用 DMX 创建内容查询通常会更轻松，但还可使用 XML/A 中的 DISCOVER 和 COMMAND 语句编写这些查询，其间您既可以使用支持 SOAP 协议的客户端，也可以在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中创建 XML/A 查询。</span><span class="sxs-lookup"><span data-stu-id="e22ff-105">Therefore, although it is generally much easier to create content queries by using DMX, you can write queries by using the DISCOVER and COMMAND statements in XML/A, either by using a client that supports the SOAP protocol, or by creating an XML/A query in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="e22ff-106">本主题说明如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中提供的 XML/A 模板来创建针对当前服务器中存储的挖掘模型的模型内容查询。</span><span class="sxs-lookup"><span data-stu-id="e22ff-106">This topic explains how to use the XML/A templates that are available in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to create a model content query against a mining model stored on the current server.</span></span>  
  
## <a name="querying-data-mining-schema-rowsets-by-using-xmla"></a><span data-ttu-id="e22ff-107">使用 XML/A 查询数据挖掘架构行集</span><span class="sxs-lookup"><span data-stu-id="e22ff-107">Querying Data Mining Schema Rowsets by Using XML/A</span></span>  
  
#### <a name="to-open-an-xmla-template"></a><span data-ttu-id="e22ff-108">打开 XML/A 模板</span><span class="sxs-lookup"><span data-stu-id="e22ff-108">To open an XML/A template</span></span>  
  
1.  <span data-ttu-id="e22ff-109">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的“视图”  菜单上，单击“模板资源管理器” 。</span><span class="sxs-lookup"><span data-stu-id="e22ff-109">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **View** menu, click **Template Explorer**.</span></span>  
  
2.  <span data-ttu-id="e22ff-110">单击多维数据集图标以打开 Analysis Server 模板列表。</span><span class="sxs-lookup"><span data-stu-id="e22ff-110">Click the cube icon to open the list of Analysis Services templates.</span></span>  
  
3.  <span data-ttu-id="e22ff-111">在模板类别列表中，展开 **XMLA**，再展开“架构行集”\*\*\*\*，然后双击“发现架构行集”\*\*\*\*，在合适的代码编辑器中打开该模板。</span><span class="sxs-lookup"><span data-stu-id="e22ff-111">In the list of template categories, expand **XMLA**, expand **Schema Rowsets**, and double-click **Discover Schema Rowsets** to open the template in the appropriate code editor.</span></span>  
  
4.  <span data-ttu-id="e22ff-112">在 **“连接到 Analysis Services”** 对话框中，填写连接信息，再单击 **“连接”**。</span><span class="sxs-lookup"><span data-stu-id="e22ff-112">In the **Connect to Analysis Services** dialog box, complete the connection information and then click **Connect**.</span></span> <span data-ttu-id="e22ff-113">此时将打开一个新的查询编辑器窗口，其中包含 **“发现架构行集”** 模板。</span><span class="sxs-lookup"><span data-stu-id="e22ff-113">A new query editor window opens, populated with the **Discover Schema Rowsets** template.</span></span>  
  
#### <a name="to-discover-column-names-from-the-mining-model-content-schema-rowset"></a><span data-ttu-id="e22ff-114">从 MINING MODEL CONTENT 架构行集中发现列名</span><span class="sxs-lookup"><span data-stu-id="e22ff-114">To discover column names from the MINING MODEL CONTENT schema rowset</span></span>  
  
1.  <span data-ttu-id="e22ff-115">打开 **“发现架构行集”** 模板后，单击 **“执行”**。</span><span class="sxs-lookup"><span data-stu-id="e22ff-115">With the **Discover Schema Rowsets** template open, click **Execute**.</span></span>  
  
     <span data-ttu-id="e22ff-116">**“结果”** 窗格中将显示返回的架构行集列表，该列表中包含当前实例中可用的所有行集的名称和行集列。</span><span class="sxs-lookup"><span data-stu-id="e22ff-116">A list of schema rowsets is returned in the **Results** pane that contains the rowset names and rowset columns for all rowsets available on the current instance.</span></span>  
  
2.  <span data-ttu-id="e22ff-117">在**查询**窗格中，将光标置于后， **\<Restriction List>** 按 enter 添加新行。</span><span class="sxs-lookup"><span data-stu-id="e22ff-117">In the **Query** pane, place the cursor after **\<Restriction List>** and press ENTER to add a new line.</span></span>  
  
3.  <span data-ttu-id="e22ff-118">将光标置于空行上，然后键入\*\* \<SchemaName> DMSCHEMA_MINING_MODEL_CONTENT \</SchemaName> \*\*</span><span class="sxs-lookup"><span data-stu-id="e22ff-118">Place the cursor on the blank line and type **\<SchemaName>DMSCHEMA_MINING_MODEL_CONTENT\</SchemaName>**</span></span>  
  
     <span data-ttu-id="e22ff-119">完整的限制部分应如下所示：</span><span class="sxs-lookup"><span data-stu-id="e22ff-119">The complete section for restrictions should appear as follows:</span></span>  
  
     `<Restrictions>`  
  
     `<RestrictionList>`  
  
     `<SchemaName>DMSCHEMA_MINING_MODEL_CONTENT</SchemaName>`  
  
     `</RestrictionList>`  
  
     `</Restrictions>`  
  
4.  <span data-ttu-id="e22ff-120">单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="e22ff-120">Click **Execute**.</span></span>  
  
     <span data-ttu-id="e22ff-121">**“结果”** 窗格将显示指定架构行集的列名列表。</span><span class="sxs-lookup"><span data-stu-id="e22ff-121">The **Results** pane shows a list of column names for the specified schema rowset.</span></span>  
  
#### <a name="to-create-a-content-query-using-the-mining-model-content-schema-rowset"></a><span data-ttu-id="e22ff-122">使用 MINING MODEL CONTENT 架构行集创建内容查询</span><span class="sxs-lookup"><span data-stu-id="e22ff-122">To create a content query using the MINING MODEL CONTENT schema rowset</span></span>  
  
1.  <span data-ttu-id="e22ff-123">在 **“发现架构行集”** 模板中，通过替换请求类型标记内的文本来更改请求类型。</span><span class="sxs-lookup"><span data-stu-id="e22ff-123">In the **Discover Schema Rowsets** template, change the request type by replacing the text inside the request type tags.</span></span>  
  
     <span data-ttu-id="e22ff-124">将以下行：</span><span class="sxs-lookup"><span data-stu-id="e22ff-124">Replace this line:</span></span>  
  
     `<RequestType>DISCOVER_SCHEMA_ROWSETS</RequestType>`  
  
     <span data-ttu-id="e22ff-125">替换为以下行：</span><span class="sxs-lookup"><span data-stu-id="e22ff-125">with the following line:</span></span>  
  
     <span data-ttu-id="e22ff-126">**\<RequestType>DMSCHEMA_MINING_MODEL_CONTENT\</RequestType>**</span><span class="sxs-lookup"><span data-stu-id="e22ff-126">**\<RequestType>DMSCHEMA_MINING_MODEL_CONTENT\</RequestType>**</span></span>  
  
2.  <span data-ttu-id="e22ff-127">向限制列表添加新条件，将限制列表更改为按名称指定挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="e22ff-127">Change the restriction list to specify a mining model by name, by adding a new condition to the restriction lists.</span></span>  
  
3.  <span data-ttu-id="e22ff-128">在模板中，将光标置于 `<Restriction List>` 之后，然后按 Enter 键以添加新行。</span><span class="sxs-lookup"><span data-stu-id="e22ff-128">In the template, place the cursor after `<Restriction List>` and press ENTER to add a new line.</span></span>  
  
4.  <span data-ttu-id="e22ff-129">将光标置于空行上，然后键入 **<MODEL_NAME>My model name</MODEL_NAME>**</span><span class="sxs-lookup"><span data-stu-id="e22ff-129">Place the cursor on the blank line and type **<MODEL_NAME>My model name</MODEL_NAME>**</span></span>  
  
     <span data-ttu-id="e22ff-130">完整的限制部分应如下所示：</span><span class="sxs-lookup"><span data-stu-id="e22ff-130">The complete section for restrictions should appear as follows:</span></span>  
  
     `<Restrictions>`  
  
     `<RestrictionList>`  
  
     `<MODEL_NAME>My model name</MODEL_NAME>`  
  
     `</RestrictionList>`  
  
     `</Restrictions>`  
  
5.  <span data-ttu-id="e22ff-131">单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="e22ff-131">Click **Execute**.</span></span>  
  
     <span data-ttu-id="e22ff-132">“结果”窗格将显示架构定义以及指定模型的值。</span><span class="sxs-lookup"><span data-stu-id="e22ff-132">The Results pane displays the schema definition, together with the values for the specified model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e22ff-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e22ff-133">See Also</span></span>  
 <span data-ttu-id="e22ff-134">[挖掘模型内容 &#40;Analysis Services 数据挖掘&#41;](mining-model-content-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="e22ff-134">[Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="e22ff-135">Data Mining Schema Rowsets</span><span class="sxs-lookup"><span data-stu-id="e22ff-135">Data Mining Schema Rowsets</span></span>](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/data-mining-schema-rowsets) 
  
  
