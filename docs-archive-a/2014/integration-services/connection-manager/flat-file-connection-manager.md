---
title: 平面文件连接管理器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connection managers [Integration Services], Flat File
- connections [Integration Services], flat files
- files [Integration Services], connections
- Flat File connection manager
- flat files
- flat file connections [Integration Services]
ms.assetid: 7830f80d-af32-4e8f-a6fc-f03af6bc1946
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 961fa5ebd0c254c152cb4a84a855f719b6dfaa43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692470"
---
# <a name="flat-file-connection-manager"></a><span data-ttu-id="0a3b4-102">平面文件连接管理器</span><span class="sxs-lookup"><span data-stu-id="0a3b4-102">Flat File Connection Manager</span></span>
  <span data-ttu-id="0a3b4-103">平面文件连接管理器使包可以访问平面文件中的数据。</span><span class="sxs-lookup"><span data-stu-id="0a3b4-103">A Flat File connection manager enables a package to access data in a flat file.</span></span> <span data-ttu-id="0a3b4-104">例如，平面文件源和目标可以使用平面文件连接管理器提取和加载数据。</span><span class="sxs-lookup"><span data-stu-id="0a3b4-104">For example, the Flat File source and destination can use Flat File connection managers to extract and load data.</span></span>  
  
 <span data-ttu-id="0a3b4-105">平面文件连接管理器只能访问一个文件。</span><span class="sxs-lookup"><span data-stu-id="0a3b4-105">The Flat File connection manager can access only one file.</span></span> <span data-ttu-id="0a3b4-106">若要引用多个文件，请使用多平面文件连接管理器，而不用平面文件连接管理器。</span><span class="sxs-lookup"><span data-stu-id="0a3b4-106">To reference multiple files, use a Multiple Flat Files connection manager instead of a Flat File connection manager.</span></span> <span data-ttu-id="0a3b4-107">有关详细信息，请参阅 [Multiple Flat Files Connection Manager](multiple-flat-files-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="0a3b4-107">For more information, see [Multiple Flat Files Connection Manager](multiple-flat-files-connection-manager.md).</span></span>  
  
## <a name="column-length"></a><span data-ttu-id="0a3b4-108">列长度</span><span class="sxs-lookup"><span data-stu-id="0a3b4-108">Column Length</span></span>  
 <span data-ttu-id="0a3b4-109">默认情况下，平面文件连接管理器会将字符串列的长度设置为 50 个字符。</span><span class="sxs-lookup"><span data-stu-id="0a3b4-109">By default, the Flat File connection manager sets the length of string columns to 50 characters.</span></span> <span data-ttu-id="0a3b4-110">在 **“平面文件连接管理器编辑器”** 对话框中，可以计算示例数据，并自动调整这些列的长度，以防止发生数据截断或超过列宽的情况。</span><span class="sxs-lookup"><span data-stu-id="0a3b4-110">In the **Flat File Connection Manager Editor** dialog box, you can evaluate sample data and automatically resize the length of these columns to prevent truncation of data or excess column width.</span></span> <span data-ttu-id="0a3b4-111">而且，除非随后在平面文件源或转换中调整列长度，否则字符串列的列长度将在整个数据流中保持不变。</span><span class="sxs-lookup"><span data-stu-id="0a3b4-111">Also, unless you subsequently resize the column length in a Flat File source or a transformation, the column length of string column remains the same throughout the data flow.</span></span> <span data-ttu-id="0a3b4-112">如果这些字符串列映射到更窄的目标列，用户界面中将显示警告。</span><span class="sxs-lookup"><span data-stu-id="0a3b4-112">If these string columns map to destination columns that are narrower, warnings appear in the user interface.</span></span> <span data-ttu-id="0a3b4-113">此外，在运行时，可能由于数据截断而发生错误。</span><span class="sxs-lookup"><span data-stu-id="0a3b4-113">Moreover, at run time, errors may occur due to data truncation.</span></span> <span data-ttu-id="0a3b4-114">若要避免错误或截断，可以在平面文件连接管理器、平面文件源或转换中调整列的大小，以便与目标列兼容。</span><span class="sxs-lookup"><span data-stu-id="0a3b4-114">To avoid errors or truncation, you can resize the columns to be compatible with the destination columns in the Flat File connection manager, the Flat File source, or a transformation.</span></span> <span data-ttu-id="0a3b4-115">若要修改输出列的长度，请在 " `Length` **高级编辑器**" 对话框中的 "**输入和输出属性**" 选项卡上设置输出列的属性。</span><span class="sxs-lookup"><span data-stu-id="0a3b4-115">To modify the length of output columns, you set the `Length` property of the output column on the **Input and Output Properties** tab in the **Advanced Editor** dialog box.</span></span>  
  
 <span data-ttu-id="0a3b4-116">在已添加并配置使用连接管理器的平面文件源之后，如果在平面文件连接管理器中更新列长度，则不必在平面文件源中手动调整输出列的大小。</span><span class="sxs-lookup"><span data-stu-id="0a3b4-116">If you update column lengths in the Flat File connection manager after you have added and configured the Flat File source that uses the connection manager, you do not have to manually resize the output columns in the Flat File source.</span></span> <span data-ttu-id="0a3b4-117">打开 **“平面文件源”** 对话框时，平面文件源将提供同步列元数据的选项。</span><span class="sxs-lookup"><span data-stu-id="0a3b4-117">When you open the **Flat File Source** dialog box, the Flat File source provides an option to synchronize the column metadata.</span></span>  
  
## <a name="configuration-of-the-flat-file-connection-manager"></a><span data-ttu-id="0a3b4-118">平面文件连接管理器的配置</span><span class="sxs-lookup"><span data-stu-id="0a3b4-118">Configuration of the Flat File Connection Manager</span></span>  
 <span data-ttu-id="0a3b4-119">将平面文件连接管理器添加到包时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 会创建将在运行时解析为平面文件连接的连接管理器，设置平面文件连接属性，并将平面文件连接管理器添加到包的 `Connections` 集合。</span><span class="sxs-lookup"><span data-stu-id="0a3b4-119">When you add a Flat File connection manager to a package, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to a Flat File connection at run time, sets the Flat File connection properties, and adds the Flat File connection manager to the `Connections` collection of the package.</span></span>  
  
 <span data-ttu-id="0a3b4-120">该连接管理器的 `ConnectionManagerType` 属性设置为 `FLATFILE`。</span><span class="sxs-lookup"><span data-stu-id="0a3b4-120">The `ConnectionManagerType` property of the connection manager is set to `FLATFILE`.</span></span>  
  
 <span data-ttu-id="0a3b4-121">默认情况下，平面文件连接管理器始终检查未被引号引起的数据中的行分隔符，在找到行分隔符时开始一个新行。</span><span class="sxs-lookup"><span data-stu-id="0a3b4-121">By default, the Flat File connection manager always checks for a row delimiter in unquoted data, and starts a new row when a row delimiter is found.</span></span> <span data-ttu-id="0a3b4-122">这使连接管理器可以正确地分析具有缺少列字段的行的文件。</span><span class="sxs-lookup"><span data-stu-id="0a3b4-122">This enables the connection manager to correctly parse files with rows that are missing column fields.</span></span>  
  
 <span data-ttu-id="0a3b4-123">在某些情况下，禁用此功能可以提高包性能。</span><span class="sxs-lookup"><span data-stu-id="0a3b4-123">In some cases, disabling this feature may improve package performance.</span></span> <span data-ttu-id="0a3b4-124">通过将平面文件连接管理器属性**AlwaysCheckForRowDelimiters**设置为，可以禁用此功能 `False` 。</span><span class="sxs-lookup"><span data-stu-id="0a3b4-124">You can disable this feature by setting the Flat File connection manager property, **AlwaysCheckForRowDelimiters**, to `False`.</span></span>  
  
 <span data-ttu-id="0a3b4-125">可以按下列方式配置平面文件连接管理器：</span><span class="sxs-lookup"><span data-stu-id="0a3b4-125">You can configure the Flat File connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="0a3b4-126">指定要使用的文件、区域设置和代码页。</span><span class="sxs-lookup"><span data-stu-id="0a3b4-126">Specify the file, locale, and code page to use.</span></span> <span data-ttu-id="0a3b4-127">区域设置用于解释受区域设置影响的数据（如日期），代码页用于将字符串数据转换为 Unicode。</span><span class="sxs-lookup"><span data-stu-id="0a3b4-127">The locale is used to interpret locale-sensitive data such as dates, and the code page is used to convert string data to Unicode.</span></span>  
  
-   <span data-ttu-id="0a3b4-128">指定文件格式。</span><span class="sxs-lookup"><span data-stu-id="0a3b4-128">Specify the file format.</span></span> <span data-ttu-id="0a3b4-129">可以使用带分隔符、具有固定宽度或右边未对齐的文件格式。</span><span class="sxs-lookup"><span data-stu-id="0a3b4-129">You can use a delimited, fixed width, or ragged right format.</span></span>  
  
-   <span data-ttu-id="0a3b4-130">指定标题行、数据流和列分隔符。</span><span class="sxs-lookup"><span data-stu-id="0a3b4-130">Specify a header row, data row, and column delimiters.</span></span> <span data-ttu-id="0a3b4-131">列分隔符可以在文件级别设置，而在列级别被覆盖。</span><span class="sxs-lookup"><span data-stu-id="0a3b4-131">Column delimiters can be set at the file level and overwritten at the column level.</span></span>  
  
-   <span data-ttu-id="0a3b4-132">指示文件中的第一行是否包含列名称。</span><span class="sxs-lookup"><span data-stu-id="0a3b4-132">Indicate whether the first row in the file contains column names.</span></span>  
  
-   <span data-ttu-id="0a3b4-133">指定文本限定符。</span><span class="sxs-lookup"><span data-stu-id="0a3b4-133">Specify a text qualifier character.</span></span> <span data-ttu-id="0a3b4-134">可以将每一列配置为识别文本限定符。</span><span class="sxs-lookup"><span data-stu-id="0a3b4-134">Each column can be configured to recognize a text qualifier.</span></span>  
  
     <span data-ttu-id="0a3b4-135">现在支持将限定符嵌入限定的字符串。</span><span class="sxs-lookup"><span data-stu-id="0a3b4-135">The use of a qualifier character to embed a qualifier character into a qualified string is now supported.</span></span> <span data-ttu-id="0a3b4-136">文本限定符的双实例将被解释为文字，即该字符串的单个实例。</span><span class="sxs-lookup"><span data-stu-id="0a3b4-136">The double instance of a text qualifier is interpreted as a literal, single instance of that string.</span></span> <span data-ttu-id="0a3b4-137">例如，如果文本限定符是单引号并且输入数据为 'abc'、'def'、'g'hi'，则输出数据为 abc、def、g'hi。</span><span class="sxs-lookup"><span data-stu-id="0a3b4-137">For example, if the text qualifier is a single quote and the input data is 'abc', 'def', 'g'hi', the output data is abc, def, g'hi.</span></span>  
  
-   <span data-ttu-id="0a3b4-138">对各列设置诸如名称、数据类型和最大宽度等属性。</span><span class="sxs-lookup"><span data-stu-id="0a3b4-138">Set properties such as the name, data type, and maximum width on individual columns.</span></span>  
  
 <span data-ttu-id="0a3b4-139">通过在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]的“属性”窗口中指定表达式，可以设置平面文件连接管理器的 ConnectionString 属性。</span><span class="sxs-lookup"><span data-stu-id="0a3b4-139">You can set the ConnectionString property for the Flat File connection manager by specifying an expression in the Properties window of [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="0a3b4-140">为避免验证错误，请执行以下操作。</span><span class="sxs-lookup"><span data-stu-id="0a3b4-140">To avoid a validation error, do the following.</span></span>  
  
-   <span data-ttu-id="0a3b4-141">使用表达式指定文件时，在 **“平面文件连接管理器编辑器”** 的 **“文件名”** 框中添加文件路径。</span><span class="sxs-lookup"><span data-stu-id="0a3b4-141">When you use an expression to specify the file, add a file path in the **File name** box in the **Flat File Connection Manager Editor**.</span></span>  
  
-   <span data-ttu-id="0a3b4-142">将平面文件连接管理器的 **“DelayValidation”** 属性设置为 **“True”**。</span><span class="sxs-lookup"><span data-stu-id="0a3b4-142">Set the **DelayValidation** property on the Flat File connection manager to **True**.</span></span>  
  
 <span data-ttu-id="0a3b4-143">使用平面文件连接管理器和平面文件目标，您可以在运行时使用表达式创建文件名。</span><span class="sxs-lookup"><span data-stu-id="0a3b4-143">You can use an expression to create a file name at runtime by using the Flat File connection manager with the Flat File destination.</span></span>  
  
 <span data-ttu-id="0a3b4-144">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="0a3b4-144">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="0a3b4-145">有关可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="0a3b4-145">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="0a3b4-146">平面文件连接管理器编辑器（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="0a3b4-146">Flat File Connection Manager Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="0a3b4-147">平面文件连接管理器编辑器（“列”页）</span><span class="sxs-lookup"><span data-stu-id="0a3b4-147">Flat File Connection Manager Editor &#40;Columns Page&#41;</span></span>](../flat-file-connection-manager-editor-columns-page.md)  
  
-   [<span data-ttu-id="0a3b4-148">平面文件连接管理器编辑器（“高级”页）</span><span class="sxs-lookup"><span data-stu-id="0a3b4-148">Flat File Connection Manager Editor &#40;Advanced Page&#41;</span></span>](../flat-file-connection-manager-editor-advanced-page.md)  
  
-   [<span data-ttu-id="0a3b4-149">平面文件连接管理器编辑器（“预览”页）</span><span class="sxs-lookup"><span data-stu-id="0a3b4-149">Flat File Connection Manager Editor &#40;Preview Page&#41;</span></span>](../flat-file-connection-manager-editor-preview-page.md)  
  
 <span data-ttu-id="0a3b4-150">有关以编程方式配置连接管理器的信息，请参阅 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 和 [以编程方式添加连接](../building-packages-programmatically/adding-connections-programmatically.md)项目。</span><span class="sxs-lookup"><span data-stu-id="0a3b4-150">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
  
