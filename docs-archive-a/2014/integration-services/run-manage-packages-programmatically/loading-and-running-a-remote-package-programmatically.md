---
title: 以编程方式加载和运行远程包 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Integration Services packages, running
- packages [Integration Services], running
- remote packages [Integration Services]
ms.assetid: 9f6ef376-3408-46bf-b5fa-fc7b18c689c9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 06565140ae8ea3603461e2944e242aa91213de47
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692997"
---
# <a name="loading-and-running-a-remote-package-programmatically"></a><span data-ttu-id="085c4-102">以编程方式加载和运行远程包</span><span class="sxs-lookup"><span data-stu-id="085c4-102">Loading and Running a Remote Package Programmatically</span></span>
  <span data-ttu-id="085c4-103">若要从未安装 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 的本地计算机运行远程包，请启动这些包，以便它们可在安装了 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 的远程计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="085c4-103">To run remote packages from a local computer that does not have [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installed, start the packages so that they run on the remote computer on which [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] is installed.</span></span> <span data-ttu-id="085c4-104">为此，可在本地计算机上使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理、Web 服务或远程组件来启动远程计算机上的包。</span><span class="sxs-lookup"><span data-stu-id="085c4-104">You do this by having the local computer use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, a Web service, or a remote component to start the packages on the remote computer.</span></span> <span data-ttu-id="085c4-105">如果尝试直接从本地计算机启动远程包，则这些包将加载到本地计算机上，并尝试在本地计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="085c4-105">If you try to start the remote packages directly from the local computer, the packages will load onto and try to run from the local computer.</span></span> <span data-ttu-id="085c4-106">如果本地计算机未安装 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]，这些包将不会运行。</span><span class="sxs-lookup"><span data-stu-id="085c4-106">If the local computer does not have [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installed, the packages will not run.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="085c4-107">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 外，你不能在未安装 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 的客户端计算机上运行包，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 许可条款可能不允许你在其他计算机上安装 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="085c4-107">You cannot run packages outside [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] on a client computer that does not have [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installed, and the terms of your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] licensing might not let you install [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] on additional computers.</span></span> [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="085c4-108">是服务器组件，不可再分发至客户端计算机。</span><span class="sxs-lookup"><span data-stu-id="085c4-108">is a server component and is not redistributable to client computers.</span></span>  
  
 <span data-ttu-id="085c4-109">或者，您也可以从安装了 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 的本地计算机运行远程包。</span><span class="sxs-lookup"><span data-stu-id="085c4-109">Alternately, you can run a remote package from a local computer that has [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installed.</span></span> <span data-ttu-id="085c4-110">有关详细信息，请参阅[以编程方式加载和运行本地包](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="085c4-110">For more information, see [Loading and Running a Local Package Programmatically](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md).</span></span>  
  
##  <a name="running-a-remote-package-on-the-remote-computer"></a><a name="top"></a><span data-ttu-id="085c4-111">在远程计算机上运行远程包</span><span class="sxs-lookup"><span data-stu-id="085c4-111">Running a Remote Package on the Remote Computer</span></span>  
 <span data-ttu-id="085c4-112">如上所述，可以用多种方法在远程服务器上运行远程包：</span><span class="sxs-lookup"><span data-stu-id="085c4-112">As mentioned above, there are multiple ways in which you can run a remote package on a remote server:</span></span>  
  
-   [<span data-ttu-id="085c4-113">使用 SQL Server 代理以编程方式运行远程包</span><span class="sxs-lookup"><span data-stu-id="085c4-113">Use SQL Server Agent to run the remote package programmatically</span></span>](#agent)  
  
-   [<span data-ttu-id="085c4-114">使用 Web 服务或远程组件以编程方式运行远程包</span><span class="sxs-lookup"><span data-stu-id="085c4-114">Use a Web service or remote component to run the remote package programmatically</span></span>](#service)  
  
 <span data-ttu-id="085c4-115">本主题中使用的几乎所有加载和保存包的方法都需要引用 `Microsoft.SqlServer.ManagedDTS` 程序集。</span><span class="sxs-lookup"><span data-stu-id="085c4-115">Almost all the methods that are used in this topic to load and save packages require a reference to the `Microsoft.SqlServer.ManagedDTS` assembly.</span></span> <span data-ttu-id="085c4-116">本主题中演示的用于执行**sp_start_job**存储过程的 ADO.NET 方法例外，该方法只需要对的引用 `System.Data` 。</span><span class="sxs-lookup"><span data-stu-id="085c4-116">The exception is the ADO.NET approach demonstrated in this topic for executing the **sp_start_job** stored procedure, which requires only a reference to `System.Data`.</span></span> <span data-ttu-id="085c4-117">在新项目中添加对 `Microsoft.SqlServer.ManagedDTS` 程序集的引用后，请使用 `using` 或 `Imports` 语句导入 <xref:Microsoft.SqlServer.Dts.Runtime> 命名空间。</span><span class="sxs-lookup"><span data-stu-id="085c4-117">After you add the reference to the `Microsoft.SqlServer.ManagedDTS` assembly in a new project, import the <xref:Microsoft.SqlServer.Dts.Runtime> namespace with a `using` or `Imports` statement.</span></span>  
  
###  <a name="using-sql-server-agent-to-run-a-remote-package-programmatically-on-the-server"></a><a name="agent"></a><span data-ttu-id="085c4-118">使用 SQL Server 代理以编程方式在服务器上运行远程包</span><span class="sxs-lookup"><span data-stu-id="085c4-118">Using SQL Server Agent to Run a Remote Package Programmatically on the Server</span></span>  
 <span data-ttu-id="085c4-119">下面的代码示例演示如何以编程方式使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理在服务器上运行远程包。</span><span class="sxs-lookup"><span data-stu-id="085c4-119">The following code sample demonstrates how to programmatically use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to run a remote package on the server.</span></span> <span data-ttu-id="085c4-120">该示例代码调用系统存储过程 sp_start_job，该存储过程启动一个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业。</span><span class="sxs-lookup"><span data-stu-id="085c4-120">The code sample calls the system stored procedure, **sp_start_job**, which launches a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job.</span></span> <span data-ttu-id="085c4-121">该存储过程启动的作业名为 `RunSSISPackage`，并且此作业位于远程计算机上。</span><span class="sxs-lookup"><span data-stu-id="085c4-121">The job that the procedure launches is named `RunSSISPackage`, and this job is on the remote computer.</span></span> <span data-ttu-id="085c4-122">然后 `RunSSISPackage` 作业在远程计算机上运行包。</span><span class="sxs-lookup"><span data-stu-id="085c4-122">The `RunSSISPackage` job then runs the package on the remote computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="085c4-123">sp_start_job 存储过程的返回值指示该存储过程是否已成功启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业。</span><span class="sxs-lookup"><span data-stu-id="085c4-123">The return value of the **sp_start_job** stored procedure indicates whether the stored procedure was able to start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job successfully.</span></span> <span data-ttu-id="085c4-124">此返回值不指示该包成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="085c4-124">The return value does not indicate whether the package succeeded or failed.</span></span>  
  
 <span data-ttu-id="085c4-125">有关对从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业运行的包进行故障排除的信息，请参阅 Microsoft 文章[从 SQL Server 代理作业步骤调用 SSIS 包时 SSIS 包不运行](https://support.microsoft.com/kb/918760)。</span><span class="sxs-lookup"><span data-stu-id="085c4-125">For information on troubleshooting packages that are run from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs, see the Microsoft article, [An SSIS package does not run when you call the SSIS package from a SQL Server Agent job step](https://support.microsoft.com/kb/918760).</span></span>  
  
### <a name="sample-code"></a><span data-ttu-id="085c4-126">代码示例</span><span class="sxs-lookup"><span data-stu-id="085c4-126">Sample Code</span></span>  
  
```vb  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  
  Sub Main()  
  
    Dim jobConnection As SqlConnection  
    Dim jobCommand As SqlCommand  
    Dim jobReturnValue As SqlParameter  
    Dim jobParameter As SqlParameter  
    Dim jobResult As Integer  
  
    jobConnection = New SqlConnection("Data Source=(local);Initial Catalog=msdb;Integrated Security=SSPI")  
    jobCommand = New SqlCommand("sp_start_job", jobConnection)  
    jobCommand.CommandType = CommandType.StoredProcedure  
  
    jobReturnValue = New SqlParameter("@RETURN_VALUE", SqlDbType.Int)  
    jobReturnValue.Direction = ParameterDirection.ReturnValue  
    jobCommand.Parameters.Add(jobReturnValue)  
  
    jobParameter = New SqlParameter("@job_name", SqlDbType.VarChar)  
    jobParameter.Direction = ParameterDirection.Input  
    jobCommand.Parameters.Add(jobParameter)  
    jobParameter.Value = "RunSSISPackage"  
  
    jobConnection.Open()  
    jobCommand.ExecuteNonQuery()  
    jobResult = DirectCast(jobCommand.Parameters("@RETURN_VALUE").Value, Integer)  
    jobConnection.Close()  
  
    Select Case jobResult  
      Case 0  
        Console.WriteLine("SQL Server Agent job, RunSISSPackage, started successfully.")  
      Case Else  
        Console.WriteLine("SQL Server Agent job, RunSISSPackage, failed to start.")  
    End Select  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace LaunchSSISPackageAgent_CS  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      SqlConnection jobConnection;  
      SqlCommand jobCommand;  
      SqlParameter jobReturnValue;  
      SqlParameter jobParameter;  
      int jobResult;  
  
      jobConnection = new SqlConnection("Data Source=(local);Initial Catalog=msdb;Integrated Security=SSPI");  
      jobCommand = new SqlCommand("sp_start_job", jobConnection);  
      jobCommand.CommandType = CommandType.StoredProcedure;  
  
      jobReturnValue = new SqlParameter("@RETURN_VALUE", SqlDbType.Int);  
      jobReturnValue.Direction = ParameterDirection.ReturnValue;  
      jobCommand.Parameters.Add(jobReturnValue);  
  
      jobParameter = new SqlParameter("@job_name", SqlDbType.VarChar);  
      jobParameter.Direction = ParameterDirection.Input;  
      jobCommand.Parameters.Add(jobParameter);  
      jobParameter.Value = "RunSSISPackage";  
  
      jobConnection.Open();  
      jobCommand.ExecuteNonQuery();  
      jobResult = (Int32)jobCommand.Parameters["@RETURN_VALUE"].Value;  
      jobConnection.Close();  
  
      switch (jobResult)  
      {  
        case 0:  
          Console.WriteLine("SQL Server Agent job, RunSISSPackage, started successfully.");  
          break;  
        default:  
          Console.WriteLine("SQL Server Agent job, RunSISSPackage, failed to start.");  
          break;  
      }  
      Console.Read();  
    }  
  }  
}  
```  
  
 
  
###  <a name="using-a-web-service-or-remote-component-to-run-a-remote-package-programmatically"></a><a name="service"></a><span data-ttu-id="085c4-127">使用 Web 服务或远程组件以编程方式运行远程包</span><span class="sxs-lookup"><span data-stu-id="085c4-127">Using a Web Service or Remote Component to Run a Remote Package Programmatically</span></span>  
 <span data-ttu-id="085c4-128">上面的以编程方式在服务器上运行包的解决方案不需要服务器上的任何自定义代码。</span><span class="sxs-lookup"><span data-stu-id="085c4-128">The previous solution for running packages programmatically on the server does not require any custom code on the server.</span></span> <span data-ttu-id="085c4-129">但是，您可能更倾向于不依赖 SQL Server 代理来执行包的解决方案。</span><span class="sxs-lookup"><span data-stu-id="085c4-129">However, you may prefer a solution that does not rely on SQL Server Agent to execute packages.</span></span> <span data-ttu-id="085c4-130">下面的示例演示可在服务器上创建用于在本地启动 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包的 Web 服务，以及可用于从客户端计算机调用 Web 服务的测试应用程序。</span><span class="sxs-lookup"><span data-stu-id="085c4-130">The following example demonstrates a Web service that can be created on the server to start [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages locally, and a test application that can be used to call the Web service from a client computer.</span></span> <span data-ttu-id="085c4-131">如果你更倾向于创建远程组件而不是 Web 服务，则可在远程组件中使用同一代码逻辑，只需很少的更改。</span><span class="sxs-lookup"><span data-stu-id="085c4-131">If you prefer to create a remote component instead of a Web service, you can use the same code logic with very few changes in a remote component.</span></span> <span data-ttu-id="085c4-132">但是，与 Web 服务相比，远程组件可能需要更广泛的配置。</span><span class="sxs-lookup"><span data-stu-id="085c4-132">However a remote component may require more extensive configuration than a Web service.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="085c4-133">使用 Web 服务的默认身份验证和授权设置，加载和执行包时通常没有足够的权限来访问 SQL Server 或文件系统。</span><span class="sxs-lookup"><span data-stu-id="085c4-133">With its default settings for authentication and authorization, a Web service generally does not have sufficient permissions to access SQL Server or the file system to load and execute packages.</span></span> <span data-ttu-id="085c4-134">可能需要在 web.config 文件中配置 Web 服务的身份验证和授权设置并相应地分配数据库和文件系统权限，以便为 Web 服务分配适当的权限  。</span><span class="sxs-lookup"><span data-stu-id="085c4-134">You may have to assign appropriate permissions to the Web service by configuring its authentication and authorization settings in the **web.config** file and assigning database and file system permissions as appropriate.</span></span> <span data-ttu-id="085c4-135">有关 Web、数据库和文件系统权限的全面讨论已超出了本主题的范围。</span><span class="sxs-lookup"><span data-stu-id="085c4-135">A complete discussion of Web, database, and file system permissions is beyond the scope of this topic.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="085c4-136"><xref:Microsoft.SqlServer.Dts.Runtime.Application> 类中用于 SSIS 包存储的方法仅支持“.”、localhost 或本地服务器的服务器名称。</span><span class="sxs-lookup"><span data-stu-id="085c4-136">The methods of the <xref:Microsoft.SqlServer.Dts.Runtime.Application> class for working with the SSIS Package Store support only ".", localhost, or the server name for the local server.</span></span> <span data-ttu-id="085c4-137">不能使用“(local)”。</span><span class="sxs-lookup"><span data-stu-id="085c4-137">You cannot use "(local)".</span></span>  
  
### <a name="sample-code"></a><span data-ttu-id="085c4-138">代码示例</span><span class="sxs-lookup"><span data-stu-id="085c4-138">Sample Code</span></span>  
 <span data-ttu-id="085c4-139">下面的代码示例演示如何创建和测试 Web 服务。</span><span class="sxs-lookup"><span data-stu-id="085c4-139">The following code samples show how to create and test the Web service.</span></span>  
  
#### <a name="creating-the-web-service"></a><span data-ttu-id="085c4-140">创建 Web 服务</span><span class="sxs-lookup"><span data-stu-id="085c4-140">Creating the Web Service</span></span>  
 <span data-ttu-id="085c4-141">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包可从文件或 SQL Server 直接加载，也可以从 SSIS 包存储区加载，该存储区在 SQL Server 和特殊文件系统文件夹中管理包存储。{2}</span><span class="sxs-lookup"><span data-stu-id="085c4-141">An [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package can be loaded directly from a file, directly from SQL Server, or from the SSIS Package Store, which manages package storage in both SQL Server and special file system folders.</span></span> <span data-ttu-id="085c4-142">此示例支持所有可用选项，方法是使用 `Select Case` 或 `switch` 构造来选择启动包所用的相应语法，并相应地连接输入参数。</span><span class="sxs-lookup"><span data-stu-id="085c4-142">This sample supports all the available options by using a `Select Case` or `switch` construct to select the appropriate syntax for starting the package and to concatenate the input arguments appropriately.</span></span> <span data-ttu-id="085c4-143">LaunchPackage Web 服务方法返回的包执行结果为整数形式，而不是 <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> 值，以便客户端计算机不需要引用任何 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 程序集。</span><span class="sxs-lookup"><span data-stu-id="085c4-143">The LaunchPackage Web service method returns the result of package execution as an integer instead of a <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> value so that client computers do not require a reference to any [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] assemblies.</span></span>  
  
###### <a name="to-create-a-web-service-to-run-packages-on-the-server-programmatically"></a><span data-ttu-id="085c4-144">以编程方式创建 Web 服务以在服务器上运行包</span><span class="sxs-lookup"><span data-stu-id="085c4-144">To create a Web service to run packages on the server programmatically</span></span>  
  
1.  <span data-ttu-id="085c4-145">打开 Visual Studio，并使用首选的编程语言创建一个 Web 服务项目。</span><span class="sxs-lookup"><span data-stu-id="085c4-145">Open Visual Studio and create a Web service project in your preferred programming language.</span></span> <span data-ttu-id="085c4-146">示例代码将该项目命名为 LaunchSSISPackageService。</span><span class="sxs-lookup"><span data-stu-id="085c4-146">The sample code uses the name LaunchSSISPackageService for the project.</span></span>  
  
2.  <span data-ttu-id="085c4-147">添加对的引用 `Microsoft.SqlServer.ManagedDTS` ，并向 `Imports` `using` **Microsoft SqlServer**命名空间的代码文件添加或语句。</span><span class="sxs-lookup"><span data-stu-id="085c4-147">Add a reference to `Microsoft.SqlServer.ManagedDTS` and add an `Imports` or `using` statement to the code file for the **Microsoft.SqlServer.Dts.Runtime** namespace.</span></span>  
  
3.  <span data-ttu-id="085c4-148">将 LaunchPackage Web 服务方法的示例代码粘贴到类中。</span><span class="sxs-lookup"><span data-stu-id="085c4-148">Paste the sample code for the LaunchPackage Web service method into the class.</span></span> <span data-ttu-id="085c4-149">（该示例显示了代码窗口的全部内容。）</span><span class="sxs-lookup"><span data-stu-id="085c4-149">(The sample shows the whole contents of the code window.)</span></span>  
  
4.  <span data-ttu-id="085c4-150">生成该 Web 服务，并通过为 LaunchPackage 方法的输入参数提供一组指向现有包的有效值来进行测试。</span><span class="sxs-lookup"><span data-stu-id="085c4-150">Build and test the Web service by providing a set of valid values for the input arguments of the LaunchPackage method that point to an existing package.</span></span> <span data-ttu-id="085c4-151">例如，如果 package1.dtsx 存储在服务器的 C:\My Packages 中，则传递“file”作为 sourceType 的值，“C:\My Packages”作为 sourceLocation 的值，以及“package1”（不带扩展名）作为 packageName 的值。</span><span class="sxs-lookup"><span data-stu-id="085c4-151">For example, if package1.dtsx is stored on the server in C:\My Packages, pass "file" as the value of the sourceType, "C:\My Packages" as the value of sourceLocation, and "package1" (without the extension) as the value of packageName.</span></span>  
  
```vb  
Imports System.Web  
Imports System.Web.Services  
Imports System.Web.Services.Protocols  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports System.IO  
  
<WebService(Namespace:="http://dtsue/")> _  
<WebServiceBinding(ConformsTo:=WsiProfiles.BasicProfile1_1)> _  
<Global.Microsoft.VisualBasic.CompilerServices.DesignerGenerated()> _  
Public Class LaunchSSISPackageService  
  Inherits System.Web.Services.WebService  
  
  ' LaunchPackage Method Parameters:  
  ' 1. sourceType: file, sql, dts  
  ' 2. sourceLocation: file system folder, (none), logical folder  
  ' 3. packageName: for file system, ".dtsx" extension is appended  
  
  <WebMethod()> _  
  Public Function LaunchPackage( _  
    ByVal sourceType As String, _  
    ByVal sourceLocation As String, _  
    ByVal packageName As String) As Integer 'DTSExecResult  
  
    Dim packagePath As String  
    Dim myPackage As Package  
    Dim integrationServices As New Application  
  
    ' Combine path and file name.  
    packagePath = Path.Combine(sourceLocation, packageName)  
  
    Select Case sourceType  
      Case "file"  
        ' Package is stored as a file.  
        ' Add extension if not present.  
        If String.IsNullOrEmpty(Path.GetExtension(packagePath)) Then  
          packagePath = String.Concat(packagePath, ".dtsx")  
        End If  
        If File.Exists(packagePath) Then  
          myPackage = integrationServices.LoadPackage(packagePath, Nothing)  
        Else  
          Throw New ApplicationException( _  
            "Invalid file location: " & packagePath)  
        End If  
      Case "sql"  
        ' Package is stored in MSDB.  
        ' Combine logical path and package name.  
        If integrationServices.ExistsOnSqlServer(packagePath, ".", String.Empty, String.Empty) Then  
          myPackage = integrationServices.LoadFromSqlServer( _  
            packageName, "(local)", String.Empty, String.Empty, Nothing)  
        Else  
          Throw New ApplicationException( _  
            "Invalid package name or location: " & packagePath)  
        End If  
      Case "dts"  
        ' Package is managed by SSIS Package Store.  
        ' Default logical paths are File System and MSDB.  
        If integrationServices.ExistsOnDtsServer(packagePath, ".") Then  
          myPackage = integrationServices.LoadFromDtsServer(packagePath, "localhost", Nothing)  
        Else  
          Throw New ApplicationException( _  
            "Invalid package name or location: " & packagePath)  
        End If  
      Case Else  
        Throw New ApplicationException( _  
          "Invalid sourceType argument: valid values are 'file', 'sql', and 'dts'.")  
    End Select  
  
    Return myPackage.Execute()  
  
  End Function  
  
End Class  
```  
  
```csharp  
using System;  
using System.Web;  
using System.Web.Services;  
using System.Web.Services.Protocols;  
using Microsoft.SqlServer.Dts.Runtime;  
using System.IO;  
  
[WebService(Namespace = "http://dtsue/")]  
[WebServiceBinding(ConformsTo = WsiProfiles.BasicProfile1_1)]  
public class LaunchSSISPackageServiceCS : System.Web.Services.WebService  
{  
  public LaunchSSISPackageServiceCS()  
  {  
    }  
  
  // LaunchPackage Method Parameters:  
  // 1. sourceType: file, sql, dts  
  // 2. sourceLocation: file system folder, (none), logical folder  
  // 3. packageName: for file system, ".dtsx" extension is appended  
  
  [WebMethod]  
  public int LaunchPackage(string sourceType, string sourceLocation, string packageName)  
  {   
  
    string packagePath;  
    Package myPackage;  
    Application integrationServices = new Application();  
  
    // Combine path and file name.  
    packagePath = Path.Combine(sourceLocation, packageName);  
  
    switch(sourceType)  
    {  
      case "file":  
        // Package is stored as a file.  
        // Add extension if not present.  
        if (String.IsNullOrEmpty(Path.GetExtension(packagePath)))  
        {  
          packagePath = String.Concat(packagePath, ".dtsx");  
        }  
        if (File.Exists(packagePath))  
        {  
          myPackage = integrationServices.LoadPackage(packagePath, null);  
        }  
        else  
        {  
          throw new ApplicationException("Invalid file location: "+packagePath);  
        }  
        break;  
      case "sql":  
        // Package is stored in MSDB.  
        // Combine logical path and package name.  
        if (integrationServices.ExistsOnSqlServer(packagePath, ".", String.Empty, String.Empty))  
        {  
          myPackage = integrationServices.LoadFromSqlServer(packageName, "(local)", String.Empty, String.Empty, null);  
        }  
        else  
        {  
          throw new ApplicationException("Invalid package name or location: "+packagePath);  
        }  
        break;  
      case "dts":  
        // Package is managed by SSIS Package Store.  
        // Default logical paths are File System and MSDB.  
        if (integrationServices.ExistsOnDtsServer(packagePath, "."))  
        {  
          myPackage = integrationServices.LoadFromDtsServer(packagePath, "localhost", null);  
        }  
        else  
        {  
          throw new ApplicationException("Invalid package name or location: "+packagePath);  
        }  
        break;  
      default:  
        throw new ApplicationException("Invalid sourceType argument: valid values are 'file', 'sql', and 'dts'.");  
    }  
  
    return (Int32)myPackage.Execute();  
  
  }  
  
}  
```  
  
#### <a name="testing-the-web-service"></a><span data-ttu-id="085c4-152">测试 Web 服务</span><span class="sxs-lookup"><span data-stu-id="085c4-152">Testing the Web Service</span></span>  
 <span data-ttu-id="085c4-153">下面的示例控制台应用程序使用 Web 服务运行包。</span><span class="sxs-lookup"><span data-stu-id="085c4-153">The following sample console application uses the Web service to run a package.</span></span> <span data-ttu-id="085c4-154">Web 服务的 LaunchPackage 方法返回的包执行结果为整数形式，而不是 <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> 值，以便客户端计算机不需要引用任何 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 程序集。</span><span class="sxs-lookup"><span data-stu-id="085c4-154">The LaunchPackage method of the Web service returns the result of package execution as an integer instead of a <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> value so that client computers do not require a reference to any [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] assemblies.</span></span> <span data-ttu-id="085c4-155">该示例创建私有枚举，该枚举的值镜像 <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> 值，以报告执行结果。</span><span class="sxs-lookup"><span data-stu-id="085c4-155">The sample creates a private enumeration whose values mirror the <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> values to report the results of execution.</span></span>  
  
###### <a name="to-create-a-console-application-to-test-the-web-service"></a><span data-ttu-id="085c4-156">创建用于测试 Web 服务的控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="085c4-156">To create a console application to test the Web service</span></span>  
  
1.  <span data-ttu-id="085c4-157">在 Visual Studio 中，使用首选的编程语言将新的控制台应用程序添加到包含 Web 服务项目的解决方案中。</span><span class="sxs-lookup"><span data-stu-id="085c4-157">In Visual Studio, add a new console application, using your preferred programming language, to the same solution that contains the Web service project.</span></span> <span data-ttu-id="085c4-158">示例代码将该项目命名为 LaunchSSISPackageTest。</span><span class="sxs-lookup"><span data-stu-id="085c4-158">The sample code uses the name LaunchSSISPackageTest for the project.</span></span>  
  
2.  <span data-ttu-id="085c4-159">将新的控制台应用程序设置为解决方案中的启动项目。</span><span class="sxs-lookup"><span data-stu-id="085c4-159">Set the new console application as the startup project in the solution.</span></span>  
  
3.  <span data-ttu-id="085c4-160">添加对 Web 服务项目的 Web 引用。</span><span class="sxs-lookup"><span data-stu-id="085c4-160">Add a Web reference for the Web service project.</span></span> <span data-ttu-id="085c4-161">如有必要，可调整示例代码中分配给 Web 服务代理对象的名称的变量声明。</span><span class="sxs-lookup"><span data-stu-id="085c4-161">If necessary, adjust the variable declaration in the sample code for the name that you assign to the Web service proxy object.</span></span>  
  
4.  <span data-ttu-id="085c4-162">将主例程和私有枚举的示例代码粘贴到代码中。</span><span class="sxs-lookup"><span data-stu-id="085c4-162">Paste the sample code for the Main routine and the private enumeration into the code.</span></span> <span data-ttu-id="085c4-163">（该示例显示了代码窗口的全部内容。）</span><span class="sxs-lookup"><span data-stu-id="085c4-163">(The sample shows the whole contents of the code window.)</span></span>  
  
5.  <span data-ttu-id="085c4-164">编辑调用 LaunchPackage 方法的代码行，为输入参数提供一组指向现有包的有效值。</span><span class="sxs-lookup"><span data-stu-id="085c4-164">Edit the line of code that calls the LaunchPackage method to provide a set of valid values for the input arguments that point to an existing package.</span></span> <span data-ttu-id="085c4-165">例如，如果 package1.dtsx 存储在服务器的 C:\My Packages 中，则传递“file”作为 `sourceType` 的值，“C:\My Packages”作为 `sourceLocation` 的值，以及“package1”（不带扩展名）作为 `packageName` 的值。</span><span class="sxs-lookup"><span data-stu-id="085c4-165">For example, if package1.dtsx is stored on the server in C:\My Packages, pass "file" as the value of `sourceType`, "C:\My Packages" as the value of `sourceLocation`, and "package1" (without the extension) as the value of `packageName`.</span></span>  
  
```vb  
Module LaunchSSISPackageTest  
  
  Sub Main()  
  
    Dim launchPackageService As New LaunchSSISPackageService.LaunchSSISPackageService  
    Dim packageResult As Integer  
  
    Try  
      packageResult = launchPackageService.LaunchPackage("sql", String.Empty, "SimpleTestPackage")  
    Catch ex As Exception  
      ' The type of exception returned by a Web service is:  
      '  System.Web.Services.Protocols.SoapException  
      Console.WriteLine("The following exception occurred: " & ex.Message)  
    End Try  
  
    Console.WriteLine(CType(packageResult, PackageExecutionResult).ToString)  
    Console.ReadKey()  
  
  End Sub  
  
  Private Enum PackageExecutionResult  
    PackageSucceeded  
    PackageFailed  
    PackageCompleted  
    PackageWasCancelled  
  End Enum  
  
End Module  
```  
  
```csharp  
using System;  
  
namespace LaunchSSISPackageSvcTestCS  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      LaunchSSISPackageServiceCS.LaunchSSISPackageServiceCS launchPackageService = new LaunchSSISPackageServiceCS.LaunchSSISPackageServiceCS();  
      int packageResult = 0;  
  
      try  
      {  
        packageResult = launchPackageService.LaunchPackage("sql", String.Empty, "SimpleTestPackage");  
      }  
      catch (Exception ex)  
      {  
        // The type of exception returned by a Web service is:  
        //  System.Web.Services.Protocols.SoapException  
        Console.WriteLine("The following exception occurred: " + ex.Message);  
      }  
  
      Console.WriteLine(((PackageExecutionResult)packageResult).ToString());  
      Console.ReadKey();  
  
    }  
  
    private enum PackageExecutionResult  
    {  
      PackageSucceeded,  
      PackageFailed,  
      PackageCompleted,  
      PackageWasCancelled  
    };  
  
  }  
}  
```  
  

  
## <a name="external-resources"></a><span data-ttu-id="085c4-166">外部资源</span><span class="sxs-lookup"><span data-stu-id="085c4-166">External Resources</span></span>  
  
-   <span data-ttu-id="085c4-167">technet.microsoft.com 上的视频：[如何使用 SQL Server 代理自动执行 SSIS 包（SQL Server 视频）](https://technet.microsoft.com/sqlserver/ff686764.aspx)</span><span class="sxs-lookup"><span data-stu-id="085c4-167">Video, [How to: Automate SSIS Package Execution by Using the SQL Server Agent (SQL Server Video)](https://technet.microsoft.com/sqlserver/ff686764.aspx), on technet.microsoft.com</span></span>  
  
<span data-ttu-id="085c4-168">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="085c4-168">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="085c4-169">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="085c4-169">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="085c4-170">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="085c4-170">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="085c4-171">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="085c4-171">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="085c4-172">另请参阅</span><span class="sxs-lookup"><span data-stu-id="085c4-172">See Also</span></span>  
 <span data-ttu-id="085c4-173">[了解本地执行与远程执行之间的差异](../run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md) </span><span class="sxs-lookup"><span data-stu-id="085c4-173">[Understanding the Differences between Local and Remote Execution](../run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md) </span></span>  
 <span data-ttu-id="085c4-174">[以编程方式加载和运行本地包](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md) </span><span class="sxs-lookup"><span data-stu-id="085c4-174">[Loading and Running a Local Package Programmatically](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md) </span></span>  
 [<span data-ttu-id="085c4-175">加载本地包的输出</span><span class="sxs-lookup"><span data-stu-id="085c4-175">Loading the Output of a Local Package</span></span>](../run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
  
  
