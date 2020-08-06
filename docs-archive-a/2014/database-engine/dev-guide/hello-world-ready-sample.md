---
title: Hello World Ready 示例 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
ms.assetid: 1cb94266-f702-4a57-a1ae-689a89c98757
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 7cc3088af258962a4cec615214147d1f4f09c431
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694093"
---
# <a name="hello-world-ready-sample"></a><span data-ttu-id="7a097-102">Hello World Ready 示例</span><span class="sxs-lookup"><span data-stu-id="7a097-102">Hello World Ready Sample</span></span>
  <span data-ttu-id="7a097-103">Hello World Ready 示例说明了创建、部署和测试基于公共语言运行时 (CLR) 集成的简单且全球通用存储过程所涉及的基本操作。</span><span class="sxs-lookup"><span data-stu-id="7a097-103">The Hello World Ready sample demonstrates the basic operations that are involved in creating, deploying, and testing a simple world ready common language runtime (CLR) integration-based stored procedure.</span></span> <span data-ttu-id="7a097-104">不用更改全球通用组件的源代码就可以将它轻松地本地化为全世界各个市场的各种语言。</span><span class="sxs-lookup"><span data-stu-id="7a097-104">A world-ready component can be easily localized into different languages for different markets around the world without changing the component's source code.</span></span> <span data-ttu-id="7a097-105">此示例还说明了如何通过输出参数和记录返回由存储过程动态构建并返回到客户端的数据。此示例与 Hello World 示例基本相同，只不过在对此应用程序进行本地化时，此示例更容易且更安全。</span><span class="sxs-lookup"><span data-stu-id="7a097-105">This sample also demonstrates how to return data through an output parameter and through a record, which is dynamically constructed by the stored procedure and returned to the client.This sample is almost identical to the Hello World Sample except that it is much easier and safer to localize this application.</span></span> <span data-ttu-id="7a097-106">更改已本地化的文本需要执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="7a097-106">To change localized text requires the following:</span></span>  
  
1.  <span data-ttu-id="7a097-107"> (更改 XML 文件。`resx`</span><span class="sxs-lookup"><span data-stu-id="7a097-107">Changing an XML file (the .`resx`</span></span> <span data-ttu-id="7a097-108">资源目录中特定区域性的文件) </span><span class="sxs-lookup"><span data-stu-id="7a097-108">file) for the particular culture in the resources directory</span></span>  
  
2.  <span data-ttu-id="7a097-109">使用 `resgen` 生成该语言的资源文件</span><span class="sxs-lookup"><span data-stu-id="7a097-109">Building the culture's resources file by using `resgen`</span></span>  
  
3.  <span data-ttu-id="7a097-110">生成该区域性的最新附属 DLL</span><span class="sxs-lookup"><span data-stu-id="7a097-110">Building the updated satellite DLL for that culture</span></span>  
  
4.  <span data-ttu-id="7a097-111">在 SQL Server 中删除和添加该程序集</span><span class="sxs-lookup"><span data-stu-id="7a097-111">Dropping and adding that assembly in SQL Server</span></span>  
  
 <span data-ttu-id="7a097-112">CLR 存储过程本身的源代码和程序集并不更改。</span><span class="sxs-lookup"><span data-stu-id="7a097-112">The source code and assembly for the CLR stored procedure itself does not change.</span></span> <span data-ttu-id="7a097-113">提供了 `build.cmd` 脚本，用来说明如何编译和链接资源程序集。尽管应用程序的源代码基于当前执行的程序集创建了资源管理器，但是您不必在包含存储过程的 DLL 中嵌入独立于区域性的资源。</span><span class="sxs-lookup"><span data-stu-id="7a097-113">A `build.cmd` script is provided which demonstrates how to compile and link the resource assemblies.Although the source code for the application creates a resource manager based the currently executing assembly, you do not have to embed the culture neutral resources in the DLL that contains the stored procedure.</span></span> <span data-ttu-id="7a097-114">`System.Resources.NeutralResourcesLanguage attribute` 允许附属 DLL 中存在独立于区域性的资源。</span><span class="sxs-lookup"><span data-stu-id="7a097-114">The `System.Resources.NeutralResourcesLanguage attribute` permits the culture-neutral resources to exist in a satellite DLL.</span></span> <span data-ttu-id="7a097-115">因此，最好使用单独的 DLL，以便在需要添加或更改本地化文本时，不必更改包含 CLR 存储过程的主 DLL。</span><span class="sxs-lookup"><span data-stu-id="7a097-115">It is much better to use a separate DLL for this purpose so that when localized text needs to be added or changed, the primary DLL that contains the CLR stored procedure does not have to be changed.</span></span> <span data-ttu-id="7a097-116">这对于可能含有列和其他相关性，造成类型难以删除和重新添加的 CLR 用户定义类型而言，尤为有用。通常，附属 DLL 版本必须与主程序集版本相同。</span><span class="sxs-lookup"><span data-stu-id="7a097-116">This is especially useful for CLR user-defined types that might have columns and other dependencies which would make it difficult to drop and re-add the type.Ordinarily, the satellite DLL versions must be identical to the main assembly version.</span></span> <span data-ttu-id="7a097-117">但是，使用 `SatelliteContractVersion` 属性可以允许仅更新主程序集，而不更新附属程序集。</span><span class="sxs-lookup"><span data-stu-id="7a097-117">However, you can use the `SatelliteContractVersion` attribute to allow the main assembly to be updated without updating the satellite assemblies too.</span></span> <span data-ttu-id="7a097-118">有关详细信息，请参阅 Microsoft .NET 文档中的 `ResourceManager` 类。</span><span class="sxs-lookup"><span data-stu-id="7a097-118">For more information, see the `ResourceManager` class in the Microsoft .NET documentation.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7a097-119">先决条件</span><span class="sxs-lookup"><span data-stu-id="7a097-119">Prerequisites</span></span>  
 <span data-ttu-id="7a097-120">此示例仅适用于 SQL Server 2005 和更高版本。</span><span class="sxs-lookup"><span data-stu-id="7a097-120">This sample works only with SQL Server 2005 and later versions.</span></span>  
  
 <span data-ttu-id="7a097-121">若要创建和运行此项目，必须安装下列软件：</span><span class="sxs-lookup"><span data-stu-id="7a097-121">To create and run this project the following the following software must be installed:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7a097-122">或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express。</span><span class="sxs-lookup"><span data-stu-id="7a097-122">or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express.</span></span> <span data-ttu-id="7a097-123">可以从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express 文档和示例[网站](https://www.microsoft.com/sql-server/sql-server-editions-express)免费获取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express</span><span class="sxs-lookup"><span data-stu-id="7a097-123">You can obtain [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express free of charge from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express Documentation and Samples [Web site](https://www.microsoft.com/sql-server/sql-server-editions-express)</span></span>  
  
-   <span data-ttu-id="7a097-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]开发人员[网站](https://go.microsoft.com/fwlink/?linkid=62796)提供的 AdventureWorks 数据库</span><span class="sxs-lookup"><span data-stu-id="7a097-124">The AdventureWorks database that is available at the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Developer [Web site](https://go.microsoft.com/fwlink/?linkid=62796)</span></span>  
  
-   <span data-ttu-id="7a097-125">.NET Framework SDK 2.0 或更高版本，或 Microsoft Visual Studio 2005 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="7a097-125">.NET Framework SDK 2.0 or later or Microsoft Visual Studio 2005 or later.</span></span> <span data-ttu-id="7a097-126">您可以免费获取 .NET Framework SDK。</span><span class="sxs-lookup"><span data-stu-id="7a097-126">You can obtain .NET Framework SDK free of charge.</span></span>  
  
-   <span data-ttu-id="7a097-127">此外，还必须满足以下条件：</span><span class="sxs-lookup"><span data-stu-id="7a097-127">In addition, the following conditions must be met:</span></span>  
  
-   <span data-ttu-id="7a097-128">使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例必须已启用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="7a097-128">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using must have CLR integration enabled.</span></span>  
  
-   <span data-ttu-id="7a097-129">若要启用 CLR 集成，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="7a097-129">In order to enable CLR integration, perform the following steps:</span></span>  
  
    #### <a name="enabling-clr-integration"></a><span data-ttu-id="7a097-130">启用 CLR 集成</span><span class="sxs-lookup"><span data-stu-id="7a097-130">Enabling CLR Integration</span></span>  
  
    -   <span data-ttu-id="7a097-131">执行以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 命令：</span><span class="sxs-lookup"><span data-stu-id="7a097-131">Execute the following [!INCLUDE[tsql](../../includes/tsql-md.md)] commands:</span></span>  
  
     `sp_configure 'clr enabled', 1`  
  
     `GO`  
  
     `RECONFIGURE`  
  
     `GO`  
  
    > [!NOTE]  
    >  <span data-ttu-id="7a097-132">若要启用 CLR，您必须具有 `ALTER SETTINGS` 服务器级别权限，`sysadmin` 和 `serveradmin` 固定服务器角色的成员隐式拥有该权限。</span><span class="sxs-lookup"><span data-stu-id="7a097-132">To enable CLR, you must have `ALTER SETTINGS` server level permission, which is implicitly held by members of the `sysadmin` and `serveradmin` fixed server roles.</span></span>  
  
-   <span data-ttu-id="7a097-133">必须在您使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例上安装 AdventureWorks 数据库。</span><span class="sxs-lookup"><span data-stu-id="7a097-133">The AdventureWorks database must be installed on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using.</span></span>  
  
-   <span data-ttu-id="7a097-134">如果你不是要使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的管理员，必须请管理员授予你 **CreateAssembly** 权限，才能完成安装。</span><span class="sxs-lookup"><span data-stu-id="7a097-134">If you are not an administrator for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using, you must have an administrator grant you **CreateAssembly**  permission to complete the installation.</span></span>  
  
## <a name="building-the-sample"></a><span data-ttu-id="7a097-135">生成示例</span><span class="sxs-lookup"><span data-stu-id="7a097-135">Building the Sample</span></span>  
  
#### <a name="create-and-run-the-sample-by-using-the-following-instructions"></a><span data-ttu-id="7a097-136">按照以下说明创建和运行该示例：</span><span class="sxs-lookup"><span data-stu-id="7a097-136">Create and run the sample by using the following instructions:</span></span>  
  
1.  <span data-ttu-id="7a097-137">打开 Visual Studio 或 .NET Framework 命令提示符。</span><span class="sxs-lookup"><span data-stu-id="7a097-137">Open a Visual Studio or .NET Framework command prompt.</span></span>  
  
2.  <span data-ttu-id="7a097-138">如有必要，为您的示例创建目录。</span><span class="sxs-lookup"><span data-stu-id="7a097-138">If necessary, create a directory for your sample.</span></span> <span data-ttu-id="7a097-139">对于此示例，我们将使用 C:\MySample。</span><span class="sxs-lookup"><span data-stu-id="7a097-139">For this example, we will use C:\MySample.</span></span>  
  
3.  <span data-ttu-id="7a097-140">在 c:\MySample 中，创建 `HelloWorld.vb`（用于 Visual Basic 示例）或 `HelloWorld.cs`（用于 C# 示例），并将相应的 Visual Basic 或 C# 示例代码（如下所示）复制到该文件中。</span><span class="sxs-lookup"><span data-stu-id="7a097-140">In c:\MySample, create `HelloWorld.vb` (for the Visual Basic sample) or `HelloWorld.cs` (for the C# sample) and copy the appropriate Visual Basic or C# sample code (below) into the file.</span></span>  
  
4.  <span data-ttu-id="7a097-141">在 c:\MySample 中，创建文件 `messages.resx` 并将示例代码复制到该文件中。</span><span class="sxs-lookup"><span data-stu-id="7a097-141">In c:\MySample, create the file `messages.resx` and copy the sample code into the file.</span></span>  
  
5.  <span data-ttu-id="7a097-142">在 c:\MySample 中，通过将 `messages.de.resx` 文件保存 `messages.resx` 为 `messages.de.resx` 更改行后的方式来创建文件</span><span class="sxs-lookup"><span data-stu-id="7a097-142">In c:\MySample, create the file `messages.de.resx` by saving the file `messages.resx` as `messages.de.resx` after changing the line</span></span>  
  
    -   `<value xml:space="preserve">Hello, World!</value>`  
  
    -   <span data-ttu-id="7a097-143">更改为 </span><span class="sxs-lookup"><span data-stu-id="7a097-143">To read</span></span>  
  
    -   `<value xml:space="preserve">Hallo Welt!</value>`  
  
6.  <span data-ttu-id="7a097-144">在 c:\MySample 中，通过将 `messages.es.resx` 文件保存 `messages.resx` 为 `messages.es.resx` 更改行后的方式来创建文件</span><span class="sxs-lookup"><span data-stu-id="7a097-144">In c:\MySample, create the file `messages.es.resx` by saving the file `messages.resx` as `messages.es.resx` after changing the line</span></span>  
  
    -   `<value xml:space="preserve">Hello, World!</value>`  
  
    -   <span data-ttu-id="7a097-145">更改为 </span><span class="sxs-lookup"><span data-stu-id="7a097-145">To read</span></span>  
  
    -   `<value xml:space="preserve">Hola a todos</value>`  
  
7.  <span data-ttu-id="7a097-146">在 c:\MySample 中，通过将 `messages.fr.resx` 文件保存 `messages.resx` 为 `messages.fr.resx` 更改行后的方式来创建文件</span><span class="sxs-lookup"><span data-stu-id="7a097-146">In c:\MySample, create the file `messages.fr.resx` by saving the file `messages.resx` as `messages.fr.resx` after changing the line</span></span>  
  
    -   `<value xml:space="preserve">Hello, World!</value>`  
  
    -   <span data-ttu-id="7a097-147">更改为 </span><span class="sxs-lookup"><span data-stu-id="7a097-147">To read</span></span>  
  
    -   `<value xml:space="preserve">BonjourÂ !</value>`  
  
8.  <span data-ttu-id="7a097-148">在 c:\MySample 中，通过将 `messages.fr-FR.resx` 文件保存 `messages.resx` 为 `messages.fr-FR.resx` 更改行后的方式来创建文件</span><span class="sxs-lookup"><span data-stu-id="7a097-148">In c:\MySample, create the file `messages.fr-FR.resx` by saving the file `messages.resx` as `messages.fr-FR.resx` after changing the line</span></span>  
  
    -   `<value xml:space="preserve">Hello, World!</value>`  
  
    -   <span data-ttu-id="7a097-149">更改为 </span><span class="sxs-lookup"><span data-stu-id="7a097-149">To read</span></span>  
  
    -   `<value xml:space="preserve">Bonjour de France!</value>`  
  
9. <span data-ttu-id="7a097-150">在 c:\MySample 中，通过将 `messages.it.resx` 文件保存 `messages.resx` 为 `messages.it.resx` 更改行后的方式来创建文件</span><span class="sxs-lookup"><span data-stu-id="7a097-150">In c:\MySample, create the file `messages.it.resx` by saving the file `messages.resx` as `messages.it.resx` after changing the line</span></span>  
  
    -   `<value xml:space="preserve">Hello, World!</value>`  
  
    -   <span data-ttu-id="7a097-151">更改为 </span><span class="sxs-lookup"><span data-stu-id="7a097-151">To read</span></span>  
  
    -   `<value xml:space="preserve">Buongiorno</value>`  
  
10. <span data-ttu-id="7a097-152">在 c:\MySample 中，通过将 `messages.ja.resx` 文件保存 `messages.resx` 为 `messages.ja.resx` 更改行后的方式来创建文件</span><span class="sxs-lookup"><span data-stu-id="7a097-152">In c:\MySample, create the file `messages.ja.resx` by saving the file `messages.resx` as `messages.ja.resx` after changing the line</span></span>  
  
    -   `<value xml:space="preserve">Hello, World!</value>`  
  
    -   <span data-ttu-id="7a097-153">更改为 </span><span class="sxs-lookup"><span data-stu-id="7a097-153">To read</span></span>  
  
    -   <span data-ttu-id="7a097-154">`<value xml:space="preserve">` `ã"ã‚"ã«ã¡ã¯</value>`</span><span class="sxs-lookup"><span data-stu-id="7a097-154">`<value xml:space="preserve">` `ã"ã‚"ã«ã¡ã¯</value>`</span></span>  
  
11. <span data-ttu-id="7a097-155">在 c:\MySample 中，创建文件 `build.com` 并将示例代码复制到该文件中。</span><span class="sxs-lookup"><span data-stu-id="7a097-155">In c:\MySample, create the file `build.com` and copy the sample code into the file</span></span>  
  
12. <span data-ttu-id="7a097-156">通过在命令提示符处执行文件生成操作来生成附属程序集。</span><span class="sxs-lookup"><span data-stu-id="7a097-156">Build the satellite assembles by executing the file build at the command prompt.</span></span>  
  
13. <span data-ttu-id="7a097-157">通过在命令行提示符处执行以下命令之一来编译示例代码：</span><span class="sxs-lookup"><span data-stu-id="7a097-157">Compile the sample code from the command line prompt by executing the one of the following:</span></span>  
  
    -   `Vbc /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Data.dll,C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.dll,C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Xml.dll /out:HelloWorldReady.dll /target:library HelloWorld.vb`  
  
    -   `Csc /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Data.dll /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.dll /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.XML.dll /out:HelloWorldReady.dll /target:library Hello.csCopy the tsql installation code into a file and save it as Install.sql in the sample directory.`  
  
14. <span data-ttu-id="7a097-158">如果示例安装在 `C:\MySample\` 之外的目录中，请按说明编辑文件 `Install.sql` 以指向该位置。</span><span class="sxs-lookup"><span data-stu-id="7a097-158">If the sample is installed in a directory other then `C:\MySample\`, edit the file `Install.sql` as indicated to point to that location.</span></span>  
  
15. <span data-ttu-id="7a097-159">通过执行以下命令部署程序集和存储过程：</span><span class="sxs-lookup"><span data-stu-id="7a097-159">Deploy the assembly and stored procedure by executing</span></span>  
  
    -   `sqlcmd -E -I -i install.sql`  
  
16. <span data-ttu-id="7a097-160">将 [!INCLUDE[tsql](../../includes/tsql-md.md)] 测试命令脚本复制到文件中，并将其另存为 `test.sql` 示例目录中的。</span><span class="sxs-lookup"><span data-stu-id="7a097-160">Copy [!INCLUDE[tsql](../../includes/tsql-md.md)] test command script into a file and save it as `test.sql` in the sample directory.</span></span>  
  
17. <span data-ttu-id="7a097-161">使用以下命令执行测试脚本：</span><span class="sxs-lookup"><span data-stu-id="7a097-161">Execute the test script with the following command</span></span>  
  
    -   `sqlcmd -E -I -i test.sql`  
  
18. <span data-ttu-id="7a097-162">将 [!INCLUDE[tsql](../../includes/tsql-md.md)] 清除脚本复制到一个文件中，并在示例目录中将其另存为 `cleanup.sql`。</span><span class="sxs-lookup"><span data-stu-id="7a097-162">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] cleanup script into a file and save it as `cleanup.sql` in the sample directory.</span></span>  
  
19. <span data-ttu-id="7a097-163">使用以下命令执行该脚本：</span><span class="sxs-lookup"><span data-stu-id="7a097-163">Execute the script with the  following command</span></span>  
  
    -   `sqlcmd -E -I -i cleanup.sql`  
  
## <a name="sample-code"></a><span data-ttu-id="7a097-164">代码示例</span><span class="sxs-lookup"><span data-stu-id="7a097-164">Sample Code</span></span>  
 <span data-ttu-id="7a097-165">下面是此示例的代码列表。</span><span class="sxs-lookup"><span data-stu-id="7a097-165">The following are the code listings for this sample.</span></span>  
  
 <span data-ttu-id="7a097-166">C#</span><span class="sxs-lookup"><span data-stu-id="7a097-166">C#</span></span>  
  
```  
using System;  
using System.Data;  
using System.Data.Sql;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
using System.Globalization;  
using System.Threading;  
using System.Resources;  
using System.Reflection;  
using System.Runtime.CompilerServices;  
  
[assembly: System.Resources.NeutralResourcesLanguage("", System.Resources.UltimateResourceFallbackLocation.Satellite)]  
[assembly: System.Security.Permissions.SecurityPermissionAttribute(System.Security.Permissions.SecurityAction.RequestMinimum)]  
[assembly: System.Runtime.ConstrainedExecution.ReliabilityContract(System.Runtime.ConstrainedExecution.Consistency.MayCorruptInstance, System.Runtime.ConstrainedExecution.Cer.None)]  
  
    public sealed partial class StoredProcedures  
    {  
        private StoredProcedures()  
        {  
        }  
  
        [System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1021:AvoidOutParameters"), Microsoft.SqlServer.Server.SqlProcedure]  
        public static void HelloWorldReady(string culture, out string greeting)  
        {  
ResourceManager rm   
= new ResourceManager("Messages",   
Assembly.GetExecutingAssembly());  
  
string message = rm.GetString("HelloWorld", CultureInfo.GetCultureInfo(culture));  
  
            Microsoft.SqlServer.Server.SqlMetaData columnInfo  
                = new Microsoft.SqlServer.Server.SqlMetaData("Column1", SqlDbType.NVarChar, 24);  
            SqlDataRecord greetingRecord  
                = new SqlDataRecord(new Microsoft.SqlServer.Server.SqlMetaData[] { columnInfo });  
            greetingRecord.SetString(0, message);  
            SqlContext.Pipe.Send(greetingRecord);  
            greeting = message;  
        }  
    }  
  
```  
  
 <span data-ttu-id="7a097-167">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7a097-167">Visual Basic</span></span>  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Globalization  
Imports System.Resources  
Imports System.Reflection  
Imports System.Runtime.InteropServices  
<Assembly: AssemblyVersion("1.0.*")>   
<Assembly: System.Runtime.InteropServices.ComVisible(False)>   
<Assembly: System.CLSCompliant(True)>   
<Assembly: System.Resources.NeutralResourcesLanguage("", System.Resources.UltimateResourceFallbackLocation.Satellite)>   
<Assembly: System.Security.Permissions.SecurityPermissionAttribute(System.Security.Permissions.SecurityAction.RequestMinimum)>   
<Assembly: System.Runtime.ConstrainedExecution.ReliabilityContract(System.Runtime.ConstrainedExecution.Consistency.WillNotCorruptState, Runtime.ConstrainedExecution.Cer.None)>   
  
Partial Public NotInheritable Class StoredProcedures  
    Private Sub New()  
    End Sub  
    <Microsoft.SqlServer.Server.SqlProcedure()> _  
    Public Shared Sub HelloWorldReady(ByVal culture As String, ByRef greeting As String)  
        Dim rm As New ResourceManager("Messages", Assembly.GetExecutingAssembly())  
        Dim message As String = rm.GetString("HelloWorld", CultureInfo.GetCultureInfo(culture))  
        Dim columnInfo As New Microsoft.SqlServer.Server.SqlMetaData("Column1", _  
            SqlDbType.NVarChar, 24)  
        Dim greetingRecord As New SqlDataRecord(New  _  
            Microsoft.SqlServer.Server.SqlMetaData() {columnInfo})  
        greetingRecord.SetString(0, message)  
        SqlContext.Pipe.Send(greetingRecord)  
        greeting = message  
    End Sub  
End Class  
  
```  
  
 <span data-ttu-id="7a097-168">这是用于生成附属程序集的 `build.com`。</span><span class="sxs-lookup"><span data-stu-id="7a097-168">This is `build.com`, which builds the satellite assemblies.</span></span>  
  
```  
resgen Messages.resx  
resgen Messages.de.resx  
resgen Messages.es.resx  
resgen Messages.fr.resx  
resgen Messages.fr-Fr.resx  
resgen Messages.it.resx  
resgen Messages.ja.resx  
if not exist de/ mkdir de  
if not exist es/ mkdir es  
if not exist fr/ mkdir fr  
if not exist fr-FR/ mkdir fr-FR  
if not exist it/ mkdir it  
if not exist ja/ mkdir ja  
al /t:lib /culture:de /embed:Messages.de.resources /out:de\HelloWorldReady.resources.dll  
al /t:lib /culture:es /embed:Messages.es.resources /out:es\HelloWorldReady.resources.dll  
al /t:lib /culture:fr /embed:Messages.fr.resources /out:fr\HelloWorldReady.resources.dll  
al /t:lib /culture:fr-FR /embed:Messages.fr-FR.resources /out:fr-FR\HelloWorldReady.resources.dll  
al /t:lib /culture:it /embed:Messages.it.resources /out:it\HelloWorldReady.resources.dll  
al /t:lib /culture:ja /embed:Messages.ja.resources /out:ja\HelloWorldReady.resources.dll  
al /t:lib /culture:"" /embed:Messages.resources /out:HelloWorldReady.resources.dll  
```  
  
 <span data-ttu-id="7a097-169">这是 [!INCLUDE[tsql](../../includes/tsql-md.md)] 安装脚本 (`Install.sql`)，该脚本在数据库中部署程序集并创建存储过程。</span><span class="sxs-lookup"><span data-stu-id="7a097-169">This is the [!INCLUDE[tsql](../../includes/tsql-md.md)] installation script (`Install.sql`), which deploys the assemblies and creates the stored procedure within the database.</span></span>  
  
```  
USE AdventureWorks  
GO  
  
-- Drop existing sproc and assembly if any.  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE [name] = 'usp_HelloWorldReady')  
DROP PROCEDURE usp_HelloWorldReady;  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady')  
DROP ASSEMBLY HelloWorldReady;  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.neutral')  
DROP ASSEMBLY [HelloWorldReady.resources.neutral]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.de')  
DROP ASSEMBLY [HelloWorldReady.resources.de]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.es')  
DROP ASSEMBLY [HelloWorldReady.resources.es]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.fr')  
DROP ASSEMBLY [HelloWorldReady.resources.fr]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.fr-FR')  
DROP ASSEMBLY [HelloWorldReady.resources.fr-FR]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.it')  
DROP ASSEMBLY [HelloWorldReady.resources.it]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.ja')  
DROP ASSEMBLY [HelloWorldReady.resources.ja]  
GO  
  
DECLARE @SamplesPath nvarchar(1024)  
-- You may need to modify the value of this variable if you have installed the sample someplace other than the default location.  
Set @SamplesPath = N'C:\MySample\'  
  
-- Add the assembly and CLR integration based stored procedure  
  
CREATE ASSEMBLY HelloWorldReady  
FROM @SamplesPath + 'HelloWorldReady.dll'  
WITH permission_set = Safe;  
  
CREATE ASSEMBLY [HelloWorldReady.resources.neutral]  
FROM @SamplesPath + 'HelloWorldReady.resources.dll'  
WITH permission_set = Safe;   
  
CREATE ASSEMBLY [HelloWorldReady.resources.de]  
FROM @SamplesPath + '\de\HelloWorldReady.resources.dll'  
WITH permission_set = Safe;  
  
CREATE ASSEMBLY [HelloWorldReady.resources.es]  
FROM @SamplesPath + '\es\HelloWorldReady.resources.dll'  
WITH permission_set = Safe;  
  
CREATE ASSEMBLY [HelloWorldReady.resources.fr]  
FROM @SamplesPath + '\fr\HelloWorldReady.resources.dll'  
WITH permission_set = Safe;  
  
CREATE ASSEMBLY [HelloWorldReady.resources.fr-FR]  
FROM @SamplesPath + '\fr-FR\HelloWorldReady.resources.dll'  
WITH permission_set = Safe;  
  
CREATE ASSEMBLY [HelloWorldReady.resources.it]  
FROM @SamplesPath + '\it\HelloWorldReady.resources.dll'  
WITH permission_set = Safe;  
  
CREATE ASSEMBLY [HelloWorldReady.resources.ja]  
FROM @SamplesPath + '\ja\HelloWorldReady.resources.dll'  
WITH permission_set = Safe;  
GO  
  
CREATE PROCEDURE usp_HelloWorldReady  
(  
@Culture NVarchar(12),  
@Greeting NVarchar(24) OUTPUT  
)  
AS EXTERNAL NAME HelloWorldReady.StoredProcedures.HelloWorldReady;  
GO  
  
USE master;  
GO  
```  
  
 <span data-ttu-id="7a097-170">这是 `test.sql`，该脚本通过对各个区域设置执行函数来测试该示例。</span><span class="sxs-lookup"><span data-stu-id="7a097-170">This is `test.sql`, which tests the sample by executing the functions on each locale.</span></span>  
  
```  
USE AdventureWorks  
GO  
  
DECLARE @GreetingDe nvarchar(24);  
DECLARE @GreetingDe_CH nvarchar(24);  
DECLARE @GreetingEn nvarchar(24);  
DECLARE @GreetingEs nvarchar(24);  
DECLARE @GreetingFr nvarchar(24);  
DECLARE @GreetingFr_FR nvarchar(24);  
DECLARE @GreetingIt nvarchar(24);  
DECLARE @GreetingJa nvarchar(24);  
  
--German as spoken anywhere in the world (the neutral German culture)  
EXEC usp_HelloWorldReady 'de', @GreetingDe OUTPUT;  
--German as spoken in Switzerland.  Because we don't have a specific assembly  
--for this case, the .NET Framework will automatically fall back to the neutral German culture DLL.  
EXEC usp_HelloWorldReady 'de-CH', @GreetingDe_CH OUTPUT;  
EXEC usp_HelloWorldReady 'en', @GreetingEn OUTPUT;  
EXEC usp_HelloWorldReady 'es', @GreetingEs OUTPUT;  
--French as spoken anywhere in the world (the neutral French culture)  
EXEC usp_HelloWorldReady 'fr', @GreetingFr OUTPUT  
--French as spoken in France.  Since we do have a specific assembly for this case, a specific   
--greeting is provided from that DLL.  The neutral French culture DLL is not used in this case.  
EXEC usp_HelloWorldReady 'fr-FR', @GreetingFr_FR OUTPUT  
EXEC usp_HelloWorldReady 'it', @GreetingIt OUTPUT;  
EXEC usp_HelloWorldReady 'ja', @GreetingJa OUTPUT;  
  
SELECT @GreetingDe AS OUTPUT_PARAMETER_DE;  
SELECT @GreetingDe_CH AS OUTPUT_PARAMETER_De_CH;  
SELECT @GreetingEn AS OUTPUT_PARAMETER_EN;  
SELECT @GreetingEs AS OUTPUT_PARAMETER_ES;  
SELECT @GreetingFr AS OUTPUT_PARAMETER_FR;  
SELECT @GreetingFr_FR AS OUTPUT_PARAMETER_Fr_FR;  
SELECT @GreetingIt AS OUTPUT_PARAMETER_IT;  
SELECT @GreetingJa AS OUTPUT_PARAMETER_JA;  
  
GO  
```  
  
 <span data-ttu-id="7a097-171">下面的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 从数据库中删除程序集和存储过程。</span><span class="sxs-lookup"><span data-stu-id="7a097-171">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] removes the assemblies and stored procedure from the database.</span></span>  
  
```  
USE AdventureWorks;  
GO  
  
-- Drop existing sproc and assembly if any.  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE [name] = 'usp_HelloWorldReady')  
DROP PROCEDURE usp_HelloWorldReady;  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady')  
DROP ASSEMBLY HelloWorldReady;  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.neutral')  
DROP ASSEMBLY [HelloWorldReady.resources.neutral]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.de')  
DROP ASSEMBLY [HelloWorldReady.resources.de]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.es')  
DROP ASSEMBLY [HelloWorldReady.resources.es]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.fr')  
DROP ASSEMBLY [HelloWorldReady.resources.fr]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.fr-FR')  
DROP ASSEMBLY [HelloWorldReady.resources.fr-FR]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.it')  
DROP ASSEMBLY [HelloWorldReady.resources.it]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.ja')  
DROP ASSEMBLY [HelloWorldReady.resources.ja]  
GO  
  
USE master;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="7a097-172">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7a097-172">See Also</span></span>  
 [<span data-ttu-id="7a097-173">公共语言运行时 (CLR) 集成的使用方案和示例</span><span class="sxs-lookup"><span data-stu-id="7a097-173">Usage Scenarios and Examples for Common Language Runtime &#40;CLR&#41; Integration</span></span>](../../../2014/database-engine/dev-guide/usage-scenarios-and-examples-for-common-language-runtime-clr-integration.md)  
  
  
