---
title: Hello World 示例 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
ms.assetid: fed6c358-f5ee-4d4c-9ad6-089778383ba7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0d5616c1d4ef6428a011c8e36be3757931039c9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694090"
---
# <a name="hello-world-sample"></a><span data-ttu-id="78cda-102">Hello World 示例</span><span class="sxs-lookup"><span data-stu-id="78cda-102">Hello World Sample</span></span>
  <span data-ttu-id="78cda-103">Hello World 示例说明了创建、部署和测试基于公共语言运行时 (CLR) 集成的简单存储过程所涉及的基本操作。</span><span class="sxs-lookup"><span data-stu-id="78cda-103">The Hello World sample demonstrates the basic operations that are involved in creating, deploying, and testing a simple common language runtime (CLR) integration-based stored procedure.</span></span> <span data-ttu-id="78cda-104">此示例还说明了如何通过记录返回由存储过程动态构建并返回到调用方的数据。</span><span class="sxs-lookup"><span data-stu-id="78cda-104">This sample also demonstrates how to return data through a record, which is dynamically constructed by the stored procedure and returned to the caller.</span></span>  
  
 <span data-ttu-id="78cda-105">该 `HelloWorld` 存储过程返回字符串 "Hello world！"</span><span class="sxs-lookup"><span data-stu-id="78cda-105">The `HelloWorld` stored procedure returns the string "Hello world!"</span></span> <span data-ttu-id="78cda-106">在包含一行的结果集中。</span><span class="sxs-lookup"><span data-stu-id="78cda-106">in a result set consisting of one row.</span></span> <span data-ttu-id="78cda-107">此示例演示了[SqlMetaData](https://go.microsoft.com/fwlink/?LinkID=193572)、 [SqlDataRecord 和](https://go.microsoft.com/fwlink/?LinkID=193573)类的一些[用途。）](https://go.microsoft.com/fwlink/?LinkID=193571)的一些用途是使用类。</span><span class="sxs-lookup"><span data-stu-id="78cda-107">This example illustrates some uses for the classes [Microsoft.SqlServer.Server.SqlMetaData](https://go.microsoft.com/fwlink/?LinkID=193572), [Microsoft.SqlServer.Server.SqlDataRecord](https://go.microsoft.com/fwlink/?LinkID=193573) and [Microsoft.SqlServer.Server.Pipe](https://go.microsoft.com/fwlink/?LinkID=193571).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="78cda-108">先决条件</span><span class="sxs-lookup"><span data-stu-id="78cda-108">Prerequisites</span></span>  
 <span data-ttu-id="78cda-109">若要创建和运行此项目，必须安装下列软件：</span><span class="sxs-lookup"><span data-stu-id="78cda-109">To create and run this project the following the following software must be installed:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="78cda-110">或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express。</span><span class="sxs-lookup"><span data-stu-id="78cda-110">or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express.</span></span> <span data-ttu-id="78cda-111">可以从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express 文档和示例[网站](https://www.microsoft.com/sql-server/sql-server-editions-express)免费获取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express</span><span class="sxs-lookup"><span data-stu-id="78cda-111">You can obtain [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express free of charge from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express Documentation and Samples [Web site](https://www.microsoft.com/sql-server/sql-server-editions-express)</span></span>  
  
-   <span data-ttu-id="78cda-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]开发人员[网站](https://go.microsoft.com/fwlink/?linkid=62796)提供的 AdventureWorks 数据库</span><span class="sxs-lookup"><span data-stu-id="78cda-112">The AdventureWorks database that is available at the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Developer [Web site](https://go.microsoft.com/fwlink/?linkid=62796)</span></span>  
  
-   <span data-ttu-id="78cda-113">.NET Framework SDK 2.0 或更高版本，或 Microsoft Visual Studio 2005 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="78cda-113">.NET Framework SDK 2.0 or later or Microsoft Visual Studio 2005 or later.</span></span> <span data-ttu-id="78cda-114">您可以免费获取 .NET Framework SDK。</span><span class="sxs-lookup"><span data-stu-id="78cda-114">You can obtain .NET Framework SDK free of charge.</span></span>  
  
-   <span data-ttu-id="78cda-115">此外，还必须满足以下条件：</span><span class="sxs-lookup"><span data-stu-id="78cda-115">In addition, the following conditions must be met:</span></span>  
  
-   <span data-ttu-id="78cda-116">使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例必须已启用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="78cda-116">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using must have CLR integration enabled.</span></span>  
  
-   <span data-ttu-id="78cda-117">若要启用 CLR 集成，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="78cda-117">In order to enable CLR integration, perform the following steps:</span></span>  
  
    #### <a name="enabling-clr-integration"></a><span data-ttu-id="78cda-118">启用 CLR 集成</span><span class="sxs-lookup"><span data-stu-id="78cda-118">Enabling CLR Integration</span></span>  
  
    -   <span data-ttu-id="78cda-119">执行以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 命令：</span><span class="sxs-lookup"><span data-stu-id="78cda-119">Execute the following [!INCLUDE[tsql](../../includes/tsql-md.md)] commands:</span></span>  
  
     `sp_configure 'clr enabled', 1`  
  
     `GO`  
  
     `RECONFIGURE`  
  
     `GO`  
  
    > [!NOTE]  
    >  <span data-ttu-id="78cda-120">若要启用 CLR，您必须具有 `ALTER SETTINGS` 服务器级别权限，`sysadmin` 和 `serveradmin` 固定服务器角色的成员隐式拥有该权限。</span><span class="sxs-lookup"><span data-stu-id="78cda-120">To enable CLR, you must have `ALTER SETTINGS` server level permission, which is implicitly held by members of the `sysadmin` and `serveradmin` fixed server roles.</span></span>  
  
-   <span data-ttu-id="78cda-121">必须在您使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例上安装 AdventureWorks 数据库。</span><span class="sxs-lookup"><span data-stu-id="78cda-121">The AdventureWorks database must be installed on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using.</span></span>  
  
-   <span data-ttu-id="78cda-122">如果您不是所使用的实例的管理员 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，则必须让管理员授予您**CreateAssembly**权限，才能完成安装。</span><span class="sxs-lookup"><span data-stu-id="78cda-122">If you are not an administrator for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using, you must have an administrator grant you **CreateAssembly** permission to complete the installation.</span></span>  
  
## <a name="building-the-sample"></a><span data-ttu-id="78cda-123">生成示例</span><span class="sxs-lookup"><span data-stu-id="78cda-123">Building the Sample</span></span>  
  
#### <a name="create-and-run-the-sample-by-using-the-following-instructions"></a><span data-ttu-id="78cda-124">按照以下说明创建和运行该示例：</span><span class="sxs-lookup"><span data-stu-id="78cda-124">Create and run the sample by using the following instructions:</span></span>  
  
1.  <span data-ttu-id="78cda-125">打开 Visual Studio 或 .NET Framework 命令提示符。</span><span class="sxs-lookup"><span data-stu-id="78cda-125">Open a Visual Studio or .NET Framework command prompt.</span></span>  
  
2.  <span data-ttu-id="78cda-126">如有必要，为您的示例创建目录。</span><span class="sxs-lookup"><span data-stu-id="78cda-126">If necessary, create a directory for your sample.</span></span> <span data-ttu-id="78cda-127">对于此示例，我们将使用 C:\MySample。</span><span class="sxs-lookup"><span data-stu-id="78cda-127">For this example, we will use C:\MySample.</span></span>  
  
3.  <span data-ttu-id="78cda-128">在 c:\MySample 中，创建 `HelloWorld.vb`（用于 Visual Basic 示例）或 `HelloWorld.cs`（用于 C# 示例），并将相应的 Visual Basic 或 C# 示例代码（如下所示）复制到该文件中。</span><span class="sxs-lookup"><span data-stu-id="78cda-128">In c:\MySample, create `HelloWorld.vb` (for the Visual Basic sample) or `HelloWorld.cs` (for the C# sample) and copy the appropriate Visual Basic or C# sample code (below) into the file.</span></span>  
  
4.  <span data-ttu-id="78cda-129">从命令行提示符执行以下代码之一（具体取决于所选的语言)，对示例代码进行编译。</span><span class="sxs-lookup"><span data-stu-id="78cda-129">Compile the sample code from the command line prompt by executing one of the following, depending on your choice of language.</span></span>  
  
    -   `vbc C:HelloWorld.vb /target:library`  
  
    -   `csc /target:library HelloWorld.cs`  
  
5.  <span data-ttu-id="78cda-130">将 [!INCLUDE[tsql](../../includes/tsql-md.md)] 安装代码复制到一个文件中，并在示例目录中将其另存为 `Install.sql`。</span><span class="sxs-lookup"><span data-stu-id="78cda-130">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] installation code into a file and save it as `Install.sql` in the sample directory.</span></span>  
  
6.  <span data-ttu-id="78cda-131">通过执行以下命令部署程序集和存储过程：</span><span class="sxs-lookup"><span data-stu-id="78cda-131">Deploy the assembly and stored procedure by executing</span></span>  
  
    -   `sqlcmd -E -I -i install.sql -v root = "C:\MySample\"`  
  
7.  <span data-ttu-id="78cda-132">将 [!INCLUDE[tsql](../../includes/tsql-md.md)] 测试命令脚本复制到文件中，并将其另存为 `test.sql` 示例目录中的。</span><span class="sxs-lookup"><span data-stu-id="78cda-132">Copy [!INCLUDE[tsql](../../includes/tsql-md.md)] test command script into a file and save it as `test.sql` in the sample directory.</span></span>  
  
8.  <span data-ttu-id="78cda-133">使用以下命令执行测试脚本：</span><span class="sxs-lookup"><span data-stu-id="78cda-133">Execute the test script with the following command</span></span>  
  
    -   `sqlcmd -E -I -i test.sql`  
  
9. <span data-ttu-id="78cda-134">将 [!INCLUDE[tsql](../../includes/tsql-md.md)] 清除脚本复制到一个文件中，并在示例目录中将其另存为 `cleanup.sql`。</span><span class="sxs-lookup"><span data-stu-id="78cda-134">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] cleanup script into a file and save it as `cleanup.sql` in the sample directory.</span></span>  
  
10. <span data-ttu-id="78cda-135">使用以下命令执行该脚本：</span><span class="sxs-lookup"><span data-stu-id="78cda-135">Execute the script with the  following command</span></span>  
  
    -   `sqlcmd -E -I -i cleanup.sql`  
  
## <a name="sample-code"></a><span data-ttu-id="78cda-136">代码示例</span><span class="sxs-lookup"><span data-stu-id="78cda-136">Sample Code</span></span>  
 <span data-ttu-id="78cda-137">下面是此示例的代码列表。</span><span class="sxs-lookup"><span data-stu-id="78cda-137">The following are the code listings for this sample.</span></span>  
  
 <span data-ttu-id="78cda-138">C#</span><span class="sxs-lookup"><span data-stu-id="78cda-138">C#</span></span>  
  
```  
using System;  
using System.Data;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
public partial class StoredProcedures  
{  
    [Microsoft.SqlServer.Server.SqlProcedure]  
    public static void HelloWorld()  
    {  
        Microsoft.SqlServer.Server.SqlMetaData columnInfo  
                = new Microsoft.SqlServer.Server.SqlMetaData("Column1", SqlDbType.NVarChar, 12);  
        SqlDataRecord greetingRecord  
            = new SqlDataRecord(new Microsoft.SqlServer.Server.SqlMetaData[] { columnInfo });  
        greetingRecord.SetString(0, "Hello world!");  
        SqlContext.Pipe.Send(greetingRecord);  
    }  
};  
  
```  
  
 <span data-ttu-id="78cda-139">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="78cda-139">Visual Basic</span></span>  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
  
Partial Public NotInheritable Class StoredProcedures  
    <Microsoft.SqlServer.Server.SqlProcedure()> _  
    Public Shared Sub HelloWorld()  
        Dim columnInfo As New Microsoft.SqlServer.Server.SqlMetaData("Column1", _  
            SqlDbType.NVarChar, 12)  
        Dim greetingRecord As New SqlDataRecord(New  _  
            Microsoft.SqlServer.Server.SqlMetaData() {columnInfo})  
        greetingRecord.SetString(0, "Hello World!")  
        SqlContext.Pipe.Send(greetingRecord)  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="78cda-140">这是 [!INCLUDE[tsql](../../includes/tsql-md.md)] 安装脚本 (`Install.sql`)，该脚本在数据库中部署程序集并创建存储过程。</span><span class="sxs-lookup"><span data-stu-id="78cda-140">This is the [!INCLUDE[tsql](../../includes/tsql-md.md)] installation script (`Install.sql`), which deploys the assembly and creates the stored procedure in the database.</span></span>  
  
```  
USE AdventureWorks  
GO  
IF EXISTS (SELECT * FROM sys.procedures WHERE [name] = 'usp_HelloWorld')  
DROP PROCEDURE usp_HelloWorld;  
GO  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorld')  
DROP ASSEMBLY HelloWorld;  
GO  
DECLARE @SamplesPath nvarchar(1024)  
set @SamplesPath = '$(root)'  
CREATE ASSEMBLY HelloWorld   
FROM @SamplesPath + 'HelloWorld.dll'  
WITH permission_set = Safe;  
GO  
  
CREATE PROCEDURE usp_HelloWorld  
--(  
--    @Greeting nvarchar(12) OUTPUT  
--)  
AS EXTERNAL NAME HelloWorld.[StoredProcedures].HelloWorld;  
GO  
```  
  
 <span data-ttu-id="78cda-141">这是 `test.sql`，该脚本通过执行存储过程测试该示例。</span><span class="sxs-lookup"><span data-stu-id="78cda-141">This is `test.sql`, which tests the sample by executing the stored procedure.</span></span>  
  
```  
use AdventureWorks  
go  
execute usp_HelloWorld  
  
USE AdventureWorks;  
GO  
IF EXISTS (SELECT * FROM sys.procedures WHERE [name] = 'usp_HelloWorld')  
DROP PROCEDURE usp_HelloWorld;  
GO  
```  
  
 <span data-ttu-id="78cda-142">下面的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 从数据库中删除程序集和存储过程。</span><span class="sxs-lookup"><span data-stu-id="78cda-142">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] removes the assembly and stored procedure from the database.</span></span>  
  
```  
USE AdventureWorks  
GO  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE [name] = 'usp_HelloWorld')  
DROP PROCEDURE usp_HelloWorld;  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorld')  
DROP ASSEMBLY HelloWorld;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="78cda-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="78cda-143">See Also</span></span>  
 [<span data-ttu-id="78cda-144">公共语言运行时 (CLR) 集成的使用方案和示例</span><span class="sxs-lookup"><span data-stu-id="78cda-144">Usage Scenarios and Examples for Common Language Runtime &#40;CLR&#41; Integration</span></span>](../../../2014/database-engine/dev-guide/usage-scenarios-and-examples-for-common-language-runtime-clr-integration.md)  
  
  
