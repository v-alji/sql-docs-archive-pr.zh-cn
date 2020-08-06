---
title: 部署 CLR 数据库对象 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- deployment script [CLR integration]
- common language runtime [SQL Server], deploying
- deploying assemblies [CLR integration]
- deploying [CLR integration]
ms.assetid: 00752573-3367-41a7-af98-7b7a29e8e2f2
author: rothja
ms.author: jroth
ms.openlocfilehash: daf069bc37a58a879224b2217f4dcb700c1d6e99
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576819"
---
# <a name="deploying-clr-database-objects"></a><span data-ttu-id="0a3b8-102">部署 CLR 数据库对象</span><span class="sxs-lookup"><span data-stu-id="0a3b8-102">Deploying CLR Database Objects</span></span>
  <span data-ttu-id="0a3b8-103">部署是分发要在其他计算机上安装并运行的已完成应用程序或模块的过程。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-103">Deployment is the process by which you distribute a finished application or module to be installed and run on another computer.</span></span> <span data-ttu-id="0a3b8-104">可以使用 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio 开发公共语言运行时 (CLR) 数据库对象，并将这些对象部署到测试服务器。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-104">Using [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio, you can develop common language runtime (CLR) database objects and deploy them to a test server.</span></span> <span data-ttu-id="0a3b8-105">或者，也可以使用 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework 再分发文件替代 Visual Studio 对托管数据库对象进行编译。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-105">Alternatively, the managed database objects can also be compiled with the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework redistribution files, instead of Visual Studio.</span></span> <span data-ttu-id="0a3b8-106">编译完之后，可以使用 Visual Studio 或 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句，将包含 CLR 数据库对象的程序集部署到测试服务器。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-106">Once compiled, the assemblies containing the CLR database objects can then be deployed to a test server using Visual Studio or [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="0a3b8-107">请注意，Visual Studio .NET 2003 无法用于 CLR 集成编程或部署。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-107">Note that Visual Studio .NET 2003 cannot be used for CLR integration programming or deployment.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="0a3b8-108">包含预先安装的 .NET Framework，而 Visual Studio .NET 2003 无法使用 .NET Framework 2.0 程序集。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-108">includes the .NET Framework pre-installed, and Visual Studio .NET 2003 cannot use the .NET Framework 2.0 assemblies.</span></span>  
  
 <span data-ttu-id="0a3b8-109">在测试服务器上测试并验证了 CLR 方法后，便可以使用部署脚本将这些方法分发到生产服务器。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-109">Once the CLR methods have been tested and verified on the test server, they can be distributed to production servers using a deployment script.</span></span> <span data-ttu-id="0a3b8-110">可以手动生成部署脚本，或使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 生成（请参阅本主题后面的过程）。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-110">The deployment script can be generated manually, or by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] (see the procedure later in this topic).</span></span>  
  
 <span data-ttu-id="0a3b8-111">默认情况下，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中关闭了 CLR 集成功能，必须启用该功能才能使用 CLR 程序集。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-111">The CLR integration feature is turned off by default in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and must be enabled in order to use CLR assemblies.</span></span> <span data-ttu-id="0a3b8-112">有关详细信息，请参阅 [Enabling CLR Integration](clr-integration-enabling.md)。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-112">For more information, see [Enabling CLR Integration](clr-integration-enabling.md).</span></span>  
  
## <a name="deploying-the-assembly-to-the-test-server"></a><span data-ttu-id="0a3b8-113">将程序集部署到测试服务器</span><span class="sxs-lookup"><span data-stu-id="0a3b8-113">Deploying the Assembly to the Test Server</span></span>  
 <span data-ttu-id="0a3b8-114">可以使用 Visual Studio 开发 CLR 函数、过程、触发器、用户定义类型 (UDT) 或用户定义聚合 (UDA)，并将其部署到测试服务器。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-114">Using Visual Studio, you can develop CLR functions, procedures, triggers, user-defined types (UDTs), or user-defined aggregates (UDAs), and deploy them to a test server.</span></span> <span data-ttu-id="0a3b8-115">也可以使用 .NET Framework 再分发文件附带的命令行编译器（如 csc.exe 和 vbc.exe）编译这些托管数据库对象。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-115">These managed database objects can also be compiled with the command line compilers, such as csc.exe and vbc.exe, included with the .NET Framework redistribution files.</span></span> <span data-ttu-id="0a3b8-116">开发 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 托管数据库对象不一定需要 Visual Studio 集成开发环境。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-116">The Visual Studio Integrated Development Environment is not required to develop managed database objects for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="0a3b8-117">请务必确保解决所有编译器错误和警告。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-117">Make sure that all compiler errors and warnings are resolved.</span></span> <span data-ttu-id="0a3b8-118">随后，可以使用 Visual Studio 或 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 语句，在 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 数据库中注册包含 CLR 例程的程序集。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-118">The assemblies containing the CLR routines can then be registered in a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database using Visual Studio or [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0a3b8-119">必须对 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例启用 TCP/IP 网络协议，才能使用 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio 进行远程开发、调试和开发。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-119">The TCP/IP network protocol must be enabled on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance in order to use [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio for remote development, debugging, and development.</span></span> <span data-ttu-id="0a3b8-120">有关在服务器上启用 TCP/IP 协议的详细信息，请参阅[配置客户端协议](../../database-engine/configure-windows/configure-client-protocols.md)。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-120">For more information about enabling TCP/IP protocol on the server, see [Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md).</span></span>  
  
#### <a name="to-deploy-the-assembly-using-visual-studio"></a><span data-ttu-id="0a3b8-121">使用 Visual Studio 部署程序集</span><span class="sxs-lookup"><span data-stu-id="0a3b8-121">To deploy the assembly using Visual Studio</span></span>  
  
1.  <span data-ttu-id="0a3b8-122">通过**Build** \<project name> 从 "**生成**" 菜单中选择 "生成" 来生成项目。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-122">Build the project by selecting **Build** \<project name> from the **Build** menu.</span></span>  
  
2.  <span data-ttu-id="0a3b8-123">解决所有生成错误和警告，然后将程序集部署到测试服务器。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-123">Resolve all build errors and warnings before deploying the assembly to the test server.</span></span>  
  
3.  <span data-ttu-id="0a3b8-124">从 "**生成**" 菜单中选择 "**部署**"。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-124">Select **Deploy** from the **Build** menu.</span></span> <span data-ttu-id="0a3b8-125">随后，将在 Visual Studio 中首次创建 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 项目时指定的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例和数据库中注册程序集。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-125">The assembly will then be registered in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance and database specified when the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] project was first created in Visual Studio.</span></span>  
  
#### <a name="to-deploy-the-assembly-using-transact-sql"></a><span data-ttu-id="0a3b8-126">使用 Transact-SQL 部署程序集</span><span class="sxs-lookup"><span data-stu-id="0a3b8-126">To deploy the assembly using Transact-SQL</span></span>  
  
1.  <span data-ttu-id="0a3b8-127">使用 .NET Framework 附带的命令行编译器编译源文件中的程序集。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-127">Compile the assembly from the source file using the command line compilers included with the .NET Framework.</span></span>  
  
2.  <span data-ttu-id="0a3b8-128">对于 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# 源文件：</span><span class="sxs-lookup"><span data-stu-id="0a3b8-128">For [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# source files:</span></span>  
  
3.  `csc /target:library C:\helloworld.cs`  
  
4.  <span data-ttu-id="0a3b8-129">对于 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic 源文件：</span><span class="sxs-lookup"><span data-stu-id="0a3b8-129">For [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic source files:</span></span>  
  
 `vbc /target:library C:\helloworld.vb`  
  
 <span data-ttu-id="0a3b8-130">以上命令使用 `/target` 选项启动 Visual C# 或 Visual Basic 编译器，以指定生成库 DLL。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-130">These commands launch the Visual C# or Visual Basic compiler using the `/target` option to specify building a library DLL.</span></span>  
  
1.  <span data-ttu-id="0a3b8-131">解决所有生成错误和警告，然后将程序集部署到测试服务器。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-131">Resolve all build errors and warnings before deploying the assembly to the test server.</span></span>  
  
2.  <span data-ttu-id="0a3b8-132">在测试服务器上打开 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-132">Open [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] on the test server.</span></span> <span data-ttu-id="0a3b8-133">创建一个新查询，连接到合适的测试数据库（如 AdventureWorks）。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-133">Create a new query, connected to a suitable test database (such as AdventureWorks).</span></span>  
  
3.  <span data-ttu-id="0a3b8-134">将如下 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 添加到查询中，在服务器上创建程序集。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-134">Create the assembly in the server by adding the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] to the query.</span></span>  
  
 `CREATE ASSEMBLY HelloWorld from 'c:\helloworld.dll' WITH PERMISSION_SET = SAFE;`  
  
1.  <span data-ttu-id="0a3b8-135">随后，必须在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的实例中创建过程、函数、聚合、用户定义类型或触发器。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-135">The procedure, function, aggregate, user-defined type, or trigger must then be created in the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0a3b8-136">如果 `HelloWorld` 程序集在 `HelloWorld` 类中包含名为 `Procedures` 的方法，则可以将如下 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 添加到查询中，以在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中创建名为 `hello` 的过程。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-136">If the `HelloWorld` assembly contains a method named `HelloWorld` in the `Procedures` class, the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] can be added to the query to create a procedure called `hello` in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 `CREATE PROCEDURE hello`  
  
 `AS`  
  
 `EXTERNAL NAME HelloWorld.Procedures.HelloWorld`  
  
 <span data-ttu-id="0a3b8-137">有关在中创建不同类型的托管数据库对象的详细信息 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，请参阅[Clr 用户定义函数](../clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)、 [Clr 用户](../clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md)定义的聚合、 [Clr 用户定义类型](../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)、 [clr 存储过程](../../database-engine/dev-guide/clr-stored-procedures.md)和[clr 触发器](../../database-engine/dev-guide/clr-triggers.md)。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-137">For more information about creating the different types of managed database objects in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], see [CLR User-Defined Functions](../clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md), [CLR User-Defined Aggregates](../clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md), [CLR User-Defined Types](../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md), [CLR Stored Procedures](../../database-engine/dev-guide/clr-stored-procedures.md), and [CLR Triggers](../../database-engine/dev-guide/clr-triggers.md).</span></span>  
  
## <a name="deploying-the-assembly-to-production-servers"></a><span data-ttu-id="0a3b8-138">将程序集部署到生产服务器</span><span class="sxs-lookup"><span data-stu-id="0a3b8-138">Deploying the Assembly to Production Servers</span></span>  
 <span data-ttu-id="0a3b8-139">在测试服务器上测试并验证了 CLR 数据库对象后，便可以将这些数据库对象分发到生产服务器。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-139">Once the CLR database objects have been tested and verified on the test server, they can be distributed to production servers.</span></span> <span data-ttu-id="0a3b8-140">有关调试托管数据库对象的详细信息，请参阅[调试 CLR 数据库对象](debugging-clr-database-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-140">For more information about debugging managed database objects, see [Debugging CLR Database Objects](debugging-clr-database-objects.md).</span></span>  
  
 <span data-ttu-id="0a3b8-141">托管数据库对象的部署类似于常规数据库对象（如表、[!INCLUDE[tsql](../../../includes/tsql-md.md)] 例程等）。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-141">The deployment of managed database objects is similar to that of regular database objects (tables, [!INCLUDE[tsql](../../../includes/tsql-md.md)] routines, and so on).</span></span> <span data-ttu-id="0a3b8-142">可以使用部署脚本将包含 CLR 数据库对象的程序集部署到其他服务器。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-142">The assemblies containing the CLR database objects can be deployed to other servers using a deployment script.</span></span> <span data-ttu-id="0a3b8-143">部署脚本可以使用 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] 的“生成脚本”功能生成。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-143">The deployment script can be built by using the "Generate Scripts" functionality of [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="0a3b8-144">部署脚本也可以手动生成，或使用“生成脚本”功能生成然后手动更改。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-144">The deployment script can also be built manually, or built using "Generate Scripts" and manually altered.</span></span> <span data-ttu-id="0a3b8-145">部署脚本生成之后，可以在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的其他实例上运行，以部署托管数据库对象。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-145">Once the deployment script has been built, it can be run on other instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to deploy the managed database objects.</span></span>  
  
#### <a name="to-generate-a-deployment-script-using-generate-scripts"></a><span data-ttu-id="0a3b8-146">使用“生成脚本”生成部署脚本</span><span class="sxs-lookup"><span data-stu-id="0a3b8-146">To generate a deployment script using generate scripts</span></span>  
  
1.  <span data-ttu-id="0a3b8-147">打开 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]，然后连接到注册要部署的托管程序集或数据库对象的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-147">Open [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] and connect to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance where the managed assembly or database object to be deployed is registered.</span></span>  
  
2.  <span data-ttu-id="0a3b8-148">在**对象资源管理器**中，展开 **\<server name>** 和**数据库**树。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-148">In the **Object Explorer**, expand the **\<server name>** and **Databases** trees.</span></span> <span data-ttu-id="0a3b8-149">右键单击托管数据库对象所注册到的数据库，选择 "**任务**"，然后选择 "**生成脚本**"。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-149">Right-click the database where the managed database object is registered, select **Tasks**, and then select **Generate Scripts**.</span></span> <span data-ttu-id="0a3b8-150">将打开脚本向导。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-150">The Script Wizard opens.</span></span>  
  
3.  <span data-ttu-id="0a3b8-151">从列表框中选择数据库，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-151">Select the database from the list box and click **Next**.</span></span>  
  
4.  <span data-ttu-id="0a3b8-152">在 "**选择脚本选项**" 窗格中，单击 "**下一步**"，或更改选项，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-152">In the **Choose Script Options** pane, click **Next**, or change the options and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="0a3b8-153">在 "**选择对象类型**" 窗格中，选择要部署的数据库对象的类型。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-153">In the **Choose Object Types** pane, choose the type of database object to be deployed.</span></span> <span data-ttu-id="0a3b8-154">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-154">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="0a3b8-155">对于在 "**选择对象类型**" 窗格中选择的每个对象类型，将显示 " \*\* \<type> 选择\*\*" 窗格。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-155">For every object type selected in the **Choose Object Types** pane, a **Choose \<type>** pane is presented.</span></span> <span data-ttu-id="0a3b8-156">在此窗格中，可以从在指定数据库中注册的该数据库对象类型的所有实例中进行选择。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-156">In this pane, you can choose from all the instances of that database object type registered in the specified database.</span></span> <span data-ttu-id="0a3b8-157">选择一个或多个对象，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-157">Select one or more objects and click **Next**.</span></span>  
  
7.  <span data-ttu-id="0a3b8-158">选择了所有所需的数据库对象类型后，将出现 "**输出选项**" 窗格。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-158">The **Output Options** pane comes up when all of the desired database object types have been selected.</span></span> <span data-ttu-id="0a3b8-159">选择 "**将脚本保存到文件**" 并指定脚本的文件路径。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-159">Select **Script to file** and specify a file path for the script.</span></span> <span data-ttu-id="0a3b8-160">选择“下一步”。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-160">Select **Next**.</span></span> <span data-ttu-id="0a3b8-161">查看您的选择，然后单击 "**完成**"。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-161">Review your selections and click **Finish**.</span></span> <span data-ttu-id="0a3b8-162">部署脚本将保存到指定的文件路径。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-162">The deployment script is saved to the specified file path.</span></span>  
  
## <a name="post-deployment-scripts"></a><span data-ttu-id="0a3b8-163">后期部署脚本</span><span class="sxs-lookup"><span data-stu-id="0a3b8-163">Post Deployment Scripts</span></span>  
 <span data-ttu-id="0a3b8-164">您可以运行后期部署脚本。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-164">You can run a post deployment script.</span></span>  
  
 <span data-ttu-id="0a3b8-165">若要添加后期部署脚本，请在 Visual Studio 项目目录中添加一个名为 postdeployscript.sql 的文件。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-165">To add a post deployment script, add a file called postdeployscript.sql in your Visual Studio project directory.</span></span> <span data-ttu-id="0a3b8-166">例如，在**解决方案资源管理器**中右键单击项目，然后选择 "**添加现有项**"。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-166">For example, right click your project in **Solution Explorer** and select **Add Existing Item**.</span></span> <span data-ttu-id="0a3b8-167">将文件添加到项目的根目录，而不是 TestScripts 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-167">Add the file in the root of the project, rather than in the Test Scripts folder.</span></span>  
  
 <span data-ttu-id="0a3b8-168">单击“部署”时，Visual Studio 将在项目部署完成之后运行此脚本。</span><span class="sxs-lookup"><span data-stu-id="0a3b8-168">When you click deploy, Visual Studio will run this script after the deployment of your project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a3b8-169">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0a3b8-169">See Also</span></span>  
 [<span data-ttu-id="0a3b8-170">公共语言运行时 (CLR) 集成编程概念</span><span class="sxs-lookup"><span data-stu-id="0a3b8-170">Common Language Runtime &#40;CLR&#41; Integration Programming Concepts</span></span>](common-language-runtime-clr-integration-programming-concepts.md)  
  
  
