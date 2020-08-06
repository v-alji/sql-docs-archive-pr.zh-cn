---
title: 加载本地包的输出 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data flow [Integration Services], loading results
- loading data flow results
ms.assetid: aba8ecb7-0dcf-40d0-a2a8-64da0da94b93
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6799e593ab9d5ae1a9358bf54f4927838991ebd0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692993"
---
# <a name="loading-the-output-of-a-local-package"></a><span data-ttu-id="04838-102">加载本地包的输出</span><span class="sxs-lookup"><span data-stu-id="04838-102">Loading the Output of a Local Package</span></span>
  <span data-ttu-id="04838-103">使用 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 将输出保存到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目标，或使用 System.IO  命名空间中的类将输出保存到平面文件目标时，客户端应用程序即可读取 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包的输出。</span><span class="sxs-lookup"><span data-stu-id="04838-103">Client applications can read the output of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages when the output is saved to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destinations by using [!INCLUDE[vstecado](../../includes/vstecado-md.md)], or when the output is saved to a flat file destination by using the classes in the **System.IO** namespace.</span></span> <span data-ttu-id="04838-104">但是，客户端应用程序也可以直接从内存读取包的输出，而无需中间步骤来持久化这些数据。</span><span class="sxs-lookup"><span data-stu-id="04838-104">However, a client application can also read the output of a package directly from memory, without the need for an intermediate step to persist the data.</span></span> <span data-ttu-id="04838-105">此解决方案的关键是 `Microsoft.SqlServer.Dts.DtsClient` 命名空间，其中包含 `IDbConnection` `IDbCommand` IDbDataParameter 命名空间中的、和**IDbDataParameter**接口**System.Data**的专用实现。</span><span class="sxs-lookup"><span data-stu-id="04838-105">The key to this solution is the `Microsoft.SqlServer.Dts.DtsClient` namespace, which contains specialized implementations of the `IDbConnection`, `IDbCommand`, and **IDbDataParameter** interfaces from the **System.Data** namespace.</span></span> <span data-ttu-id="04838-106">默认情况下，程序集 Microsoft.SqlServer.Dts.DtsClient.dll 安装在 %ProgramFiles%\Microsoft SQL Server\100\DTS\Binn  中。</span><span class="sxs-lookup"><span data-stu-id="04838-106">The assembly Microsoft.SqlServer.Dts.DtsClient.dll is installed by default in **%ProgramFiles%\Microsoft SQL Server\100\DTS\Binn**.</span></span>

> [!NOTE]
>  <span data-ttu-id="04838-107">本主题介绍的过程要求数据流任务以及所有父对象的 DelayValidation 属性均设置为其默认值 False\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="04838-107">The procedure described in this topic requires that the DelayValidation property of the Data Flow task and of any parent objects be set to its default value of **False**.</span></span>

## <a name="description"></a><span data-ttu-id="04838-108">说明</span><span class="sxs-lookup"><span data-stu-id="04838-108">Description</span></span>
 <span data-ttu-id="04838-109">本过程说明如何使用托管代码开发客户端应用程序，该应用程序使用 DataReader 目标直接从内存加载包的输出。</span><span class="sxs-lookup"><span data-stu-id="04838-109">This procedure demonstrates how to develop a client application in managed code that loads the output of a package with a DataReader destination directly from memory.</span></span> <span data-ttu-id="04838-110">此处总结的步骤在随后的代码示例中演示。</span><span class="sxs-lookup"><span data-stu-id="04838-110">The steps summarized here are demonstrated in the code sample that follows.</span></span>

#### <a name="to-load-data-package-output-into-a-client-application"></a><span data-ttu-id="04838-111">将数据包输出加载到客户端应用程序中</span><span class="sxs-lookup"><span data-stu-id="04838-111">To load data package output into a client application</span></span>

1.  <span data-ttu-id="04838-112">在包中，配置 DataReader 目标，以接收要读入到客户端应用程序中的输出。</span><span class="sxs-lookup"><span data-stu-id="04838-112">In the package, configure a DataReader destination to receive the output that you want to read into the client application.</span></span> <span data-ttu-id="04838-113">使用说明性的名称为 DataReader 目标命名，因为您稍后将在客户端应用程序中使用此名称。</span><span class="sxs-lookup"><span data-stu-id="04838-113">Give the DataReader destination a descriptive name, since you will use this name later in your client application.</span></span> <span data-ttu-id="04838-114">请记录 DataReader 目标的名称。</span><span class="sxs-lookup"><span data-stu-id="04838-114">Make a note of the name of the DataReader destination.</span></span>

2.  <span data-ttu-id="04838-115">在开发项目中， `Microsoft.SqlServer.Dts.DtsClient` 通过查找程序集**Microsoft.SqlServer.Dts.DtsClient.dll**来设置对命名空间的引用。</span><span class="sxs-lookup"><span data-stu-id="04838-115">In the development project, set a reference to the `Microsoft.SqlServer.Dts.DtsClient` namespace by locating the assembly **Microsoft.SqlServer.Dts.DtsClient.dll**.</span></span> <span data-ttu-id="04838-116">默认情况下，此程序集安装在 C:\Program Files\Microsoft SQL Server\100\DTS\Binn\*\*\*\* 中。</span><span class="sxs-lookup"><span data-stu-id="04838-116">By default, this assembly is installed in **C:\Program Files\Microsoft SQL Server\100\DTS\Binn**.</span></span> <span data-ttu-id="04838-117">使用 c # 或语句将命名空间导入到代码中 `Using` [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] `Imports` 。</span><span class="sxs-lookup"><span data-stu-id="04838-117">Import the namespace into your code by using the C# `Using` or the [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] `Imports` statement.</span></span>

3.  <span data-ttu-id="04838-118">在代码中，创建一个类型为的对象， `DtsClient.DtsConnection` 该对象包含一个连接字符串，其中包含**dtexec.exe**运行包所需的命令行参数。</span><span class="sxs-lookup"><span data-stu-id="04838-118">In your code, create an object of type `DtsClient.DtsConnection` with a connection string that contains the command-line parameters required by **dtexec.exe** to run the package.</span></span> <span data-ttu-id="04838-119">有关详细信息，请参阅 [dtexec Utility](../packages/dtexec-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="04838-119">For more information, see [dtexec Utility](../packages/dtexec-utility.md).</span></span> <span data-ttu-id="04838-120">然后，使用此连接字符串打开连接。</span><span class="sxs-lookup"><span data-stu-id="04838-120">Then open the connection with this connection string.</span></span> <span data-ttu-id="04838-121">还可以使用 dtexecui\*\*\*\* 实用工具直观地创建所需的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="04838-121">You can also use the **dtexecui** utility to create the required connection string visually.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="04838-122">该示例代码演示如何使用 `/FILE <path and filename>` 语法从文件系统加载包。</span><span class="sxs-lookup"><span data-stu-id="04838-122">The sample code demonstrates loading the package from the file system by using the `/FILE <path and filename>` syntax.</span></span> <span data-ttu-id="04838-123">但您也可以使用 `/SQL <package name>` 语法从 MSDB 数据库加载包，或者使用 `/DTS \<folder name>\<package name>` 语法从 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包存储区加载包。</span><span class="sxs-lookup"><span data-stu-id="04838-123">However you can also load the package from the MSDB database by using the `/SQL <package name>` syntax, or from the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package store by using the `/DTS \<folder name>\<package name>` syntax.</span></span>

4.  <span data-ttu-id="04838-124">创建类型为 `DtsClient.DtsCommand` 的对象，该对象使用先前创建的 `DtsConnection`，并将该对象的 `CommandText` 属性设置为包中 DataReader 目标的名称。</span><span class="sxs-lookup"><span data-stu-id="04838-124">Create an object of type `DtsClient.DtsCommand` that uses the previously created `DtsConnection` and set its `CommandText` property to the name of the DataReader destination in the package.</span></span> <span data-ttu-id="04838-125">然后，调用命令对象的 `ExecuteReader` 方法以将包结果加载到新的 DataReader 中。</span><span class="sxs-lookup"><span data-stu-id="04838-125">Then call the `ExecuteReader` method of the command object to load the package results into a new DataReader.</span></span>

5.  <span data-ttu-id="04838-126">还可以通过对 `DtsDataParameter` 对象使用 `DtsCommand` 对象的集合来间接参数化包的输出，以将值传递给在包中定义的变量。</span><span class="sxs-lookup"><span data-stu-id="04838-126">Optionally, you can indirectly parameterize the output of the package by using the collection of `DtsDataParameter` objects on the `DtsCommand` object to pass values to variables defined in the package.</span></span> <span data-ttu-id="04838-127">在包中，您可以使用这些变量作为查询参数或在表达式中使用这些变量以影响返回给 DataReader 目标的结果。</span><span class="sxs-lookup"><span data-stu-id="04838-127">Within the package, you can use these variables as query parameters or in expressions to affect the results returned to the DataReader destination.</span></span> <span data-ttu-id="04838-128">必须先在**DtsClient**命名空间的包中定义这些变量，然后才能将其与 `DtsDataParameter` 客户端应用程序中的对象一起使用。</span><span class="sxs-lookup"><span data-stu-id="04838-128">You must define these variables in the package in the **DtsClient** namespace before you can use them with the `DtsDataParameter` object from a client application.</span></span> <span data-ttu-id="04838-129"> (您可能需要单击 "**变量**" 窗口中的 "**选择变量列**" 工具栏按钮以显示 "**命名空间**" 列。在客户端代码中 ) ，将添加 `DtsDataParameter` 到 `Parameters` 的集合时 `DtsCommand` ，请从变量名称中省略 DtsClient 命名空间引用。</span><span class="sxs-lookup"><span data-stu-id="04838-129">(You may need to click the **Choose Variable Columns** toolbar button in the **Variables** window to display the **Namespace** column.) In your client code, when you add a `DtsDataParameter` to the `Parameters` collection of the `DtsCommand`, omit the DtsClient namespace reference from the variable name.</span></span> <span data-ttu-id="04838-130">例如：</span><span class="sxs-lookup"><span data-stu-id="04838-130">For example:</span></span>

    ```
    command.Parameters.Add(new DtsDataParameter("MyVariable", 1));
    ```

6.  <span data-ttu-id="04838-131">根据需要重复调用 DataReader 的 `Read` 方法以遍历输出数据的各行。</span><span class="sxs-lookup"><span data-stu-id="04838-131">Call the `Read` method of the DataReader repeatedly as needed to loop through the rows of output data.</span></span> <span data-ttu-id="04838-132">使用这些数据，或将这些数据保存在客户端应用程序，以供将来使用。</span><span class="sxs-lookup"><span data-stu-id="04838-132">Use the data, or save the data for later use, in the client application.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="04838-133">读取最后一行数据后，此 DataReader 实现的 `Read` 方法将再返回一次 `true`。</span><span class="sxs-lookup"><span data-stu-id="04838-133">The `Read` method of this implementation of the DataReader returns `true` one more time after the last row of data has been read.</span></span> <span data-ttu-id="04838-134">因此在 `Read` 返回 `true` 时很难使用遍历 DataReader 的常规代码。</span><span class="sxs-lookup"><span data-stu-id="04838-134">This makes it difficult to use the usual code that loops through the DataReader while `Read` returns `true`.</span></span> <span data-ttu-id="04838-135">如果您的代码在读取预期行数后尝试关闭 DataReader 或连接，而不对 `Read` 方法进行附加的最终调用时，该代码将引发未处理的异常。</span><span class="sxs-lookup"><span data-stu-id="04838-135">If your code attempts to close the DataReader or the connection after reading the expected number of rows, without an additional, final call to the `Read` method, the code will raise an unhandled exception.</span></span> <span data-ttu-id="04838-136">但是，如果您的代码尝试在此循环的最后一轮操作中读取数据，则在 `Read` 仍返回 `true` 而最后一行已传递时，该代码将引发未处理的 `ApplicationException`，并包含消息“SSIS IDataReader 已到达结果集末尾”。</span><span class="sxs-lookup"><span data-stu-id="04838-136">However, if your code attempts to read data on this final iteration through a loop, when `Read` still returns `true` but the last row has been passed, the code will raise an unhandled `ApplicationException` with the message, "The SSIS IDataReader is past the end of the resultset."</span></span> <span data-ttu-id="04838-137">此行为与其他 DataReader 实现的行为不同。</span><span class="sxs-lookup"><span data-stu-id="04838-137">This behavior is different from that of other DataReader implementations.</span></span> <span data-ttu-id="04838-138">因此，使用循环读取 DataReader 中的各行，而 `Read` 返回 `true` 时，您需要针对上次成功调用 `ApplicationException` 方法编写代码以捕获、测试和放弃此预期的 `Read`。</span><span class="sxs-lookup"><span data-stu-id="04838-138">Therefore, when using a loop to read through the rows in the DataReader while `Read` returns `true`, you need to write code to catch, test, and discard this anticipated `ApplicationException` on the last successful call to the `Read` method.</span></span> <span data-ttu-id="04838-139">或者，如果您事先知道应读取的行数，则可以处理这些行，然后在关闭 DataReader 和连接之前再调用一次 `Read` 方法。</span><span class="sxs-lookup"><span data-stu-id="04838-139">Or, if you know in advance the number of rows expected, you can process the rows, and then call the `Read` method one more time before closing the DataReader and the connection.</span></span>

7.  <span data-ttu-id="04838-140">调用 `Dispose` 对象的 `DtsCommand` 方法。</span><span class="sxs-lookup"><span data-stu-id="04838-140">Call the `Dispose` method of the `DtsCommand` object.</span></span> <span data-ttu-id="04838-141">如果已使用任何 `DtsDataParameter` 对象，这样做尤其重要。</span><span class="sxs-lookup"><span data-stu-id="04838-141">This is particularly important if you have used any `DtsDataParameter` objects.</span></span>

8.  <span data-ttu-id="04838-142">关闭 DataReader 和连接对象。</span><span class="sxs-lookup"><span data-stu-id="04838-142">Close the DataReader and the connection objects.</span></span>

## <a name="example"></a><span data-ttu-id="04838-143">示例</span><span class="sxs-lookup"><span data-stu-id="04838-143">Example</span></span>
 <span data-ttu-id="04838-144">下面的示例将运行一个包，用于计算单个聚合值并将该值保存到 DataReader 目标，然后从 DataReader 读取此值，并在 Windows 窗体的文本框中显示该值。</span><span class="sxs-lookup"><span data-stu-id="04838-144">The following example runs a package that calculates a single aggregate value and saves the value to a DataReader destination, and then reads this value from the DataReader and displays the value in a text box on a Windows Form.</span></span>

 <span data-ttu-id="04838-145">在将包的输出加载到客户端应用程序时不一定要使用参数。</span><span class="sxs-lookup"><span data-stu-id="04838-145">The use of parameters is not required when loading the output of a package into a client application.</span></span> <span data-ttu-id="04838-146">如果不想使用参数，可以在**DtsClient**命名空间中省略变量的使用，并忽略使用对象的代码 `DtsDataParameter` 。</span><span class="sxs-lookup"><span data-stu-id="04838-146">If you do not want to use a parameter, you can omit the use of the variable in the **DtsClient** namespace, and omit the code that uses the `DtsDataParameter` object.</span></span>

#### <a name="to-create-the-test-package"></a><span data-ttu-id="04838-147">创建测试包</span><span class="sxs-lookup"><span data-stu-id="04838-147">To create the test package</span></span>

1.  <span data-ttu-id="04838-148">创建新的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="04838-148">Create a new [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package.</span></span> <span data-ttu-id="04838-149">示例代码使用“DtsClientWParamPkg.dtsx”作为包的名称。</span><span class="sxs-lookup"><span data-stu-id="04838-149">The sample code uses "DtsClientWParamPkg.dtsx" as the name of the package.</span></span>

2.  <span data-ttu-id="04838-150">在 DtsClient 命名空间中添加类型为 String 的变量。</span><span class="sxs-lookup"><span data-stu-id="04838-150">Add a variable of type String in the DtsClient namespace.</span></span> <span data-ttu-id="04838-151">示例代码使用 Country 作为该变量的名称。</span><span class="sxs-lookup"><span data-stu-id="04838-151">The sample code use Country as the name of the variable.</span></span> <span data-ttu-id="04838-152">（可能需要单击“变量”\*\*\*\* 窗口中的“选择变量列”\*\*\*\* 工具栏按钮才会显示“命名空间”\*\*\*\* 列。）</span><span class="sxs-lookup"><span data-stu-id="04838-152">(You may need to click the **Choose Variable Columns** toolbar button in the **Variables** window to display the **Namespace** column.)</span></span>

3.  <span data-ttu-id="04838-153">添加用于连接 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 示例数据库的 OLE DB 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="04838-153">Add an OLE DB connection manager that connects to the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] sample database.</span></span>

4.  <span data-ttu-id="04838-154">向包添加数据流任务，并切换到数据流设计图面。</span><span class="sxs-lookup"><span data-stu-id="04838-154">Add a data flow task to the package and switch to the Data Flow design surface.</span></span>

5.  <span data-ttu-id="04838-155">向数据流添加 OLE DB 源，并将其配置为使用之前创建的 OLE DB 连接管理器以及下面的 SQL 命令：</span><span class="sxs-lookup"><span data-stu-id="04838-155">Add an OLE DB source to the data flow and configure it to use the OLE DB connection manager created previously, and the following SQL command:</span></span>

    ```
    SELECT * FROM Sales.vIndividualCustomer WHERE CountryRegionName = ?
    ```

6.  <span data-ttu-id="04838-156">单击 `Parameters` ""，然后在 "**设置查询参数**" 对话框中，将 parameter0 映射中的单个输入参数映射到 DtsClient：： Country 变量。</span><span class="sxs-lookup"><span data-stu-id="04838-156">Click `Parameters` and, in the **Set Query Parameters** dialog box, map the single input parameter in the query, Parameter0, to the DtsClient::Country variable.</span></span>

7.  <span data-ttu-id="04838-157">向数据流添加聚合转换，并将 OLE DB 源的输出连接到该转换。</span><span class="sxs-lookup"><span data-stu-id="04838-157">Add an Aggregate transformation to the data flow, and connect the output of the OLE DB source to the transformation.</span></span> <span data-ttu-id="04838-158">打开 "聚合转换编辑器" 并将其配置为对所有输入列执行 "全部计数" 操作 ( \* ) 并使用别名 CustomerCount 输出聚合值。</span><span class="sxs-lookup"><span data-stu-id="04838-158">Open the Aggregate Transformation Editor and configure it to perform a "Count all" operation on all input columns (\*) and to output the aggregated value with the alias CustomerCount.</span></span>

8.  <span data-ttu-id="04838-159">向数据流添加 DataReader 目标，并将聚合转换的输出连接到 DataReader 目标。</span><span class="sxs-lookup"><span data-stu-id="04838-159">Add a DataReader destination to the data flow and connect the output of the Aggregate transformation to the DataReader destination.</span></span> <span data-ttu-id="04838-160">示例代码使用“DataReaderDest”作为 DataReader 的名称。</span><span class="sxs-lookup"><span data-stu-id="04838-160">The sample code uses "DataReaderDest" as the name of the DataReader.</span></span> <span data-ttu-id="04838-161">为目标选择单个可用输入列 CustomerCount。</span><span class="sxs-lookup"><span data-stu-id="04838-161">Select the single available input column, CustomerCount, for the destination.</span></span>

9. <span data-ttu-id="04838-162">保存包。</span><span class="sxs-lookup"><span data-stu-id="04838-162">Save the package.</span></span> <span data-ttu-id="04838-163">接下来要创建的测试应用程序将运行该包并直接从内存检索其输出。</span><span class="sxs-lookup"><span data-stu-id="04838-163">The test application created next will run the package and retrieve its output directly from memory.</span></span>

#### <a name="to-create-the-test-application"></a><span data-ttu-id="04838-164">创建测试应用程序</span><span class="sxs-lookup"><span data-stu-id="04838-164">To create the test application</span></span>

1.  <span data-ttu-id="04838-165">创建新的 Windows 窗体应用程序。</span><span class="sxs-lookup"><span data-stu-id="04838-165">Create a new Windows Forms application.</span></span>

2.  <span data-ttu-id="04838-166">`Microsoft.SqlServer.Dts.DtsClient`通过浏览到 **%ProgramFiles%\Microsoft SQL Server\100\DTS\Binn**中具有相同名称的程序集来添加对命名空间的引用。</span><span class="sxs-lookup"><span data-stu-id="04838-166">Add a reference to the `Microsoft.SqlServer.Dts.DtsClient` namespace by browsing to the assembly of the same name in **%ProgramFiles%\Microsoft SQL Server\100\DTS\Binn**.</span></span>

3.  <span data-ttu-id="04838-167">复制以下示例代码并将其粘贴到窗体的代码模块中。</span><span class="sxs-lookup"><span data-stu-id="04838-167">Copy and paste the following sample code into the code module for the form.</span></span>

4.  <span data-ttu-id="04838-168">根据需要修改变量的值， `dtexecArgs` 使其包含**dtexec.exe**运行包所需的命令行参数。</span><span class="sxs-lookup"><span data-stu-id="04838-168">Modify the value of the `dtexecArgs` variable as required so that it contains the command-line parameters required by **dtexec.exe** to run the package.</span></span> <span data-ttu-id="04838-169">示例代码从文件系统加载包。</span><span class="sxs-lookup"><span data-stu-id="04838-169">The sample code loads the package from the file system.</span></span>

5.  <span data-ttu-id="04838-170">根据需要修改变量的值， `dataReaderName` 使其包含包中的 DataReader 目标的名称。</span><span class="sxs-lookup"><span data-stu-id="04838-170">Modify the value of the `dataReaderName` variable as required so that it contains the name of the DataReader destination in the package.</span></span>

6.  <span data-ttu-id="04838-171">在窗体中放入一个按钮和一个文本框。</span><span class="sxs-lookup"><span data-stu-id="04838-171">Put a button and a text box on the form.</span></span> <span data-ttu-id="04838-172">示例代码使用 `btnRun` 作为按钮的名称，并使用 `txtResults` 作为文本框的名称。</span><span class="sxs-lookup"><span data-stu-id="04838-172">The sample code uses `btnRun` as the name of the button, and `txtResults` as the name of the text box.</span></span>

7.  <span data-ttu-id="04838-173">运行该应用程序并单击按钮。</span><span class="sxs-lookup"><span data-stu-id="04838-173">Run the application and click the button.</span></span> <span data-ttu-id="04838-174">在短暂运行包后，您应能够看到在窗体的文本框中显示由包计算的聚合值（Canada 的客户计数）。</span><span class="sxs-lookup"><span data-stu-id="04838-174">After a brief pause while the package runs, you should see the aggregate value calculated by the package (the count of customers in Canada) displayed in the text box on the form.</span></span>

### <a name="sample-code"></a><span data-ttu-id="04838-175">代码示例</span><span class="sxs-lookup"><span data-stu-id="04838-175">Sample Code</span></span>

```vb
Imports System.Data
Imports Microsoft.SqlServer.Dts.DtsClient

Public Class Form1

  Private Sub btnRun_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnRun.Click

    Dim dtexecArgs As String
    Dim dataReaderName As String
    Dim countryName As String

    Dim dtsConnection As DtsConnection
    Dim dtsCommand As DtsCommand
    Dim dtsDataReader As IDataReader
    Dim dtsParameter As DtsDataParameter

    Windows.Forms.Cursor.Current = Cursors.WaitCursor

    dtexecArgs = "/FILE ""C:\...\DtsClientWParamPkg.dtsx"""
    dataReaderName = "DataReaderDest"
    countryName = "Canada"

    dtsConnection = New DtsConnection()
    With dtsConnection
      .ConnectionString = dtexecArgs
      .Open()
    End With

    dtsCommand = New DtsCommand(dtsConnection)
    dtsCommand.CommandText = dataReaderName

    dtsParameter = New DtsDataParameter("Country", DbType.String)
    dtsParameter.Direction = ParameterDirection.Input
    dtsCommand.Parameters.Add(dtsParameter)

    dtsParameter.Value = countryName

    dtsDataReader = dtsCommand.ExecuteReader(CommandBehavior.Default)

    With dtsDataReader
      .Read()
      txtResults.Text = .GetInt32(0).ToString("N0")
    End With

    'After reaching the end of data rows,
    ' call the Read method one more time.
    Try
      dtsDataReader.Read()
    Catch ex As Exception
      MessageBox.Show("Exception on final call to Read method:" & ControlChars.CrLf & _
      ex.Message & ControlChars.CrLf & _
      ex.InnerException.Message, "Exception on final call to Read method", _
      MessageBoxButtons.OK, MessageBoxIcon.Error)
    End Try

    ' The following method is a best practice, and is
    '  required when using DtsDataParameter objects.
    dtsCommand.Dispose()

    Try
      dtsDataReader.Close()
    Catch ex As Exception
      MessageBox.Show("Exception closing DataReader:" & ControlChars.CrLf & _
      ex.Message & ControlChars.CrLf & _
      ex.InnerException.Message, "Exception closing DataReader", _
      MessageBoxButtons.OK, MessageBoxIcon.Error)
    End Try

    Try
      dtsConnection.Close()
    Catch ex As Exception
      MessageBox.Show("Exception closing connection:" & ControlChars.CrLf & _
      ex.Message & ControlChars.CrLf & _
      ex.InnerException.Message, "Exception closing connection", _
      MessageBoxButtons.OK, MessageBoxIcon.Error)
    End Try

    Windows.Forms.Cursor.Current = Cursors.Default

  End Sub

End Class
```

```csharp
using System;
using System.Windows.Forms;
using System.Data;
using Microsoft.SqlServer.Dts.DtsClient;

namespace DtsClientWParamCS
{
  public partial class Form1 : Form
  {
    public Form1()
    {
      InitializeComponent();
      this.btnRun.Click += new System.EventHandler(this.btnRun_Click);
    }

    private void btnRun_Click(object sender, EventArgs e)
    {
      string dtexecArgs;
      string dataReaderName;
      string countryName;

      DtsConnection dtsConnection;
      DtsCommand dtsCommand;
      IDataReader dtsDataReader;
      DtsDataParameter dtsParameter;

      Cursor.Current = Cursors.WaitCursor;

      dtexecArgs = @"/FILE ""C:\...\DtsClientWParamPkg.dtsx""";
      dataReaderName = "DataReaderDest";
      countryName = "Canada";

      dtsConnection = new DtsConnection();
      {
        dtsConnection.ConnectionString = dtexecArgs;
        dtsConnection.Open();
      }

      dtsCommand = new DtsCommand(dtsConnection);
      dtsCommand.CommandText = dataReaderName;

      dtsParameter = new DtsDataParameter("Country", DbType.String);
      dtsParameter.Direction = ParameterDirection.Input;
      dtsCommand.Parameters.Add(dtsParameter);

      dtsParameter.Value = countryName;

      dtsDataReader = dtsCommand.ExecuteReader(CommandBehavior.Default);

      {
        dtsDataReader.Read();
        txtResults.Text = dtsDataReader.GetInt32(0).ToString("N0");
      }

      //After reaching the end of data rows,
      // call the Read method one more time.
      try
      {
        dtsDataReader.Read();
      }
      catch (Exception ex)
      {
        MessageBox.Show(
          "Exception on final call to Read method:\n" + ex.Message + "\n" + ex.InnerException.Message,
          "Exception on final call to Read method", MessageBoxButtons.OK, MessageBoxIcon.Error);
      }

      // The following method is a best practice, and is
      //  required when using DtsDataParameter objects.
      dtsCommand.Dispose();

      try
      {
        dtsDataReader.Close();
      }
      catch (Exception ex)
      {
        MessageBox.Show(
          "Exception closing DataReader:\n" + ex.Message + "\n" + ex.InnerException.Message,
          "Exception closing DataReader", MessageBoxButtons.OK, MessageBoxIcon.Error);
      }

      try
      {
        dtsConnection.Close();
      }
      catch (Exception ex)
      {
        MessageBox.Show(
          "Exception closing connection:\n" + ex.Message + "\n" + ex.InnerException.Message,
          "Exception closing connection", MessageBoxButtons.OK, MessageBoxIcon.Error);
      }

      Cursor.Current = Cursors.Default;

    }
  }
}
```

<span data-ttu-id="04838-176">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="04838-176">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="04838-177">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="04838-177">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="04838-178">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="04838-178">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="04838-179">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="04838-179">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="04838-180">另请参阅</span><span class="sxs-lookup"><span data-stu-id="04838-180">See Also</span></span>
 <span data-ttu-id="04838-181">[了解本地和远程执行](../run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md)[加载与运行本地包](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)之间的差异，以编程方式[加载和运行远程包](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)</span><span class="sxs-lookup"><span data-stu-id="04838-181">[Understanding the Differences between Local and Remote Execution](../run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md) [Loading and Running a Local Package Programmatically](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md) [Loading and Running a Remote Package Programmatically](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)</span></span>


