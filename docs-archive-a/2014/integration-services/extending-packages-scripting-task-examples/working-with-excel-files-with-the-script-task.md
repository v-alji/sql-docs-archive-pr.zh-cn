---
title: 使用脚本任务处理 Excel 文件 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], Excel files
- Script task [Integration Services], examples
- Excel [Integration Services]
ms.assetid: b8fa110a-2c9c-4f5a-8fe1-305555640e44
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 68a764452de548cd46e74d2a7f2f588a050a21c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586905"
---
# <a name="working-with-excel-files-with-the-script-task"></a><span data-ttu-id="a99f7-102">使用脚本任务处理 Excel 文件</span><span class="sxs-lookup"><span data-stu-id="a99f7-102">Working with Excel Files with the Script Task</span></span>
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="a99f7-103">提供了 Excel 连接管理器、Excel 源和 Excel 目标，用于处理以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel 文件格式存储在电子表格中的数据。</span><span class="sxs-lookup"><span data-stu-id="a99f7-103">provides the Excel connection manager, Excel source, and Excel destination for working with data stored in spreadsheets in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel file format.</span></span> <span data-ttu-id="a99f7-104">本主题中介绍的技术使用脚本任务获取有关可用的 Excel 数据库（工作簿文件）和表（工作表和指定范围）的信息。</span><span class="sxs-lookup"><span data-stu-id="a99f7-104">The techniques described in this topic use the Script task to obtain information about available Excel databases (workbook files) and tables (worksheets and named ranges).</span></span> <span data-ttu-id="a99f7-105">可以轻松修改这些示例以处理 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Jet OLE DB 访问接口支持的所有其他基于文件的数据源。</span><span class="sxs-lookup"><span data-stu-id="a99f7-105">These samples can easily be modified to work with any of the other file-based data sources supported by the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Jet OLE DB Provider.</span></span>  
  
 [<span data-ttu-id="a99f7-106">配置用于测试示例的包</span><span class="sxs-lookup"><span data-stu-id="a99f7-106">Configuring a Package to Test the Samples</span></span>](#configuring)  
  
 [<span data-ttu-id="a99f7-107">示例 1：检查 Excel 文件是否存在</span><span class="sxs-lookup"><span data-stu-id="a99f7-107">Example1: Check Whether an Excel File Exists</span></span>](#example1)  
  
 [<span data-ttu-id="a99f7-108">示例 2：检查 Excel 表是否存在</span><span class="sxs-lookup"><span data-stu-id="a99f7-108">Example 2: Check Whether an Excel Table Exists</span></span>](#example2)  
  
 [<span data-ttu-id="a99f7-109">示例 3：获取文件夹中的 Excel 文件的列表</span><span class="sxs-lookup"><span data-stu-id="a99f7-109">Example 3: Get a List of Excel Files in a Folder</span></span>](#example3)  
  
 [<span data-ttu-id="a99f7-110">示例 4：获取 Excel 文件中的表的列表</span><span class="sxs-lookup"><span data-stu-id="a99f7-110">Example 4: Get a List of Tables in an Excel File</span></span>](#example4)  
  
 [<span data-ttu-id="a99f7-111">显示示例的结果</span><span class="sxs-lookup"><span data-stu-id="a99f7-111">Displaying the Results of the Samples</span></span>](#testing)  
  
> [!NOTE]  
>  <span data-ttu-id="a99f7-112">如果希望创建可更方便地重用于多个包的任务，请考虑以此脚本任务示例中的代码为基础，创建自定义任务。</span><span class="sxs-lookup"><span data-stu-id="a99f7-112">If you want to create a task that you can more easily reuse across multiple packages, consider using the code in this Script task sample as the starting point for a custom task.</span></span> <span data-ttu-id="a99f7-113">有关详细信息，请参阅 [开发自定义任务](../extending-packages-custom-objects/task/developing-a-custom-task.md)。</span><span class="sxs-lookup"><span data-stu-id="a99f7-113">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
##  <a name="configuring-a-package-to-test-the-samples"></a><a name="configuring"></a> <span data-ttu-id="a99f7-114">配置用于测试示例的包</span><span class="sxs-lookup"><span data-stu-id="a99f7-114">Configuring a Package to Test the Samples</span></span>  
 <span data-ttu-id="a99f7-115">您可以配置单个包来测试本主题中的所有示例。</span><span class="sxs-lookup"><span data-stu-id="a99f7-115">You can configure a single package to test all the samples in this topic.</span></span> <span data-ttu-id="a99f7-116">这些示例使用许多相同的包变量和相同的 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 类。</span><span class="sxs-lookup"><span data-stu-id="a99f7-116">The samples use many of the same package variables and the same [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] classes.</span></span>  
  
#### <a name="to-configure-a-package-for-use-with-the-examples-in-this-topic"></a><span data-ttu-id="a99f7-117">将包配置为用于本主题中的示例</span><span class="sxs-lookup"><span data-stu-id="a99f7-117">To configure a package for use with the examples in this topic</span></span>  
  
1.  <span data-ttu-id="a99f7-118">在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 中创建新的 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 项目，并打开默认的包进行编辑。</span><span class="sxs-lookup"><span data-stu-id="a99f7-118">Create a new [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and open the default package for editing.</span></span>  
  
2.  <span data-ttu-id="a99f7-119">**变量**。</span><span class="sxs-lookup"><span data-stu-id="a99f7-119">**Variables**.</span></span> <span data-ttu-id="a99f7-120">打开“变量”\*\*\*\* 窗口并定义以下变量：</span><span class="sxs-lookup"><span data-stu-id="a99f7-120">Open the **Variables** window and define the following variables:</span></span>  
  
    -   <span data-ttu-id="a99f7-121">`String` 类型的 `ExcelFile`。</span><span class="sxs-lookup"><span data-stu-id="a99f7-121">`ExcelFile`, of type `String`.</span></span> <span data-ttu-id="a99f7-122">输入现有 Excel 工作簿的完整路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="a99f7-122">Enter the complete path and filename to an existing Excel workbook.</span></span>  
  
    -   <span data-ttu-id="a99f7-123">`String` 类型的 `ExcelTable`。</span><span class="sxs-lookup"><span data-stu-id="a99f7-123">`ExcelTable`, of type `String`.</span></span> <span data-ttu-id="a99f7-124">输入以 `ExcelFile` 变量值命名的工作簿中的现有工作簿或指定范围的名称。</span><span class="sxs-lookup"><span data-stu-id="a99f7-124">Enter the name of an existing worksheet or named range in the workbook named in the value of the `ExcelFile` variable.</span></span> <span data-ttu-id="a99f7-125">此值区分大小写。</span><span class="sxs-lookup"><span data-stu-id="a99f7-125">This value is case-sensitive.</span></span>  
  
    -   <span data-ttu-id="a99f7-126">`Boolean` 类型的 `ExcelFileExists`。</span><span class="sxs-lookup"><span data-stu-id="a99f7-126">`ExcelFileExists`, of type `Boolean`.</span></span>  
  
    -   <span data-ttu-id="a99f7-127">`Boolean` 类型的 `ExcelTableExists`。</span><span class="sxs-lookup"><span data-stu-id="a99f7-127">`ExcelTableExists`, of type `Boolean`.</span></span>  
  
    -   <span data-ttu-id="a99f7-128">`String` 类型的 `ExcelFolder`。</span><span class="sxs-lookup"><span data-stu-id="a99f7-128">`ExcelFolder`, of type `String`.</span></span> <span data-ttu-id="a99f7-129">输入至少包含一个 Excel 工作簿的文件夹的完整路径。</span><span class="sxs-lookup"><span data-stu-id="a99f7-129">Enter the complete path of a folder that contains at least one Excel workbook.</span></span>  
  
    -   <span data-ttu-id="a99f7-130">`Object` 类型的 `ExcelFiles`。</span><span class="sxs-lookup"><span data-stu-id="a99f7-130">`ExcelFiles`, of type `Object`.</span></span>  
  
    -   <span data-ttu-id="a99f7-131">`Object` 类型的 `ExcelTables`。</span><span class="sxs-lookup"><span data-stu-id="a99f7-131">`ExcelTables`, of type `Object`.</span></span>  
  
3.  <span data-ttu-id="a99f7-132">Imports 语句\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a99f7-132">**Imports statements**.</span></span> <span data-ttu-id="a99f7-133">多数代码示例都要求您在脚本文件的开头处导入一个或两个下列 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 命名空间：</span><span class="sxs-lookup"><span data-stu-id="a99f7-133">Most of the code samples require you to import one or both of the following [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] namespaces at the top of your script file:</span></span>  
  
    -   <span data-ttu-id="a99f7-134">`System.IO` 用于文件系统操作。</span><span class="sxs-lookup"><span data-stu-id="a99f7-134">`System.IO`, for file system operations.</span></span>  
  
    -   <span data-ttu-id="a99f7-135">`System.Data.OleDb` 用于将 Excel 文件作为数据源打开。</span><span class="sxs-lookup"><span data-stu-id="a99f7-135">`System.Data.OleDb`, to open Excel files as data sources.</span></span>  
  
4.  <span data-ttu-id="a99f7-136">**引用**。</span><span class="sxs-lookup"><span data-stu-id="a99f7-136">**References**.</span></span> <span data-ttu-id="a99f7-137">从 Excel 文件读取架构信息的代码示例在脚本项目中需要对 `System.Xml` 命名空间的附加引用。</span><span class="sxs-lookup"><span data-stu-id="a99f7-137">The code samples that read schema information from Excel files require an additional reference in the script project to the `System.Xml` namespace.</span></span>  
  
5.  <span data-ttu-id="a99f7-138">设置脚本组件的默认脚本语言，方法是使用“选项”\*\*\*\* 对话框的“常规”\*\*\*\* 页上的“脚本语言”\*\*\*\* 选项。</span><span class="sxs-lookup"><span data-stu-id="a99f7-138">Set the default scripting language for the Script component by using the **Scripting language** option on the **General** page of the **Options** dialog box.</span></span> <span data-ttu-id="a99f7-139">有关详细信息，请参阅 [General Page](../general-page-of-integration-services-designers-options.md)。</span><span class="sxs-lookup"><span data-stu-id="a99f7-139">For more information, see [General Page](../general-page-of-integration-services-designers-options.md).</span></span>  
  
##  <a name="example-1-description-check-whether-an-excel-file-exists"></a><a name="example1"></a> <span data-ttu-id="a99f7-140">示例 1 说明：检查 Excel 文件是否存在</span><span class="sxs-lookup"><span data-stu-id="a99f7-140">Example 1 Description: Check Whether an Excel File Exists</span></span>  
 <span data-ttu-id="a99f7-141">本示例可确定 `ExcelFile` 变量中指定的 Excel 工作簿文件是否存在，然后根据该结果设置 `ExcelFileExists` 变量的布尔值。</span><span class="sxs-lookup"><span data-stu-id="a99f7-141">This example determines whether the Excel workbook file specified in the `ExcelFile` variable exists, and then sets the Boolean value of the `ExcelFileExists` variable to the result.</span></span> <span data-ttu-id="a99f7-142">可以使用此布尔值在包的工作流中进行分支。</span><span class="sxs-lookup"><span data-stu-id="a99f7-142">You can use this Boolean value for branching in the workflow of the package.</span></span>  
  
#### <a name="to-configure-this-script-task-example"></a><span data-ttu-id="a99f7-143">配置此脚本任务示例</span><span class="sxs-lookup"><span data-stu-id="a99f7-143">To configure this Script Task example</span></span>  
  
1.  <span data-ttu-id="a99f7-144">向包中添加新的脚本任务，并将其名称更改为 `ExcelFileExists` 。</span><span class="sxs-lookup"><span data-stu-id="a99f7-144">Add a new Script task to the package and change its name to `ExcelFileExists`.</span></span>  
  
2.  <span data-ttu-id="a99f7-145">在“脚本任务编辑器”\*\*\*\* 的“脚本”\*\*\*\* 选项卡上，单击“ReadOnlyVariables”\*\*\*\*，然后使用下列任一方法输入属性值：</span><span class="sxs-lookup"><span data-stu-id="a99f7-145">In the **Script Task Editor**, on the **Script** tab, click **ReadOnlyVariables** and enter the property value using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="a99f7-146">键入 `ExcelFile`。</span><span class="sxs-lookup"><span data-stu-id="a99f7-146">Type `ExcelFile`.</span></span>  
  
         <span data-ttu-id="a99f7-147">- 或 -</span><span class="sxs-lookup"><span data-stu-id="a99f7-147">-or-</span></span>  
  
    -   <span data-ttu-id="a99f7-148">单击属性字段旁的**省略号 ("**) " 按钮，然后在 "**选择变量**" 对话框中选择 `ExcelFile` 变量。</span><span class="sxs-lookup"><span data-stu-id="a99f7-148">Click the ellipsis (**...**) button next to the property field, and in the **Select variables** dialog box, select the `ExcelFile` variable.</span></span>  
  
3.  <span data-ttu-id="a99f7-149">单击“ReadWriteVariables”\*\*\*\*，然后使用下列任一方法输入属性值：</span><span class="sxs-lookup"><span data-stu-id="a99f7-149">Click **ReadWriteVariables** and enter the property value using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="a99f7-150">键入 `ExcelFileExists`。</span><span class="sxs-lookup"><span data-stu-id="a99f7-150">Type `ExcelFileExists`.</span></span>  
  
         <span data-ttu-id="a99f7-151">- 或 -</span><span class="sxs-lookup"><span data-stu-id="a99f7-151">-or-</span></span>  
  
    -   <span data-ttu-id="a99f7-152">单击属性字段旁的**省略号 ("**) " 按钮，然后在 "**选择变量**" 对话框中选择 `ExcelFileExists` 变量。</span><span class="sxs-lookup"><span data-stu-id="a99f7-152">Click the ellipsis (**...**) button next to the property field, and in the **Select variables** dialog box, select the `ExcelFileExists` variable.</span></span>  
  
4.  <span data-ttu-id="a99f7-153">单击“编辑脚本”\*\*\*\* 以打开脚本编辑器。</span><span class="sxs-lookup"><span data-stu-id="a99f7-153">Click **Edit Script** to open the script editor.</span></span>  
  
5.  <span data-ttu-id="a99f7-154">在脚本文件的开头处添加针对 `Imports` 命名空间的 `System.IO` 语句。</span><span class="sxs-lookup"><span data-stu-id="a99f7-154">Add an `Imports` statement for the `System.IO` namespace at the top of the script file.</span></span>  
  
6.  <span data-ttu-id="a99f7-155">添加以下代码。</span><span class="sxs-lookup"><span data-stu-id="a99f7-155">Add the following code.</span></span>  
  
### <a name="example-1-code"></a><span data-ttu-id="a99f7-156">示例 1 代码</span><span class="sxs-lookup"><span data-stu-id="a99f7-156">Example 1 Code</span></span>  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Dim fileToTest As String  
  
    fileToTest = Dts.Variables("ExcelFile").Value.ToString  
    If File.Exists(fileToTest) Then  
      Dts.Variables("ExcelFileExists").Value = True  
    Else  
      Dts.Variables("ExcelFileExists").Value = False  
    End If  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
  public void Main()  
  {  
    string fileToTest;  
  
    fileToTest = Dts.Variables["ExcelFile"].Value.ToString();  
    if (File.Exists(fileToTest))  
    {  
      Dts.Variables["ExcelFileExists"].Value = true;  
    }  
    else  
    {  
      Dts.Variables["ExcelFileExists"].Value = false;  
    }  
  
    Dts.TaskResult = (int)ScriptResults.Success;  
  }  
}  
```  
  
##  <a name="example-2-description-check-whether-an-excel-table-exists"></a><a name="example2"></a> <span data-ttu-id="a99f7-157">示例 2 说明：检查 Excel 表是否存在</span><span class="sxs-lookup"><span data-stu-id="a99f7-157">Example 2 Description: Check Whether an Excel Table Exists</span></span>  
 <span data-ttu-id="a99f7-158">本示例可确定 `ExcelTable` 变量中指定的 Excel 工作表或命名范围是否存在于 `ExcelFile` 变量中指定的 Excel 工作簿文件中，然后根据该结果设置 `ExcelTableExists` 变量的布尔值。</span><span class="sxs-lookup"><span data-stu-id="a99f7-158">This example determines whether the Excel worksheet or named range specified in the `ExcelTable` variable exists in the Excel workbook file specified in the `ExcelFile` variable, and then sets the Boolean value of the `ExcelTableExists` variable to the result.</span></span> <span data-ttu-id="a99f7-159">可以使用此布尔值在包的工作流中进行分支。</span><span class="sxs-lookup"><span data-stu-id="a99f7-159">You can use this Boolean value for branching in the workflow of the package.</span></span>  
  
#### <a name="to-configure-this-script-task-example"></a><span data-ttu-id="a99f7-160">配置此脚本任务示例</span><span class="sxs-lookup"><span data-stu-id="a99f7-160">To configure this Script Task example</span></span>  
  
1.  <span data-ttu-id="a99f7-161">向包中添加新的脚本任务，并将其名称更改为 `ExcelTableExists` 。</span><span class="sxs-lookup"><span data-stu-id="a99f7-161">Add a new Script task to the package and change its name to `ExcelTableExists`.</span></span>  
  
2.  <span data-ttu-id="a99f7-162">在“脚本任务编辑器”\*\*\*\* 的“脚本”\*\*\*\* 选项卡上，单击“ReadOnlyVariables”\*\*\*\*，然后使用下列任一方法输入属性值：</span><span class="sxs-lookup"><span data-stu-id="a99f7-162">In the **Script Task Editor**, on the **Script** tab, click **ReadOnlyVariables** and enter the property value using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="a99f7-163">键入 `ExcelTable` 并 `ExcelFile` 以逗号分隔`.`</span><span class="sxs-lookup"><span data-stu-id="a99f7-163">Type `ExcelTable` and `ExcelFile` separated by commas`.`</span></span>  
  
         <span data-ttu-id="a99f7-164">- 或 -</span><span class="sxs-lookup"><span data-stu-id="a99f7-164">-or-</span></span>  
  
    -   <span data-ttu-id="a99f7-165">单击属性字段旁的**省略号 ("**) " 按钮，然后在 "**选择变量**" 对话框中选择 `ExcelTable` 和 `ExcelFile` 变量。</span><span class="sxs-lookup"><span data-stu-id="a99f7-165">Click the ellipsis (**...**) button next to the property field, and in the **Select variables** dialog box, select the `ExcelTable` and `ExcelFile` variables.</span></span>  
  
3.  <span data-ttu-id="a99f7-166">单击“ReadWriteVariables”\*\*\*\*，然后使用下列任一方法输入属性值：</span><span class="sxs-lookup"><span data-stu-id="a99f7-166">Click **ReadWriteVariables** and enter the property value using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="a99f7-167">键入 `ExcelTableExists`。</span><span class="sxs-lookup"><span data-stu-id="a99f7-167">Type `ExcelTableExists`.</span></span>  
  
         <span data-ttu-id="a99f7-168">- 或 -</span><span class="sxs-lookup"><span data-stu-id="a99f7-168">-or-</span></span>  
  
    -   <span data-ttu-id="a99f7-169">单击属性字段旁的**省略号 ("**) " 按钮，然后在 "**选择变量**" 对话框中选择 `ExcelTableExists` 变量。</span><span class="sxs-lookup"><span data-stu-id="a99f7-169">Click the ellipsis (**...**) button next to the property field, and in the **Select variables** dialog box, select the `ExcelTableExists` variable.</span></span>  
  
4.  <span data-ttu-id="a99f7-170">单击“编辑脚本”\*\*\*\* 以打开脚本编辑器。</span><span class="sxs-lookup"><span data-stu-id="a99f7-170">Click **Edit Script** to open the script editor.</span></span>  
  
5.  <span data-ttu-id="a99f7-171">在脚本项目中添加对 `System.Xml` 程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="a99f7-171">Add a reference to the `System.Xml` assembly in the script project.</span></span>  
  
6.  <span data-ttu-id="a99f7-172">在脚本文件的开头处添加针对 `Imports` 和 `System.IO` 命名空间的 `System.Data.OleDb` 语句。</span><span class="sxs-lookup"><span data-stu-id="a99f7-172">Add `Imports` statements for the `System.IO` and `System.Data.OleDb` namespaces at the top of the script file.</span></span>  
  
7.  <span data-ttu-id="a99f7-173">添加以下代码。</span><span class="sxs-lookup"><span data-stu-id="a99f7-173">Add the following code.</span></span>  
  
### <a name="example-2-code"></a><span data-ttu-id="a99f7-174">示例 2 代码</span><span class="sxs-lookup"><span data-stu-id="a99f7-174">Example 2 Code</span></span>  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Dim fileToTest As String  
    Dim tableToTest As String  
    Dim connectionString As String  
    Dim excelConnection As OleDbConnection  
    Dim excelTables As DataTable  
    Dim excelTable As DataRow  
    Dim currentTable As String  
  
    fileToTest = Dts.Variables("ExcelFile").Value.ToString  
    tableToTest = Dts.Variables("ExcelTable").Value.ToString  
  
    Dts.Variables("ExcelTableExists").Value = False  
    If File.Exists(fileToTest) Then  
      connectionString = "Provider=Microsoft.Jet.OLEDB.4.0;" & _  
        "Data Source=" & fileToTest & _  
        ";Extended Properties=Excel 8.0"  
      excelConnection = New OleDbConnection(connectionString)  
      excelConnection.Open()  
      excelTables = excelConnection.GetSchema("Tables")  
      For Each excelTable In excelTables.Rows  
        currentTable = excelTable.Item("TABLE_NAME").ToString  
        If currentTable = tableToTest Then  
          Dts.Variables("ExcelTableExists").Value = True  
        End If  
      Next  
    End If  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
    public void Main()  
        {  
            string fileToTest;  
            string tableToTest;  
            string connectionString;  
            OleDbConnection excelConnection;  
            DataTable excelTables;  
            string currentTable;  
  
            fileToTest = Dts.Variables["ExcelFile"].Value.ToString();  
            tableToTest = Dts.Variables["ExcelTable"].Value.ToString();  
  
            Dts.Variables["ExcelTableExists"].Value = false;  
            if (File.Exists(fileToTest))  
            {  
                connectionString = "Provider=Microsoft.Jet.OLEDB.4.0;" +  
                "Data Source=" + fileToTest + ";Extended Properties=Excel 8.0";  
                excelConnection = new OleDbConnection(connectionString);  
                excelConnection.Open();  
                excelTables = excelConnection.GetSchema("Tables");  
                foreach (DataRow excelTable in excelTables.Rows)  
                {  
                    currentTable = excelTable["TABLE_NAME"].ToString();  
                    if (currentTable == tableToTest)  
                    {  
                        Dts.Variables["ExcelTableExists"].Value = true;  
                    }  
                }  
            }  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
}  
```  
  
##  <a name="example-3-description-get-a-list-of-excel-files-in-a-folder"></a><a name="example3"></a> <span data-ttu-id="a99f7-175">示例 3 说明：获取文件夹中的 Excel 文件的列表</span><span class="sxs-lookup"><span data-stu-id="a99f7-175">Example 3 Description: Get a List of Excel Files in a Folder</span></span>  
 <span data-ttu-id="a99f7-176">本示例使用由 `ExcelFolder` 变量值指定的文件夹中找到的 Excel 文件的列表来填充数组，然后将该数组复制到 `ExcelFiles` 变量。</span><span class="sxs-lookup"><span data-stu-id="a99f7-176">This example fills an array with the list of Excel files found in the folder specified in the value of the `ExcelFolder` variable, and then copies the array into the `ExcelFiles` variable.</span></span> <span data-ttu-id="a99f7-177">您可以使用 Foreach 源变量枚举器循环访问数组中的文件。</span><span class="sxs-lookup"><span data-stu-id="a99f7-177">You can use the Foreach from Variable enumerator to iterate over the files in the array.</span></span>  
  
#### <a name="to-configure-this-script-task-example"></a><span data-ttu-id="a99f7-178">配置此脚本任务示例</span><span class="sxs-lookup"><span data-stu-id="a99f7-178">To configure this Script Task example</span></span>  
  
1.  <span data-ttu-id="a99f7-179">将新的脚本任务添加到包，并将其名称更改为 GetExcelFiles\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a99f7-179">Add a new Script task to the package and change its name to **GetExcelFiles**.</span></span>  
  
2.  <span data-ttu-id="a99f7-180">打开“脚本任务编辑器”\*\*\*\*，在“脚本”\*\*\*\* 选项卡上单击“ReadOnlyVariables”\*\*\*\*，然后使用下列任一方法输入属性值：</span><span class="sxs-lookup"><span data-stu-id="a99f7-180">Open the **Script Task Editor**, on the **Script** tab, click **ReadOnlyVariables** and enter the property value using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="a99f7-181">键入 `ExcelFolder`</span><span class="sxs-lookup"><span data-stu-id="a99f7-181">Type `ExcelFolder`</span></span>  
  
         <span data-ttu-id="a99f7-182">- 或 -</span><span class="sxs-lookup"><span data-stu-id="a99f7-182">-or-</span></span>  
  
    -   <span data-ttu-id="a99f7-183">单击属性字段旁的省略号 (…) 按钮，然后在“选择变量”对话框中选择“ExcelFolder”变量\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a99f7-183">Click the ellipsis (**...**) button next to the property field, and in the **Select variables** dialog box, select the ExcelFolder variable.</span></span>  
  
3.  <span data-ttu-id="a99f7-184">单击“ReadWriteVariables”\*\*\*\*，然后使用下列任一方法输入属性值：</span><span class="sxs-lookup"><span data-stu-id="a99f7-184">Click **ReadWriteVariables** and enter the property value using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="a99f7-185">键入 `ExcelFiles`。</span><span class="sxs-lookup"><span data-stu-id="a99f7-185">Type `ExcelFiles`.</span></span>  
  
         <span data-ttu-id="a99f7-186">- 或 -</span><span class="sxs-lookup"><span data-stu-id="a99f7-186">-or-</span></span>  
  
    -   <span data-ttu-id="a99f7-187">单击属性字段旁的省略号 (…) 按钮，然后在“选择变量”对话框中选择“ExcelFile”变量\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a99f7-187">Click the ellipsis (**...**) button next to the property field, and in the **Select variables** dialog box, select the ExcelFiles variable.</span></span>  
  
4.  <span data-ttu-id="a99f7-188">单击“编辑脚本”\*\*\*\* 以打开脚本编辑器。</span><span class="sxs-lookup"><span data-stu-id="a99f7-188">Click **Edit Script** to open the script editor.</span></span>  
  
5.  <span data-ttu-id="a99f7-189">在脚本文件的开头处添加针对 `Imports` 命名空间的 `System.IO` 语句。</span><span class="sxs-lookup"><span data-stu-id="a99f7-189">Add an `Imports` statement for the `System.IO` namespace at the top of the script file.</span></span>  
  
6.  <span data-ttu-id="a99f7-190">添加以下代码。</span><span class="sxs-lookup"><span data-stu-id="a99f7-190">Add the following code.</span></span>  
  
### <a name="example-3-code"></a><span data-ttu-id="a99f7-191">示例 3 代码</span><span class="sxs-lookup"><span data-stu-id="a99f7-191">Example 3 Code</span></span>  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Const FILE_PATTERN As String = "*.xls"  
  
    Dim excelFolder As String  
    Dim excelFiles As String()  
  
    excelFolder = Dts.Variables("ExcelFolder").Value.ToString  
    excelFiles = Directory.GetFiles(excelFolder, FILE_PATTERN)  
  
    Dts.Variables("ExcelFiles").Value = excelFiles  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
  public void Main()  
  {  
    const string FILE_PATTERN = "*.xls";  
  
    string excelFolder;  
    string[] excelFiles;  
  
    excelFolder = Dts.Variables["ExcelFolder"].Value.ToString();  
    excelFiles = Directory.GetFiles(excelFolder, FILE_PATTERN);  
  
    Dts.Variables["ExcelFiles"].Value = excelFiles;  
  
    Dts.TaskResult = (int)ScriptResults.Success;  
  }  
}  
```  
  
### <a name="alternate-solution"></a><span data-ttu-id="a99f7-192">备用解决方案</span><span class="sxs-lookup"><span data-stu-id="a99f7-192">Alternate Solution</span></span>  
 <span data-ttu-id="a99f7-193">如果不使用脚本任务将 Excel 文件列表收集到数组中，则还可以使用 ForEach 文件枚举器来循环访问文件夹中的所有 Excel 文件。</span><span class="sxs-lookup"><span data-stu-id="a99f7-193">Instead of using a Script task to gather a list of Excel files into an array, you can also use the ForEach File enumerator to iterate over all the Excel files in a folder.</span></span> <span data-ttu-id="a99f7-194">有关详细信息，请参阅[使用 Foreach 循环容器循环遍历 Excel 文件和表](../control-flow/foreach-loop-container.md)。</span><span class="sxs-lookup"><span data-stu-id="a99f7-194">For more information, see [Loop through Excel Files and Tables by Using a Foreach Loop Container](../control-flow/foreach-loop-container.md).</span></span>  
  
##  <a name="example-4-description-get-a-list-of-tables-in-an-excel-file"></a><a name="example4"></a> <span data-ttu-id="a99f7-195">示例 4 说明：获取 Excel 文件中的表的列表</span><span class="sxs-lookup"><span data-stu-id="a99f7-195">Example 4 Description: Get a List of Tables in an Excel File</span></span>  
 <span data-ttu-id="a99f7-196">本示例使用在 Excel 工作簿文件中找到的由 `ExcelFile` 变量值指定的工作表和指定范围列表来填充数组，然后将该数组复制到 `ExcelTables` 变量。</span><span class="sxs-lookup"><span data-stu-id="a99f7-196">This example fills an array with the list of worksheets and named ranges found in the Excel workbook file specified by the value of the `ExcelFile` variable, and then copies the array into the `ExcelTables` variable.</span></span> <span data-ttu-id="a99f7-197">您可以使用 Foreach 源变量枚举器循环访问数组中的表。</span><span class="sxs-lookup"><span data-stu-id="a99f7-197">You can use the Foreach from Variable Enumerator to iterate over the tables in the array.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a99f7-198">Excel 工作簿中的表列表同时包括工作表（具有 $ 后缀）和指定范围。</span><span class="sxs-lookup"><span data-stu-id="a99f7-198">The list of tables in an Excel workbook includes both worksheets (which have the $ suffix) and named ranges.</span></span> <span data-ttu-id="a99f7-199">如果要从列表中只筛选出工作表或指定范围，则必须添加其他代码来实现这一点。</span><span class="sxs-lookup"><span data-stu-id="a99f7-199">If you have to filter the list for only worksheets or only named ranges, you may have to add additional code for this purpose.</span></span>  
  
#### <a name="to-configure-this-script-task-example"></a><span data-ttu-id="a99f7-200">配置此脚本任务示例</span><span class="sxs-lookup"><span data-stu-id="a99f7-200">To configure this Script Task example</span></span>  
  
1.  <span data-ttu-id="a99f7-201">将新的脚本任务添加到包中，并将其名称更改为 GetExcelTables\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a99f7-201">Add a new Script task to the package and change its name to **GetExcelTables**.</span></span>  
  
2.  <span data-ttu-id="a99f7-202">打开“脚本任务编辑器”\*\*\*\*，在“脚本”\*\*\*\* 选项卡上单击“ReadOnlyVariables”\*\*\*\*，然后使用下列任一方法输入属性值：</span><span class="sxs-lookup"><span data-stu-id="a99f7-202">Open the **Script Task Editor**, on the **Script** tab, click **ReadOnlyVariables** and enter the property value using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="a99f7-203">键入 `ExcelFile`。</span><span class="sxs-lookup"><span data-stu-id="a99f7-203">Type `ExcelFile`.</span></span>  
  
         <span data-ttu-id="a99f7-204">- 或 -</span><span class="sxs-lookup"><span data-stu-id="a99f7-204">-or-</span></span>  
  
    -   <span data-ttu-id="a99f7-205">单击属性字段旁的省略号 (…) 按钮，然后在“选择变量”对话框中选择“ExcelFile”变量\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a99f7-205">Click the ellipsis (**...**) button next to the property field, and in the **Select variables** dialog box, select the ExcelFile variable.</span></span>  
  
3.  <span data-ttu-id="a99f7-206">单击“ReadWriteVariables”\*\*\*\*，然后使用下列任一方法输入属性值：</span><span class="sxs-lookup"><span data-stu-id="a99f7-206">Click **ReadWriteVariables** and enter the property value using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="a99f7-207">键入 `ExcelTables`。</span><span class="sxs-lookup"><span data-stu-id="a99f7-207">Type `ExcelTables`.</span></span>  
  
         <span data-ttu-id="a99f7-208">- 或 -</span><span class="sxs-lookup"><span data-stu-id="a99f7-208">-or-</span></span>  
  
    -   <span data-ttu-id="a99f7-209">单击属性字段旁的省略号 (…) 按钮，然后在“选择变量”对话框中选择“ExcelTables”变量\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a99f7-209">Click the ellipsis (**...**) button next to the property field, and in the **Select variables** dialog box, select the ExcelTablesvariable.</span></span>  
  
4.  <span data-ttu-id="a99f7-210">单击“编辑脚本”\*\*\*\* 以打开脚本编辑器。</span><span class="sxs-lookup"><span data-stu-id="a99f7-210">Click **Edit Script** to open the script editor.</span></span>  
  
5.  <span data-ttu-id="a99f7-211">`System.Xml`在脚本项目中添加对命名空间的引用。</span><span class="sxs-lookup"><span data-stu-id="a99f7-211">Add a reference to the `System.Xml` namespace in the script project.</span></span>  
  
6.  <span data-ttu-id="a99f7-212">在脚本文件的开头处添加针对 `Imports` 命名空间的 `System.Data.OleDb` 语句。</span><span class="sxs-lookup"><span data-stu-id="a99f7-212">Add an `Imports` statement for the `System.Data.OleDb` namespace at the top of the script file.</span></span>  
  
7.  <span data-ttu-id="a99f7-213">添加以下代码。</span><span class="sxs-lookup"><span data-stu-id="a99f7-213">Add the following code.</span></span>  
  
### <a name="example-4-code"></a><span data-ttu-id="a99f7-214">示例 4 代码</span><span class="sxs-lookup"><span data-stu-id="a99f7-214">Example 4 Code</span></span>  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Dim excelFile As String  
    Dim connectionString As String  
    Dim excelConnection As OleDbConnection  
    Dim tablesInFile As DataTable  
    Dim tableCount As Integer = 0  
    Dim tableInFile As DataRow  
    Dim currentTable As String  
    Dim tableIndex As Integer = 0  
  
    Dim excelTables As String()  
  
    excelFile = Dts.Variables("ExcelFile").Value.ToString  
    connectionString = "Provider=Microsoft.Jet.OLEDB.4.0;" & _  
        "Data Source=" & excelFile & _  
        ";Extended Properties=Excel 8.0"  
    excelConnection = New OleDbConnection(connectionString)  
    excelConnection.Open()  
    tablesInFile = excelConnection.GetSchema("Tables")  
    tableCount = tablesInFile.Rows.Count  
    ReDim excelTables(tableCount - 1)  
    For Each tableInFile In tablesInFile.Rows  
      currentTable = tableInFile.Item("TABLE_NAME").ToString  
      excelTables(tableIndex) = currentTable  
      tableIndex += 1  
    Next  
  
    Dts.Variables("ExcelTables").Value = excelTables  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
  public void Main()  
        {  
            string excelFile;  
            string connectionString;  
            OleDbConnection excelConnection;  
            DataTable tablesInFile;  
            int tableCount = 0;  
            string currentTable;  
            int tableIndex = 0;  
  
            string[] excelTables = new string[5];  
  
            excelFile = Dts.Variables["ExcelFile"].Value.ToString();  
            connectionString = "Provider=Microsoft.Jet.OLEDB.4.0;" +  
                "Data Source=" + excelFile + ";Extended Properties=Excel 8.0";  
            excelConnection = new OleDbConnection(connectionString);  
            excelConnection.Open();  
            tablesInFile = excelConnection.GetSchema("Tables");  
            tableCount = tablesInFile.Rows.Count;  
  
            foreach (DataRow tableInFile in tablesInFile.Rows)  
            {  
                currentTable = tableInFile["TABLE_NAME"].ToString();  
                excelTables[tableIndex] = currentTable;  
                tableIndex += 1;  
            }  
  
            Dts.Variables["ExcelTables"].Value = excelTables;  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
}  
```  
  
### <a name="alternate-solution"></a><span data-ttu-id="a99f7-215">备用解决方案</span><span class="sxs-lookup"><span data-stu-id="a99f7-215">Alternate Solution</span></span>  
 <span data-ttu-id="a99f7-216">如果不使用脚本任务将 Excel 表列表收集到数组中，则还可以使用 ForEach ADO.NET 架构行集枚举器来循环访问 Excel 工作簿文件中的所有表（即，工作表和指定范围）。</span><span class="sxs-lookup"><span data-stu-id="a99f7-216">Instead of using a Script task to gather a list of Excel tables into an array, you can also use the ForEach ADO.NET Schema Rowset Enumerator to iterate over all the tables (that is, worksheets and named ranges) in an Excel workbook file.</span></span> <span data-ttu-id="a99f7-217">有关详细信息，请参阅[使用 Foreach 循环容器循环遍历 Excel 文件和表](../control-flow/foreach-loop-container.md)。</span><span class="sxs-lookup"><span data-stu-id="a99f7-217">For more information, see [Loop through Excel Files and Tables by Using a Foreach Loop Container](../control-flow/foreach-loop-container.md).</span></span>  
  
##  <a name="displaying-the-results-of-the-samples"></a><a name="testing"></a><span data-ttu-id="a99f7-218">显示示例的结果</span><span class="sxs-lookup"><span data-stu-id="a99f7-218">Displaying the Results of the Samples</span></span>  
 <span data-ttu-id="a99f7-219">如果已在同一个包中配置本主题的所有示例，则可以将所有脚本任务连接到用于显示所有示例输出的其他脚本任务。</span><span class="sxs-lookup"><span data-stu-id="a99f7-219">If you have configured each of the examples in this topic in the same package, you can connect all the Script tasks to an additional Script task that displays the output of all the examples.</span></span>  
  
#### <a name="to-configure-a-script-task-to-display-the-output-of-the-examples-in-this-topic"></a><span data-ttu-id="a99f7-220">配置用于显示本主题中的示例输出的脚本任务</span><span class="sxs-lookup"><span data-stu-id="a99f7-220">To configure a Script task to display the output of the examples in this topic</span></span>  
  
1.  <span data-ttu-id="a99f7-221">将新的脚本任务添加到包中，并将其名称更改为 DisplayResults\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a99f7-221">Add a new Script task to the package and change its name to **DisplayResults**.</span></span>  
  
2.  <span data-ttu-id="a99f7-222">将四个示例脚本任务彼此连接，以便每个任务在前一个任务成功完成后运行，然后将第四个示例任务连接到 DisplayResults\*\*\*\* 任务。</span><span class="sxs-lookup"><span data-stu-id="a99f7-222">Connect each of the four example Script tasks to one another, so that each task runs after the preceding task completes successfully, and connect the fourth example task to the **DisplayResults** task.</span></span>  
  
3.  <span data-ttu-id="a99f7-223">在“脚本任务编辑器”\*\*\*\* 中打开 DisplayResults\*\*\*\* 任务。</span><span class="sxs-lookup"><span data-stu-id="a99f7-223">Open the **DisplayResults** task in the **Script Task Editor**.</span></span>  
  
4.  <span data-ttu-id="a99f7-224">在“脚本”\*\*\*\* 选项卡中单击“ReadOnlyVariables”\*\*\*\* 然后使用下列任一方法添加[配置用于测试示例的包](#configuring)中列出的七个变量：</span><span class="sxs-lookup"><span data-stu-id="a99f7-224">On the **Script** tab, click **ReadOnlyVariables** and use one of the following methods to add all seven variables listed in [Configuring a Package to Test the Samples](#configuring):</span></span>  
  
    -   <span data-ttu-id="a99f7-225">键入用逗号分隔的每个变量的名称。</span><span class="sxs-lookup"><span data-stu-id="a99f7-225">Type the name of each variable separated by commas.</span></span>  
  
         <span data-ttu-id="a99f7-226">- 或 -</span><span class="sxs-lookup"><span data-stu-id="a99f7-226">-or-</span></span>  
  
    -   <span data-ttu-id="a99f7-227">单击属性字段旁的省略号 (…) 按钮，然后在“”选择变量对话框中选择变量\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a99f7-227">Click the ellipsis (**...**) button next to the property field, and in the **Select variables** dialog box, selecting the variables.</span></span>  
  
5.  <span data-ttu-id="a99f7-228">单击“编辑脚本”\*\*\*\* 以打开脚本编辑器。</span><span class="sxs-lookup"><span data-stu-id="a99f7-228">Click **Edit Script** to open the script editor.</span></span>  
  
6.  <span data-ttu-id="a99f7-229">在脚本文件的开头处添加针对 `Imports` 和 `Microsoft.VisualBasic` 命名空间的 `System.Windows.Forms` 语句。</span><span class="sxs-lookup"><span data-stu-id="a99f7-229">Add `Imports` statements for the `Microsoft.VisualBasic` and `System.Windows.Forms` namespaces at the top of the script file.</span></span>  
  
7.  <span data-ttu-id="a99f7-230">添加以下代码。</span><span class="sxs-lookup"><span data-stu-id="a99f7-230">Add the following code.</span></span>  
  
8.  <span data-ttu-id="a99f7-231">运行包，然后检查消息框中显示的结果。</span><span class="sxs-lookup"><span data-stu-id="a99f7-231">Run the package and examine the results displayed in a message box.</span></span>  
  
### <a name="code-to-display-the-results"></a><span data-ttu-id="a99f7-232">编写显示结果的代码</span><span class="sxs-lookup"><span data-stu-id="a99f7-232">Code to Display the Results</span></span>  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Const EOL As String = ControlChars.CrLf  
  
    Dim results As String  
    Dim filesInFolder As String()  
    Dim fileInFolder As String  
    Dim tablesInFile As String()  
    Dim tableInFile As String  
  
    results = _  
      "Final values of variables:" & EOL & _  
      "ExcelFile: " & Dts.Variables("ExcelFile").Value.ToString & EOL & _  
      "ExcelFileExists: " & Dts.Variables("ExcelFileExists").Value.ToString & EOL & _  
      "ExcelTable: " & Dts.Variables("ExcelTable").Value.ToString & EOL & _  
      "ExcelTableExists: " & Dts.Variables("ExcelTableExists").Value.ToString & EOL & _  
      "ExcelFolder: " & Dts.Variables("ExcelFolder").Value.ToString & EOL & _  
      EOL  
  
    results &= "Excel files in folder: " & EOL  
    filesInFolder = DirectCast(Dts.Variables("ExcelFiles").Value, String())  
    For Each fileInFolder In filesInFolder  
      results &= " " & fileInFolder & EOL  
    Next  
    results &= EOL  
  
    results &= "Excel tables in file: " & EOL  
    tablesInFile = DirectCast(Dts.Variables("ExcelTables").Value, String())  
    For Each tableInFile In tablesInFile  
      results &= " " & tableInFile & EOL  
    Next  
  
    MessageBox.Show(results, "Results", MessageBoxButtons.OK, MessageBoxIcon.Information)  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
  public void Main()  
        {  
            const string EOL = "\r";  
  
            string results;  
            string[] filesInFolder;  
            //string fileInFolder;  
            string[] tablesInFile;  
            //string tableInFile;  
  
            results = "Final values of variables:" + EOL + "ExcelFile: " + Dts.Variables["ExcelFile"].Value.ToString() + EOL + "ExcelFileExists: " + Dts.Variables["ExcelFileExists"].Value.ToString() + EOL + "ExcelTable: " + Dts.Variables["ExcelTable"].Value.ToString() + EOL + "ExcelTableExists: " + Dts.Variables["ExcelTableExists"].Value.ToString() + EOL + "ExcelFolder: " + Dts.Variables["ExcelFolder"].Value.ToString() + EOL + EOL;  
  
            results += "Excel files in folder: " + EOL;  
            filesInFolder = (string[])(Dts.Variables["ExcelFiles"].Value);  
            foreach (string fileInFolder in filesInFolder)  
            {  
                results += " " + fileInFolder + EOL;  
            }  
            results += EOL;  
  
            results += "Excel tables in file: " + EOL;  
            tablesInFile = (string[])(Dts.Variables["ExcelTables"].Value);  
            foreach (string tableInFile in tablesInFile)  
            {  
                results += " " + tableInFile + EOL;  
            }  
  
            MessageBox.Show(results, "Results", MessageBoxButtons.OK, MessageBoxIcon.Information);  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
}  
```  
  
<span data-ttu-id="a99f7-233">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="a99f7-233">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="a99f7-234">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="a99f7-234">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="a99f7-235">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="a99f7-235">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="a99f7-236">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="a99f7-236">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a99f7-237">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a99f7-237">See Also</span></span>  
 <span data-ttu-id="a99f7-238">[Excel 连接管理器](../connection-manager/excel-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="a99f7-238">[Excel Connection Manager](../connection-manager/excel-connection-manager.md) </span></span>  
 [<span data-ttu-id="a99f7-239">使用 Foreach 循环容器循环遍历 Excel 文件和表</span><span class="sxs-lookup"><span data-stu-id="a99f7-239">Loop through Excel Files and Tables by Using a Foreach Loop Container</span></span>](../control-flow/foreach-loop-container.md)  
  
  
