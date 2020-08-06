---
title: 配置 Foreach 循环容器 |Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Foreach Loop containers
- containers [Integration Services], Foreach Loop
ms.assetid: 519c6f96-5e1f-47d2-b96a-d49946948c25
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 85fb399f51e22e091fac9b1d8d332b9a12e7d77e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578362"
---
# <a name="configure-a-foreach-loop-container"></a><span data-ttu-id="45193-102">配置 Foreach 循环容器</span><span class="sxs-lookup"><span data-stu-id="45193-102">Configure a Foreach Loop Container</span></span>
  <span data-ttu-id="45193-103">此过程介绍如何配置 Foreach 循环容器，包括如何在枚举器级和容器级上配置属性表达式。</span><span class="sxs-lookup"><span data-stu-id="45193-103">This procedure describes how to configure a Foreach Loop container, including property expressions at the enumerator and container levels.</span></span>  
  
### <a name="to-configure-the-foreach-loop-container"></a><span data-ttu-id="45193-104">配置 Foreach 循环容器</span><span class="sxs-lookup"><span data-stu-id="45193-104">To configure the Foreach Loop container</span></span>  
  
1.  <span data-ttu-id="45193-105">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="45193-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="45193-106">单击“控制流”  选项卡，然后双击 Foreach 循环。</span><span class="sxs-lookup"><span data-stu-id="45193-106">Click the **Control Flow** tab and double-click the Foreach Loop.</span></span>  
  
3.  <span data-ttu-id="45193-107">在 **“Foreach 循环编辑器”** 对话框中，单击 **“常规”** ，并且，根据需要还可以修改 Foreach 循环的名称和说明。</span><span class="sxs-lookup"><span data-stu-id="45193-107">In the **Foreach Loop Editor** dialog box, click **General** and, optionally, modify the name and description of the Foreach Loop.</span></span>  
  
4.  <span data-ttu-id="45193-108">单击 **“集合”** ，然后从 **“枚举器”** 列表中选择一个枚举器类型。</span><span class="sxs-lookup"><span data-stu-id="45193-108">Click **Collection** and select an enumerator type from the **Enumerator** list.</span></span>  
  
5.  <span data-ttu-id="45193-109">指定一个枚举器并对枚举器选项进行如下设置：</span><span class="sxs-lookup"><span data-stu-id="45193-109">Specify an enumerator and set enumerator options as follows:</span></span>  
  
    -   <span data-ttu-id="45193-110">若要使用 Foreach 文件枚举器，请提供包含要枚举的文件的文件夹，指定文件名和文件类型筛选器，并指定是否返回完全合格的文件名。</span><span class="sxs-lookup"><span data-stu-id="45193-110">To usethe Foreach File enumerator, provide the folder that contains the files to enumerate, specify a filter for the file name and type, and specify whether the fully qualified file name should be returned.</span></span> <span data-ttu-id="45193-111">另外，还请指定是否包含子文件夹，以枚举更多文件。</span><span class="sxs-lookup"><span data-stu-id="45193-111">Also, indicate whether to recurse through subfolders for more files.</span></span>  
  
    -   <span data-ttu-id="45193-112">若要使用 Foreach 项枚举器，请单击 **“列”** ，然后在 **“For Each Item 列”** 对话框中，单击 **“添加”** 来添加列。</span><span class="sxs-lookup"><span data-stu-id="45193-112">To use the Foreach Item enumerator, click **Columns**, and, in the **For Each Item Columns** dialog box, click **Add** to add columns.</span></span> <span data-ttu-id="45193-113">在 **“数据类型”** 列表中为每个列选择一个数据类型，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="45193-113">Select a data type in the **Data Type** list for each column, and click **OK**.</span></span>  
  
         <span data-ttu-id="45193-114">在列中键入值或从列表中选择值。</span><span class="sxs-lookup"><span data-stu-id="45193-114">Type values in the columns or select values from lists.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="45193-115">若要添加新行，请在刚才输入的单元格之外，单击任一位置。</span><span class="sxs-lookup"><span data-stu-id="45193-115">To add a new row, click anywhere outside the cell in which you typed.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="45193-116">如果值与列数据类型不兼容，文本将突出显示。</span><span class="sxs-lookup"><span data-stu-id="45193-116">If a value is not compatible with the column data type, the text is highlighted.</span></span>  
  
    -   <span data-ttu-id="45193-117">若要使用 Foreach ADO 枚举器，请选择一个现有的变量，或在 **“ADO 对象源变量”** 列表，单击 **“新建变量”** 来指定一个变量（包含要枚举的 ADO 对象的名称），然后选择一个枚举模式选项。</span><span class="sxs-lookup"><span data-stu-id="45193-117">To use the Foreach ADO enumerator, select an existing variable or click **New variable** in the **ADO object source variable** list to specify the variable that contains the name of the ADO object to enumerate, and select an enumeration mode option.</span></span>  
  
         <span data-ttu-id="45193-118">如果要创建新变量，请在 **“添加变量”** 对话框中设置该变量的属性。</span><span class="sxs-lookup"><span data-stu-id="45193-118">If creating a new variable, set the variable properties in the **Add Variable** dialog box.</span></span>  
  
    -   <span data-ttu-id="45193-119">若要使用 Foreach ADO.NET 架构行集枚举器，请选择一个现有的 ADO.NET 连接，或在 **“连接”** 列表中，单击 **“新建连接”** ，然后选择一个架构。</span><span class="sxs-lookup"><span data-stu-id="45193-119">To use the Foreach ADO.NET Schema Rowset enumerator, select an existing ADO.NET connection or click **New connection** in the **Connection** list, and then select a schema.</span></span>  
  
         <span data-ttu-id="45193-120">也可以单击 **“设置限制”** ，选择架构限制，选择包含限制值的变量，或键入限制值，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="45193-120">Optionally, click **Set Restrictions** and select schema restrictions, select the variable that contains the restriction value or type the restriction value, and click **OK**.</span></span>  
  
    -   <span data-ttu-id="45193-121">若要使用 Foreach 源变量枚举器，请在 **“变量”** 列表中选择变量。</span><span class="sxs-lookup"><span data-stu-id="45193-121">To use the Foreach From Variable enumerator, select a variable in the **Variable** list.</span></span>  
  
    -   <span data-ttu-id="45193-122">若要使用 Foreach NodeList 枚举器，请单击 DocumentSourceType 并从列表中选择源类型，然后单击 DocumentSource。</span><span class="sxs-lookup"><span data-stu-id="45193-122">To use the Foreach NodeList enumerator, click DocumentSourceType and select the source type from the list, and then click DocumentSource.</span></span> <span data-ttu-id="45193-123">根据为 DocumentSourceType 选择的值，请从列表中选择变量或文件连接，或创建新变量或文件连接，或在“文档源编辑器”  中键入 XML 源代码。</span><span class="sxs-lookup"><span data-stu-id="45193-123">Depending on the value selected for DocumentSourceType, select a variable or a file connection from the list, create a new variable or file connection, or type the XML source in the **Document Source Editor**.</span></span>  
  
         <span data-ttu-id="45193-124">接下来，单击 EnumerationType 并从列表中选择枚举类型。</span><span class="sxs-lookup"><span data-stu-id="45193-124">Next, click EnumerationType and select an enumeration type from the list.</span></span> <span data-ttu-id="45193-125">如果 EnumerationType 是 **Navigator、Node 或 NodeText**，则单击 OuterXPathStringSourceType 并选择源类型，然后单击 OuterXPathString。</span><span class="sxs-lookup"><span data-stu-id="45193-125">If EnumerationType is **Navigator, Node, or NodeText**, click OuterXPathStringSourceType and select the source type, and then click OuterXPathString.</span></span> <span data-ttu-id="45193-126">根据为 OuterXPathStringSourceType 设置的值，请从列表中选择变量或文件连接，或创建新的变量或文件连接，或键入外部 XML 路径语言 (XPath) 表达式的字符串。</span><span class="sxs-lookup"><span data-stu-id="45193-126">Depending on the value set for OuterXPathStringSourceType, select a variable or a file connection from the list, create a new variable or file connection, or type the string for the outer XML Path Language (XPath) expression.</span></span>  
  
         <span data-ttu-id="45193-127">如果 EnumerationType 是 **ElementCollection**，则按上文所述设置 OuterXPathStringSourceType 和 OuterXPathString。</span><span class="sxs-lookup"><span data-stu-id="45193-127">If EnumerationType is **ElementCollection**,set OuterXPathStringSourceType and OuterXPathString as described above.</span></span> <span data-ttu-id="45193-128">然后，单击 InnerElementType 并选择内部元素的枚举类型，然后单击 InnerXPathStringSourceType。</span><span class="sxs-lookup"><span data-stu-id="45193-128">Then, click InnerElementType and select an enumeration type for the inner elements, and then click InnerXPathStringSourceType.</span></span> <span data-ttu-id="45193-129">根据为 InnerXPathStringSourceType 设置的值，请选择变量或文件连接，创建新的变量或文件连接，或键入内部 XPath 表达式的字符串。</span><span class="sxs-lookup"><span data-stu-id="45193-129">Depending on the value set for InnerXPathStringSourceType, select a variable or a file connection, create a new variable or file connection, or type the string for the inner XPath expression.</span></span>  
  
    -   <span data-ttu-id="45193-130">若要使用 Foreach SMO 枚举器，请选择一个现有的 ADO.NET 连接，或在 **“连接”** 列表中，单击 **“新建连接”** ，然后键入需要的字符串或单击 **“浏览”** 。</span><span class="sxs-lookup"><span data-stu-id="45193-130">To use the Foreach SMO enumerator, select an existing ADO.NET connection or click **New connection** in the **Connection** list, and then either type the string to use or click **Browse**.</span></span> <span data-ttu-id="45193-131">如果选择单击 **“浏览”** ，则请在 **“选择 SMO 枚举”** 对话框中，选择要枚举的对象类型和枚举类型，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="45193-131">If you click **Browse**, in the **Select SMO Enumeration** dialog box, select the object type to enumerate and the enumeration type, and click **OK**.</span></span>  
  
6.  <span data-ttu-id="45193-132">也可单击“集合”页上的“表达式”文本框中的浏览按钮 (…) 来创建可用于更新属性值的表达式    。</span><span class="sxs-lookup"><span data-stu-id="45193-132">Optionally, click the browse button **(...)** in the **Expressions** text box on the **Collection** page to create expressions that update property values.</span></span> <span data-ttu-id="45193-133">有关详细信息，请参阅 [添加或更改属性表达式](expressions/add-or-change-a-property-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="45193-133">For more information, see [Add or Change a Property Expression](expressions/add-or-change-a-property-expression.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="45193-134"> 在 **“属性”** 列表中列出的属性因枚举器而异。</span><span class="sxs-lookup"><span data-stu-id="45193-134">The properties listed in the **Property** list varies by enumerator.</span></span>  
  
7.  <span data-ttu-id="45193-135">也可以单击 **“变量映射”** ，将对象属性映射到集合值，然后进行下列操作：</span><span class="sxs-lookup"><span data-stu-id="45193-135">Optionally, click **Variable Mappings** to map object properties to the collection value, and then do the following:</span></span>  
  
    1.  <span data-ttu-id="45193-136">在“变量”列表中选择变量，或单击“\<New Variable>”创建新变量 。</span><span class="sxs-lookup"><span data-stu-id="45193-136">In the **Variables** list, select a variable or click **\<New Variable>** to create a new variable.</span></span>  
  
    2.  <span data-ttu-id="45193-137">如果要添加新变量，那么请在 **“添加变量”** 对话框中设置该变量的属性，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="45193-137">If you add a new variable, set the variable properties in the **Add Variable** dialog box and click **OK**.</span></span>  
  
    3.  <span data-ttu-id="45193-138">如果使用 For Each Item 枚举器，可以在 **“索引”** 列表中来更新索引值。</span><span class="sxs-lookup"><span data-stu-id="45193-138">If you use the For Each Item enumerator, you can update the index value in the **Index** list.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="45193-139">该索引值指示项中哪个列将映射到变量。</span><span class="sxs-lookup"><span data-stu-id="45193-139">The index value indicates which column in the item to map to the variable.</span></span> <span data-ttu-id="45193-140">只有 For Each Item 枚举器可以使用 0 以外的索引值。</span><span class="sxs-lookup"><span data-stu-id="45193-140">Only the For Each Item enumerator can use an index value other than 0.</span></span>  
  
8.  <span data-ttu-id="45193-141">也可以单击 **“表达式”** ，然后在 **“表达式”** 页上，为 Foreach 循环容器的属性创建属性表达式。</span><span class="sxs-lookup"><span data-stu-id="45193-141">Optionally, click **Expressions** and, on the **Expressions** page, create property expressions for the properties of the Foreach Loop container.</span></span> <span data-ttu-id="45193-142">有关详细信息，请参阅 [添加或更改属性表达式](expressions/add-or-change-a-property-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="45193-142">For more information, see [Add or Change a Property Expression](expressions/add-or-change-a-property-expression.md).</span></span>  
  
9. <span data-ttu-id="45193-143">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="45193-143">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45193-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="45193-144">See Also</span></span>  
 [<span data-ttu-id="45193-145">Foreach 循环容器</span><span class="sxs-lookup"><span data-stu-id="45193-145">Foreach Loop Container</span></span>](control-flow/foreach-loop-container.md)  
  
  
