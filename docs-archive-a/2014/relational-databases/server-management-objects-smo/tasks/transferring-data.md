---
title: 传输数据 |Microsoft Docs
ms.custom: ''
ms.date: 10/20/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- data transfers [SMO]
- transferring data
ms.assetid: eea255c3-8251-40f0-973b-fe4ef6cb5261
author: stevestein
ms.author: sstein
ms.openlocfilehash: dcbcdc1e61c2d18f6a98f797385145f04dfecc7c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689818"
---
# <a name="transferring-data"></a><span data-ttu-id="b3de1-102">传输数据</span><span class="sxs-lookup"><span data-stu-id="b3de1-102">Transferring Data</span></span>
  <span data-ttu-id="b3de1-103"> 类是一个实用工具类，它提供用于传输对象和数据的工具。</span><span class="sxs-lookup"><span data-stu-id="b3de1-103">The <xref:Microsoft.SqlServer.Management.Smo.Transfer> class is a utility class that provides tools to transfer objects and data.</span></span>  
  
 <span data-ttu-id="b3de1-104">通过在目标服务器上执行生成的脚本可以传输数据库架构中的对象。</span><span class="sxs-lookup"><span data-stu-id="b3de1-104">Objects in the database schema are transferred by executing a generated script on the target server.</span></span> <span data-ttu-id="b3de1-105">使用动态创建的 DTS 包传输 <xref:Microsoft.SqlServer.Management.Smo.Table> 数据。</span><span class="sxs-lookup"><span data-stu-id="b3de1-105"><xref:Microsoft.SqlServer.Management.Smo.Table> data is transferred with a dynamically created DTS package.</span></span>  
  
 <span data-ttu-id="b3de1-106"> 对象除包含 DMO 中的  对象的所有功能之外，还包含其他  功能。</span><span class="sxs-lookup"><span data-stu-id="b3de1-106">The <xref:Microsoft.SqlServer.Management.Smo.Transfer> object contains all the functionality of the <xref:Microsoft.SqlServer.Management.Smo.Transfer> objects in DMO and additional [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] functionality.</span></span> <span data-ttu-id="b3de1-107">但是，在中的 SMO 中 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] ， <xref:Microsoft.SqlServer.Management.Smo.Transfer> 对象使用[SQLBulkCopy](https://msdn.microsoft.com/library/system.data.sqlclient.sqlbulkcopy\(v=VS.90\).aspx) API 来传输数据。</span><span class="sxs-lookup"><span data-stu-id="b3de1-107">However, in SMO in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], the <xref:Microsoft.SqlServer.Management.Smo.Transfer> object uses the [SQLBulkCopy](https://msdn.microsoft.com/library/system.data.sqlclient.sqlbulkcopy\(v=VS.90\).aspx) API to transfer data.</span></span> <span data-ttu-id="b3de1-108">同样，用于执行数据传输的方法和属性驻留在 <xref:Microsoft.SqlServer.Management.Smo.Transfer> 对象中，而不是 <xref:Microsoft.SqlServer.Management.Smo.Database> 对象中。</span><span class="sxs-lookup"><span data-stu-id="b3de1-108">Also, the methods and properties that are used to perform data transfers reside on the <xref:Microsoft.SqlServer.Management.Smo.Transfer> object instead of the <xref:Microsoft.SqlServer.Management.Smo.Database> object.</span></span> <span data-ttu-id="b3de1-109">将功能从实例类移到实用工具类符合轻型对象模型，因为仅在需要特定任务的代码时才加载它们。</span><span class="sxs-lookup"><span data-stu-id="b3de1-109">Moving functionality from the instance classes to utility classes is consistent with a lighter object model because the code for specific tasks is loaded only when it is required.</span></span>  
  
 <span data-ttu-id="b3de1-110"> 对象不支持向  低于  的实例版本的目标数据库传输数据。</span><span class="sxs-lookup"><span data-stu-id="b3de1-110">The <xref:Microsoft.SqlServer.Management.Smo.Transfer> object does not support data transfers to a target database that has a <xref:Microsoft.SqlServer.Management.Smo.Database.CompatibilityLevel%2A> less than the version of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3de1-111">示例</span><span class="sxs-lookup"><span data-stu-id="b3de1-111">Example</span></span>  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="transferring-schema-and-data-from-one-database-to-another-in-visual-basic"></a><span data-ttu-id="b3de1-112">在 Visual Basic 中于数据库之间传输架构和数据</span><span class="sxs-lookup"><span data-stu-id="b3de1-112">Transferring Schema and Data from One Database to Another in Visual Basic</span></span>  
 <span data-ttu-id="b3de1-113">此代码实例说明如何使用 <xref:Microsoft.SqlServer.Management.Smo.Transfer> 对象在数据库之间传输架构和数据。</span><span class="sxs-lookup"><span data-stu-id="b3de1-113">This code example shows how to transfer schema and data from one database to another using the <xref:Microsoft.SqlServer.Management.Smo.Transfer> object.</span></span>  
  
```vb
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Reference the AdventureWorks2012 2008R2 database
Dim db As Database
db = srv.Databases("AdventureWorks2012")
'Create a new database that is to be destination database.
Dim dbCopy As Database
dbCopy = New Database(srv, "AdventureWorks2012Copy")
dbCopy.Create()
'Define a Transfer object and set the required options and properties.
Dim xfr As Transfer
xfr = New Transfer(db)
xfr.CopyAllTables = True
xfr.Options.WithDependencies = True
xfr.Options.ContinueScriptingOnError = True
xfr.DestinationDatabase = "AdventureWorks2012Copy"
xfr.DestinationServer = srv.Name
xfr.DestinationLoginSecure = True
xfr.CopySchema = True
'Script the transfer. Alternatively perform immediate data transfer with TransferData method.
xfr.ScriptTransfer()
```
  
## <a name="transferring-schema-and-data-from-one-database-to-another-in-visual-c"></a><span data-ttu-id="b3de1-114">在 Visual C# 中于数据库之间传输架构和数据</span><span class="sxs-lookup"><span data-stu-id="b3de1-114">Transferring Schema and Data from One Database to Another in Visual C#</span></span>  
 <span data-ttu-id="b3de1-115">此代码实例说明如何使用 <xref:Microsoft.SqlServer.Management.Smo.Transfer> 对象在数据库之间传输架构和数据。</span><span class="sxs-lookup"><span data-stu-id="b3de1-115">This code example shows how to transfer schema and data from one database to another using the <xref:Microsoft.SqlServer.Management.Smo.Transfer> object.</span></span>  
  
```csharp
{  
            Server srv;  
            srv = new Server();  
            //Reference the AdventureWorks2012 database   
            Database db;  
            db = srv.Databases["AdventureWorks2012"];  
            //Create a new database that is to be destination database.   
            Database dbCopy;  
            dbCopy = new Database(srv, "AdventureWorks2012Copy");  
            dbCopy.Create();  
            //Define a Transfer object and set the required options and properties.   
            Transfer xfr;  
            xfr = new Transfer(db);  
            xfr.CopyAllTables = true;  
            xfr.Options.WithDependencies = true;  
            xfr.Options.ContinueScriptingOnError = true;  
            xfr.DestinationDatabase = "AdventureWorks2012Copy";  
            xfr.DestinationServer = srv.Name;  
            xfr.DestinationLoginSecure = true;  
            xfr.CopySchema = true;  
            //Script the transfer. Alternatively perform immediate data transfer   
            // with TransferData method.   
            xfr.ScriptTransfer();  
        }   
```  
  
## <a name="transferring-schema-and-data-from-one-database-to-another-in-powershell"></a><span data-ttu-id="b3de1-116">在 PowerShell 中于数据库之间传输架构和数据</span><span class="sxs-lookup"><span data-stu-id="b3de1-116">Transferring Schema and Data from One Database to Another in PowerShell</span></span>  
 <span data-ttu-id="b3de1-117">此代码实例说明如何使用 <xref:Microsoft.SqlServer.Management.Smo.Transfer> 对象在数据库之间传输架构和数据。</span><span class="sxs-lookup"><span data-stu-id="b3de1-117">This code example shows how to transfer schema and data from one database to another using the <xref:Microsoft.SqlServer.Management.Smo.Transfer> object.</span></span>  
  
```powershell
#Connect to the local, default instance of SQL Server.  
  
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Reference the AdventureWorks2012 database.  
$db = $srv.Databases["AdventureWorks2012"]  
  
#Create a database to hold the copy of AdventureWorks  
$dbCopy = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Database -ArgumentList $srv, "AdventureWorksCopy"  
$dbCopy.Create()  
  
#Define a Transfer object and set the required options and properties.  
$xfr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Transfer -ArgumentList $db  
  
#Set this objects properties  
$xfr.CopyAllTables = $true  
$xfr.Options.WithDependencies = $true  
$xfr.Options.ContinueScriptingOnError = $true  
$xfr.DestinationDatabase = "AdventureWorksCopy"  
$xfr.DestinationServer = $srv.Name  
$xfr.DestinationLoginSecure = $true  
$xfr.CopySchema = $true  
"Scripting Data Transfer"  
#Script the transfer. Alternatively perform immediate data transfer with TransferData method.  
$xfr.ScriptTransfer()  
```  
