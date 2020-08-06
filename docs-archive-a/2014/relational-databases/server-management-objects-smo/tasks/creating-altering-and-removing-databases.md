---
title: 创建、更改和删除数据库 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- databases [SMO]
- databases [SMO], creating
- databases [SMO], modifying
- databases [SMO], deleting
ms.assetid: fcfb3ec2-7556-4f72-971a-501295892cb0
author: stevestein
ms.author: sstein
ms.openlocfilehash: e8bd34e939fcbc1ecfc5238f5fc4524d187d3f30
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692829"
---
# <a name="creating-altering-and-removing-databases"></a><span data-ttu-id="e00c2-102">创建、更改和删除数据库</span><span class="sxs-lookup"><span data-stu-id="e00c2-102">Creating, Altering, and Removing Databases</span></span>
  <span data-ttu-id="e00c2-103">在 SMO 中，数据库由 <xref:Microsoft.SqlServer.Management.Smo.Database> 对象表示。</span><span class="sxs-lookup"><span data-stu-id="e00c2-103">In SMO, a database is represented by the <xref:Microsoft.SqlServer.Management.Smo.Database> object.</span></span>  
  
 <span data-ttu-id="e00c2-104">不必创建 <xref:Microsoft.SqlServer.Management.Smo.Database> 对象便可修改或删除数据库。</span><span class="sxs-lookup"><span data-stu-id="e00c2-104">It is not necessary to create a <xref:Microsoft.SqlServer.Management.Smo.Database> object to modify or remove it.</span></span> <span data-ttu-id="e00c2-105">通过使用集合可以引用数据库。</span><span class="sxs-lookup"><span data-stu-id="e00c2-105">The database can be referenced by using a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e00c2-106">示例</span><span class="sxs-lookup"><span data-stu-id="e00c2-106">Example</span></span>  
 <span data-ttu-id="e00c2-107">若要使用所提供的任何代码示例，您必须选择创建应用程序所需的编程环境、编程模板和编程语言。</span><span class="sxs-lookup"><span data-stu-id="e00c2-107">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="e00c2-108">有关详细信息，请参阅[在 Visual studio .net 中创建 VISUAL BASIC SMO 项目](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)或[在 visual Studio .Net 中创建 VISUAL C&#35; smo 项目](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。</span><span class="sxs-lookup"><span data-stu-id="e00c2-108">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-altering-and-removing-a-database-in-visual-basic"></a><span data-ttu-id="e00c2-109">在 Visual Basic 中创建、更改和删除数据库</span><span class="sxs-lookup"><span data-stu-id="e00c2-109">Creating, Altering, and Removing a Database in Visual Basic</span></span>  
 <span data-ttu-id="e00c2-110">此代码示例创建了一个新数据库。</span><span class="sxs-lookup"><span data-stu-id="e00c2-110">This code example creates a new database.</span></span> <span data-ttu-id="e00c2-111">将为该数据库自动创建文件和文件组。</span><span class="sxs-lookup"><span data-stu-id="e00c2-111">Files and file groups are automatically created for the database.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBDatabase1](SMO How to#SMO_VBDatabase1)]  -->  
  
## <a name="creating-altering-and-removing-a-database-in-visual-c"></a><span data-ttu-id="e00c2-112">在 Visual C# 中创建、更改和删除数据库</span><span class="sxs-lookup"><span data-stu-id="e00c2-112">Creating, Altering, and Removing a Database in Visual C#</span></span>  
 <span data-ttu-id="e00c2-113">此代码示例创建了一个新数据库。</span><span class="sxs-lookup"><span data-stu-id="e00c2-113">This code example creates a new database.</span></span> <span data-ttu-id="e00c2-114">将为该数据库自动创建文件和文件组。</span><span class="sxs-lookup"><span data-stu-id="e00c2-114">Files and file groups are automatically created for the database.</span></span>  
  
```csharp
{  
                //Connect to the local, default instance of SQL Server.   
                Server srv;  
                srv = new Server();  
                //Define a Database object variable by supplying the server and the database name arguments in the constructor.   
                Database db;  
                db = new Database(srv, "Test_SMO_Database");  
                //Create the database on the instance of SQL Server.   
                db.Create();  
                //Reference the database and display the date when it was created.   
                db = srv.Databases["Test_SMO_Database"];  
                Console.WriteLine(db.CreateDate);  
                //Remove the database.   
                db.Drop();  
            }  
```  
  
## <a name="creating-altering-and-removing-a-database-in-powershell"></a><span data-ttu-id="e00c2-115">在 PowerShell 中创建、更改和删除数据库</span><span class="sxs-lookup"><span data-stu-id="e00c2-115">Creating, Altering, and Removing a Database in PowerShell</span></span>  
 <span data-ttu-id="e00c2-116">此代码示例创建了一个新数据库。</span><span class="sxs-lookup"><span data-stu-id="e00c2-116">This code example creates a new database.</span></span> <span data-ttu-id="e00c2-117">将为该数据库自动创建文件和文件组。</span><span class="sxs-lookup"><span data-stu-id="e00c2-117">Files and file groups are automatically created for the database.</span></span>  
  
```powershell
#Get a server object which corresponds to the default instance  
cd \sql\localhost\  
$srv = Get-Item default  
  
#Create a new database  
$db = New-Object -TypeName Microsoft.SqlServer.Management.Smo.Database -argumentlist $srv, "Test_SMO_Database"  
$db.Create()  
  
#Reference the database and display the date when it was created.
$db = $srv.Databases["Test_SMO_Database"]  
$db.CreateDate  
  
#Drop the database  
$db.Drop()  
```  
  
## <a name="see-also"></a><span data-ttu-id="e00c2-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e00c2-118">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.Database>  
