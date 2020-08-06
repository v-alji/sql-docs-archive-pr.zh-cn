---
title: 高级数据挖掘查询编辑器 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 27e7fc46-689d-43a4-9647-1c27d182bdd6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2aadf4df75b1ccf6001ad8e97d589ce5666f56ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579433"
---
# <a name="advanced-data-mining-query-editor"></a><span data-ttu-id="8f698-102">高级数据挖掘查询编辑器</span><span class="sxs-lookup"><span data-stu-id="8f698-102">Advanced Data Mining Query Editor</span></span>
  <span data-ttu-id="8f698-103">**数据挖掘查询高级编辑器**是一种工具，可帮助您生成自定义模型和查询。</span><span class="sxs-lookup"><span data-stu-id="8f698-103">The **Data Mining Query Advanced Editor** is a tool to help you build custom models and queries.</span></span>  
  
 <span data-ttu-id="8f698-104">该编辑器提供一组具有可单击链接的模板。</span><span class="sxs-lookup"><span data-stu-id="8f698-104">The editor provides a set of templates with clickable links.</span></span> <span data-ttu-id="8f698-105">只需单击每个链接并使用对话框即可选择对象或值并生成复杂的数据挖掘扩展插件 (DMX) 语句。</span><span class="sxs-lookup"><span data-stu-id="8f698-105">Just click each link, and use the dialog boxes to select objects or values and build complex Data Mining Extensions (DMX) statements.</span></span> <span data-ttu-id="8f698-106">可以将视图切换为文本编辑模型以手动修改 DMX 语句。</span><span class="sxs-lookup"><span data-stu-id="8f698-106">You can switch the view to text editing model to modify the DMX statement manually.</span></span>  
  
 <span data-ttu-id="8f698-107">若要转到**数据挖掘查询高级编辑器**，请单击 "**查询**"，然后单击 "**高级**"。</span><span class="sxs-lookup"><span data-stu-id="8f698-107">To get to the **Data Mining Query Advanced Editor**, click **Query** and then click **Advanced**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="8f698-108">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="8f698-108">UI element list</span></span>  
 <span data-ttu-id="8f698-109">**DMX“查询”窗格**</span><span class="sxs-lookup"><span data-stu-id="8f698-109">**DMX Query pane**</span></span>  
 <span data-ttu-id="8f698-110">您可以在此处查看当前 DMX 语句。</span><span class="sxs-lookup"><span data-stu-id="8f698-110">Here you can see the current DMX statement.</span></span>  
  
 <span data-ttu-id="8f698-111">在窗格中右键单击，可复制当前 DMX 语句。</span><span class="sxs-lookup"><span data-stu-id="8f698-111">Right-click in the pane to copy the current DMX statement.</span></span>  
  
 <span data-ttu-id="8f698-112">您还可在语句的任何突出显示部分上单击，打开特定于该子句的选项。</span><span class="sxs-lookup"><span data-stu-id="8f698-112">You can click any highlighted part of the statement to get options specific to that clause.</span></span> <span data-ttu-id="8f698-113">例如，若要删除、添加或编辑输出，请右键单击该 **\<Output>** 链接。</span><span class="sxs-lookup"><span data-stu-id="8f698-113">For example, to delete, add, or edit an output, right-click the **\<Output>** link.</span></span>  
  
 <span data-ttu-id="8f698-114">**编辑查询/查询生成器**</span><span class="sxs-lookup"><span data-stu-id="8f698-114">**Edit Query/Query Builder**</span></span>  
 <span data-ttu-id="8f698-115">使用此按钮可在文本编辑器之间切换编辑器，您可以在其中直接编写 DMX 语句;和**查询生成器**，可帮助您生成 DMX 语句。</span><span class="sxs-lookup"><span data-stu-id="8f698-115">Use this button to switch the editor between a text editor, where you can write DMX statements directly; and the **Query Builder**, which helps you build a DMX statement.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8f698-116">**警告：** 如果在运行查询之前切换视图，则会出现一条消息，指出可能会丢失某些更改。</span><span class="sxs-lookup"><span data-stu-id="8f698-116">**Warning:** If you switch views before the query has been run, a message appears stating that you might lose some changes.</span></span> <span data-ttu-id="8f698-117">如果 DMX 语句有效，在许多情况下，**查询生成器**可能会成功转换这些更改。</span><span class="sxs-lookup"><span data-stu-id="8f698-117">If the DMX statement is valid, in many cases the **Query Builder** might successfully convert these changes.</span></span> <span data-ttu-id="8f698-118">但是，如果您生成了特别复杂的 DMX 语句，则务必在切换视图之前保存您的工作。</span><span class="sxs-lookup"><span data-stu-id="8f698-118">However, if you have built a particularly complex DMX statement, you should definitely save your work before switching views.</span></span>  
  
 <span data-ttu-id="8f698-119">**DMX 模板**</span><span class="sxs-lookup"><span data-stu-id="8f698-119">**DMX Templates**</span></span>  
 <span data-ttu-id="8f698-120">单击，然后从包含 DMX 示例的模板列表中进行选择。</span><span class="sxs-lookup"><span data-stu-id="8f698-120">Click and select from a list of templates that contain DMX examples.</span></span> <span data-ttu-id="8f698-121">模板仅提供有关您可能需要的每种模型或预测查询的信息（包括使用嵌套表的查询）和用于管理模型的 DMX 语句。</span><span class="sxs-lookup"><span data-stu-id="8f698-121">The templates provide just about every type of model or prediction query that you might need, including queries that use nested tables, and DMX statements to manage models.</span></span> <span data-ttu-id="8f698-122">即使您有一定的 DMX 知识，模板也可以通过提供正确的语法来节省您的时间。</span><span class="sxs-lookup"><span data-stu-id="8f698-122">Even if you know some DMX, the templates can save you time by getting the syntax right.</span></span>  
  
 <span data-ttu-id="8f698-123">**选择模型**</span><span class="sxs-lookup"><span data-stu-id="8f698-123">**Choose Model**</span></span>  
 <span data-ttu-id="8f698-124">单击可查看当前连接上可用的数据挖掘模型的列表。</span><span class="sxs-lookup"><span data-stu-id="8f698-124">Click to view a list of data mining models available on the current connection.</span></span>  
  
 <span data-ttu-id="8f698-125">还可以通过单击 " **Dmx 查询**" 窗格中 dmx 语句中的模型名称来显示可用模型的列表。</span><span class="sxs-lookup"><span data-stu-id="8f698-125">You can also display a list of available models by clicking on the model name in the DMX statement in the **DMX Query** pane.</span></span> <span data-ttu-id="8f698-126">模型名称通常以红色突出显示。</span><span class="sxs-lookup"><span data-stu-id="8f698-126">The model name is typically highlighted in red.</span></span>  
  
 <span data-ttu-id="8f698-127">**选择输入**</span><span class="sxs-lookup"><span data-stu-id="8f698-127">**Select Input**</span></span>  
 <span data-ttu-id="8f698-128">单击可选择用作挖掘模型的输入的数据。</span><span class="sxs-lookup"><span data-stu-id="8f698-128">Click to choose the data to use as input to the mining model.</span></span> <span data-ttu-id="8f698-129">如果未指定数据源，还可以单击 " **\<Input>** **DMX 查询**" 窗格中以红色突出显示的链接。</span><span class="sxs-lookup"><span data-stu-id="8f698-129">If no data source has been specified, you can also click the **\<Input>** link, which is highlighted in red in the **DMX Query** pane.</span></span>  
  
 <span data-ttu-id="8f698-130">从下拉列表中选择 " \*\* \@ InputRowset\*\* " 以打开 "**替换 InputRowset** " 对话框，并修改现有输入。</span><span class="sxs-lookup"><span data-stu-id="8f698-130">Select **\@InputRowset** from the dropdown list to open the **Replace InputRowset** dialog box and modify an existing input.</span></span>  
  
 <span data-ttu-id="8f698-131">选择 "**添加输入**" 可打开 "**添加输入**" 对话框，并指定新数据源。</span><span class="sxs-lookup"><span data-stu-id="8f698-131">Select **Add Input** to open the **Add Input** dialog box and specify a new data source.</span></span>  
  
 <span data-ttu-id="8f698-132">您还可以通过单击 " \*\* \@ InputRowset\*\* " 链接来修改现有的输入，该链接在 "DMX 查询" 窗格中以红色突出显示。</span><span class="sxs-lookup"><span data-stu-id="8f698-132">You can also modify an existing input by clicking the **\@InputRowset** link, which is highlighted in red in the DMX Query pane.</span></span>  
  
 <span data-ttu-id="8f698-133">**地图列**</span><span class="sxs-lookup"><span data-stu-id="8f698-133">**Map Columns**</span></span>  
 <span data-ttu-id="8f698-134">从挖掘模型中选择列，然后将这些列映射到外部数据源中的列。</span><span class="sxs-lookup"><span data-stu-id="8f698-134">Select columns from the mining model and then map them to columns in the external data source.</span></span>  
  
 <span data-ttu-id="8f698-135">还可以单击 **\<Mapping>** "DMX 查询" 窗格中突出显示的链接。</span><span class="sxs-lookup"><span data-stu-id="8f698-135">You can also click the highlighted **\<Mapping>** link in the DMX Query pane.</span></span>  
  
 <span data-ttu-id="8f698-136">**添加输出**</span><span class="sxs-lookup"><span data-stu-id="8f698-136">**Add Output**</span></span>  
 <span data-ttu-id="8f698-137">单击可选择应作为预测查询的一部分输出的列。</span><span class="sxs-lookup"><span data-stu-id="8f698-137">Click to choose the columns that should be output as part of a prediction query.</span></span>  
  
 <span data-ttu-id="8f698-138">还可以单击 **\<Add Output>** "DMX 查询" 窗格中突出显示的链接。</span><span class="sxs-lookup"><span data-stu-id="8f698-138">You can also click the highlighted **\<Add Output>** link in the DMX Query pane.</span></span>  
  
 <span data-ttu-id="8f698-139">**模型列**</span><span class="sxs-lookup"><span data-stu-id="8f698-139">**Model Columns**</span></span>  
 <span data-ttu-id="8f698-140">列出所选挖掘模型中的列。</span><span class="sxs-lookup"><span data-stu-id="8f698-140">Lists the columns in the selected mining model.</span></span> <span data-ttu-id="8f698-141">列名旁边的菱形标记表明该列是可预测列。</span><span class="sxs-lookup"><span data-stu-id="8f698-141">A diamond mark next to the column name indicates that the column is a predictable column.</span></span>  
  
 <span data-ttu-id="8f698-142">**输入列**</span><span class="sxs-lookup"><span data-stu-id="8f698-142">**Input Columns**</span></span>  
 <span data-ttu-id="8f698-143">列出外部数据源中已被添加为输入的列。</span><span class="sxs-lookup"><span data-stu-id="8f698-143">Lists the columns from the external data source that have been added as inputs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f698-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8f698-144">See Also</span></span>  
 [<span data-ttu-id="8f698-145">查询 &#40;SQL Server 数据挖掘外接程序&#41;</span><span class="sxs-lookup"><span data-stu-id="8f698-145">Query &#40;SQL Server Data Mining Add-ins&#41;</span></span>](query-sql-server-data-mining-add-ins.md)  
  
  
