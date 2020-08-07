---
title: 有关 GEOMETRY、GEOGRAPHY 和 HIERARCHYID 的客户端使用情况的警告 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 500ee6b3-2154-45d2-a3cf-8760166d9413
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 66898aa056800c0a7573b5afa73762785706ff7a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586106"
---
# <a name="warning-about-client-side-usage-of-geometry-geography-and-hierarchyid"></a><span data-ttu-id="d8e34-102">关于客户端对 GEOMETRY、GEOGRAPHY 和 HIERARCHYID 的使用的警告</span><span class="sxs-lookup"><span data-stu-id="d8e34-102">Warning about client side usage of GEOMETRY, GEOGRAPHY and HIERARCHYID</span></span>
  <span data-ttu-id="d8e34-103">包含空间数据类型的程序集**Microsoft.SqlServer.Types.dll**已从版本10.0 升级到11.0 版。</span><span class="sxs-lookup"><span data-stu-id="d8e34-103">The assembly **Microsoft.SqlServer.Types.dll**, which contains the spatial data types, has been upgraded from version 10.0 to version 11.0.</span></span> <span data-ttu-id="d8e34-104">满足某些条件时，引用此程序集的自定义应用程序可能会失败。</span><span class="sxs-lookup"><span data-stu-id="d8e34-104">Custom applications that reference this assembly may fail when certain conditions are true.</span></span>  
  
## <a name="component"></a><span data-ttu-id="d8e34-105">组件</span><span class="sxs-lookup"><span data-stu-id="d8e34-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="d8e34-106">说明</span><span class="sxs-lookup"><span data-stu-id="d8e34-106">Description</span></span>  
 <span data-ttu-id="d8e34-107">包含空间数据类型的程序集**Microsoft.SqlServer.Types.dll**已从版本10.0 升级到11.0 版。</span><span class="sxs-lookup"><span data-stu-id="d8e34-107">The assembly **Microsoft.SqlServer.Types.dll**, which contains the spatial data types, has been upgraded from version 10.0 to version 11.0.</span></span> <span data-ttu-id="d8e34-108">满足以下条件时，引用此程序集的自定义应用程序可能失败：</span><span class="sxs-lookup"><span data-stu-id="d8e34-108">Custom applications that reference this assembly may fail when the following conditions are true.</span></span>  
  
-   <span data-ttu-id="d8e34-109">将自定义应用程序从安装了的计算机移 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 到仅安装了的计算机时 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，应用程序将失败，因为**SqlTypes**程序集的引用版本10.0 不存在。</span><span class="sxs-lookup"><span data-stu-id="d8e34-109">When you move a custom application from a computer on which [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] was installed to a computer on which only [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] is installed, the application will fail because the referenced version 10.0 of the **SqlTypes** assembly is not present.</span></span> <span data-ttu-id="d8e34-110">您可能会看到此错误消息：`"Could not load file or assembly 'Microsoft.SqlServer.Types, Version=10.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91' or one of its dependencies. The system cannot find the file specified."`</span><span class="sxs-lookup"><span data-stu-id="d8e34-110">You may see this error message: `"Could not load file or assembly 'Microsoft.SqlServer.Types, Version=10.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91' or one of its dependencies. The system cannot find the file specified."`</span></span>  
  
-   <span data-ttu-id="d8e34-111">当引用**SqlTypes**程序集版本11.0 时，还安装了版本10.0，你可能会看到以下错误消息：`"System.InvalidCastException: Unable to cast object of type 'Microsoft.SqlServer.Types.SqlGeometry' to type 'Microsoft.SqlServer.Types.SqlGeometry'."`</span><span class="sxs-lookup"><span data-stu-id="d8e34-111">When you reference the **SqlTypes** assembly version 11.0, and version 10.0 is also installed, you may see this error message: `"System.InvalidCastException: Unable to cast object of type 'Microsoft.SqlServer.Types.SqlGeometry' to type 'Microsoft.SqlServer.Types.SqlGeometry'."`</span></span>  
  
-   <span data-ttu-id="d8e34-112">如果从以 .NET 3.5、4或4.5 为目标的自定义应用程序引用**SqlTypes**程序集版本11.0，则该应用程序将失败，因为 SqlClient 按设计加载程序集的版本10.0。</span><span class="sxs-lookup"><span data-stu-id="d8e34-112">When you reference the **SqlTypes** assembly version 11.0 from a custom application that targets .NET 3.5, 4, or 4.5, the application will fail because SqlClient by design loads version 10.0 of the assembly.</span></span> <span data-ttu-id="d8e34-113">当应用程序调用以下方法之一时，将出现此失败：</span><span class="sxs-lookup"><span data-stu-id="d8e34-113">This failure occurs when the application calls one of the following methods:</span></span>  
  
    -   <span data-ttu-id="d8e34-114">`GetValue` 类的 `SqlDataReader` 方法</span><span class="sxs-lookup"><span data-stu-id="d8e34-114">`GetValue` method of the `SqlDataReader` class</span></span>  
  
    -   <span data-ttu-id="d8e34-115">`GetValues` 类的 `SqlDataReader` 方法</span><span class="sxs-lookup"><span data-stu-id="d8e34-115">`GetValues` method of the `SqlDataReader` class</span></span>  
  
    -   <span data-ttu-id="d8e34-116">`SqlDataReader` 类的方括号索引运算符 []</span><span class="sxs-lookup"><span data-stu-id="d8e34-116">bracket index operator [] of the `SqlDataReader` class</span></span>  
  
    -   <span data-ttu-id="d8e34-117">`ExecuteScalar` 类的 `SqlCommand` 方法</span><span class="sxs-lookup"><span data-stu-id="d8e34-117">`ExecuteScalar` method of the `SqlCommand` class</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="d8e34-118">纠正措施</span><span class="sxs-lookup"><span data-stu-id="d8e34-118">Corrective Action</span></span>  
 <span data-ttu-id="d8e34-119">您可以使用以下方法之一来解决此问题：</span><span class="sxs-lookup"><span data-stu-id="d8e34-119">You can work around this issue by using one of the following methods:</span></span>  
  
-   <span data-ttu-id="d8e34-120">您可以通过调用 `GetSqlBytes` 方法替代以上所列的 Get 方法来检索 CLR [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系统类型，在您的代码中解决此问题，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="d8e34-120">You can work around this issue in your code by calling the `GetSqlBytes` method, instead of the Get methods listed above, to retrieve CLR [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system types, as shown in the following example:</span></span>  
  
    ```csharp  
    string query = "SELECT [SpatialColumn] FROM [SpatialTable]";  
          using (SqlConnection conn = new SqlConnection("..."))  
          {  
                SqlCommand cmd = new SqlCommand(query, conn);  
  
                conn.Open();  
                SqlDataReader reader = cmd.ExecuteReader();  
  
                while (reader.Read())  
                {  
                      // In version 11.0 only  
                      SqlGeometry g =   
    SqlGeometry.Deserialize(reader.GetSqlBytes(0));  
  
                      // In version 10.0 or 11.0  
                      SqlGeometry g2 = new SqlGeometry();  
                      g.Read(new BinaryReader(reader.GetSqlBytes(0).Stream));  
                }  
          }  
    ```  
  
-   <span data-ttu-id="d8e34-121">您可以通过在应用程序配置文件中使用程序集重定向来解决此问题，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="d8e34-121">You can work around this issue by using assembly redirection in the application configuration file, as shown in the following example:</span></span>  
  
    ```xml  
    <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
        ...  
        <dependentAssembly>  
            <assemblyIdentity name="Microsoft.SqlServer.Types" publicKeyToken="89845dcd8080cc91" culture="neutral" />  
            <bindingRedirect oldVersion="10.0.0.0" newVersion="11.0.0.0" />  
        </dependentAssembly>  
        ...  
    </assemblyBinding>  
    ```  
  
-   <span data-ttu-id="d8e34-122">您可以通过为“类型系统版本”属性指定值“SQL Server 2012”以强制 SqlClient 加载程序集的版本 11.0，解决此问题。</span><span class="sxs-lookup"><span data-stu-id="d8e34-122">You can work around this issue in your connection string by specifying a value of "SQL Server 2012" for the "Type System Version" attribute to force SqlClient to load version 11.0 of the assembly.</span></span> <span data-ttu-id="d8e34-123">此连接字符串属性仅在 .NET 4.5 和更高版本中使用。</span><span class="sxs-lookup"><span data-stu-id="d8e34-123">This connection string attribute is available only in .NET 4.5 and above.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8e34-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d8e34-124">See Also</span></span>  
 <span data-ttu-id="d8e34-125">[数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="d8e34-125">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="d8e34-126">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="d8e34-126">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md
)  
  
  
