---
title: Foreach 循环编辑器 (收集页面) |Microsoft Docs
ms.custom: ''
ms.date: 08/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.foreachloopcontainer.collection.f1
ms.assetid: 95a19dde-61ca-4d9b-aa3d-131fa4264296
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a90ce0c8971c57ef90b502cfde298605a73c253d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694524"
---
# <a name="foreach-loop-editor-collection-page"></a><span data-ttu-id="b39dc-102">Foreach 循环编辑器（“集合”页）</span><span class="sxs-lookup"><span data-stu-id="b39dc-102">Foreach Loop Editor (Collection Page)</span></span>
  <span data-ttu-id="b39dc-103">可以使用“Foreach 循环编辑器”\*\*\*\* 对话框的“集合”\*\*\*\* 页，指定枚举器类型以及配置枚举器。</span><span class="sxs-lookup"><span data-stu-id="b39dc-103">Use the **Collection** pageof the **Foreach Loop Editor** dialog box to specify the enumerator type and configure the enumerator.</span></span>  
  
 <span data-ttu-id="b39dc-104">若要了解有关 Foreach 循环容器以及如何对其进行配置的信息，请参阅 [Foreach 循环容器](control-flow/foreach-loop-container.md) 和 [配置 Foreach 循环容器](../../2014/integration-services/configure-a-foreach-loop-container.md)。</span><span class="sxs-lookup"><span data-stu-id="b39dc-104">To learn about the Foreach Loop container and how to configure it, see [Foreach Loop Container](control-flow/foreach-loop-container.md) and [Configure a Foreach Loop Container](../../2014/integration-services/configure-a-foreach-loop-container.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="b39dc-105">静态选项</span><span class="sxs-lookup"><span data-stu-id="b39dc-105">Static Options</span></span>  
 <span data-ttu-id="b39dc-106">**枚举器**</span><span class="sxs-lookup"><span data-stu-id="b39dc-106">**Enumerator**</span></span>  
 <span data-ttu-id="b39dc-107">从列表中选择枚举器类型。</span><span class="sxs-lookup"><span data-stu-id="b39dc-107">Select the enumerator type from the list.</span></span> <span data-ttu-id="b39dc-108">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="b39dc-108">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="b39dc-109">值</span><span class="sxs-lookup"><span data-stu-id="b39dc-109">Value</span></span>|<span data-ttu-id="b39dc-110">说明</span><span class="sxs-lookup"><span data-stu-id="b39dc-110">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b39dc-111">**Foreach 文件枚举器**</span><span class="sxs-lookup"><span data-stu-id="b39dc-111">**Foreach File Enumerator**</span></span>|<span data-ttu-id="b39dc-112">枚举文件。</span><span class="sxs-lookup"><span data-stu-id="b39dc-112">Enumerate files.</span></span> <span data-ttu-id="b39dc-113">选择此值将显示 **“Foreach 文件枚举器”** 部分中的动态选项。</span><span class="sxs-lookup"><span data-stu-id="b39dc-113">Selecting this value displays the dynamic options in the section, **Foreach File Enumerator**.</span></span>|  
|<span data-ttu-id="b39dc-114">**Foreach 项枚举器**</span><span class="sxs-lookup"><span data-stu-id="b39dc-114">**Foreach Item Enumerator**</span></span>|<span data-ttu-id="b39dc-115">枚举项中的值。</span><span class="sxs-lookup"><span data-stu-id="b39dc-115">Enumerate values in an item.</span></span> <span data-ttu-id="b39dc-116">选择此值将显示 **“Foreach Item 枚举器”** 部分中的动态选项。</span><span class="sxs-lookup"><span data-stu-id="b39dc-116">Selecting this value displays the dynamic options in the section, **Foreach Item Enumerator**.</span></span>|  
|<span data-ttu-id="b39dc-117">**Foreach ADO 枚举器**</span><span class="sxs-lookup"><span data-stu-id="b39dc-117">**Foreach ADO Enumerator**</span></span>|<span data-ttu-id="b39dc-118">枚举表或表中的行。</span><span class="sxs-lookup"><span data-stu-id="b39dc-118">Enumerate tables or rows in tables.</span></span> <span data-ttu-id="b39dc-119">选择此值将显示 **“Foreach ADO 枚举器”** 部分中的动态选项。</span><span class="sxs-lookup"><span data-stu-id="b39dc-119">Selecting this value displays the dynamic options in the section, **Foreach ADO Enumerator**.</span></span>|  
|<span data-ttu-id="b39dc-120">**Foreach ADO.NET 架构行集枚举器**</span><span class="sxs-lookup"><span data-stu-id="b39dc-120">**Foreach ADO.NET Schema Rowset Enumerator**</span></span>|<span data-ttu-id="b39dc-121">枚举架构。</span><span class="sxs-lookup"><span data-stu-id="b39dc-121">Enumerate a schema.</span></span> <span data-ttu-id="b39dc-122">选择此值将显示 **“Foreach ADO.NET 枚举器”** 部分中的动态选项。</span><span class="sxs-lookup"><span data-stu-id="b39dc-122">Selecting this value displays the dynamic options in the section, **Foreach ADO.NET Enumerator**.</span></span>|  
|<span data-ttu-id="b39dc-123">**Foreach 源变量枚举器**</span><span class="sxs-lookup"><span data-stu-id="b39dc-123">**Foreach From Variable Enumerator**</span></span>|<span data-ttu-id="b39dc-124">枚举变量中的值。</span><span class="sxs-lookup"><span data-stu-id="b39dc-124">Enumerate the value in a variable.</span></span> <span data-ttu-id="b39dc-125">选择此值将显示 **“Foreach 源变量枚举器”** 部分中的动态选项。</span><span class="sxs-lookup"><span data-stu-id="b39dc-125">Selecting this value displays the dynamic options in the section, **Foreach From Variable Enumerator**.</span></span>|  
|<span data-ttu-id="b39dc-126">**Foreach Nodelist 枚举器**</span><span class="sxs-lookup"><span data-stu-id="b39dc-126">**Foreach Nodelist Enumerator**</span></span>|<span data-ttu-id="b39dc-127">枚举 XML 文档中的节点。</span><span class="sxs-lookup"><span data-stu-id="b39dc-127">Enumerate nodes in an XML document.</span></span> <span data-ttu-id="b39dc-128">选择此值将显示 **“Foreach Nodelist 枚举器”** 部分中的动态选项。</span><span class="sxs-lookup"><span data-stu-id="b39dc-128">Selecting this value displays the dynamic options in the section, **Foreach Nodelist Enumerator**.</span></span>|  
|<span data-ttu-id="b39dc-129">**Foreach SMO 枚举器**</span><span class="sxs-lookup"><span data-stu-id="b39dc-129">**Foreach SMO Enumerator**</span></span>|<span data-ttu-id="b39dc-130">枚举 SMO 对象。</span><span class="sxs-lookup"><span data-stu-id="b39dc-130">Enumerate a SMO object.</span></span> <span data-ttu-id="b39dc-131">选择此值将显示 **“Foreach SMO 枚举器”** 部分中的动态选项。</span><span class="sxs-lookup"><span data-stu-id="b39dc-131">Selecting this value displays the dynamic options in the section, **Foreach SMO Enumerator**.</span></span>|  
|<span data-ttu-id="b39dc-132">**Foreach Azure Blob 枚举器**</span><span class="sxs-lookup"><span data-stu-id="b39dc-132">**Foreach Azure Blob Enumerator**</span></span>|<span data-ttu-id="b39dc-133">枚举指定 blob 位置中的 blob 文件。</span><span class="sxs-lookup"><span data-stu-id="b39dc-133">Enumerate blob files in the specified blob location.</span></span> <span data-ttu-id="b39dc-134">选择此值将显示 **“Foreach Azure Blob 枚举器”** 部分中的动态选项。</span><span class="sxs-lookup"><span data-stu-id="b39dc-134">Selecting this value displays the dynamic options in the section, **Foreach Azure Blob Enumerator**.</span></span>|  
|<span data-ttu-id="b39dc-135">**Foreach ADLS 文件枚举器**</span><span class="sxs-lookup"><span data-stu-id="b39dc-135">**Foreach ADLS File Enumerator**</span></span>|<span data-ttu-id="b39dc-136">在 ADLS 上枚举带有筛选器的文件。</span><span class="sxs-lookup"><span data-stu-id="b39dc-136">Enumerate files on ADLS with filters.</span></span> <span data-ttu-id="b39dc-137">选择此值会显示“Foreach ADLS 文件枚举器”  部分中的动态选项。</span><span class="sxs-lookup"><span data-stu-id="b39dc-137">Selecting this value displays the dynamic options in the section, **Foreach ADLS File Enumerator**.</span></span>|
  
 <span data-ttu-id="b39dc-138">**表达式**</span><span class="sxs-lookup"><span data-stu-id="b39dc-138">**Expressions**</span></span>  
 <span data-ttu-id="b39dc-139">单击或展开 **表达式** 可以查看现有属性表达式的列表。</span><span class="sxs-lookup"><span data-stu-id="b39dc-139">Click or expand **Expressions** to view the list of existing property expressions.</span></span> <span data-ttu-id="b39dc-140">单击省略号按钮 (…) 可以添加枚举器属性的属性表达式，或编辑并计算现有属性表达式  。</span><span class="sxs-lookup"><span data-stu-id="b39dc-140">Click the ellipsis button **(...)** to add a property expression for an enumerator property, or edit and evaluate an existing property expression.</span></span>  
  
 <span data-ttu-id="b39dc-141">**相关主题：** [Integration Services &#40;SSIS&#41; 表达式](expressions/integration-services-ssis-expressions.md)、[属性表达式编辑器](expressions/property-expressions-editor.md)、[表达式生成器](expressions/expression-builder.md)</span><span class="sxs-lookup"><span data-stu-id="b39dc-141">**Related Topics:**  [Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md), [Property Expressions Editor](expressions/property-expressions-editor.md), [Expression Builder](expressions/expression-builder.md)</span></span>  
  
## <a name="enumerator-dynamic-options"></a><span data-ttu-id="b39dc-142">枚举器动态选项</span><span class="sxs-lookup"><span data-stu-id="b39dc-142">Enumerator Dynamic Options</span></span>  
  
### <a name="enumerator--foreach-file-enumerator"></a><span data-ttu-id="b39dc-143">Enumerator = Foreach 文件枚举器</span><span class="sxs-lookup"><span data-stu-id="b39dc-143">Enumerator = Foreach File Enumerator</span></span>  
 <span data-ttu-id="b39dc-144">您可以使用 Foreach 文件枚举器枚举文件夹中的文件。</span><span class="sxs-lookup"><span data-stu-id="b39dc-144">You use the Foreach File enumerator to enumerate files in a folder.</span></span> <span data-ttu-id="b39dc-145">例如，如果 Foreach 循环包括执行 SQL 任务，则可以使用 Foreach 文件枚举器枚举包含执行 SQL 任务运行的 SQL 语句的文件。</span><span class="sxs-lookup"><span data-stu-id="b39dc-145">For example, if the Foreach Loop includes an Execute SQL task, you can use the Foreach File enumerator to enumerate files that contain SQL statements that the Execute SQL task runs.</span></span> <span data-ttu-id="b39dc-146">可以将枚举器配置为包括子文件夹。</span><span class="sxs-lookup"><span data-stu-id="b39dc-146">The enumerator can be configured to include subfolders.</span></span>  
  
 <span data-ttu-id="b39dc-147">Foreach 文件枚举器枚举的文件夹和子文件夹的内容可能在执行循环时发生更改，因为循环中的外部进程或任务会在执行循环时添加、重命名或删除文件。</span><span class="sxs-lookup"><span data-stu-id="b39dc-147">The content of the folders and subfolders that the Foreach File enumerator enumerates might change while the loop is executing because external processes or tasks in the loop add, rename, or delete files while the loop is executing.</span></span> <span data-ttu-id="b39dc-148">这意味着可能会出现许多意外情况：</span><span class="sxs-lookup"><span data-stu-id="b39dc-148">This means that a number of unexpected situations may occur:</span></span>  
  
-   <span data-ttu-id="b39dc-149">如果删除文件，则 Foreach 循环中的某个任务可能会处理一组与后续任务所用的文件不同的文件。</span><span class="sxs-lookup"><span data-stu-id="b39dc-149">If files are deleted, one task in the Foreach Loop may perform work on a different set of files than the files used by subsequent tasks.</span></span>  
  
-   <span data-ttu-id="b39dc-150">如果重命名文件并且外部进程自动添加文件以替换重命名的文件，则 Foreach 循环可能针对相同的文件内容执行两次操作。</span><span class="sxs-lookup"><span data-stu-id="b39dc-150">If files are renamed and an external process automatically adds files to replace the renamed files, the Foreach Loop might perform work twice on the same file content.</span></span>  
  
-   <span data-ttu-id="b39dc-151">如果添加文件，则可能很难确定 Foreach 循环要处理的文件。</span><span class="sxs-lookup"><span data-stu-id="b39dc-151">If files are added, it may be difficult to determine for which files the Foreach Loop performed work.</span></span>  
  
 <span data-ttu-id="b39dc-152">**文件夹**</span><span class="sxs-lookup"><span data-stu-id="b39dc-152">**Folder**</span></span>  
 <span data-ttu-id="b39dc-153">提供要枚举的根文件夹的路径。</span><span class="sxs-lookup"><span data-stu-id="b39dc-153">Provide the path of the root folder to enumerate.</span></span>  
  
 <span data-ttu-id="b39dc-154">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="b39dc-154">**Browse**</span></span>  
 <span data-ttu-id="b39dc-155">浏览以定位到根文件夹。</span><span class="sxs-lookup"><span data-stu-id="b39dc-155">Browse to locate the root folder.</span></span>  
  
 <span data-ttu-id="b39dc-156">**文件**</span><span class="sxs-lookup"><span data-stu-id="b39dc-156">**Files**</span></span>  
 <span data-ttu-id="b39dc-157">指定要枚举的文件。</span><span class="sxs-lookup"><span data-stu-id="b39dc-157">Specify the files to enumerate.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b39dc-158">使用通配符 (\*) 可以指定要包括在集合中的文件。</span><span class="sxs-lookup"><span data-stu-id="b39dc-158">Use wildcard characters (\*) to specify the files to include in the collection.</span></span> <span data-ttu-id="b39dc-159">例如，要包括名称包含“abc”的文件，请使用下面的筛选器：abc\*\*。</span><span class="sxs-lookup"><span data-stu-id="b39dc-159">For example, to include files with names that contain "abc", use the following filter: \*abc\*.</span></span>  
>   
>  <span data-ttu-id="b39dc-160">当指定文件扩展名时，枚举器还会返回与所追加的附加字符具有相同扩展名的文件。</span><span class="sxs-lookup"><span data-stu-id="b39dc-160">When you specify a file name extension, the enumerator also returns files that have the same extension with additional characters appended.</span></span> <span data-ttu-id="b39dc-161">（这与操作系统中的 **dir** 命令的行为相同，该命令也会比较 8.3 文件名以检查是否具有向后兼容性。）枚举器的这种行为可能会导致意外的结果。</span><span class="sxs-lookup"><span data-stu-id="b39dc-161">(This is the same behavior as that of the **dir** command in the operating system, which also compares 8.3 file names for backward compatibility.) This behavior of the enumerator could cause unexpected results.</span></span> <span data-ttu-id="b39dc-162">例如，您只想枚举 Excel 2003 文件且指定了“\*.xls”。</span><span class="sxs-lookup"><span data-stu-id="b39dc-162">For example, you want to enumerate only Excel 2003 files, and you specify "\*.xls".</span></span> <span data-ttu-id="b39dc-163">但是，枚举器还会返回 Excel 2007 文件，因为这些文件具有扩展名“.xlsx”。</span><span class="sxs-lookup"><span data-stu-id="b39dc-163">However, the enumerator will also return Excel 2007 files because those files have the extension, ".xlsx".</span></span>  
>   
>  <span data-ttu-id="b39dc-164">可以通过在“集合”页上展开“表达式”，选择 FileSpec 属性，然后单击省略号按钮 (…) 来添加属性表达式，从而使用表达式指定要在集合中包含的文件    。</span><span class="sxs-lookup"><span data-stu-id="b39dc-164">You can use an expression to specify the files to include in a collection, by expanding **Expressions** on the **Collection** page, selecting the **FileSpec** property, and then clicking the ellipsis button (...) to add the property expression.</span></span> <span data-ttu-id="b39dc-165">有关动态选择指定文件的详细信息，请参阅[SSIS-动态设置文件掩码： FileSpec](https://rajsudeep.blogspot.com/2010/09/ssisdynamically-set-file-mask-filespec.html)</span><span class="sxs-lookup"><span data-stu-id="b39dc-165">For more information about dynamically selecting specified files, see [SSIS-Dynamically set File Mask : FileSpec](https://rajsudeep.blogspot.com/2010/09/ssisdynamically-set-file-mask-filespec.html)</span></span>  
  
 <span data-ttu-id="b39dc-166">**完全限定的**</span><span class="sxs-lookup"><span data-stu-id="b39dc-166">**Fully qualified**</span></span>  
 <span data-ttu-id="b39dc-167">选择此项可以检索文件名的完全限定路径。</span><span class="sxs-lookup"><span data-stu-id="b39dc-167">Select to retrieve the fully qualified path of file names.</span></span> <span data-ttu-id="b39dc-168">如果在“文件”选项中指定通配符，则返回的完全限定路径与该筛选条件匹配。</span><span class="sxs-lookup"><span data-stu-id="b39dc-168">If wildcard characters are specified in the Files option, then the fully-qualified paths that are returned match the filter.</span></span>  
  
 <span data-ttu-id="b39dc-169">**仅名称**</span><span class="sxs-lookup"><span data-stu-id="b39dc-169">**Name only**</span></span>  
 <span data-ttu-id="b39dc-170">选择此项可以只检索文件名。</span><span class="sxs-lookup"><span data-stu-id="b39dc-170">Select to retrieve only the file names.</span></span> <span data-ttu-id="b39dc-171">如果在“文件”选项中指定了通配符，则返回的文件名与该筛选条件匹配。</span><span class="sxs-lookup"><span data-stu-id="b39dc-171">If wildcard characters are specified in the Files option, then the file names returned match the filter.</span></span>  
  
 <span data-ttu-id="b39dc-172">**名称和扩展名**</span><span class="sxs-lookup"><span data-stu-id="b39dc-172">**Name and extension**</span></span>  
 <span data-ttu-id="b39dc-173">选择此项可以检索文件名及其文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="b39dc-173">Select to retrieve the file names and their file name extensions.</span></span> <span data-ttu-id="b39dc-174">如果在“文件”选项中指定通配符，则返回的文件名和文件扩展名与该筛选条件匹配。</span><span class="sxs-lookup"><span data-stu-id="b39dc-174">If wildcard characters are specified in the Files option, then the name and extension of files returned match the filter.</span></span>  
  
 <span data-ttu-id="b39dc-175">**遍历子文件夹**</span><span class="sxs-lookup"><span data-stu-id="b39dc-175">**Traverse Subfolders**</span></span>  
 <span data-ttu-id="b39dc-176">选择此项可以在枚举中包括子文件夹。</span><span class="sxs-lookup"><span data-stu-id="b39dc-176">Select to include the subfolders in the enumeration.</span></span>  
  
### <a name="enumerator--foreach-item-enumerator"></a><span data-ttu-id="b39dc-177">Enumerator = Foreach Item 枚举器</span><span class="sxs-lookup"><span data-stu-id="b39dc-177">Enumerator = Foreach Item Enumerator</span></span>  
 <span data-ttu-id="b39dc-178">您可以使用 Foreach Item 枚举器枚举集合中的项。</span><span class="sxs-lookup"><span data-stu-id="b39dc-178">You use the Foreach Item enumerator to enumerate items in a collection.</span></span> <span data-ttu-id="b39dc-179">您将通过指定一个和多个列的值来定义集合中的项。</span><span class="sxs-lookup"><span data-stu-id="b39dc-179">You define the items in the collection by specifying columns and column values.</span></span> <span data-ttu-id="b39dc-180">一行中的列将定义一个项。</span><span class="sxs-lookup"><span data-stu-id="b39dc-180">The columns in a row define an item.</span></span> <span data-ttu-id="b39dc-181">例如，指定执行进程任务运行的可执行文件以及此任务所用的工作目录的项包含两列，一列列出可执行文件的名称，另一列列出工作目录。</span><span class="sxs-lookup"><span data-stu-id="b39dc-181">For example, an item that specifies the executables that an Execute Process task runs and the working directory that the task uses has two columns, one that lists the names of executables and one that lists the working directory.</span></span> <span data-ttu-id="b39dc-182">行数决定循环重复的次数。</span><span class="sxs-lookup"><span data-stu-id="b39dc-182">The number of rows determines the number of times that the loop is repeated.</span></span> <span data-ttu-id="b39dc-183">如果表有 10 行，则循环重复 10 次。</span><span class="sxs-lookup"><span data-stu-id="b39dc-183">If the table has 10 rows, the loop repeats 10 times.</span></span>  
  
 <span data-ttu-id="b39dc-184">若要更新执行进程任务的属性，可以使用列索引将变量映射到项列。</span><span class="sxs-lookup"><span data-stu-id="b39dc-184">To update the properties of the Execute Process task, you map variables to item columns by using the index of the column.</span></span> <span data-ttu-id="b39dc-185">枚举器项中定义的第一列的索引值为 0，第二列的索引值为 1，依次类推。</span><span class="sxs-lookup"><span data-stu-id="b39dc-185">The first column defined in the enumerator item has the index value 0, the second column 1, and so on.</span></span> <span data-ttu-id="b39dc-186">变量值将随着循环的每次重复而更新。</span><span class="sxs-lookup"><span data-stu-id="b39dc-186">The variable values are updated with each repeat of the loop.</span></span> <span data-ttu-id="b39dc-187">然后，可以通过使用这些变量的属性表达式更新执行进程任务的 `Executable` 和 `WorkingDirectory` 属性。</span><span class="sxs-lookup"><span data-stu-id="b39dc-187">The `Executable` and `WorkingDirectory` properties of the Execute Process task can then be updated by property expressions that use these variables.</span></span>  
  
 <span data-ttu-id="b39dc-188">**定义 For Each 项集合中的项**</span><span class="sxs-lookup"><span data-stu-id="b39dc-188">**Define the items in the For Each Item collection**</span></span>  
 <span data-ttu-id="b39dc-189">为表中的每个列提供值。</span><span class="sxs-lookup"><span data-stu-id="b39dc-189">Provide a value for each column in the table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b39dc-190">在行列中输入值后，新行将自动添加到表中。</span><span class="sxs-lookup"><span data-stu-id="b39dc-190">A new row is automatically added to the table after you enter values in row columns.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b39dc-191">如果所提供的值与列数据类型不兼容，则文本以红色显示。</span><span class="sxs-lookup"><span data-stu-id="b39dc-191">If the values provided are not compatible with the column data type, the text is colored red.</span></span>  
  
 <span data-ttu-id="b39dc-192">**列数据类型**</span><span class="sxs-lookup"><span data-stu-id="b39dc-192">**Column data type**</span></span>  
 <span data-ttu-id="b39dc-193">列出活动列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="b39dc-193">Lists the data type of the active column.</span></span>  
  
 <span data-ttu-id="b39dc-194">**删除**</span><span class="sxs-lookup"><span data-stu-id="b39dc-194">**Remove**</span></span>  
 <span data-ttu-id="b39dc-195">选择项，再单击 **“删除”** ，即可从列表中删除它。</span><span class="sxs-lookup"><span data-stu-id="b39dc-195">Select an item, and then click **Remove** to remove it from the list.</span></span>  
  
 <span data-ttu-id="b39dc-196">**“列”**</span><span class="sxs-lookup"><span data-stu-id="b39dc-196">**Columns**</span></span>  
 <span data-ttu-id="b39dc-197">单击此项可以配置项中的列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="b39dc-197">Click to configure the data type of the columns in the item.</span></span>  
  
 <span data-ttu-id="b39dc-198">**相关主题：** [“For Each Item 列”对话框 UI 参考](../../2014/integration-services/for-each-item-columns-dialog-box-ui-reference.md)</span><span class="sxs-lookup"><span data-stu-id="b39dc-198">**Related Topics:** [For Each Item Columns Dialog Box UI Reference](../../2014/integration-services/for-each-item-columns-dialog-box-ui-reference.md)</span></span>  
  
### <a name="enumerator--foreach-ado-enumerator"></a><span data-ttu-id="b39dc-199">Enumerator = Foreach ADO 枚举器</span><span class="sxs-lookup"><span data-stu-id="b39dc-199">Enumerator = Foreach ADO Enumerator</span></span>  
 <span data-ttu-id="b39dc-200">您可以使用 Foreach ADO 枚举器枚举变量中存储的 ADO 或 ADO.NET 对象中的行或表。</span><span class="sxs-lookup"><span data-stu-id="b39dc-200">You use the Foreach ADO enumerator to enumerate rows or tables in an ADO or ADO.NET object that is stored in a variable.</span></span> <span data-ttu-id="b39dc-201">例如，如果 Foreach 循环包括可将数据集写入变量的脚本任务，则可以使用 Foreach ADO 枚举器枚举数据集中的行。</span><span class="sxs-lookup"><span data-stu-id="b39dc-201">For example, if the Foreach Loop includes a Script task that writes a dataset to a variable, you can use the Foreach ADO enumerator to enumerate the rows in the dataset.</span></span> <span data-ttu-id="b39dc-202">如果变量包含 ADO.NET 数据集，则可以将枚举器配置为枚举多个表中的行或枚举表。</span><span class="sxs-lookup"><span data-stu-id="b39dc-202">If the variable contains an ADO.NET dataset, the enumerator can be configured to enumerate rows in multiple tables or to enumerate tables.</span></span>  
  
 <span data-ttu-id="b39dc-203">**ADO 对象源变量**</span><span class="sxs-lookup"><span data-stu-id="b39dc-203">**ADO object source variable**</span></span>  
 <span data-ttu-id="b39dc-204">从列表中选择用户定义的变量，或单击“\<**New variable...**>”创建新变量。</span><span class="sxs-lookup"><span data-stu-id="b39dc-204">Select a user-defined variable in the list, or click \<**New variable...**> to create a new variable.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b39dc-205">变量必须有 Object 数据类型，否则会发生错误。</span><span class="sxs-lookup"><span data-stu-id="b39dc-205">The variable must have the Object data type, otherwise an error occurs.</span></span>  
  
 <span data-ttu-id="b39dc-206">**相关主题：** [Integration Services &#40;SSIS&#41; 变量](integration-services-ssis-variables.md)、[添加变量](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="b39dc-206">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
 <span data-ttu-id="b39dc-207">**第一个表中的行**</span><span class="sxs-lookup"><span data-stu-id="b39dc-207">**Rows in first table**</span></span>  
 <span data-ttu-id="b39dc-208">选择此项将只枚举第一个表中的行。</span><span class="sxs-lookup"><span data-stu-id="b39dc-208">Select to enumerate only rows in the first table.</span></span>  
  
 <span data-ttu-id="b39dc-209">**所有表中的行(仅限于 ADO.NET 数据集)**</span><span class="sxs-lookup"><span data-stu-id="b39dc-209">**Rows in all tables (ADO.NET dataset only)**</span></span>  
 <span data-ttu-id="b39dc-210">选择此项将枚举所有表中的行。</span><span class="sxs-lookup"><span data-stu-id="b39dc-210">Select to enumerate rows in all tables.</span></span> <span data-ttu-id="b39dc-211">只有当要枚举的对象是同一 ADO.NET 数据集的所有成员时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="b39dc-211">This option is available only if the objects to enumerate are all members of the same ADO.NET dataset.</span></span>  
  
 <span data-ttu-id="b39dc-212">**所有表(仅限于 ADO.NET 数据集)**</span><span class="sxs-lookup"><span data-stu-id="b39dc-212">**All tables (ADO.NET dataset only)**</span></span>  
 <span data-ttu-id="b39dc-213">选择此项将只枚举表。</span><span class="sxs-lookup"><span data-stu-id="b39dc-213">Select to enumerate tables only.</span></span>  
  
### <a name="enumerator--foreach-adonet-schema-rowset-enumerator"></a><span data-ttu-id="b39dc-214">Enumerator = Foreach ADO.NET 架构行集枚举器</span><span class="sxs-lookup"><span data-stu-id="b39dc-214">Enumerator = Foreach ADO.NET Schema Rowset Enumerator</span></span>  
 <span data-ttu-id="b39dc-215">您可以使用 Foreach ADO.NET 架构行集枚举器枚举指定数据源的架构。</span><span class="sxs-lookup"><span data-stu-id="b39dc-215">You use the Foreach ADO.NET Schema Rowset enumerator to enumerate a schema for a specified data source.</span></span> <span data-ttu-id="b39dc-216">例如，如果 Foreach 循环包括执行 SQL 任务，则可以使用 Foreach ADO.NET 架构行集枚举器枚举架构（例如， **AdventureWorks** 数据库中的列），使用执行 SQL 任务获取架构权限。</span><span class="sxs-lookup"><span data-stu-id="b39dc-216">For example, if the Foreach Loop includes an Execute SQL task, you can use the Foreach ADO.NET Schema Rowset enumerator to enumerate schemas such as the columns in the **AdventureWorks** database, and the Execute SQL task to get the schema permissions.</span></span>  
  
 <span data-ttu-id="b39dc-217">**Connection**</span><span class="sxs-lookup"><span data-stu-id="b39dc-217">**Connection**</span></span>  
 <span data-ttu-id="b39dc-218">从列表中选择 ADO.NET 连接管理器，或单击“\<**New connection...**>”创建新的 ADO.NET 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="b39dc-218">Select an ADO.NET connection manager in the list, or click \<**New connection...**> to create a new ADO.NET connection manager.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b39dc-219">ADO.NET 连接管理器必须使用 .NET provider for OLE DB。</span><span class="sxs-lookup"><span data-stu-id="b39dc-219">The ADO.NET connection manager must use a .NET provider for OLE DB.</span></span> <span data-ttu-id="b39dc-220">如果连接到 SQL Server，则建议使用的访问接口为 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] **“连接管理器”** 对话框的 **.Net Providers for OleDb** 部分中列出的  Native Client。</span><span class="sxs-lookup"><span data-stu-id="b39dc-220">If connecting to SQL Server, the recommended provider to use is the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client, listed in the **.Net Providers for OleDb** section of the **Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="b39dc-221">**相关主题：** [ADO 连接管理器](connection-manager/ado-connection-manager.md)、[配置 ADO.NET 连接管理器](configure-ado-net-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="b39dc-221">**Related Topics:** [ADO Connection Manager](connection-manager/ado-connection-manager.md), [Configure ADO.NET Connection Manager](configure-ado-net-connection-manager.md)</span></span>  
  
 <span data-ttu-id="b39dc-222">**架构**</span><span class="sxs-lookup"><span data-stu-id="b39dc-222">**Schema**</span></span>  
 <span data-ttu-id="b39dc-223">选择要枚举的架构。</span><span class="sxs-lookup"><span data-stu-id="b39dc-223">Select the schema to enumerate.</span></span>  
  
 <span data-ttu-id="b39dc-224">**设置限制**</span><span class="sxs-lookup"><span data-stu-id="b39dc-224">**Set Restrictions**</span></span>  
 <span data-ttu-id="b39dc-225">设置要应用于指定架构的限制。</span><span class="sxs-lookup"><span data-stu-id="b39dc-225">Set the restrictions to apply to the specified schema.</span></span>  
  
 <span data-ttu-id="b39dc-226">**相关主题：** [“架构限制”对话框](../../2014/integration-services/schema-restrictions-dialog-box.md)</span><span class="sxs-lookup"><span data-stu-id="b39dc-226">**Related Topics:** [Schema Restrictions Dialog Box](../../2014/integration-services/schema-restrictions-dialog-box.md)</span></span>  
  
### <a name="enumerator--foreach-from-variable-enumerator"></a><span data-ttu-id="b39dc-227">Enumerator = Foreach 源变量枚举器</span><span class="sxs-lookup"><span data-stu-id="b39dc-227">Enumerator = Foreach From Variable Enumerator</span></span>  
 <span data-ttu-id="b39dc-228">您可以使用 Foreach 源变量枚举器枚举指定变量中的可枚举对象。</span><span class="sxs-lookup"><span data-stu-id="b39dc-228">You use the Foreach From Variable enumerator to enumerate the enumerable objects in the specified variable.</span></span> <span data-ttu-id="b39dc-229">例如，如果 Foreach 循环包括运行查询并在变量中存储结果的执行 SQL 任务，则可以使用 Foreach 源变量枚举器枚举查询结果。</span><span class="sxs-lookup"><span data-stu-id="b39dc-229">For example, if the Foreach Loop includes an Execute SQL task that runs a query and stores the result in a variable, you can use the Foreach From Variable enumerator to enumerate the query results.</span></span>  
  
 <span data-ttu-id="b39dc-230">**变量**</span><span class="sxs-lookup"><span data-stu-id="b39dc-230">**Variable**</span></span>  
 <span data-ttu-id="b39dc-231">在列表中选择变量，或单击“\<**New variable...**>创建一个新变量。</span><span class="sxs-lookup"><span data-stu-id="b39dc-231">Select a variable in the list, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="b39dc-232">**相关主题：** [Integration Services &#40;SSIS&#41; 变量](integration-services-ssis-variables.md)、[添加变量](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="b39dc-232">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
### <a name="enumerator--foreach-nodelist-enumerator"></a><span data-ttu-id="b39dc-233">Enumerator = Foreach NodeList 枚举器</span><span class="sxs-lookup"><span data-stu-id="b39dc-233">Enumerator = Foreach NodeList Enumerator</span></span>  
 <span data-ttu-id="b39dc-234">您可以使用 Foreach Nodelist 枚举器枚举一组通过将 XPath 表达式应用到 XML 文件而生成的 XML 节点。</span><span class="sxs-lookup"><span data-stu-id="b39dc-234">You use the Foreach Nodelist enumerator to enumerate the set of XML nodes that results from applying an XPath expression to an XML file.</span></span> <span data-ttu-id="b39dc-235">例如，如果 Foreach 循环包括脚本任务，则可以使用 Foreach NodeList 枚举器将满足 XPath 表达式条件的值从 XML 文件传递到脚本任务。</span><span class="sxs-lookup"><span data-stu-id="b39dc-235">For example, if the Foreach Loop includes a Script task, you can use the Foreach NodeList enumerator to pass a value that meets the XPath expression criteria from the XML file to the Script task.</span></span>  
  
 <span data-ttu-id="b39dc-236">应用到 XML 文件的 XPath 表达式为外部 XPath 运算，存储于 OuterXPathString 属性中。</span><span class="sxs-lookup"><span data-stu-id="b39dc-236">The XPath expression that applies to the XML file is the outer XPath operation, stored in the OuterXPathString property.</span></span> <span data-ttu-id="b39dc-237">如果 XPath 枚举类型设置为 `ElementCollection` ，则 Foreach NodeList 枚举器可以将内部 XPath 表达式（存储在 InnerXPathString 属性中）应用到元素的集合。</span><span class="sxs-lookup"><span data-stu-id="b39dc-237">If the XPath enumeration type is set to `ElementCollection`, the Foreach NodeList enumerator can apply an inner XPath expression, stored in the InnerXPathString property, to a collection of element.</span></span>  
  
 <span data-ttu-id="b39dc-238">若要了解有关使用 XML 文档和数据的详细信息，请参阅 MSDN Library 中的“[Employing XML in the .NET Framework](https://go.microsoft.com/fwlink/?LinkId=56214)”。</span><span class="sxs-lookup"><span data-stu-id="b39dc-238">To learn more about working with XML documents and data, see "[Employing XML in the .NET Framework](https://go.microsoft.com/fwlink/?LinkId=56214)" in the MSDN Library.</span></span>  
  
 <span data-ttu-id="b39dc-239">**DocumentSourceType**</span><span class="sxs-lookup"><span data-stu-id="b39dc-239">**DocumentSourceType**</span></span>  
 <span data-ttu-id="b39dc-240">选择 XML 文档的源类型。</span><span class="sxs-lookup"><span data-stu-id="b39dc-240">Select the source type of the XML document.</span></span> <span data-ttu-id="b39dc-241">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="b39dc-241">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="b39dc-242">值</span><span class="sxs-lookup"><span data-stu-id="b39dc-242">Value</span></span>|<span data-ttu-id="b39dc-243">说明</span><span class="sxs-lookup"><span data-stu-id="b39dc-243">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b39dc-244">**直接输入**</span><span class="sxs-lookup"><span data-stu-id="b39dc-244">**Direct input**</span></span>|<span data-ttu-id="b39dc-245">将源设置为 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="b39dc-245">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="b39dc-246">**文件连接**</span><span class="sxs-lookup"><span data-stu-id="b39dc-246">**File connection**</span></span>|<span data-ttu-id="b39dc-247">选择包含 XML 文档的文件。</span><span class="sxs-lookup"><span data-stu-id="b39dc-247">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="b39dc-248">**变量**</span><span class="sxs-lookup"><span data-stu-id="b39dc-248">**Variable**</span></span>|<span data-ttu-id="b39dc-249">将源设置为包含 XML 文档的变量。</span><span class="sxs-lookup"><span data-stu-id="b39dc-249">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="b39dc-250">**DocumentSource**</span><span class="sxs-lookup"><span data-stu-id="b39dc-250">**DocumentSource**</span></span>  
 <span data-ttu-id="b39dc-251">如果将 DocumentSourceType 设置为“直接输入”，请提供 XML 代码，或单击省略号按钮 (…) 以通过使用“文档源编辑器”对话框来提供 XML    。</span><span class="sxs-lookup"><span data-stu-id="b39dc-251">If **DocumentSourceType** is set to **Direct input**, provide the XML code, or click the ellipsis (...) button to provide XML by using the **Document Source Edito**r dialog box.</span></span>  
  
 <span data-ttu-id="b39dc-252">如果 DocumentSourceType 设置为“文件连接”，请选择“文件连接管理器”，或单击“\<**New connection...**>”创建新的连接管理器 。</span><span class="sxs-lookup"><span data-stu-id="b39dc-252">If **DocumentSourceType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="b39dc-253">**相关主题：** [文件连接管理器](connection-manager/file-connection-manager.md)、[文件连接管理器编辑器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="b39dc-253">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="b39dc-254">如果 DocumentSourceType 设置为“变量”，请选择现有变量，或单击“\<**New variable...**>”创建新变量 。</span><span class="sxs-lookup"><span data-stu-id="b39dc-254">If **DocumentSourceType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="b39dc-255">**相关主题：** [Integration Services &#40;SSIS&#41; 变量](integration-services-ssis-variables.md)、[添加变量](../../2014/integration-services/add-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="b39dc-255">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
 <span data-ttu-id="b39dc-256">**EnumerationType**</span><span class="sxs-lookup"><span data-stu-id="b39dc-256">**EnumerationType**</span></span>  
 <span data-ttu-id="b39dc-257">从列表中选择枚举类型。</span><span class="sxs-lookup"><span data-stu-id="b39dc-257">Select an enumeration type from the list.</span></span> <span data-ttu-id="b39dc-258">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="b39dc-258">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="b39dc-259">值</span><span class="sxs-lookup"><span data-stu-id="b39dc-259">Value</span></span>|<span data-ttu-id="b39dc-260">说明</span><span class="sxs-lookup"><span data-stu-id="b39dc-260">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b39dc-261">**Navigator**</span><span class="sxs-lookup"><span data-stu-id="b39dc-261">**Navigator**</span></span>|<span data-ttu-id="b39dc-262">使用 XPathNavigator 进行枚举。</span><span class="sxs-lookup"><span data-stu-id="b39dc-262">Enumerate using an XPathNavigator.</span></span>|  
|<span data-ttu-id="b39dc-263">**Node**</span><span class="sxs-lookup"><span data-stu-id="b39dc-263">**Node**</span></span>|<span data-ttu-id="b39dc-264">枚举 XPath 运算返回的节点。</span><span class="sxs-lookup"><span data-stu-id="b39dc-264">Enumerate nodes returned by an XPath operation.</span></span>|  
|<span data-ttu-id="b39dc-265">**NodeText**</span><span class="sxs-lookup"><span data-stu-id="b39dc-265">**NodeText**</span></span>|<span data-ttu-id="b39dc-266">枚举 XPath 运算返回的文本节点。</span><span class="sxs-lookup"><span data-stu-id="b39dc-266">Enumerate text nodes returned by an XPath operation.</span></span>|  
|`ElementCollection`|<span data-ttu-id="b39dc-267">枚举 XPath 运算返回的元素节点。</span><span class="sxs-lookup"><span data-stu-id="b39dc-267">Enumerates element nodes returned by an XPath operation.</span></span>|  
  
 <span data-ttu-id="b39dc-268">**OuterXPathStringSourceType**</span><span class="sxs-lookup"><span data-stu-id="b39dc-268">**OuterXPathStringSourceType**</span></span>  
 <span data-ttu-id="b39dc-269">选择 XPath 字符串的源类型。</span><span class="sxs-lookup"><span data-stu-id="b39dc-269">Select the source type of the XPath string.</span></span> <span data-ttu-id="b39dc-270">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="b39dc-270">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="b39dc-271">值</span><span class="sxs-lookup"><span data-stu-id="b39dc-271">Value</span></span>|<span data-ttu-id="b39dc-272">说明</span><span class="sxs-lookup"><span data-stu-id="b39dc-272">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b39dc-273">**直接输入**</span><span class="sxs-lookup"><span data-stu-id="b39dc-273">**Direct input**</span></span>|<span data-ttu-id="b39dc-274">将源设置为 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="b39dc-274">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="b39dc-275">**文件连接**</span><span class="sxs-lookup"><span data-stu-id="b39dc-275">**File connection**</span></span>|<span data-ttu-id="b39dc-276">选择包含 XML 文档的文件。</span><span class="sxs-lookup"><span data-stu-id="b39dc-276">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="b39dc-277">**变量**</span><span class="sxs-lookup"><span data-stu-id="b39dc-277">**Variable**</span></span>|<span data-ttu-id="b39dc-278">将源设置为包含 XML 文档的变量。</span><span class="sxs-lookup"><span data-stu-id="b39dc-278">Set the source to a variable that contains the XML document.</span></span>|  
  
 `OuterXPathString`  
 <span data-ttu-id="b39dc-279">如果将 **OuterXPathStringSourceType** 设置为“直接输出”  ，请提供 XPath 字符串。</span><span class="sxs-lookup"><span data-stu-id="b39dc-279">If **OuterXPathStringSourceType** is set to **Direct input**, provide the XPath string.</span></span>  
  
 <span data-ttu-id="b39dc-280">如果 OuterXPathStringSourceType 设置为“文件连接”，请选择“文件连接管理器”，或单击“\<**New connection...**>创建新的连接管理器 。</span><span class="sxs-lookup"><span data-stu-id="b39dc-280">If **OuterXPathStringSourceType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="b39dc-281">**相关主题：** [文件连接管理器](connection-manager/file-connection-manager.md)、[文件连接管理器编辑器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="b39dc-281">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="b39dc-282">如果 OuterXPathStringSourceType 设置为“变量”，请选择现有变量，或单击“\<**New variable...**>创建新的变量 。</span><span class="sxs-lookup"><span data-stu-id="b39dc-282">If **OuterXPathStringSourceType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="b39dc-283">**相关主题：** [Integration Services &#40;SSIS&#41; 变量](integration-services-ssis-variables.md)、[添加变量](../../2014/integration-services/add-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="b39dc-283">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
 <span data-ttu-id="b39dc-284">**InnerElementType**</span><span class="sxs-lookup"><span data-stu-id="b39dc-284">**InnerElementType**</span></span>  
 <span data-ttu-id="b39dc-285">如果将**EnumerationType**设置为 `ElementCollection` ，请在列表中选择内部元素的类型。</span><span class="sxs-lookup"><span data-stu-id="b39dc-285">If **EnumerationType** is set to `ElementCollection`, select the type of inner element in the list.</span></span>  
  
 <span data-ttu-id="b39dc-286">**InnerXPathStringSourceType**</span><span class="sxs-lookup"><span data-stu-id="b39dc-286">**InnerXPathStringSourceType**</span></span>  
 <span data-ttu-id="b39dc-287">选择内部 XPath 字符串的源类型。</span><span class="sxs-lookup"><span data-stu-id="b39dc-287">Select the source type of the inner XPath string.</span></span> <span data-ttu-id="b39dc-288">此属性具有下表所列的选项。</span><span class="sxs-lookup"><span data-stu-id="b39dc-288">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="b39dc-289">值</span><span class="sxs-lookup"><span data-stu-id="b39dc-289">Value</span></span>|<span data-ttu-id="b39dc-290">说明</span><span class="sxs-lookup"><span data-stu-id="b39dc-290">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b39dc-291">**直接输入**</span><span class="sxs-lookup"><span data-stu-id="b39dc-291">**Direct input**</span></span>|<span data-ttu-id="b39dc-292">将源设置为 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="b39dc-292">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="b39dc-293">**文件连接**</span><span class="sxs-lookup"><span data-stu-id="b39dc-293">**File connection**</span></span>|<span data-ttu-id="b39dc-294">选择包含 XML 文档的文件。</span><span class="sxs-lookup"><span data-stu-id="b39dc-294">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="b39dc-295">**变量**</span><span class="sxs-lookup"><span data-stu-id="b39dc-295">**Variable**</span></span>|<span data-ttu-id="b39dc-296">将源设置为包含 XML 文档的变量。</span><span class="sxs-lookup"><span data-stu-id="b39dc-296">Set the source to a variable that contains the XML document.</span></span>|  
  
 `InnerXPathString`  
 <span data-ttu-id="b39dc-297">如果将 **InnerXPathStringSourceType** 设置为“直接输入”  ，请提供 XPath 字符串。</span><span class="sxs-lookup"><span data-stu-id="b39dc-297">If **InnerXPathStringSourceType** is set to **Direct input**, provide the XPath string.</span></span>  
  
 <span data-ttu-id="b39dc-298">如果 InnerXPathStringSourceType 设置为“文件连接”，请选择“文件连接管理器”，或单击“\<**New connection...**>创建新的连接管理器 。</span><span class="sxs-lookup"><span data-stu-id="b39dc-298">If **InnerXPathStringSourceType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="b39dc-299">**相关主题：** [文件连接管理器](connection-manager/file-connection-manager.md)、[文件连接管理器编辑器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="b39dc-299">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="b39dc-300">如果 InnerXPathStringSourceType 设置为“变量”，请选择现有变量，或单击“\<**New variable...**>创建新的变量 。</span><span class="sxs-lookup"><span data-stu-id="b39dc-300">If **InnerXPathStringSourceType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="b39dc-301">**相关主题：** [Integration Services &#40;SSIS&#41; 变量](integration-services-ssis-variables.md)、[添加变量](../../2014/integration-services/add-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="b39dc-301">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
### <a name="enumerator--foreach-smo-enumerator"></a><span data-ttu-id="b39dc-302">Enumerator = Foreach SMO 枚举器</span><span class="sxs-lookup"><span data-stu-id="b39dc-302">Enumerator = Foreach SMO Enumerator</span></span>  
 <span data-ttu-id="b39dc-303">您可以使用 Foreach SMO 枚举器枚举 SQL Server 管理对象 (SMO) 对象。</span><span class="sxs-lookup"><span data-stu-id="b39dc-303">You use the Foreach SMO enumerator to enumerate SQL Server Management Object (SMO) objects.</span></span> <span data-ttu-id="b39dc-304">例如，如果 Foreach 循环包括执行 SQL 任务，则可以使用 Foreach SMO 枚举器枚举 **AdventureWorks** 数据库中的表并运行计算每个表中行数的查询。</span><span class="sxs-lookup"><span data-stu-id="b39dc-304">For example, if the Foreach Loop includes an Execute SQL task, you can use the Foreach SMO enumerator to enumerate the tables in the **AdventureWorks** database and run queries that counts the number of rows in each table.</span></span>  
  
 <span data-ttu-id="b39dc-305">**Connection**</span><span class="sxs-lookup"><span data-stu-id="b39dc-305">**Connection**</span></span>  
 <span data-ttu-id="b39dc-306">选择现有 ADO.NET 连接管理器，或单击“\<**New connection...**>”以创建新的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="b39dc-306">Select an existing ADO.NET connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="b39dc-307">相关主题：[ADO.NET 连接管理器](connection-manager/ado-net-connection-manager.md)、[配置 ADO.NET 连接管理器](configure-ado-net-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="b39dc-307">Related Topics: [ADO.NET Connection Manager](connection-manager/ado-net-connection-manager.md), [Configure ADO.NET Connection Manager](configure-ado-net-connection-manager.md)</span></span>  
  
 <span data-ttu-id="b39dc-308">**枚举**</span><span class="sxs-lookup"><span data-stu-id="b39dc-308">**Enumerate**</span></span>  
 <span data-ttu-id="b39dc-309">指定要枚举的 SMO 对象。</span><span class="sxs-lookup"><span data-stu-id="b39dc-309">Specify the SMO object to enumerate.</span></span>  
  
 <span data-ttu-id="b39dc-310">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="b39dc-310">**Browse**</span></span>  
 <span data-ttu-id="b39dc-311">选择 SMO 枚举。</span><span class="sxs-lookup"><span data-stu-id="b39dc-311">Select the SMO enumeration.</span></span>  
  
 <span data-ttu-id="b39dc-312">**相关主题：** [“选择 SMO 枚举”对话框](../../2014/integration-services/select-smo-enumeration-dialog-box.md)</span><span class="sxs-lookup"><span data-stu-id="b39dc-312">**Related Topics:** [Select SMO Enumeration Dialog Box](../../2014/integration-services/select-smo-enumeration-dialog-box.md)</span></span>  
  
### <a name="enumerator--foreach-azure-blob-enumerator"></a><span data-ttu-id="b39dc-313">枚举器 = Foreach Azure Blob 枚举器</span><span class="sxs-lookup"><span data-stu-id="b39dc-313">Enumerator = Foreach Azure Blob Enumerator</span></span>  
 <span data-ttu-id="b39dc-314">**Azure Blob 枚举器**允许 SSIS 程序包在指定的 blob 位置枚举 blob 文件。</span><span class="sxs-lookup"><span data-stu-id="b39dc-314">The  **Azure Blob Enumerator**r enables an SSIS package to enumerate blob files in the specified blob location.</span></span> <span data-ttu-id="b39dc-315">枚举的 blob 文件名可以存储在变量中并用于 Foreach 循环容器内的任务。</span><span class="sxs-lookup"><span data-stu-id="b39dc-315">The name of enumerated blob file can be stored in a variable and used in tasks inside the Foreach Loop Container.</span></span>  
  
 <span data-ttu-id="b39dc-316">**Azure 存储连接管理器**</span><span class="sxs-lookup"><span data-stu-id="b39dc-316">**Azure storage connection manager**</span></span>  
 <span data-ttu-id="b39dc-317">选择一个现有的 Azure 存储连接管理器或创建一个新的、引用 Azure 存储帐户的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="b39dc-317">Select an existing Azure Storage Connection Manager or create a new one that refers to an Azure Storage Account.</span></span>  
  
 <span data-ttu-id="b39dc-318">相关主题：[Azure 存储连接管理器](connection-manager/azure-storage-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="b39dc-318">Related Topics: [Azure Storage Connection Manager](connection-manager/azure-storage-connection-manager.md).</span></span>  
  
 <span data-ttu-id="b39dc-319">**Blob 容器名称**</span><span class="sxs-lookup"><span data-stu-id="b39dc-319">**Blob container name**</span></span>  
 <span data-ttu-id="b39dc-320">指定包含要枚举的 blob 文件的 blob 容器。</span><span class="sxs-lookup"><span data-stu-id="b39dc-320">Specify the name of the blob container that contains the blob files to be enumerated..</span></span>  
  
 <span data-ttu-id="b39dc-321">**Blob 目录**</span><span class="sxs-lookup"><span data-stu-id="b39dc-321">**Blob directory**</span></span>  
 <span data-ttu-id="b39dc-322">指定包含要枚举的 blob 文件的 blob 目录。</span><span class="sxs-lookup"><span data-stu-id="b39dc-322">Specify the specify the blob directory that contains the blob files to be enumerated.</span></span> <span data-ttu-id="b39dc-323">该 blob 目录是一个虚拟层次结构。</span><span class="sxs-lookup"><span data-stu-id="b39dc-323">The blob directory is a virtual hierarchical structure.</span></span>  
  
 <span data-ttu-id="b39dc-324">**Blob 名称筛选器**</span><span class="sxs-lookup"><span data-stu-id="b39dc-324">**Blob name filter**</span></span>  
 <span data-ttu-id="b39dc-325">指定用于枚举具有特定名称模式的文件的名称筛选器。</span><span class="sxs-lookup"><span data-stu-id="b39dc-325">Specify a name filter to enumerate files with a certain name pattern.</span></span> <span data-ttu-id="b39dc-326">例如</span><span class="sxs-lookup"><span data-stu-id="b39dc-326">E.g.</span></span> <span data-ttu-id="b39dc-327">MySheet\*.xls\* 将包含如 MySheet001.xls 和 MySheetABC.xlsx 等文件。</span><span class="sxs-lookup"><span data-stu-id="b39dc-327">MySheet\*.xls\* will include files such as MySheet001.xls and MySheetABC.xlsx.</span></span>  
  
 <span data-ttu-id="b39dc-328">**Blob 时间范围(自/至)筛选器**</span><span class="sxs-lookup"><span data-stu-id="b39dc-328">**Blob time range from/to filter**</span></span>  
 <span data-ttu-id="b39dc-329">指定时间范围筛选器。</span><span class="sxs-lookup"><span data-stu-id="b39dc-329">Specify a time range filter.</span></span> <span data-ttu-id="b39dc-330">将枚举在 **TimeRangeFrom** 之后以及在 **TimeRangeTo** 之前修改的文件。</span><span class="sxs-lookup"><span data-stu-id="b39dc-330">Files modified after **TimeRangeFrom** and before **TimeRangeTo** will be enumerated.</span></span>  
### <a name="enumerator--foreach-adls-file-enumerator"></a><span data-ttu-id="b39dc-331"> 枚举器 = Foreach ADLS 文件枚举器</span><span class="sxs-lookup"><span data-stu-id="b39dc-331">Enumerator = Foreach ADLS File Enumerator</span></span>  
<span data-ttu-id="b39dc-332">**ADLS 文件枚举器**使 SSIS 包能够使用筛选器枚举 ADLS 上的文件。</span><span class="sxs-lookup"><span data-stu-id="b39dc-332">The **ADLS File Enumerator** enables an SSIS package to enumerate files on ADLS with filters.</span></span> <span data-ttu-id="b39dc-333">枚举文件的反斜杠 `/`)  (可以存储在变量中并用于 Foreach 循环容器内的任务中。</span><span class="sxs-lookup"><span data-stu-id="b39dc-333">The slash (`/`)-prefixed full path of enumerated files can be stored in a variable and used in tasks inside the Foreach Loop Container.</span></span>
  
<span data-ttu-id="b39dc-334">**AzureDataLakeConnection**</span><span class="sxs-lookup"><span data-stu-id="b39dc-334">**AzureDataLakeConnection**</span></span>  
<span data-ttu-id="b39dc-335">指定 Azure Data Lake 连接管理器，或创建一个引用 ADLS 帐户的新连接管理器。</span><span class="sxs-lookup"><span data-stu-id="b39dc-335">Specifies an Azure Data Lake connection manager, or creates a new one that refers to an ADLS account.</span></span>   
  
<span data-ttu-id="b39dc-336">**AzureDataLakeDirectory**</span><span class="sxs-lookup"><span data-stu-id="b39dc-336">**AzureDataLakeDirectory**</span></span>  
<span data-ttu-id="b39dc-337">指定要搜索的 ADLS 目录。</span><span class="sxs-lookup"><span data-stu-id="b39dc-337">Specifies the ADLS directory to search.</span></span>
  
<span data-ttu-id="b39dc-338">**FileNamePattern**</span><span class="sxs-lookup"><span data-stu-id="b39dc-338">**FileNamePattern**</span></span>  
<span data-ttu-id="b39dc-339">指定文件名筛选器。</span><span class="sxs-lookup"><span data-stu-id="b39dc-339">Specifies a file name filter.</span></span> <span data-ttu-id="b39dc-340">仅枚举名称与指定模式匹配的文件。</span><span class="sxs-lookup"><span data-stu-id="b39dc-340">Only files whose name matches the specified pattern will be enumerated.</span></span> <span data-ttu-id="b39dc-341">支持 `*` 和 `?` 通配符。</span><span class="sxs-lookup"><span data-stu-id="b39dc-341">Wildcards `*` and `?` are supported.</span></span> 
  
<span data-ttu-id="b39dc-342">**SearchRecursively**</span><span class="sxs-lookup"><span data-stu-id="b39dc-342">**SearchRecursively**</span></span>  
<span data-ttu-id="b39dc-343">指定是否在指定目录中以递归方式搜索。</span><span class="sxs-lookup"><span data-stu-id="b39dc-343">Specifies whether to search recursively within the specified directory.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="b39dc-344">外部资源</span><span class="sxs-lookup"><span data-stu-id="b39dc-344">External Resources</span></span>  
  
-   <span data-ttu-id="b39dc-345">bidn.com 上的博客文章 [用于各节点列表枚举器的 SSIS](https://go.microsoft.com/fwlink/?LinkId=220671)。</span><span class="sxs-lookup"><span data-stu-id="b39dc-345">Blog entry, [SSIS For Each Node List Enumerator](https://go.microsoft.com/fwlink/?LinkId=220671), on bidn.com.</span></span>  
  
-   <span data-ttu-id="b39dc-346">博客文章[： SSIS-动态设置文件掩码： FileSpec](https://rajsudeep.blogspot.com/2010/09/ssisdynamically-set-file-mask-filespec.html)。</span><span class="sxs-lookup"><span data-stu-id="b39dc-346">Blog entry, [SSIS-Dynamically set File Mask : FileSpec](https://rajsudeep.blogspot.com/2010/09/ssisdynamically-set-file-mask-filespec.html).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b39dc-347">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b39dc-347">See Also</span></span>  
 <span data-ttu-id="b39dc-348">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="b39dc-348">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="b39dc-349">[Foreach 循环编辑器 &#40;常规页&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="b39dc-349">[Foreach Loop Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="b39dc-350">[Foreach 循环编辑器 &#40;的 "变量映射" 页&#41;](../../2014/integration-services/foreach-loop-editor-variable-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="b39dc-350">[Foreach Loop Editor &#40;Variable Mappings Page&#41;](../../2014/integration-services/foreach-loop-editor-variable-mappings-page.md) </span></span>  
 <span data-ttu-id="b39dc-351">[“表达式”页](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="b39dc-351">[Expressions Page](expressions/expressions-page.md) </span></span>  
 [<span data-ttu-id="b39dc-352">For 循环容器</span><span class="sxs-lookup"><span data-stu-id="b39dc-352">For Loop Container</span></span>](control-flow/for-loop-container.md)  
  
  
