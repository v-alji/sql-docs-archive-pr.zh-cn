---
title: 多平面文件连接管理器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Multiple Flat Files connection manager
- connections [Integration Services], flat files
- flat files
- flat file connections [Integration Services]
- connection managers [Integration Services], Multiple Flat Files
- multiple flat file connections
ms.assetid: 31fc3f7a-d323-44f5-a907-1fa3de66631a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a17125fedb495daabc4838161b3260c0d5590319
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589831"
---
# <a name="multiple-flat-files-connection-manager"></a><span data-ttu-id="61cf7-102">多平面文件连接管理器</span><span class="sxs-lookup"><span data-stu-id="61cf7-102">Multiple Flat Files Connection Manager</span></span>
  <span data-ttu-id="61cf7-103">多平面文件连接管理器使包可以访问多个平面文件中的数据。</span><span class="sxs-lookup"><span data-stu-id="61cf7-103">A Multiple Flat Files connection manager enables a package to access data in multiple flat files.</span></span> <span data-ttu-id="61cf7-104">例如，数据流任务在循环容器（例如 For 循环容器）内时，平面文件源可以使用多平面文件连接管理器。</span><span class="sxs-lookup"><span data-stu-id="61cf7-104">For example, a Flat File source can use a Multiple Flat Files connection manager when the Data Flow task is inside a loop container, such as the For Loop container.</span></span> <span data-ttu-id="61cf7-105">在容器的每个循环中，平面文件源从多平面文件连接管理器提供的下一个文件名加载数据。</span><span class="sxs-lookup"><span data-stu-id="61cf7-105">On each loop of the container, the Flat File source loads data from the next file name that the Multiple Flat Files connection manager provides.</span></span>  
  
 <span data-ttu-id="61cf7-106">将多平面文件连接管理器添加到包时，将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 创建一个连接管理器，该连接管理器将在运行时解析为多平面文件连接，设置多平面文件连接管理器的属性，并将多平面文件连接管理器添加到 `Connections` 包的集合。</span><span class="sxs-lookup"><span data-stu-id="61cf7-106">When you add a Multiple Flat Files connection manager to a package, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to a Multiple Flat Files connection at run time, sets the properties on the Multiple Flat Files connection manager, and adds the Multiple Flat Files connection manager to the `Connections` collection of the package.</span></span>  
  
 <span data-ttu-id="61cf7-107">该连接管理器的 `ConnectionManagerType` 属性设置为 `MULTIFLATFILE`。</span><span class="sxs-lookup"><span data-stu-id="61cf7-107">The `ConnectionManagerType` property of the connection manager is set to `MULTIFLATFILE`.</span></span>  
  
 <span data-ttu-id="61cf7-108">可以按下列方式配置多平面文件连接管理器：</span><span class="sxs-lookup"><span data-stu-id="61cf7-108">You can configure the Multiple Flat Files connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="61cf7-109">指定要使用的文件、区域设置和代码页。</span><span class="sxs-lookup"><span data-stu-id="61cf7-109">Specify the files, locale, and code page to use.</span></span> <span data-ttu-id="61cf7-110">区域设置用于解释受区域设置影响的数据（如日期），代码页用于将字符串数据转换为 Unicode。</span><span class="sxs-lookup"><span data-stu-id="61cf7-110">The locale is used to interpret locale-sensitive data such as dates, and the code page is used to convert string data to Unicode.</span></span>  
  
-   <span data-ttu-id="61cf7-111">指定文件格式。</span><span class="sxs-lookup"><span data-stu-id="61cf7-111">Specify the file format.</span></span> <span data-ttu-id="61cf7-112">可以使用带分隔符、具有固定宽度或右边未对齐的文件格式。</span><span class="sxs-lookup"><span data-stu-id="61cf7-112">You can use a delimited, fixed width, or ragged right format.</span></span>  
  
-   <span data-ttu-id="61cf7-113">指定标题行、数据流和列分隔符。</span><span class="sxs-lookup"><span data-stu-id="61cf7-113">Specify a header row, data row, and column delimiters.</span></span> <span data-ttu-id="61cf7-114">列分隔符可以在文件级别设置，而在列级别被覆盖。</span><span class="sxs-lookup"><span data-stu-id="61cf7-114">Column delimiters can be set at the file level and overwritten at the column level.</span></span>  
  
-   <span data-ttu-id="61cf7-115">指示文件中的第一行是否包含列名称。</span><span class="sxs-lookup"><span data-stu-id="61cf7-115">Indicate whether the first row in the files contains column names.</span></span>  
  
-   <span data-ttu-id="61cf7-116">指定文本限定符。</span><span class="sxs-lookup"><span data-stu-id="61cf7-116">Specify a text qualifier character.</span></span> <span data-ttu-id="61cf7-117">可以将每一列配置为识别文本限定符。</span><span class="sxs-lookup"><span data-stu-id="61cf7-117">Each column can be configured to recognize a text qualifier.</span></span>  
  
-   <span data-ttu-id="61cf7-118">对各列设置诸如名称、数据类型和最大宽度等属性。</span><span class="sxs-lookup"><span data-stu-id="61cf7-118">Set properties such as the name, data type, and maximum width on individual columns.</span></span>  
  
 <span data-ttu-id="61cf7-119">当多平面文件连接管理器引用多个文件时，文件的路径由竖线 (|) 分隔。</span><span class="sxs-lookup"><span data-stu-id="61cf7-119">When the Multiple Flat Files connection manager references multiple files, the paths of the files are separated by the pipe (|) character.</span></span> <span data-ttu-id="61cf7-120">连接管理器的 `ConnectionString` 属性的格式如下：</span><span class="sxs-lookup"><span data-stu-id="61cf7-120">The `ConnectionString` property of the connection manager has the following format:</span></span>  
  
 \<*path*>|\<*path*>  
  
 <span data-ttu-id="61cf7-121">也可以使用通配符来指定多个文件。</span><span class="sxs-lookup"><span data-stu-id="61cf7-121">You can also specify multiple files by using wildcard characters.</span></span> <span data-ttu-id="61cf7-122">例如，若要引用 C 驱动器上的所有文本文件， `ConnectionString` 可以将属性的值设置为 c： \\ \* .txt。</span><span class="sxs-lookup"><span data-stu-id="61cf7-122">For example, to reference all the text files on the C drive, the value of the `ConnectionString` property can be set to C:\\*.txt.</span></span>  
  
 <span data-ttu-id="61cf7-123">如果多平面文件连接管理器引用多个文件，则所有文件必须具有相同格式。</span><span class="sxs-lookup"><span data-stu-id="61cf7-123">If a Multiple Flat Files connection manager references multiple files, all the files must have the same format.</span></span>  
  
 <span data-ttu-id="61cf7-124">默认情况下，多平面文件连接管理器将字符串列的长度设置为 50 个字符。</span><span class="sxs-lookup"><span data-stu-id="61cf7-124">By default, the Multiple Flat Files connection manager sets the length of string columns to 50 characters.</span></span> <span data-ttu-id="61cf7-125">在 **“多个平面文件连接管理器编辑器”** 对话框中，可以计算示例数据，并自动调整这些列的长度大小，以防止发生数据截断或超过列宽的情况。</span><span class="sxs-lookup"><span data-stu-id="61cf7-125">In the **Multiple Flat Files Connection Manager Editor** dialog box, you can evaluate sample data and automatically resize the length of these columns to prevent truncation of data or excess column width.</span></span> <span data-ttu-id="61cf7-126">除非在平面文件源或转换过程中调整列长度的大小，否则列长度将在整个数据流中保持不变。</span><span class="sxs-lookup"><span data-stu-id="61cf7-126">Unless you resize the column length in a Flat File source or a transformation, the column length remains the same throughout the data flow.</span></span> <span data-ttu-id="61cf7-127">如果这些列映射到更窄的目标列，则用户界面将显示警告，在运行时，则可能由于数据截断而发生错误。</span><span class="sxs-lookup"><span data-stu-id="61cf7-127">If these columns map to destination columns that are narrower, warnings appear in the user interface, and at run time, errors may occur due to data truncation.</span></span> <span data-ttu-id="61cf7-128">可以在平面文件连接管理器、平面文件源或转换过程中调整列的大小，以便与目标列兼容。</span><span class="sxs-lookup"><span data-stu-id="61cf7-128">You can resize the columns to be compatible with the destination columns in the Flat File connection manager, the Flat File source, or a transformation.</span></span> <span data-ttu-id="61cf7-129">若要修改输出列的长度，请在 " `Length` **高级编辑器**" 对话框中的 "**输入和输出属性**" 选项卡上设置输出列的属性。</span><span class="sxs-lookup"><span data-stu-id="61cf7-129">To modify the length of output columns, you set the `Length` property of the output column on the **Input and Output Properties** tab in the **Advanced Editor** dialog box.</span></span>  
  
 <span data-ttu-id="61cf7-130">在已添加并配置了使用连接管理器的平面文件源之后，如果在多平面文件连接管理器中更新了列长度，则不必在平面文件源中手动调整输出列的大小。</span><span class="sxs-lookup"><span data-stu-id="61cf7-130">If you update column lengths in the Multiple Flat Files connection manager after you have added and configured the Flat File source that uses the connection manager, you do not have to manually resize the output columns in the Flat File source.</span></span> <span data-ttu-id="61cf7-131">打开 **“平面文件源”** 对话框时，平面文件源将提供同步列元数据的选项。</span><span class="sxs-lookup"><span data-stu-id="61cf7-131">When you open the **Flat File Source** dialog box, the Flat File source provides an option to synchronize the column metadata.</span></span>  
  
## <a name="configuration-of-the-multiple-flat-files-connection-manager"></a><span data-ttu-id="61cf7-132">多平面文件连接管理器的配置</span><span class="sxs-lookup"><span data-stu-id="61cf7-132">Configuration of the Multiple Flat Files Connection Manager</span></span>  
 <span data-ttu-id="61cf7-133">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="61cf7-133">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="61cf7-134">有关可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="61cf7-134">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="61cf7-135">多平面文件连接管理器编辑器（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="61cf7-135">Multiple Flat Files Connection Manager Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="61cf7-136">多平面文件连接管理器编辑器（“列”页）</span><span class="sxs-lookup"><span data-stu-id="61cf7-136">Multiple Flat Files Connection Manager Editor &#40;Columns Page&#41;</span></span>](../multiple-flat-files-connection-manager-editor-columns-page.md)  
  
-   [<span data-ttu-id="61cf7-137">多平面文件连接管理器编辑器（“高级”页）</span><span class="sxs-lookup"><span data-stu-id="61cf7-137">Multiple Flat Files Connection Manager Editor &#40;Advanced Page&#41;</span></span>](../multiple-flat-files-connection-manager-editor-advanced-page.md)  
  
-   [<span data-ttu-id="61cf7-138">多平面文件连接管理器编辑器（“预览”页）</span><span class="sxs-lookup"><span data-stu-id="61cf7-138">Multiple Flat Files Connection Manager Editor &#40;Preview Page&#41;</span></span>](../multiple-flat-files-connection-manager-editor-preview-page.md)  
  
 <span data-ttu-id="61cf7-139">有关以编程方式配置连接管理器的信息，请参阅 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 和 [以编程方式添加连接](../building-packages-programmatically/adding-connections-programmatically.md)项目。</span><span class="sxs-lookup"><span data-stu-id="61cf7-139">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61cf7-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="61cf7-140">See Also</span></span>  
 <span data-ttu-id="61cf7-141">[平面文件源](../data-flow/flat-file-source.md) </span><span class="sxs-lookup"><span data-stu-id="61cf7-141">[Flat File Source](../data-flow/flat-file-source.md) </span></span>  
 <span data-ttu-id="61cf7-142">[平面文件目标](../data-flow/flat-file-destination.md) </span><span class="sxs-lookup"><span data-stu-id="61cf7-142">[Flat File Destination](../data-flow/flat-file-destination.md) </span></span>  
 [<span data-ttu-id="61cf7-143">Integration Services (SSIS) 连接</span><span class="sxs-lookup"><span data-stu-id="61cf7-143">Integration Services &#40;SSIS&#41; Connections</span></span>](integration-services-ssis-connections.md)  
  
  
