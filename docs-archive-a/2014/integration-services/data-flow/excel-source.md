---
title: Excel 源 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.excelsource.f1
helpviewer_keywords:
- Excel [Integration Services]
- sources [Integration Services], Excel
ms.assetid: e66349f3-b1b8-4763-89b7-7803541a4d62
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c1324ca9e9b9535b8598e3e2de22f6c06c350b7b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694062"
---
# <a name="excel-source"></a><span data-ttu-id="ed61f-102">Excel 源</span><span class="sxs-lookup"><span data-stu-id="ed61f-102">Excel Source</span></span>
  <span data-ttu-id="ed61f-103">Excel 源从 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel 工作簿的工作表或范围中提取数据。</span><span class="sxs-lookup"><span data-stu-id="ed61f-103">The Excel source extracts data from worksheets or ranges in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel workbooks.</span></span>  
  
 <span data-ttu-id="ed61f-104">Excel 源提供了四种提取数据的数据访问方式：</span><span class="sxs-lookup"><span data-stu-id="ed61f-104">The Excel source provides four different data access modes for extracting data:</span></span>  
  
-   <span data-ttu-id="ed61f-105">表或视图。</span><span class="sxs-lookup"><span data-stu-id="ed61f-105">A table or view.</span></span>  
  
-   <span data-ttu-id="ed61f-106">变量中指定的表或视图。</span><span class="sxs-lookup"><span data-stu-id="ed61f-106">A table or view specified in a variable.</span></span>  
  
-   <span data-ttu-id="ed61f-107">SQL 语句的运行结果。</span><span class="sxs-lookup"><span data-stu-id="ed61f-107">The results of an SQL statement.</span></span> <span data-ttu-id="ed61f-108">查询可以是参数化查询。</span><span class="sxs-lookup"><span data-stu-id="ed61f-108">The query can be a parameterized query.</span></span>  
  
-   <span data-ttu-id="ed61f-109">存储在变量中的 SQL 语句的运行结果。</span><span class="sxs-lookup"><span data-stu-id="ed61f-109">The results of an SQL statement stored in a variable.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ed61f-110">在 Excel 中，工作表或范围等同于表或视图。</span><span class="sxs-lookup"><span data-stu-id="ed61f-110">In Excel, a worksheet or range is the equivalent of a table or view.</span></span> <span data-ttu-id="ed61f-111">Excel 源和目标编辑器中的可用表列表显示现有工作表（以追加到工作表名称后的 $ 符号标识，如 Sheet1$）和命名区域（不用 $ 符号标识，如 MyRange）。</span><span class="sxs-lookup"><span data-stu-id="ed61f-111">The list of available tables in the Excel Source and Destination editors displays existing worksheets (identified by the $ sign appended to the worksheet name, such as Sheet1$) and named ranges (identified by the absence of the $ sign, such as MyRange).</span></span> <span data-ttu-id="ed61f-112">有关详细信息，请参阅“使用注意事项”部分。</span><span class="sxs-lookup"><span data-stu-id="ed61f-112">For more information, see the Usage Considerations section.</span></span>  
  
 <span data-ttu-id="ed61f-113">Excel 源使用 Excel 连接管理器与数据源建立连接，连接管理器可指定要使用的工作簿文件。</span><span class="sxs-lookup"><span data-stu-id="ed61f-113">The Excel source uses an Excel connection manager to connect to a data source, and the connection manager specifies the workbook file to use.</span></span> <span data-ttu-id="ed61f-114">有关详细信息，请参阅 [Excel Connection Manager](../connection-manager/excel-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="ed61f-114">For more information, see [Excel Connection Manager](../connection-manager/excel-connection-manager.md).</span></span>  
  
 <span data-ttu-id="ed61f-115">Excel 源有一个常规输出和一个错误输出。</span><span class="sxs-lookup"><span data-stu-id="ed61f-115">The Excel source has one regular output and one error output.</span></span>  
  
## <a name="usage-considerations"></a><span data-ttu-id="ed61f-116">使用注意事项</span><span class="sxs-lookup"><span data-stu-id="ed61f-116">Usage Considerations</span></span>  
 <span data-ttu-id="ed61f-117">Excel 连接管理器使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for Jet 4.0 及其支持的 Excel ISAM（索引顺序存取方法）驱动程序来连接 Excel 数据源，并在 Excel 数据源中进行数据读写操作。</span><span class="sxs-lookup"><span data-stu-id="ed61f-117">The Excel Connection Manager uses the [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for Jet 4.0 and its supporting Excel ISAM (Indexed Sequential Access Method) driver to connect and read and write data to Excel data sources.</span></span>  
  
 <span data-ttu-id="ed61f-118">许多现有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 知识库文章都记录了该访问接口和驱动程序的行为。虽然这些文章并非专门介绍 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 或其前身 Data Transformation Services，但您仍可了解到一些可能导致意外结果的行为。</span><span class="sxs-lookup"><span data-stu-id="ed61f-118">Many existing [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base articles document the behavior of this provider and driver, and although these articles are not specific to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] or its predecessor Data Transformation Services, you may want to know about certain behaviors that can lead to unexpected results.</span></span> <span data-ttu-id="ed61f-119">有关 Excel 驱动程序的使用及行为的一般信息，请参阅 [如何将 ADO 与来自 Visual Basic 或 VBA 的 Excel 数据一起使用](https://support.microsoft.com/kb/257819)。</span><span class="sxs-lookup"><span data-stu-id="ed61f-119">For general information on the use and behavior of the Excel driver, see [HOWTO: Use ADO with Excel Data from Visual Basic or VBA](https://support.microsoft.com/kb/257819).</span></span>  
  
 <span data-ttu-id="ed61f-120">当从 Excel 数据源读取数据时，Jet 访问接口和 Excel 驱动程序的下列行为可能会导致意外结果。</span><span class="sxs-lookup"><span data-stu-id="ed61f-120">The following behaviors of the Jet provider with the Excel driver can lead to unexpected results when reading data from an Excel data source.</span></span>  
  
-   <span data-ttu-id="ed61f-121">**数据源**。</span><span class="sxs-lookup"><span data-stu-id="ed61f-121">**Data sources**.</span></span> <span data-ttu-id="ed61f-122">Excel 工作簿中的数据源可以是工作表（必须追加 $ 符号，如 Sheet1$）或命名区域（如 MyRange）。</span><span class="sxs-lookup"><span data-stu-id="ed61f-122">The source of data in an Excel workbook can be a worksheet, to which the $ sign must be appended (for example, Sheet1$), or a named range (for example, MyRange).</span></span> <span data-ttu-id="ed61f-123">在 SQL 语句中，工作表的名称必须加以分隔（如 [Sheet1$]），以避免 $ 符号引起语法错误。</span><span class="sxs-lookup"><span data-stu-id="ed61f-123">In a SQL statement, the name of a worksheet must be delimited (for example, [Sheet1$]) to avoid a syntax error caused by the $ sign.</span></span> <span data-ttu-id="ed61f-124">查询生成器可自动添加这些分隔符。</span><span class="sxs-lookup"><span data-stu-id="ed61f-124">The Query Builder automatically adds these delimiters.</span></span> <span data-ttu-id="ed61f-125">指定工作表或范围时，该驱动程序将读取从工作表或范围左上角第一个非空单元开始的连续单元块。</span><span class="sxs-lookup"><span data-stu-id="ed61f-125">When you specify a worksheet or range, the driver reads the contiguous block of cells starting with the first non-empty cell in the upper-left corner of the worksheet or range.</span></span> <span data-ttu-id="ed61f-126">因此，源数据中不能有空行，在标题或页眉行与数据行之间也不能有空行。</span><span class="sxs-lookup"><span data-stu-id="ed61f-126">Therefore you cannot have empty rows in the source data, or an empty row between title or header rows and the data rows.</span></span>  
  
-   <span data-ttu-id="ed61f-127">**缺少值**。</span><span class="sxs-lookup"><span data-stu-id="ed61f-127">**Missing values**.</span></span> <span data-ttu-id="ed61f-128">Excel 驱动程序读取指定源中一定数量的行（默认情况下为 8 行）以推测每列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="ed61f-128">The Excel driver reads a certain number of rows (by default, 8 rows) in the specified source to guess at the data type of each column.</span></span> <span data-ttu-id="ed61f-129">如果推测出列可能包含混合数据类型（尤其是混合了文本数据的数值数据时），驱动程序将决定采用占多数的数据类型，并对包含其他类型数据的单元返回 Null 值。</span><span class="sxs-lookup"><span data-stu-id="ed61f-129">When a column appears to contain mixed data types, especially numeric data mixed with text data, the driver decides in favor of the majority data type, and returns null values for cells that contain data of the other type.</span></span> <span data-ttu-id="ed61f-130">（如果各种数据类型的数量相当，则采用数值类型。）Excel 工作表中大部分单元格格式设置选项不会影响此数据类型判断。</span><span class="sxs-lookup"><span data-stu-id="ed61f-130">(In a tie, the numeric type wins.) Most cell formatting options in the Excel worksheet do not seem to affect this data type determination.</span></span> <span data-ttu-id="ed61f-131">可以通过指定导入模式来修改 Excel 驱动程序的此行为。</span><span class="sxs-lookup"><span data-stu-id="ed61f-131">You can modify this behavior of the Excel driver by specifying Import Mode.</span></span> <span data-ttu-id="ed61f-132">若要指定导入模式，请在 `IMEX=1` "**属性**" 窗口中将添加到 Excel 连接管理器的连接字符串中的扩展属性的值。</span><span class="sxs-lookup"><span data-stu-id="ed61f-132">To specify Import Mode, add `IMEX=1` to the value of Extended Properties in the connection string of the Excel connection manager in the **Properties** window.</span></span> <span data-ttu-id="ed61f-133">有关详细信息，请参阅 [PRB: Excel Values Returned as NULL Using DAO OpenRecordset（PRB：使用 DAO OpenRecordset 返回的 Excel NULL 值）](https://support.microsoft.com/kb/194124)。</span><span class="sxs-lookup"><span data-stu-id="ed61f-133">For more information, see [PRB: Excel Values Returned as NULL Using DAO OpenRecordset](https://support.microsoft.com/kb/194124).</span></span>  
  
-   <span data-ttu-id="ed61f-134">**截断的文本**。</span><span class="sxs-lookup"><span data-stu-id="ed61f-134">**Truncated text**.</span></span> <span data-ttu-id="ed61f-135">驱动程序在确定 Excel 列是否包含文本数据时，它将基于采样的最长值来选择数据类型（字符串或 memo）。</span><span class="sxs-lookup"><span data-stu-id="ed61f-135">When the driver determines that an Excel column contains text data, the driver selects the data type (string or memo) based on the longest value that it samples.</span></span> <span data-ttu-id="ed61f-136">如果驱动程序没有在其采样的行中发现任何长于 255 个字符的值，那么它会将该列视为 255 个字符的字符串的列而不是 memo 列。</span><span class="sxs-lookup"><span data-stu-id="ed61f-136">If the driver does not discover any values longer than 255 characters in the rows that it samples, it treats the column as a 255-character string column instead of a memo column.</span></span> <span data-ttu-id="ed61f-137">因此，长度超过 255 个字符的值可能会被截断。</span><span class="sxs-lookup"><span data-stu-id="ed61f-137">Therefore, values longer than 255 characters may be truncated.</span></span> <span data-ttu-id="ed61f-138">若要从 memo 列导入数据而不发生截断，必须确保至少一个采样行中的 memo 列包含的值的长度超过 255 个字符，否则必须增加驱动程序采样的行数，使其包括这样的行。</span><span class="sxs-lookup"><span data-stu-id="ed61f-138">To import data from a memo column without truncation, you must make sure that the memo column in at least one of the sampled rows contains a value longer than 255 characters, or you must increase the number of rows sampled by the driver to include such a row.</span></span> <span data-ttu-id="ed61f-139">你可以通过增加 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Jet\4.0\Engines\Excel** 注册表项下的 **TypeGuessRows** 的值来增加用作示例的行数。</span><span class="sxs-lookup"><span data-stu-id="ed61f-139">You can increase the number of rows sampled by increasing the value of **TypeGuessRows** under the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Jet\4.0\Engines\Excel** registry key.</span></span> <span data-ttu-id="ed61f-140">有关详细信息，请参阅 [PRB：从 Jet 4.0 OLEDB 源传输数据失败并出现错误](https://support.microsoft.com/kb/281517)。</span><span class="sxs-lookup"><span data-stu-id="ed61f-140">For more information, see [PRB: Transfer of Data from Jet 4.0 OLEDB Source Fails w/ Error](https://support.microsoft.com/kb/281517).</span></span>  
  
-   <span data-ttu-id="ed61f-141">**数据类型**。</span><span class="sxs-lookup"><span data-stu-id="ed61f-141">**Data types**.</span></span> <span data-ttu-id="ed61f-142">Excel 驱动程序只识别有限的一组数据类型。</span><span class="sxs-lookup"><span data-stu-id="ed61f-142">The Excel driver recognizes only a limited set of data types.</span></span> <span data-ttu-id="ed61f-143">例如，所有数值列均解释为双精度 (DT_R8)，并且所有字符串列（除了 memo 列）均解释为 255 个字符的 Unicode 字符串 (DT_WSTR)。</span><span class="sxs-lookup"><span data-stu-id="ed61f-143">For example, all numeric columns are interpreted as doubles (DT_R8), and all string columns (other than memo columns) are interpreted as 255-character Unicode strings (DT_WSTR).</span></span> [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="ed61f-144">按如下所示方式映射 Excel 数据类型：</span><span class="sxs-lookup"><span data-stu-id="ed61f-144">maps the Excel data types as follows:</span></span>  
  
    -   <span data-ttu-id="ed61f-145">数值 - 双精度浮点 (DT_R8)</span><span class="sxs-lookup"><span data-stu-id="ed61f-145">Numeric - double-precision float (DT_R8)</span></span>  
  
    -   <span data-ttu-id="ed61f-146">货币 - 货币 (DT_CY)</span><span class="sxs-lookup"><span data-stu-id="ed61f-146">Currency - currency (DT_CY)</span></span>  
  
    -   <span data-ttu-id="ed61f-147">布尔 - 布尔 (DT_BOOL)</span><span class="sxs-lookup"><span data-stu-id="ed61f-147">Boolean - Boolean (DT_BOOL)</span></span>  
  
    -   <span data-ttu-id="ed61f-148">日期/时间- `datetime` (DT_DATE) </span><span class="sxs-lookup"><span data-stu-id="ed61f-148">Date/time - `datetime` (DT_DATE)</span></span>  
  
    -   <span data-ttu-id="ed61f-149">字符串 - Unicode 字符串，长度为 255 (DT_WSTR)</span><span class="sxs-lookup"><span data-stu-id="ed61f-149">String - Unicode string, length 255 (DT_WSTR)</span></span>  
  
    -   <span data-ttu-id="ed61f-150">Memo - Unicode 文本流 (DT_NTEXT)</span><span class="sxs-lookup"><span data-stu-id="ed61f-150">Memo - Unicode text stream (DT_NTEXT)</span></span>  
  
-   <span data-ttu-id="ed61f-151">**数据类型和长度转换**。</span><span class="sxs-lookup"><span data-stu-id="ed61f-151">**Data type and length conversions**.</span></span> [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="ed61f-152">不隐式转换数据类型。</span><span class="sxs-lookup"><span data-stu-id="ed61f-152">does not implicitly convert data types.</span></span> <span data-ttu-id="ed61f-153">因此，在将其加载到非 Excel 目标之前，可能需要使用“派生列”或“数据转换”转换来显式转换 Excel 数据，或在将它加载到 Excel 目标之前，对非 Excel 数据进行转换。</span><span class="sxs-lookup"><span data-stu-id="ed61f-153">As a result, you may need to use Derived Column or Data Conversion transformations to convert Excel data explicitly before loading it into a non-Excel destination, or to convert non-Excel data before loading it into an Excel destination.</span></span> <span data-ttu-id="ed61f-154">这种情况下，可能需要通过使用导入和导出向导（它将自动配置所需转换）来创建初始包。</span><span class="sxs-lookup"><span data-stu-id="ed61f-154">In this case, it may be useful to create the initial package by using the Import and Export Wizard, which configures the necessary conversions for you.</span></span> <span data-ttu-id="ed61f-155">下面是一些可能必需的转换的示例：</span><span class="sxs-lookup"><span data-stu-id="ed61f-155">Some examples of the conversions that may be required include the following:</span></span>  
  
    -   <span data-ttu-id="ed61f-156">Unicode Excel 字符串列与具有特定代码页的非 Unicode 字符串列之间的转换</span><span class="sxs-lookup"><span data-stu-id="ed61f-156">Conversion between Unicode Excel string columns and non-Unicode string columns with specific codepages</span></span>  
  
    -   <span data-ttu-id="ed61f-157">在 255 个字符的 Excel 字符串列和不同长度的字符串列之间转换</span><span class="sxs-lookup"><span data-stu-id="ed61f-157">Conversion between 255-character Excel string columns and string columns of different lengths</span></span>  
  
    -   <span data-ttu-id="ed61f-158">双精度 Excel 数值列与其他类型的数值列之间的转换</span><span class="sxs-lookup"><span data-stu-id="ed61f-158">Conversion between double-precision Excel numeric columns and numeric columns of other types</span></span>  
  
## <a name="excel-source-configuration"></a><span data-ttu-id="ed61f-159">Excel 源配置</span><span class="sxs-lookup"><span data-stu-id="ed61f-159">Excel Source Configuration</span></span>  
 <span data-ttu-id="ed61f-160">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="ed61f-160">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="ed61f-161">有关可以在 **“Excel 源编辑器”** 对话框中设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="ed61f-161">For more information about the properties that you can set in the **Excel Source Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="ed61f-162">Excel 源编辑器（“连接管理器”页）</span><span class="sxs-lookup"><span data-stu-id="ed61f-162">Excel Source Editor &#40;Connection Manager Page&#41;</span></span>](../excel-source-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="ed61f-163">Excel 源编辑器（“列”页）</span><span class="sxs-lookup"><span data-stu-id="ed61f-163">Excel Source Editor &#40;Columns Page&#41;</span></span>](../excel-source-editor-columns-page.md)  
  
-   [<span data-ttu-id="ed61f-164">Excel 源编辑器（“错误输出”页）</span><span class="sxs-lookup"><span data-stu-id="ed61f-164">Excel Source Editor &#40;Error Output Page&#41;</span></span>](../excel-source-editor-error-output-page.md)  
  
 <span data-ttu-id="ed61f-165">**“高级编辑器”** 对话框反映了所有能以编程方式设置的属性。</span><span class="sxs-lookup"><span data-stu-id="ed61f-165">The **Advanced Editor** dialog box reflects all the properties that can be set programmatically.</span></span> <span data-ttu-id="ed61f-166">有关可以在 **“高级编辑器”** 对话框中或以编程方式设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="ed61f-166">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="ed61f-167">Common Properties</span><span class="sxs-lookup"><span data-stu-id="ed61f-167">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="ed61f-168">Excel 自定义属性</span><span class="sxs-lookup"><span data-stu-id="ed61f-168">Excel Custom Properties</span></span>](excel-custom-properties.md)  
  
 <span data-ttu-id="ed61f-169">有关循环遍历 Excel 文件中的某个组的信息，请参阅 [使用 Foreach 循环容器，循环遍历 Excel 文件和表](../control-flow/foreach-loop-container.md)。</span><span class="sxs-lookup"><span data-stu-id="ed61f-169">For information about looping through a group of Excel files, see [Loop through Excel Files and Tables by Using a Foreach Loop Container](../control-flow/foreach-loop-container.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="ed61f-170">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="ed61f-170">Related Tasks</span></span>  

-   [<span data-ttu-id="ed61f-171">使用 SQL Server Integration Services (SSIS) 将数据导入 Excel 或从 Excel 导出数据</span><span class="sxs-lookup"><span data-stu-id="ed61f-171">Import data from Excel or export data to Excel with SQL Server Integration Services (SSIS)</span></span>](../load-data-to-from-excel-with-ssis.md)

-   [<span data-ttu-id="ed61f-172">将查询参数映射到数据流组件中的变量</span><span class="sxs-lookup"><span data-stu-id="ed61f-172">Map Query Parameters to Variables in a Data Flow Component</span></span>](map-query-parameters-to-variables-in-a-data-flow-component.md)  
  
-   [<span data-ttu-id="ed61f-173">设置数据流组件的属性</span><span class="sxs-lookup"><span data-stu-id="ed61f-173">Set the Properties of a Data Flow Component</span></span>](set-the-properties-of-a-data-flow-component.md)  
  
-   [<span data-ttu-id="ed61f-174">为合并转换和合并联接转换排序数据</span><span class="sxs-lookup"><span data-stu-id="ed61f-174">Sort Data for the Merge and Merge Join Transformations</span></span>](transformations/sort-data-for-the-merge-and-merge-join-transformations.md)  
  
-   [<span data-ttu-id="ed61f-175">使用 Foreach 循环容器循环遍历 Excel 文件和表</span><span class="sxs-lookup"><span data-stu-id="ed61f-175">Loop through Excel Files and Tables by Using a Foreach Loop Container</span></span>](../control-flow/foreach-loop-container.md)  
  
## <a name="related-content"></a><span data-ttu-id="ed61f-176">相关内容</span><span class="sxs-lookup"><span data-stu-id="ed61f-176">Related Content</span></span>  
  
-   <span data-ttu-id="ed61f-177">hrvoje.piasevoli.com 上的博客文章： [在 SSIS 中从 64 位 Excel 导入数据](https://go.microsoft.com/fwlink/?LinkId=217673)。</span><span class="sxs-lookup"><span data-stu-id="ed61f-177">Blog entry, [Importing data from 64-bit Excel in SSIS](https://go.microsoft.com/fwlink/?LinkId=217673), on hrvoje.piasevoli.com</span></span>  
  
-   <span data-ttu-id="ed61f-178">SSIS 中的博客文章[连接到 Excel (.xlsx) ](https://microsoft-ssis.blogspot.com/2014/02/connecting-to-excel-xlsx-in-ssis.html)。</span><span class="sxs-lookup"><span data-stu-id="ed61f-178">Blog entry, [Connecting to Excel (XLSX) in SSIS](https://microsoft-ssis.blogspot.com/2014/02/connecting-to-excel-xlsx-in-ssis.html).</span></span>  
  
  
