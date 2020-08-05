---
title: 使用 Foreach 循环容器循环遍历 Excel 文件和表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], Excel
- Excel [Integration Services]
- connection managers [Integration Services], Excel
ms.assetid: a5393c1a-cc37-491a-a260-7aad84dbff68
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 51de779b6869d80245302741035e6169aa750c83
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580817"
---
# <a name="loop-through-excel-files-and-tables-by-using-a-foreach-loop-container"></a><span data-ttu-id="a914c-102">使用 Foreach 循环容器，循环遍历 Excel 文件和表</span><span class="sxs-lookup"><span data-stu-id="a914c-102">Loop through Excel Files and Tables by Using a Foreach Loop Container</span></span>
  <span data-ttu-id="a914c-103">本主题中的过程介绍如何使用具有相应枚举器的 Foreach 循环容器循环访问文件夹中的 Excel 工作簿或 Excel 工作簿中的表。</span><span class="sxs-lookup"><span data-stu-id="a914c-103">The procedures in this topic describe how to loop through the Excel workbooks in a folder, or through the tables in an Excel workbook, by using the Foreach Loop container with the appropriate enumerator.</span></span>  
  
### <a name="to-loop-through-excel-files-by-using-the-foreach-file-enumerator"></a><span data-ttu-id="a914c-104">使用 Foreach 文件枚举器循环遍历 Excel 文件</span><span class="sxs-lookup"><span data-stu-id="a914c-104">To loop through Excel files by using the Foreach File enumerator</span></span>  
  
1.  <span data-ttu-id="a914c-105">创建一个将在每次循环迭代中接收当前 Excel 路径和文件名的字符串变量。</span><span class="sxs-lookup"><span data-stu-id="a914c-105">Create a string variable that will receive the current Excel path and file name on each iteration of the loop.</span></span> <span data-ttu-id="a914c-106">若要避免验证问题，请分配有效的 Excel 路径和文件名作为该变量的初始值。</span><span class="sxs-lookup"><span data-stu-id="a914c-106">To avoid validation issues, assign a valid Excel path and file name as the initial value of the variable.</span></span> <span data-ttu-id="a914c-107">（本过程后面显示的示例表达式将使用变量名 `ExcelFile`。）</span><span class="sxs-lookup"><span data-stu-id="a914c-107">(The sample expression shown later in this procedure uses the variable name, `ExcelFile`.)</span></span>  
  
2.  <span data-ttu-id="a914c-108">（可选）创建另一个字符串变量，用于存放 Excel 连接字符串的扩展属性参数的值。</span><span class="sxs-lookup"><span data-stu-id="a914c-108">Optionally, create another string variable that will hold the value for the Extended Properties argument of the Excel connection string.</span></span> <span data-ttu-id="a914c-109">此参数包含一系列值，这些值指定 Excel 版本并确定第一行是否包含列名称，以及是否使用导入模式。</span><span class="sxs-lookup"><span data-stu-id="a914c-109">This argument contains a series of values that specify the Excel version and determine whether the first row contains column names, and whether import mode is used.</span></span> <span data-ttu-id="a914c-110">（此过程随后显示的示例表达式将使用变量名 `ExtProperties`，其初始值为“`Excel 8.0;HDR=Yes`”。）</span><span class="sxs-lookup"><span data-stu-id="a914c-110">(The sample expression shown later in this procedure uses the variable name `ExtProperties`, with an initial value of "`Excel 8.0;HDR=Yes`".)</span></span>  
  
     <span data-ttu-id="a914c-111">如果您未使用扩展属性参数的变量，必须手动将它添加到包含连接字符串的表达式。</span><span class="sxs-lookup"><span data-stu-id="a914c-111">If you do not use a variable for the Extended Properties argument, then you must add it manually to the expression that contains the connection string.</span></span>  
  
3.  <span data-ttu-id="a914c-112">将 Foreach 循环容器添加到 "**控制流**" 选项卡中。有关如何配置 Foreach 循环容器的信息，请参阅[配置 Foreach 循环容器](foreach-loop-container.md)。</span><span class="sxs-lookup"><span data-stu-id="a914c-112">Add a Foreach Loop container to the **Control Flow** tab. For information about how to configure the Foreach Loop Container, see [Configure a Foreach Loop Container](foreach-loop-container.md).</span></span>  
  
4.  <span data-ttu-id="a914c-113">在“Foreach 循环编辑器”\*\*\*\* 的“集合”\*\*\*\* 页上，选择“Foreach 文件”枚举器，并指定 Excel 工作簿所在的文件夹，然后指定文件筛选器（通常是 \*.xls）。</span><span class="sxs-lookup"><span data-stu-id="a914c-113">On the **Collection** page of the **Foreach Loop Editor**, select the Foreach File enumerator, specify the folder in which the Excel workbooks are located, and specify the file filter (ordinarily \*.xls).</span></span>  
  
5.  <span data-ttu-id="a914c-114">在“变量映射”\*\*\*\* 页中，将索引 0 映射到用户定义字符串变量，该变量将在每个循环迭代中接收当前 Excel 路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="a914c-114">On the **Variable Mapping** page, map Index 0 to a user-defined string variable that will receive the current Excel path and file name on each iteration of the loop.</span></span> <span data-ttu-id="a914c-115">（本过程后面显示的示例表达式将使用变量名 `ExcelFile`。）</span><span class="sxs-lookup"><span data-stu-id="a914c-115">(The sample expression shown later in this procedure uses the variable name `ExcelFile`.)</span></span>  
  
6.  <span data-ttu-id="a914c-116">关闭 **“Foreach 循环编辑器”**。</span><span class="sxs-lookup"><span data-stu-id="a914c-116">Close the **Foreach Loop Editor**.</span></span>  
  
7.  <span data-ttu-id="a914c-117">按照 [在包中添加、删除或共享连接管理器](../add-delete-or-share-a-connection-manager-in-a-package.md)中所述，将 Excel 连接管理器添加到包。</span><span class="sxs-lookup"><span data-stu-id="a914c-117">Add an Excel connection manager to the package as described in [Add, Delete, or Share a Connection Manager in a Package](../add-delete-or-share-a-connection-manager-in-a-package.md).</span></span> <span data-ttu-id="a914c-118">为连接选择一个现有 Excel 工作簿文件以避免出现验证错误。</span><span class="sxs-lookup"><span data-stu-id="a914c-118">Select an existing Excel workbook file for the connection to avoid validation errors.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="a914c-119">若要避免在对使用此 Excel 连接管理器的任务和数据流组件进行配置时出现验证错误，请在 **“Excel 连接管理器编辑器”** 中选择一个现有的 Excel 工作簿。</span><span class="sxs-lookup"><span data-stu-id="a914c-119">To avoid validation errors as you configure tasks and data flow components that use this Excel connection manager, select an existing Excel workbook in the **Excel Connection Manager Editor**.</span></span> <span data-ttu-id="a914c-120">在您按照下列步骤为 `ConnectionString` 属性配置表达式以后，连接管理器在运行时将不使用此工作簿。</span><span class="sxs-lookup"><span data-stu-id="a914c-120">The connection manager will not use this workbook at run time after you configure an expression for the `ConnectionString` property as described in the following steps.</span></span> <span data-ttu-id="a914c-121">在创建并配置包后，可在“属性”窗口中清除 `ConnectionString` 属性的值。</span><span class="sxs-lookup"><span data-stu-id="a914c-121">After you create and configure the package, you can clear the value of the `ConnectionString` property in the Properties window.</span></span> <span data-ttu-id="a914c-122">但是，如果清除此值，要等到 Foreach 循环运行时 Excel 连接管理器的连接字符串属性才会有效。</span><span class="sxs-lookup"><span data-stu-id="a914c-122">However, if you clear this value, the connection string property of the Excel connection manager is no longer valid until the Foreach Loop runs.</span></span> <span data-ttu-id="a914c-123">因此，在使用了连接管理器的任务中，必须将 `DelayValidation` 属性设置为 `True` 以避免出现验证错误。</span><span class="sxs-lookup"><span data-stu-id="a914c-123">Therefore you must set the `DelayValidation` property to `True` on the tasks in which the connection manager is used, or on the package, to avoid validation errors.</span></span>  
    >   
    >  <span data-ttu-id="a914c-124">还必须使用 Excel 连接管理器的 `False` 属性的默认值 `RetainSameConnection`。</span><span class="sxs-lookup"><span data-stu-id="a914c-124">You must also use the default value of `False` for the `RetainSameConnection` property of the Excel connection manager.</span></span> <span data-ttu-id="a914c-125">如果将此值更改为 `True`，该循环的每次迭代将继续打开第一个 Excel 工作簿。</span><span class="sxs-lookup"><span data-stu-id="a914c-125">If you change this value to `True`, each iteration of the loop will continue to open the first Excel workbook.</span></span>  
  
8.  <span data-ttu-id="a914c-126">选择新的 Excel 连接管理器，并在“属性”窗口中单击 **“表达式”** 属性，然后单击省略号。</span><span class="sxs-lookup"><span data-stu-id="a914c-126">Select the new Excel connection manager, click the **Expressions** property in the Properties window, and then click the ellipsis.</span></span>  
  
9. <span data-ttu-id="a914c-127">在 "**属性表达式编辑器**" 中，选择 `ConnectionString` 属性，然后单击省略号。</span><span class="sxs-lookup"><span data-stu-id="a914c-127">In the **Property Expressions Editor**, select the `ConnectionString` property, and then click the ellipsis.</span></span>  
  
10. <span data-ttu-id="a914c-128">在表达式生成器中，输入以下表达式：</span><span class="sxs-lookup"><span data-stu-id="a914c-128">In the Expression Builder, enter the following expression:</span></span>  
  
    ```  
    "Provider=Microsoft.Jet.OLEDB.4.0;Data Source=" +  @[User::ExcelFile] + ";Extended Properties=\"" + @[User::ExtProperties] + "\""  
    ```  
  
     <span data-ttu-id="a914c-129">注意使用转义符“\\”来转义扩展属性参数的值前后所需的内部引号。</span><span class="sxs-lookup"><span data-stu-id="a914c-129">Note the use of the escape character "\\" to escape the inner quotation marks required around the value of the Extended Properties argument.</span></span>  
  
     <span data-ttu-id="a914c-130">扩展属性参数不是可选的。</span><span class="sxs-lookup"><span data-stu-id="a914c-130">The Extended Properties argument is not optional.</span></span> <span data-ttu-id="a914c-131">如果您未使用变量来包含其值，则必须手动将它添加到表达式中，如针对 Excel 2003 文件的以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="a914c-131">If you do not use a variable to contain its value, then you must add it manually to the expression, as in the following example for an Excel 2003 file:</span></span>  
  
    ```  
    "Provider=Microsoft.Jet.OLEDB.4.0;Data Source=" +  @[User::ExcelFile] + ";Extended Properties=Excel 8.0"  
    ```  
  
11. <span data-ttu-id="a914c-132">在 Foreach 循环容器中创建任务，这些任务使用 Excel 连接管理器来在每个与指定的文件位置和模式匹配的 Excel 工作簿上执行相同的操作。</span><span class="sxs-lookup"><span data-stu-id="a914c-132">Create tasks in the Foreach Loop container that use the Excel connection manager to perform the same operations on each Excel workbook that matches the specified file location and pattern.</span></span>  
  
### <a name="to-loop-through-excel-tables-by-using-the-foreach-adonet-schema-rowset-enumerator"></a><span data-ttu-id="a914c-133">使用 Foreach ADO.NET 架构行集枚举器循环遍历 Excel 表</span><span class="sxs-lookup"><span data-stu-id="a914c-133">To loop through Excel tables by using the Foreach ADO.NET Schema Rowset enumerator</span></span>  
  
1.  <span data-ttu-id="a914c-134">创建使用 Microsoft Jet OLE DB 访问接口连接 Excel 工作簿的 ADO.NET 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="a914c-134">Create an ADO.NET connection manager that uses the Microsoft Jet OLE DB Provider to connect to an Excel workbook.</span></span> <span data-ttu-id="a914c-135">在 **“连接管理器”** 对话框的“所有”页上，确保输入 Excel 8.0 作为“扩展属性”的值。</span><span class="sxs-lookup"><span data-stu-id="a914c-135">On the All page of the **Connection Manager** dialog box, make sure that you enter Excel 8.0 as the value of the Extended Properties property.</span></span> <span data-ttu-id="a914c-136">有关详细信息，请参阅 [在包中添加、删除或共享连接管理器](../add-delete-or-share-a-connection-manager-in-a-package.md)。</span><span class="sxs-lookup"><span data-stu-id="a914c-136">For more information, see [Add, Delete, or Share a Connection Manager in a Package](../add-delete-or-share-a-connection-manager-in-a-package.md).</span></span>  
  
2.  <span data-ttu-id="a914c-137">创建一个字符串变量，用于在每次循环迭代中接收当前表的名称。</span><span class="sxs-lookup"><span data-stu-id="a914c-137">Create a string variable that will receive the name of the current table on each iteration of the loop.</span></span>  
  
3.  <span data-ttu-id="a914c-138">将 Foreach 循环容器添加到 "**控制流**" 选项卡中。有关如何配置 Foreach 循环容器的信息，请参阅[配置 Foreach 循环容器](foreach-loop-container.md)。</span><span class="sxs-lookup"><span data-stu-id="a914c-138">Add a Foreach Loop container to the **Control Flow** tab. For information about how to configure the Foreach Loop container, see [Configure a Foreach Loop Container](foreach-loop-container.md).</span></span>  
  
4.  <span data-ttu-id="a914c-139">在 **“Foreach 循环编辑器”** 的 **“集合”** 页上，选择 Foreach ADO.NET 架构行级枚举器。</span><span class="sxs-lookup"><span data-stu-id="a914c-139">On the **Collection** page of the **Foreach Loop Editor**, select the Foreach ADO.NET Schema Rowset enumerator.</span></span>  
  
5.  <span data-ttu-id="a914c-140">对于 **“连接”** 的值，请选择前面创建的 ADO.NET 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="a914c-140">As the value of **Connection**, select the ADO.NET connection manager that you created previously.</span></span>  
  
6.  <span data-ttu-id="a914c-141">对于 **“架构”** 的值，选择“表”。</span><span class="sxs-lookup"><span data-stu-id="a914c-141">As the value of **Schema**, select Tables.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a914c-142">Excel 工作簿中的表列表同时包括工作表（具有 $ 后缀）和指定范围。</span><span class="sxs-lookup"><span data-stu-id="a914c-142">The list of tables in an Excel workbook includes both worksheets (which have the $ suffix) and named ranges.</span></span> <span data-ttu-id="a914c-143">如果要从列表中只筛选出工作表或指定范围，则必须在脚本任务中编写自定义代码来实现这一点。</span><span class="sxs-lookup"><span data-stu-id="a914c-143">If you have to filter the list for only worksheets or only named ranges, you may have to write custom code in a Script task for this purpose.</span></span> <span data-ttu-id="a914c-144">有关详细信息，请参阅 [使用脚本任务使用的 Excel 文件](script-task.md)。</span><span class="sxs-lookup"><span data-stu-id="a914c-144">For more information, see [Working with Excel Files with the Script Task](script-task.md).</span></span>  
  
7.  <span data-ttu-id="a914c-145">在 **“变量映射”** 页上，将索引 2 映射到以前创建的字符串变量，以存放当前表的名称。</span><span class="sxs-lookup"><span data-stu-id="a914c-145">On the **Variable Mappings** page, map Index 2 to the string variable created earlier to hold the name of the current table.</span></span>  
  
8.  <span data-ttu-id="a914c-146">关闭 **“Foreach 循环编辑器”**。</span><span class="sxs-lookup"><span data-stu-id="a914c-146">Close the **Foreach Loop Editor**.</span></span>  
  
9. <span data-ttu-id="a914c-147">在 Foreach 循环容器中创建任务，这些任务使用 Excel 连接管理器对指定工作簿中的每个 Excel 表执行相同的操作。</span><span class="sxs-lookup"><span data-stu-id="a914c-147">Create tasks in the Foreach Loop container that use the Excel connection manager to perform the same operations on each Excel table in the specified workbook.</span></span> <span data-ttu-id="a914c-148">如果你使用脚本任务来检查枚举表名或处理每个表，请记住将字符串变量添加到脚本任务的 ReadOnlyVariables 属性。</span><span class="sxs-lookup"><span data-stu-id="a914c-148">If you use a Script Task to examine the enumerated table name or to work with each table, remember to add the string variable to the ReadOnlyVariables property of the Script task.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a914c-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a914c-149">See Also</span></span>  
 <span data-ttu-id="a914c-150">[使用 SQL Server Integration Services (SSIS 从 Excel 导入数据或将数据导出到 excel) ](../load-data-to-from-excel-with-ssis.md) [配置 Foreach 循环容器](foreach-loop-container.md) </span><span class="sxs-lookup"><span data-stu-id="a914c-150">[Import data from Excel or export data to Excel with SQL Server Integration Services (SSIS)](../load-data-to-from-excel-with-ssis.md) [Configure a Foreach Loop Container](foreach-loop-container.md) </span></span>  
 <span data-ttu-id="a914c-151">[添加或更改属性表达式](../expressions/add-or-change-a-property-expression.md) </span><span class="sxs-lookup"><span data-stu-id="a914c-151">[Add or Change a Property Expression](../expressions/add-or-change-a-property-expression.md) </span></span>  
 <span data-ttu-id="a914c-152">[Excel 连接管理器](../connection-manager/excel-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="a914c-152">[Excel Connection Manager](../connection-manager/excel-connection-manager.md) </span></span>  
 <span data-ttu-id="a914c-153">[Excel 源](../data-flow/excel-source.md) </span><span class="sxs-lookup"><span data-stu-id="a914c-153">[Excel Source](../data-flow/excel-source.md) </span></span>  
 <span data-ttu-id="a914c-154">[Excel 目标](../data-flow/excel-destination.md) </span><span class="sxs-lookup"><span data-stu-id="a914c-154">[Excel Destination](../data-flow/excel-destination.md) </span></span>  
 [<span data-ttu-id="a914c-155">使用脚本任务处理 Excel 文件</span><span class="sxs-lookup"><span data-stu-id="a914c-155">Working with Excel Files with the Script Task</span></span>](script-task.md)  
  
  
