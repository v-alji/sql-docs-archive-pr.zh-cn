---
title: 表格)  (的数据库表示形式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 16a233fb-f83b-4ca1-acb5-6186eca0a62c
author: minewiskan
ms.author: owend
ms.openlocfilehash: c327e07685e98e6fa9f992025510e869d909e5ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580423"
---
# <a name="database-representationtabular"></a><span data-ttu-id="d954a-102">数据库表示形式（表格）</span><span class="sxs-lookup"><span data-stu-id="d954a-102">Database Representation(Tabular)</span></span>
  <span data-ttu-id="d954a-103">在表格模式下，数据库为表格模型中所有对象的容器。</span><span class="sxs-lookup"><span data-stu-id="d954a-103">In Tabular Mode, the database is the container for all objects in the tabular model.</span></span>  
  
## <a name="database-representation"></a><span data-ttu-id="d954a-104">数据库表示形式</span><span class="sxs-lookup"><span data-stu-id="d954a-104">Database Representation</span></span>  
 <span data-ttu-id="d954a-105">数据库是构成表格模型的所有对象所在的地方。</span><span class="sxs-lookup"><span data-stu-id="d954a-105">The database is the place where all objects that form a tabular model reside.</span></span> <span data-ttu-id="d954a-106">开发人员可以查找数据库中包含的连接、表和角色等多种对象。</span><span class="sxs-lookup"><span data-stu-id="d954a-106">Contained by the database, the developer finds objects like connections, tables, roles and many more.</span></span>  
  
### <a name="database-in-amo"></a><span data-ttu-id="d954a-107">AMO 中的数据库</span><span class="sxs-lookup"><span data-stu-id="d954a-107">Database in AMO</span></span>  
 <span data-ttu-id="d954a-108">在使用 AMO 管理表格模型数据库时，AMO 中的 <xref:Microsoft.AnalysisServices.Database> 对象与表格模型中的数据库逻辑对象一对一匹配。</span><span class="sxs-lookup"><span data-stu-id="d954a-108">When using AMO to manage a tabular model database, the <xref:Microsoft.AnalysisServices.Database> object in AMO matches one-to-one the database logical object in a tabular model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d954a-109">为了获取对 AMO 中数据库对象的访问权限，用户需要有权访问服务器对象并且连接到该服务器对象。</span><span class="sxs-lookup"><span data-stu-id="d954a-109">In order to gain access to a database object, in AMO, the user needs to have access to a server object and connect to it.</span></span>  
  
### <a name="database-in-adomdnet"></a><span data-ttu-id="d954a-110">ADOMD.Net 中的数据库</span><span class="sxs-lookup"><span data-stu-id="d954a-110">Database in ADOMD.Net</span></span>  
 <span data-ttu-id="d954a-111">在使用 ADOMD 查询表格模型数据库时，通过 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> 对象来获取与特定数据库的连接。</span><span class="sxs-lookup"><span data-stu-id="d954a-111">When using ADOMD to consult and query a tabular model database, connection to a specific database is obtained through the <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> object.</span></span>  
  
 <span data-ttu-id="d954a-112">您可以使用以下代码段直接连接到某个数据库：</span><span class="sxs-lookup"><span data-stu-id="d954a-112">You can connect directly to a certain database using the following code snippet:</span></span>  
  
```csharp  
using ADOMD = Microsoft.AnalysisServices.AdomdClient;  
...  
   ADOMD.AdomdConnection currrentCnx = new ADOMD.AdomdConnection("Data Source=<<server\instance>>;Catalog=<<database>>");  
   currrentCnx.Open();  
...  
  
```  
  
 <span data-ttu-id="d954a-113">此外，通过现有连接对象（即尚未关闭），您可以按以下代码段中所示将当前数据库更改为另一数据库：</span><span class="sxs-lookup"><span data-stu-id="d954a-113">Also, over an existing connection object (that hasn't been closed), you can change the current database to another as shown in the following code snippet:</span></span>  
  
```csharp  
currentCnx.ChangeDatabase("myOtherDatabase");  
  
```  
  
## <a name="database-in-amo"></a><span data-ttu-id="d954a-114">AMO 中的数据库</span><span class="sxs-lookup"><span data-stu-id="d954a-114">Database in AMO</span></span>  
 <span data-ttu-id="d954a-115">在使用 AMO 管理数据库对象时，请从 <xref:Microsoft.AnalysisServices.Server> 对象开始操作。</span><span class="sxs-lookup"><span data-stu-id="d954a-115">When using AMO to manage a database object, start with a <xref:Microsoft.AnalysisServices.Server> object.</span></span> <span data-ttu-id="d954a-116">然后在数据库集合中搜索您的数据库或通过向集合添加一个数据库来创建新数据库。</span><span class="sxs-lookup"><span data-stu-id="d954a-116">Then search for your database in the databases collection or create a new database by adding one to the collection.</span></span>  
  
 <span data-ttu-id="d954a-117">下面的代码片段演示了在检查数据库不存在后连接到服务器并创建空数据库的步骤：</span><span class="sxs-lookup"><span data-stu-id="d954a-117">The following code snippet shows the steps to connect to a server and create an empty database, after checking the database doesn't exist:</span></span>  
  
```  
  
AMO.Server CurrentServer = new AMO.Server();  
try  
{  
    CurrentServer.Connect(currentServerName);  
}  
catch (Exception cnxException)  
{  
    MessageBox.Show(string.Format("Error while trying to connect to server: [{0}]\nError message: {1}", currentServerName, cnxException.Message), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
    return;  
}  
newDatabaseName = DatabaseName.Text;  
if (CurrentServer.Databases.Contains(newDatabaseName))  
{  
    return;  
}  
try  
{  
    AMO.Database newDatabase = CurrentServer.Databases.Add(newDatabaseName);  
  
    CurrentServer.Update();  
}  
catch (Exception createDBxc)  
{  
    MessageBox.Show(String.Format("Database [{0}] couldn't be created.\n{1}", newDatabaseName, createDBxc.Message), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
    newDatabaseAvailable = false;  
}  
  
```  
  
 <span data-ttu-id="d954a-118">为了真正理解如何使用 AMO 创建和操作数据库表示形式，请参阅“表格 AMO 2012”示例中的源代码；具体来讲，请查看以下源文件：Database.cs。</span><span class="sxs-lookup"><span data-stu-id="d954a-118">For a practical understanding on how to use AMO to create and manipulate database representations, see source code in the Tabular AMO 2012 sample; specifically check in the following source file: Database.cs.</span></span> <span data-ttu-id="d954a-119">示例代码仅作为对此处所述逻辑概念的支持提供，不应用于生产环境中。</span><span class="sxs-lookup"><span data-stu-id="d954a-119">Sample code is provided only as a support to the logical concepts explained here, and should not be used in a production environment.</span></span>  
  
  
