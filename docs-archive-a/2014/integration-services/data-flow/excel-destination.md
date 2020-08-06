---
title: Excel 目标 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.exceldest.f1
helpviewer_keywords:
- destinations [Integration Services], Excel
- Excel [Integration Services]
ms.assetid: 37c07446-1264-4814-b4f5-9c66d333bb24
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3e959f14e52fc045cb0cbc2ba0255d20bd0356d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694060"
---
# <a name="excel-destination"></a><span data-ttu-id="9c40a-102">Excel 目标</span><span class="sxs-lookup"><span data-stu-id="9c40a-102">Excel Destination</span></span>
  <span data-ttu-id="9c40a-103">Excel 目标将数据加载到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel 工作簿中的工作表或范围中。</span><span class="sxs-lookup"><span data-stu-id="9c40a-103">The Excel destination loads data into worksheets or ranges in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel workbooks.</span></span>  
  
## <a name="access-modes"></a><span data-ttu-id="9c40a-104">访问模式</span><span class="sxs-lookup"><span data-stu-id="9c40a-104">Access Modes</span></span>  
 <span data-ttu-id="9c40a-105">Excel 目标为数据加载提供了三种数据访问模式：</span><span class="sxs-lookup"><span data-stu-id="9c40a-105">The Excel destination provides three different data access modes for loading data:</span></span>  
  
-   <span data-ttu-id="9c40a-106">表或视图。</span><span class="sxs-lookup"><span data-stu-id="9c40a-106">A table or view.</span></span>  
  
-   <span data-ttu-id="9c40a-107">变量中指定的表或视图。</span><span class="sxs-lookup"><span data-stu-id="9c40a-107">A table or view specified in a variable.</span></span>  
  
-   <span data-ttu-id="9c40a-108">SQL 语句的运行结果。</span><span class="sxs-lookup"><span data-stu-id="9c40a-108">The results of an SQL statement.</span></span> <span data-ttu-id="9c40a-109">查询可以是参数化查询。</span><span class="sxs-lookup"><span data-stu-id="9c40a-109">The query can be a parameterized query.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9c40a-110">在 Excel 中，工作表或范围等同于表或视图。</span><span class="sxs-lookup"><span data-stu-id="9c40a-110">In Excel, a worksheet or range is the equivalent of a table or view.</span></span> <span data-ttu-id="9c40a-111">Excel 源和目标编辑器中可用表的列表仅显示现有的工作表（以追加到电子表格名称之后的 $ 符号为标识，如 Sheet1$）和指定范围（以 $ 符号的缺失为标识，如 MyRange）。</span><span class="sxs-lookup"><span data-stu-id="9c40a-111">The lists of available tables in the Excel Source and Destination editors display only existing worksheets (identified by the $ sign appended to the worksheet name, such as Sheet1$) and named ranges (identified by the absence of the $ sign, such as MyRange).</span></span>  
  
## <a name="usage-considerations"></a><span data-ttu-id="9c40a-112">使用注意事项</span><span class="sxs-lookup"><span data-stu-id="9c40a-112">Usage Considerations</span></span>  
 <span data-ttu-id="9c40a-113">Excel 连接管理器使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for Jet 4.0 及其支持的 Excel ISAM（索引顺序存取方法）驱动程序来连接 Excel 数据源，并在 Excel 数据源中进行数据读写操作。</span><span class="sxs-lookup"><span data-stu-id="9c40a-113">The Excel Connection Manager uses the [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for Jet 4.0 and its supporting Excel ISAM (Indexed Sequential Access Method) driver to connect and read and write data to Excel data sources.</span></span>  
  
 <span data-ttu-id="9c40a-114">许多现有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 知识库文章都记录了该访问接口和驱动程序的行为。虽然这些文章并非专门介绍 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 或其前身 Data Transformation Services，但您仍可了解到一些可能导致意外结果的行为。</span><span class="sxs-lookup"><span data-stu-id="9c40a-114">Many existing [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base articles document the behavior of this provider and driver, and although these articles are not specific to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] or its predecessor Data Transformation Services, you may want to know about certain behaviors that can lead to unexpected results.</span></span> <span data-ttu-id="9c40a-115">有关 Excel 驱动程序的使用及行为的一般信息，请参阅 [如何将 ADO 与来自 Visual Basic 或 VBA 的 Excel 数据一起使用](https://support.microsoft.com/kb/257819)。</span><span class="sxs-lookup"><span data-stu-id="9c40a-115">For general information on the use and behavior of the Excel driver, see [HOWTO: Use ADO with Excel Data from Visual Basic or VBA](https://support.microsoft.com/kb/257819).</span></span>  
  
 <span data-ttu-id="9c40a-116">在将数据保存到 Excel 目标时，Excel 驱动程序所附带的 Jet 访问接口的以下行为可以导致意外的结果。</span><span class="sxs-lookup"><span data-stu-id="9c40a-116">The following behaviors of the Jet provider that is included with the Excel driver can lead to unexpected results when saving data to an Excel destination.</span></span>  
  
-   <span data-ttu-id="9c40a-117">**保存文本数据**。</span><span class="sxs-lookup"><span data-stu-id="9c40a-117">**Saving text data**.</span></span> <span data-ttu-id="9c40a-118">Excel 驱动程序将文本数据值保存到 Excel 目标时，驱动程序将在每个单元内的文本之前添加单引号字符 (') 以确保所保存的值将被解释为文本值。</span><span class="sxs-lookup"><span data-stu-id="9c40a-118">When the Excel driver saves text data values to an Excel destination, the driver precedes the text in each cell with the single quote character (') to ensure that the saved values will be interpreted as text values.</span></span> <span data-ttu-id="9c40a-119">如果拥有或要开发将读取或处理所保存的数据的其他应用程序，则可能需要包括特殊的措施，以处理位于每个文本值前面的单引号字符。</span><span class="sxs-lookup"><span data-stu-id="9c40a-119">If you have or develop other applications that read or process the saved data, you may need to include special handling for the single quote character that precedes each text value.</span></span>  
  
     <span data-ttu-id="9c40a-120">有关如何避免包括单引号的信息，请参阅 msdn.com 上的博客文章： [在 SSIS 包中使用 Excel 目标数据流组件时，单引号会在数据转换成 Excel 时追加到所有字符串](https://go.microsoft.com/fwlink/?LinkId=400876)。</span><span class="sxs-lookup"><span data-stu-id="9c40a-120">For information on how to avoid including the single quote, see this blog post, [Single quote is appended to all strings when data is transformed to excel when using Excel destination data flow component in SSIS package](https://go.microsoft.com/fwlink/?LinkId=400876), on msdn.com.</span></span>  
  
-   <span data-ttu-id="9c40a-121">**保存 memo (ntext) 数据**。</span><span class="sxs-lookup"><span data-stu-id="9c40a-121">**Saving memo (ntext) da**ta.</span></span> <span data-ttu-id="9c40a-122">若要将大于 255 个字符的字符串成功地保存到 Excel 列中，驱动程序必须将该目标列的数据类型识别为 **memo** ，而不是 **string**。</span><span class="sxs-lookup"><span data-stu-id="9c40a-122">Before you can successfully save strings longer than 255 characters to an Excel column, the driver must recognize the data type of the destination column as **memo** and not **string**.</span></span> <span data-ttu-id="9c40a-123">如果目标表中已存在数据行，则由驱动程序抽样的前几行的 memo 列中必须至少包含一个长度大于 255 个字符的值的实例。</span><span class="sxs-lookup"><span data-stu-id="9c40a-123">If the destination table already contains rows of data, then the first few rows that are sampled by the driver must contain at least one instance of a value longer than 255 characters in the memo column.</span></span> <span data-ttu-id="9c40a-124">如果目标表是在包设计或运行时创建的，则 CREATE TABLE 语句必须使用 LONGTEXT (或其同义词之一) 作为备注列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="9c40a-124">If the destination table is created during package design or at run time, then the CREATE TABLE statement must use LONGTEXT (or one of its synonyms) as the data type of the memo column.</span></span>  
  
-   <span data-ttu-id="9c40a-125">**数据类型**。</span><span class="sxs-lookup"><span data-stu-id="9c40a-125">**Data types**.</span></span> <span data-ttu-id="9c40a-126">Excel 驱动程序只识别有限的一组数据类型。</span><span class="sxs-lookup"><span data-stu-id="9c40a-126">The Excel driver recognizes only a limited set of data types.</span></span> <span data-ttu-id="9c40a-127">例如，所有数值列均解释为双精度 (DT_R8)，并且所有字符串列（除了 memo 列）均解释为 255 个字符的 Unicode 字符串 (DT_WSTR)。</span><span class="sxs-lookup"><span data-stu-id="9c40a-127">For example, all numeric columns are interpreted as doubles (DT_R8), and all string columns (other than memo columns) are interpreted as 255-character Unicode strings (DT_WSTR).</span></span> [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="9c40a-128">按如下所示方式映射 Excel 数据类型：</span><span class="sxs-lookup"><span data-stu-id="9c40a-128">maps the Excel data types as follows:</span></span>  
  
    -   <span data-ttu-id="9c40a-129">数值    双精度浮点 (DT_R8)</span><span class="sxs-lookup"><span data-stu-id="9c40a-129">Numeric    double-precision float (DT_R8)</span></span>  
  
    -   <span data-ttu-id="9c40a-130">货币     货币 (DT_CY)</span><span class="sxs-lookup"><span data-stu-id="9c40a-130">Currency     currency (DT_CY)</span></span>  
  
    -   <span data-ttu-id="9c40a-131">布尔     布尔 (DT_BOOL)</span><span class="sxs-lookup"><span data-stu-id="9c40a-131">Boolean     Boolean (DT_BOOL)</span></span>  
  
    -   <span data-ttu-id="9c40a-132">日期/时间 `datetime` (DT_DATE) </span><span class="sxs-lookup"><span data-stu-id="9c40a-132">Date/time     `datetime` (DT_DATE)</span></span>  
  
    -   <span data-ttu-id="9c40a-133">字符串     Unicode 字符串，长度为 255 (DT_WSTR)</span><span class="sxs-lookup"><span data-stu-id="9c40a-133">String     Unicode string, length 255 (DT_WSTR)</span></span>  
  
    -   <span data-ttu-id="9c40a-134">Memo     Unicode 文本流 (DT_NTEXT)</span><span class="sxs-lookup"><span data-stu-id="9c40a-134">Memo     Unicode text stream (DT_NTEXT)</span></span>  
  
-   <span data-ttu-id="9c40a-135">**数据类型和长度转换**。</span><span class="sxs-lookup"><span data-stu-id="9c40a-135">**Data type and length conversions**.</span></span> [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="9c40a-136">不隐式转换数据类型。</span><span class="sxs-lookup"><span data-stu-id="9c40a-136">does not implicitly convert data types.</span></span> <span data-ttu-id="9c40a-137">因此，在将 Excel 数据加载到非 Excel 目标中之前，可能需要使用“派生列”或“数据转换”转换机制显式地转换它，或者在将其加载到 Excel 目标中之前将其转换为非 Excel 数据。</span><span class="sxs-lookup"><span data-stu-id="9c40a-137">As a result, you may need to use the Derived Column or Data Conversion transformations to convert Excel data explicitly before loading it into a non-Excel destination, or to convert non-Excel data before loading it into an Excel destination.</span></span> <span data-ttu-id="9c40a-138">这种情况下，可能需要通过使用导入和导出向导（它将自动配置所需转换）来创建初始包。</span><span class="sxs-lookup"><span data-stu-id="9c40a-138">In this case, it may be useful to create the initial package by using the Import and Export Wizard, which configures the necessary conversions for you.</span></span> <span data-ttu-id="9c40a-139">下面是一些可能必需的转换的示例：</span><span class="sxs-lookup"><span data-stu-id="9c40a-139">Some examples of the conversions that may be required include the following:</span></span>  
  
    -   <span data-ttu-id="9c40a-140">Unicode Excel 字符串列与具有特定代码页的非 Unicode 字符串列之间的转换。</span><span class="sxs-lookup"><span data-stu-id="9c40a-140">Conversion between Unicode Excel string columns and non-Unicode string columns with specific codepages.</span></span>  
  
    -   <span data-ttu-id="9c40a-141">在 255 个字符的 Excel 字符串列和不同长度的字符串列之间转换。</span><span class="sxs-lookup"><span data-stu-id="9c40a-141">Conversion between 255-character Excel string columns and string columns of different lengths.</span></span>  
  
    -   <span data-ttu-id="9c40a-142">双精度 Excel 数值列与其他类型的数值列之间的转换。</span><span class="sxs-lookup"><span data-stu-id="9c40a-142">Conversion between double-precision Excel numeric columns and numeric columns of other types.</span></span>  
  
## <a name="configuration-of-the-excel-destination"></a><span data-ttu-id="9c40a-143">Excel 目标的配置</span><span class="sxs-lookup"><span data-stu-id="9c40a-143">Configuration of the Excel Destination</span></span>  
 <span data-ttu-id="9c40a-144">Excel 目标使用 Excel 连接管理器连接到数据源，而连接管理器指定要使用的工作簿文件。</span><span class="sxs-lookup"><span data-stu-id="9c40a-144">The Excel destination uses an Excel connection manager to connect to a data source, and the connection manager specifies the workbook file to use.</span></span> <span data-ttu-id="9c40a-145">有关详细信息，请参阅 [Excel Connection Manager](../connection-manager/excel-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="9c40a-145">For more information, see [Excel Connection Manager](../connection-manager/excel-connection-manager.md).</span></span>  
  
 <span data-ttu-id="9c40a-146">Excel 目标具有一个常规输入和一个错误输出。</span><span class="sxs-lookup"><span data-stu-id="9c40a-146">The Excel destination has one regular input and one error output.</span></span>  
  
 <span data-ttu-id="9c40a-147">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="9c40a-147">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="9c40a-148">有关可以在 **“Excel 目标编辑器”** 对话框中设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="9c40a-148">For more information about the properties that you can set in the **Excel Destination Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="9c40a-149">Excel 目标编辑器（“连接管理器”页）</span><span class="sxs-lookup"><span data-stu-id="9c40a-149">Excel Destination Editor &#40;Connection Manager Page&#41;</span></span>](../excel-destination-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="9c40a-150">Excel 目标编辑器（“映射”页）</span><span class="sxs-lookup"><span data-stu-id="9c40a-150">Excel Destination Editor &#40;Mappings Page&#41;</span></span>](../excel-destination-editor-mappings-page.md)  
  
-   [<span data-ttu-id="9c40a-151">Excel 目标编辑器（“错误输出”页）</span><span class="sxs-lookup"><span data-stu-id="9c40a-151">Excel Destination Editor &#40;Error Output Page&#41;</span></span>](../excel-destination-editor-error-output-page.md)  
  
 <span data-ttu-id="9c40a-152">**“高级编辑器”** 对话框反映了所有能以编程方式设置的属性。</span><span class="sxs-lookup"><span data-stu-id="9c40a-152">The **Advanced Editor** dialog box reflects all the properties that can be set programmatically.</span></span> <span data-ttu-id="9c40a-153">有关可以在 **“高级编辑器”** 对话框中或以编程方式设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="9c40a-153">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="9c40a-154">Common Properties</span><span class="sxs-lookup"><span data-stu-id="9c40a-154">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="9c40a-155">Excel 自定义属性</span><span class="sxs-lookup"><span data-stu-id="9c40a-155">Excel Custom Properties</span></span>](excel-custom-properties.md)  
  
 <span data-ttu-id="9c40a-156">有关如何设置属性的详细信息，请参阅 [设置数据流组件的属性](set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="9c40a-156">For more information about how to set properties, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="9c40a-157">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="9c40a-157">Related Tasks</span></span>  
  
-   [<span data-ttu-id="9c40a-158">使用 SQL Server Integration Services (SSIS) 将数据导入 Excel 或从 Excel 导出数据</span><span class="sxs-lookup"><span data-stu-id="9c40a-158">Import data from Excel or export data to Excel with SQL Server Integration Services (SSIS)</span></span>](../load-data-to-from-excel-with-ssis.md)  
  
-   [<span data-ttu-id="9c40a-159">使用 Foreach 循环容器循环遍历 Excel 文件和表</span><span class="sxs-lookup"><span data-stu-id="9c40a-159">Loop through Excel Files and Tables by Using a Foreach Loop Container</span></span>](../control-flow/foreach-loop-container.md)  
  
-   [<span data-ttu-id="9c40a-160">设置数据流组件的属性</span><span class="sxs-lookup"><span data-stu-id="9c40a-160">Set the Properties of a Data Flow Component</span></span>](set-the-properties-of-a-data-flow-component.md)  
  
## <a name="see-also"></a><span data-ttu-id="9c40a-161">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9c40a-161">See Also</span></span>  
 <span data-ttu-id="9c40a-162">[Excel 源](excel-source.md) </span><span class="sxs-lookup"><span data-stu-id="9c40a-162">[Excel Source](excel-source.md) </span></span>  
 <span data-ttu-id="9c40a-163">[Integration Services (SSIS) 变量](../integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="9c40a-163">[Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) </span></span>  
 <span data-ttu-id="9c40a-164">[数据流](data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="9c40a-164">[Data Flow](data-flow.md) </span></span>  
 [<span data-ttu-id="9c40a-165">使用脚本任务处理 Excel 文件</span><span class="sxs-lookup"><span data-stu-id="9c40a-165">Working with Excel Files with the Script Task</span></span>](../extending-packages-scripting-task-examples/working-with-excel-files-with-the-script-task.md)  
  
  
