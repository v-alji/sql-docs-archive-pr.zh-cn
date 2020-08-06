---
title: SQL Server Native Client 对 LocalDB 的支持 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 127569d1-a9f7-49bf-a561-c084986a8871
author: rothja
ms.author: jroth
ms.openlocfilehash: b08ea46e8db1b665280116a439b95748f69d03ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579554"
---
# <a name="sql-server-native-client-support-for-localdb"></a><span data-ttu-id="5599a-102">SQL Server Native Client 对 LocalDB 的支持</span><span class="sxs-lookup"><span data-stu-id="5599a-102">SQL Server Native Client Support for LocalDB</span></span>
  <span data-ttu-id="5599a-103">从 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 开始，将提供 SQL Server 的称作 LocalDB 的轻型版本。</span><span class="sxs-lookup"><span data-stu-id="5599a-103">Beginning in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], a lightweight version of SQL Server, called LocalDB, will be available.</span></span> <span data-ttu-id="5599a-104">本主题介绍如何连接到 LocalDB 实例中的数据库。</span><span class="sxs-lookup"><span data-stu-id="5599a-104">This topic discusses how to connect to a database in a LocalDB instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5599a-105">备注</span><span class="sxs-lookup"><span data-stu-id="5599a-105">Remarks</span></span>  
 <span data-ttu-id="5599a-106">有关 LocalDB 的详细信息，包括如何安装 LocalDB 和配置您的 LocalDB 实例，请参阅：</span><span class="sxs-lookup"><span data-stu-id="5599a-106">For more information about LocalDB, including how to install LocalDB and configure your LocalDB instance, see:</span></span>  
  
-   [<span data-ttu-id="5599a-107">SQL Server Express LocalDB 参考</span><span class="sxs-lookup"><span data-stu-id="5599a-107">SQL Server Express LocalDB Reference</span></span>](../../sql-server-express-localdb-reference.md)  
  
-   [<span data-ttu-id="5599a-108">SQL Server 2014 Express LocalDB</span><span class="sxs-lookup"><span data-stu-id="5599a-108">SQL Server 2014 Express LocalDB</span></span>](../../../database-engine/configure-windows/sql-server-2016-express-localdb.md)  
  
 <span data-ttu-id="5599a-109">总之，通过 LocalDB，您可以：</span><span class="sxs-lookup"><span data-stu-id="5599a-109">To summarize, LocalDB allows you to:</span></span>  
  
-   <span data-ttu-id="5599a-110">使用 `sqllocaldb.exe i` 发现默认实例的名称。</span><span class="sxs-lookup"><span data-stu-id="5599a-110">Use `sqllocaldb.exe i` to discover the name of the default instance.</span></span>  
  
-   <span data-ttu-id="5599a-111">使用 `AttachDBFilename` 连接字符串关键字指定服务器应附加的数据库文件。</span><span class="sxs-lookup"><span data-stu-id="5599a-111">Use the `AttachDBFilename` connection string keyword to specify which database file the server should attach.</span></span> <span data-ttu-id="5599a-112">使用时 `AttachDBFilename` ，如果未使用**数据库**连接字符串关键字指定数据库的名称，则在应用程序关闭时，将从 LocalDB 实例中删除数据库。</span><span class="sxs-lookup"><span data-stu-id="5599a-112">When using `AttachDBFilename`, if you do not specify the name of the database with the **Database** connection string keyword, the database will be removed from the LocalDB instance when the application closes.</span></span>  
  
-   <span data-ttu-id="5599a-113">在您的连接字符串中指定 LocalDB 实例：</span><span class="sxs-lookup"><span data-stu-id="5599a-113">Specify a LocalDB instance in your connection string:</span></span>  
  
```  
SERVER=(localdb)\v11.0  
```  
  
 <span data-ttu-id="5599a-114">如果需要，您可以使用 sqllocaldb.exe 创建 LocalDB 实例。</span><span class="sxs-lookup"><span data-stu-id="5599a-114">If necessary, you can create a LocalDB instance with sqllocaldb.exe.</span></span> <span data-ttu-id="5599a-115">还可以使用 sqlcmd.exe 添加和修改 LocalDB 实例中的数据库。</span><span class="sxs-lookup"><span data-stu-id="5599a-115">You can also use sqlcmd.exe to add and modify databases in a LocalDB instance.</span></span> <span data-ttu-id="5599a-116">例如，`sqlcmd -S (localdb)\v11.0` 。</span><span class="sxs-lookup"><span data-stu-id="5599a-116">For example, `sqlcmd -S (localdb)\v11.0`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5599a-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5599a-117">See Also</span></span>  
 [<span data-ttu-id="5599a-118">SQL Server Native Client 功能</span><span class="sxs-lookup"><span data-stu-id="5599a-118">SQL Server Native Client Features</span></span>](sql-server-native-client-features.md)  
  
  
