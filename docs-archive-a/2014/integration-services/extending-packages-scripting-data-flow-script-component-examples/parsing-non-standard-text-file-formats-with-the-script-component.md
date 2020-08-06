---
title: 使用脚本组件分析非标准文本文件格式 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- text file reading [Integration Services]
- Script component [Integration Services], non-standard text file formats
- transformations [Integration Services], components
- Script component [Integration Services], examples
ms.assetid: 1fda034d-09e4-4647-9a9f-e8d508c2cc8f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6a0ca1a0d10bdad40d39a366864a07d2b0a61d13
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688039"
---
# <a name="parsing-non-standard-text-file-formats-with-the-script-component"></a><span data-ttu-id="c4fdf-102">使用脚本组件分析非标准文本文件格式</span><span class="sxs-lookup"><span data-stu-id="c4fdf-102">Parsing Non-Standard Text File Formats with the Script Component</span></span>
  <span data-ttu-id="c4fdf-103">当源数据以非标准格式排列时，您可能会发现在一个脚本中合并所有分析逻辑要比将多个 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 转换链接在一起以实现相同结果更方便。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-103">When your source data is arranged in a non-standard format, you may find it more convenient to consolidate all your parsing logic in a single script than to chain together multiple [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] transformations to achieve the same result.</span></span>  
  
 [<span data-ttu-id="c4fdf-104">示例 1：分析以行分隔的记录</span><span class="sxs-lookup"><span data-stu-id="c4fdf-104">Example 1: Parsing Row-Delimited Records</span></span>](#example1)  
  
 [<span data-ttu-id="c4fdf-105">示例 2：拆分父记录和子记录</span><span class="sxs-lookup"><span data-stu-id="c4fdf-105">Example 2: Splitting Parent and Child Records</span></span>](#example2)  
  
> [!NOTE]  
>  <span data-ttu-id="c4fdf-106">如果希望创建可更方便地重用于多个数据流任务和多个包的组件，请考虑以此脚本组件示例中的代码为基础，创建自定义数据流组件。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-106">If you want to create a component that you can more easily reuse across multiple Data Flow tasks and multiple packages, consider using the code in this Script component sample as the starting point for a custom data flow component.</span></span> <span data-ttu-id="c4fdf-107">有关详细信息，请参阅 [开发自定义数据流组件](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-107">For more information, see [Developing a Custom Data Flow Component](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).</span></span>  
  
##  <a name="example-1-parsing-row-delimited-records"></a><a name="example1"></a> <span data-ttu-id="c4fdf-108">示例 1：分析以行分隔的记录</span><span class="sxs-lookup"><span data-stu-id="c4fdf-108">Example 1: Parsing Row-Delimited Records</span></span>  
 <span data-ttu-id="c4fdf-109">本示例演示如何采用其中包含的每列数据显示在单独一行中的文本文件，并使用脚本组件对该文件进行分析，分析结果写入目标表。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-109">This example shows how to take a text file in which each column of data appears on a separate line and parse it into a destination table by using the Script component.</span></span>  
  
 <span data-ttu-id="c4fdf-110">有关如何配置脚本组件以用作数据流中的转换的详细信息，请参阅[使用脚本组件创建同步转换](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)和[使用脚本组件创建异步转换](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-110">For more information about how to configure the Script component for use as a transformation in the data flow, see [Creating a Synchronous Transformation with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)and [Creating an Asynchronous Transformation with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md).</span></span>  
  
#### <a name="to-configure-this-script-component-example"></a><span data-ttu-id="c4fdf-111">配置此脚本组件示例</span><span class="sxs-lookup"><span data-stu-id="c4fdf-111">To configure this Script Component example</span></span>  
  
1.  <span data-ttu-id="c4fdf-112">创建并保存包含以下源数据且名为 **rowdelimiteddata.txt** 的文本文件：</span><span class="sxs-lookup"><span data-stu-id="c4fdf-112">Create and save a text file named **rowdelimiteddata.txt** that contains the following source data:</span></span>  
  
    ```  
    FirstName: Nancy  
    LastName: Davolio  
    Title: Sales Representative  
    City: Seattle  
    StateProvince: WA  
  
    FirstName: Andrew  
    LastName: Fuller  
    Title: Vice President, Sales  
    City: Tacoma  
    StateProvince: WA  
  
    FirstName: Steven  
    LastName: Buchanan  
    Title: Sales Manager  
    City: London  
    StateProvince:  
  
    ```  
  
2.  <span data-ttu-id="c4fdf-113">打开 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 并连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-113">Open [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
3.  <span data-ttu-id="c4fdf-114">选择目标数据库，并打开新查询窗口。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-114">Select a destination database, and open a new query window.</span></span> <span data-ttu-id="c4fdf-115">在该查询窗口中，执行以下脚本以创建目标表：</span><span class="sxs-lookup"><span data-stu-id="c4fdf-115">In the query window, execute the following script to create the destination table:</span></span>  
  
    ```  
    create table RowDelimitedData  
    (  
    FirstName varchar(32),  
    LastName varchar(32),  
    Title varchar(32),  
    City varchar(32),  
    StateProvince varchar(32)  
    )  
  
    ```  
  
4.  <span data-ttu-id="c4fdf-116">打开 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 并创建名为 ParseRowDelim.dtsx 的新 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-116">Open [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] and create a new [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package named ParseRowDelim.dtsx.</span></span>  
  
5.  <span data-ttu-id="c4fdf-117">向包中添加平面文件连接管理器，将其命名为 RowDelimitedData 并配置其连接到在前面步骤中创建的 rowdelimiteddata.txt 文件。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-117">Add a Flat File connection manager to the package, name it RowDelimitedData, and configure it to connect to the rowdelimiteddata.txt file that you created in a previous step.</span></span>  
  
6.  <span data-ttu-id="c4fdf-118">向包中添加 OLE DB 连接管理器，并配置其连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例和在其中创建了目标表的数据库。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-118">Add an OLE DB connection manager to the package and configure it to connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the database in which you created the destination table.</span></span>  
  
7.  <span data-ttu-id="c4fdf-119">向包中添加数据流任务并单击 SSIS 设计器的“数据流”  选项卡。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-119">Add a Data Flow task to the package and click the **Data Flow** tab of SSIS Designer.</span></span>  
  
8.  <span data-ttu-id="c4fdf-120">向数据流添加平面文件源，并将其配置为使用 RowDelimitedData 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-120">Add a Flat File Source to the data flow and configure it to use the RowDelimitedData connection manager.</span></span> <span data-ttu-id="c4fdf-121">在“平面文件源编辑器”的“列”页中，选择可用的单一外部列。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-121">On the **Columns** page of the **Flat File Source Editor**, select the single available external column.</span></span>  
  
9. <span data-ttu-id="c4fdf-122">向数据流添加脚本组件并将其配置为转换。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-122">Add a Script Component to the data flow and configure it as a transformation.</span></span> <span data-ttu-id="c4fdf-123">将平面文件源的输出连接到脚本组件。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-123">Connect the output of the Flat File Source to the Script Component.</span></span>  
  
10. <span data-ttu-id="c4fdf-124">双击脚本组件，显示“脚本转换编辑器”  。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-124">Double-click the Script component to display the **Script Transformation Editor**.</span></span>  
  
11. <span data-ttu-id="c4fdf-125">在“脚本转换编辑器”的“输入列”页中，选择可用的单一输入列。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-125">On the **Input Columns** page of the **Script Transformation Editor**, select the single available input column.</span></span>  
  
12. <span data-ttu-id="c4fdf-126">在 "**脚本转换编辑器**" 的 "**输入和输出**" 页中，选择 "输出 0" 并将其设置 `SynchronousInputID` 为 "无"。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-126">On the **Inputs and Outputs** page of the **Script Transformation Editor**, select Output 0 and set its `SynchronousInputID` to None.</span></span> <span data-ttu-id="c4fdf-127">创建 5 个输出列，所有 [DT_STR] 类型字符串的长度为 32：</span><span class="sxs-lookup"><span data-stu-id="c4fdf-127">Create 5 output columns, all of type string [DT_STR] with a length of 32:</span></span>  
  
    -   <span data-ttu-id="c4fdf-128">FirstName</span><span class="sxs-lookup"><span data-stu-id="c4fdf-128">FirstName</span></span>  
  
    -   <span data-ttu-id="c4fdf-129">LastName</span><span class="sxs-lookup"><span data-stu-id="c4fdf-129">LastName</span></span>  
  
    -   <span data-ttu-id="c4fdf-130">标题</span><span class="sxs-lookup"><span data-stu-id="c4fdf-130">Title</span></span>  
  
    -   <span data-ttu-id="c4fdf-131">城市</span><span class="sxs-lookup"><span data-stu-id="c4fdf-131">City</span></span>  
  
    -   <span data-ttu-id="c4fdf-132">StateProvince</span><span class="sxs-lookup"><span data-stu-id="c4fdf-132">StateProvince</span></span>  
  
13. <span data-ttu-id="c4fdf-133">在 "**脚本转换编辑器**" 的 "**脚本**" 页上，单击 "**编辑脚本**"，然后输入在示例的类中显示的代码 `ScriptMain` 。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-133">On the **Script** page of the **Script Transformation Editor**, click **Edit Script** and enter the code shown in the `ScriptMain` class of the example.</span></span> <span data-ttu-id="c4fdf-134">关闭脚本开发环境和“脚本转换编辑器”  。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-134">Close the script development environment and the **Script Transformation Editor**.</span></span>  
  
14. <span data-ttu-id="c4fdf-135">向数据流添加 SQL Server 目标。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-135">Add a SQL Server Destination to the data flow.</span></span> <span data-ttu-id="c4fdf-136">将该目标配置为使用 OLE DB 连接管理器和 RowDelimitedData 表。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-136">Configure it to use the OLE DB connection manager and the RowDelimitedData table.</span></span> <span data-ttu-id="c4fdf-137">将脚本组件的输出连接到此目标。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-137">Connect the output of the Script Component to this destination.</span></span>  
  
15. <span data-ttu-id="c4fdf-138">运行包。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-138">Run the package.</span></span> <span data-ttu-id="c4fdf-139">包运行完毕后，检查 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目标表中的记录。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-139">After the package has finished, examine the records in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination table.</span></span>  
  
```vb  
Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
  
    Dim columnName As String  
    Dim columnValue As String  
  
    ' Check for an empty row.  
    If Row.Column0.Trim.Length > 0 Then  
        columnName = Row.Column0.Substring(0, Row.Column0.IndexOf(":"))  
        ' Check for an empty value after the colon.  
        If Row.Column0.Substring(Row.Column0.IndexOf(":")).TrimEnd.Length > 1 Then  
            ' Extract the column value from after the colon and space.  
            columnValue = Row.Column0.Substring(Row.Column0.IndexOf(":") + 2)  
            Select Case columnName  
                Case "FirstName"  
                    ' The FirstName value indicates a new record.  
                    Me.Output0Buffer.AddRow()  
                    Me.Output0Buffer.FirstName = columnValue  
                Case "LastName"  
                    Me.Output0Buffer.LastName = columnValue  
                Case "Title"  
                    Me.Output0Buffer.Title = columnValue  
                Case "City"  
                    Me.Output0Buffer.City = columnValue  
                Case "StateProvince"  
                    Me.Output0Buffer.StateProvince = columnValue  
            End Select  
        End If  
    End If  
  
End Sub  
```  
  
```csharp  
public override void Input0_ProcessInputRow(Input0Buffer Row)  
    {  
  
        string columnName;  
        string columnValue;  
  
        // Check for an empty row.  
        if (Row.Column0.Trim().Length > 0)  
        {  
            columnName = Row.Column0.Substring(0, Row.Column0.IndexOf(":"));  
            // Check for an empty value after the colon.  
            if (Row.Column0.Substring(Row.Column0.IndexOf(":")).TrimEnd().Length > 1)  
            // Extract the column value from after the colon and space.  
            {  
                columnValue = Row.Column0.Substring(Row.Column0.IndexOf(":") + 2);  
                switch (columnName)  
                {  
                    case "FirstName":  
                        // The FirstName value indicates a new record.  
                        this.Output0Buffer.AddRow();  
                        this.Output0Buffer.FirstName = columnValue;  
                        break;  
                    case "LastName":  
                        this.Output0Buffer.LastName = columnValue;  
                        break;  
                    case "Title":  
                        this.Output0Buffer.Title = columnValue;  
                        break;  
                    case "City":  
                        this.Output0Buffer.City = columnValue;  
                        break;  
                    case "StateProvince":  
                        this.Output0Buffer.StateProvince = columnValue;  
                        break;  
                }  
            }  
        }  
  
    }  
```  
  
##  <a name="example-2-splitting-parent-and-child-records"></a><a name="example2"></a> <span data-ttu-id="c4fdf-140">示例 2：拆分父记录和子记录</span><span class="sxs-lookup"><span data-stu-id="c4fdf-140">Example 2: Splitting Parent and Child Records</span></span>  
 <span data-ttu-id="c4fdf-141">本示例演示如何采用格式为父记录行的前面有一个分隔符行，父记录行后跟任意个子记录行的文本文件，并使用脚本组件对其进行分析，分析结果写入已适当规范化的父目标表和子目标表中。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-141">This example shows how to take a text file, in which a separator row precedes a parent record row that is followed by an indefinite number of child record rows, and parse it into properly normalized parent and child destination tables by using the Script component.</span></span> <span data-ttu-id="c4fdf-142">这是一个简单的示例，它易于调整以适合每个父记录和子记录使用多行或多列的源文件，只要有办法识别每个记录的开始和结尾。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-142">This simple example could easily be adapted for source files that use more than one row or column for each parent and child record, as long as there is some way to identify the beginning and end of each record.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="c4fdf-143">此示例仅供演示之用。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-143">This sample is intended for demonstration purposes only.</span></span> <span data-ttu-id="c4fdf-144">如果多次运行该示例，则会在目标表中插入重复的键值。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-144">If you run the sample more than once, it inserts duplicate key values into the destination table.</span></span>  
  
 <span data-ttu-id="c4fdf-145">有关如何配置脚本组件以用作数据流中的转换的详细信息，请参阅[使用脚本组件创建同步转换](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)和[使用脚本组件创建异步转换](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-145">For more information about how to configure the Script component for use as a transformation in the data flow, see [Creating a Synchronous Transformation with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)and [Creating an Asynchronous Transformation with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md).</span></span>  
  
#### <a name="to-configure-this-script-component-example"></a><span data-ttu-id="c4fdf-146">配置此脚本组件示例</span><span class="sxs-lookup"><span data-stu-id="c4fdf-146">To configure this Script Component example</span></span>  
  
1.  <span data-ttu-id="c4fdf-147">创建并保存包含以下源数据且名为 **parentchilddata.txt** 的文本文件：</span><span class="sxs-lookup"><span data-stu-id="c4fdf-147">Create and save a text file named **parentchilddata.txt** that contains the following source data:</span></span>  
  
    ```  
    **********  
    PARENT 1 DATA  
    child 1 data  
    child 2 data  
    child 3 data  
    child 4 data  
    **********  
    PARENT 2 DATA  
    child 5 data  
    child 6 data  
    child 7 data  
    child 8 data  
    **********  
  
    ```  
  
2.  <span data-ttu-id="c4fdf-148">打开 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 并连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-148">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
3.  <span data-ttu-id="c4fdf-149">选择目标数据库，并打开新查询窗口。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-149">Select a destination database, and open a new query window.</span></span> <span data-ttu-id="c4fdf-150">在该查询窗口中，执行以下脚本以创建目标表：</span><span class="sxs-lookup"><span data-stu-id="c4fdf-150">In the query window, execute the following script to create the destination tables:</span></span>  
  
    ```  
    CREATE TABLE [dbo].[Parents]([ParentID] [int] NOT NULL,  
    [ParentRecord] [varchar](32) NOT NULL,  
     CONSTRAINT [PK_Parents] PRIMARY KEY CLUSTERED   
    ([ParentID] ASC))  
    GO  
    CREATE TABLE [dbo].[Children]([ChildID] [int] NOT NULL,  
    [ParentID] [int] NOT NULL,  
    [ChildRecord] [varchar](32) NOT NULL,  
     CONSTRAINT [PK_Children] PRIMARY KEY CLUSTERED   
    ([ChildID] ASC))  
    GO  
    ALTER TABLE [dbo].[Children] ADD CONSTRAINT [FK_Children_Parents] FOREIGN KEY([ParentID])  
    REFERENCES [dbo].[Parents] ([ParentID])  
  
    ```  
  
4.  <span data-ttu-id="c4fdf-151">打开 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 并创建名为 SplitParentChild.dtsx 的新 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-151">Open [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and create a new [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package named SplitParentChild.dtsx.</span></span>  
  
5.  <span data-ttu-id="c4fdf-152">向包中添加平面文件连接管理器，将其命名为 ParentChildData 并配置其连接到在前面步骤中创建的 parentchilddata.txt 文件。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-152">Add a Flat File connection manager to the package, name it ParentChildData, and configure it to connect to the parentchilddata.txt file that you created in a previous step.</span></span>  
  
6.  <span data-ttu-id="c4fdf-153">向包中添加 OLE DB 连接管理器，并配置其连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例和在其中创建目标表的数据库。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-153">Add an OLE DB connection manager to the package and configure it to connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the database in which you created the destination tables.</span></span>  
  
7.  <span data-ttu-id="c4fdf-154">向包中添加数据流任务并单击 SSIS 设计器的“数据流”  选项卡。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-154">Add a Data Flow task to the package and click the **Data Flow** tab of SSIS Designer.</span></span>  
  
8.  <span data-ttu-id="c4fdf-155">向数据流添加平面文件源，并将其配置为使用 ParentChildData 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-155">Add a Flat File Source to the data flow and configure it to use the ParentChildData connection manager.</span></span> <span data-ttu-id="c4fdf-156">在“平面文件源编辑器”的“列”页中，选择可用的单一外部列。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-156">On the **Columns** page of the **Flat File Source Editor**, select the single available external column.</span></span>  
  
9. <span data-ttu-id="c4fdf-157">向数据流添加脚本组件并将其配置为转换。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-157">Add a Script Component to the data flow and configure it as a transformation.</span></span> <span data-ttu-id="c4fdf-158">将平面文件源的输出连接到脚本组件。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-158">Connect the output of the Flat File Source to the Script Component.</span></span>  
  
10. <span data-ttu-id="c4fdf-159">双击脚本组件，显示“脚本转换编辑器”  。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-159">Double-click the Script component to display the **Script Transformation Editor**.</span></span>  
  
11. <span data-ttu-id="c4fdf-160">在“脚本转换编辑器”的“输入列”页中，选择可用的单一输入列。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-160">On the **Input Columns** page of the **Script Transformation Editor**, select the single available input column.</span></span>  
  
12. <span data-ttu-id="c4fdf-161">在 "**脚本转换编辑器**" 的 "**输入和输出**" 页中，选择 "输出 0"，将其重命名为 ParentRecords，并将其设置 `SynchronousInputID` 为 None。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-161">On the **Inputs and Outputs** page of the **Script Transformation Editor**, select Output 0, rename it to ParentRecords, and set its `SynchronousInputID` to None.</span></span> <span data-ttu-id="c4fdf-162">创建 2 个输出列：</span><span class="sxs-lookup"><span data-stu-id="c4fdf-162">Create 2 output columns:</span></span>  
  
    -   <span data-ttu-id="c4fdf-163">ParentID（主键），类型为四字节有符号整数 [DT_I4]</span><span class="sxs-lookup"><span data-stu-id="c4fdf-163">ParentID (the primary key), of type four-byte signed integer [DT_I4]</span></span>  
  
    -   <span data-ttu-id="c4fdf-164">ParentRecord，类型为长度为 32 的字符串 [DT_STR]。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-164">ParentRecord, of type string [DT_STR] with a length of 32.</span></span>  
  
13. <span data-ttu-id="c4fdf-165">创建第二个输出，并将其命名为 ChildRecords。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-165">Create a second output and name it ChildRecords.</span></span> <span data-ttu-id="c4fdf-166">新输出的 `SynchronousInputID` 已设置为 None。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-166">The `SynchronousInputID` of the new output is already set to None.</span></span> <span data-ttu-id="c4fdf-167">创建 3 个输出列：</span><span class="sxs-lookup"><span data-stu-id="c4fdf-167">Create 3 output columns:</span></span>  
  
    -   <span data-ttu-id="c4fdf-168">ChildID（主键），类型为四字节有符号整数 [DT_I4]</span><span class="sxs-lookup"><span data-stu-id="c4fdf-168">ChildID (the primary key), of type four-byte signed integer [DT_I4]</span></span>  
  
    -   <span data-ttu-id="c4fdf-169">ParentID（外键），类型也为四字节有符号整数 [DT_I4]</span><span class="sxs-lookup"><span data-stu-id="c4fdf-169">ParentID (the foreign key), also of type four-byte signed integer [DT_I4]</span></span>  
  
    -   <span data-ttu-id="c4fdf-170">ChildRecord，类型为长度为 50 的字符串 [DT_STR]</span><span class="sxs-lookup"><span data-stu-id="c4fdf-170">ChildRecord, of type string [DT_STR] with a length of 50</span></span>  
  
14. <span data-ttu-id="c4fdf-171">在“脚本转换编辑器”的“脚本”页中，单击“编辑脚本”。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-171">On the **Script** page of the **Script Transformation Editor**, click **Edit Script**.</span></span> <span data-ttu-id="c4fdf-172">在 `ScriptMain` 类中，输入在示例中显示的代码。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-172">In the `ScriptMain` class, enter the code shown in the example.</span></span> <span data-ttu-id="c4fdf-173">关闭脚本开发环境和“脚本转换编辑器”  。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-173">Close the script development environment and the **Script Transformation Editor**.</span></span>  
  
15. <span data-ttu-id="c4fdf-174">向数据流添加 SQL Server 目标。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-174">Add a SQL Server Destination to the data flow.</span></span> <span data-ttu-id="c4fdf-175">将脚本组件的 ParentRecords 输出连接到此目标。将此目标配置为使用 OLE DB 连接管理器和 Parents 表。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-175">Connect the ParentRecords output of the Script Component to this destination.Configure it to use the OLE DB connection manager and the Parents table.</span></span>  
  
16. <span data-ttu-id="c4fdf-176">向数据流添加另一个 SQL Server 目标。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-176">Add another SQL Server Destination to the data flow.</span></span> <span data-ttu-id="c4fdf-177">将脚本组件的 ChildRecords 输出连接到此目标。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-177">Connect the ChildRecords output of the Script Component to this destination.</span></span> <span data-ttu-id="c4fdf-178">将此目标配置为使用 OLE DB 连接管理器和 Children 表。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-178">Configure it to use the OLE DB connection manager and the Children table.</span></span>  
  
17. <span data-ttu-id="c4fdf-179">运行包。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-179">Run the package.</span></span> <span data-ttu-id="c4fdf-180">包运行完毕后，检查两个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目标表中的父记录和子记录。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-180">After the package has finished, examine the parent and child records in the two [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination tables.</span></span>  
  
```vb  
Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
  
    Static nextRowIsParent As Boolean = False  
    Static parentCounter As Integer = 0  
    Static childCounter As Integer = 0  
  
    ' If current row starts with separator characters,  
    '  then following row contains new parent record.  
    If Row.Column0.StartsWith("***") Then  
        nextRowIsParent = True  
    Else  
        If nextRowIsParent Then  
            ' Current row contains parent record.  
            parentCounter += 1  
            Me.ParentRecordsBuffer.AddRow()  
            Me.ParentRecordsBuffer.ParentID = parentCounter  
            Me.ParentRecordsBuffer.ParentRecord = Row.Column0  
            nextRowIsParent = False  
        Else  
            ' Current row contains child record.  
            childCounter += 1  
            Me.ChildRecordsBuffer.AddRow()  
            Me.ChildRecordsBuffer.ChildID = childCounter  
            Me.ChildRecordsBuffer.ParentID = parentCounter  
            Me.ChildRecordsBuffer.ChildRecord = Row.Column0  
        End If  
    End If  
  
End Sub  
```  
  
```csharp  
public override void Input0_ProcessInputRow(Input0Buffer Row)  
    {  
  
    int static_Input0_ProcessInputRow_childCounter = 0;  
    int static_Input0_ProcessInputRow_parentCounter = 0;  
    bool static_Input0_ProcessInputRow_nextRowIsParent = false;  
  
        // If current row starts with separator characters,   
        // then following row contains new parent record.   
        if (Row.Column0.StartsWith("***"))  
        {  
            static_Input0_ProcessInputRow_nextRowIsParent = true;  
        }  
        else  
        {  
            if (static_Input0_ProcessInputRow_nextRowIsParent)  
            {  
                // Current row contains parent record.   
                static_Input0_ProcessInputRow_parentCounter += 1;  
                this.ParentRecordsBuffer.AddRow();  
                this.ParentRecordsBuffer.ParentID = static_Input0_ProcessInputRow_parentCounter;  
                this.ParentRecordsBuffer.ParentRecord = Row.Column0;  
                static_Input0_ProcessInputRow_nextRowIsParent = false;  
            }  
            else  
            {  
                // Current row contains child record.   
                static_Input0_ProcessInputRow_childCounter += 1;  
                this.ChildRecordsBuffer.AddRow();  
                this.ChildRecordsBuffer.ChildID = static_Input0_ProcessInputRow_childCounter;  
                this.ChildRecordsBuffer.ParentID = static_Input0_ProcessInputRow_parentCounter;  
                this.ChildRecordsBuffer.ChildRecord = Row.Column0;  
            }  
        }  
  
    }  
```  
  
<span data-ttu-id="c4fdf-181">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="c4fdf-181">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="c4fdf-182">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="c4fdf-182">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="c4fdf-183">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="c4fdf-183">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="c4fdf-184">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-184">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4fdf-185">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c4fdf-185">See Also</span></span>  
 [<span data-ttu-id="c4fdf-186">使用脚本组件创建同步转换</span><span class="sxs-lookup"><span data-stu-id="c4fdf-186">Creating a Synchronous Transformation with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)  
 [<span data-ttu-id="c4fdf-187">使用脚本组件创建异步转换</span><span class="sxs-lookup"><span data-stu-id="c4fdf-187">Creating an Asynchronous Transformation with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)  
  
  
