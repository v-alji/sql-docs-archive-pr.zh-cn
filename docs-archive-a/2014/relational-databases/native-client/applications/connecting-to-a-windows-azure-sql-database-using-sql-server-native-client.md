---
title: 使用 SQL Server Native Client 连接到 Azure SQL 数据库 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 0dc20bb6-b142-4259-b87b-427d2ba798af
author: rothja
ms.author: jroth
ms.openlocfilehash: 177c655f97e32f2044460e87c6cd775cdf8fcde9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587774"
---
# <a name="connecting-to-an-azure-sql-database-using-sql-server-native-client"></a><span data-ttu-id="16da3-102">使用 SQL Server Native Client 连接到 Azure SQL 数据库</span><span class="sxs-lookup"><span data-stu-id="16da3-102">Connecting to an Azure SQL Database Using SQL Server Native Client</span></span>
  <span data-ttu-id="16da3-103">有关演示如何使用 Native Client 连接到的示例 [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，请参阅[开发： (Azure SQL 数据库) 的操作指南主题](https://msdn.microsoft.com/library/ee621787.aspx)。</span><span class="sxs-lookup"><span data-stu-id="16da3-103">For a sample that shows how to connect to a [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, see [Development: How-to Topics (Azure SQL Database)](https://msdn.microsoft.com/library/ee621787.aspx).</span></span>  
  
## <a name="known-issues-when-connecting-to-a-sql-database"></a><span data-ttu-id="16da3-104">连接到 SQL Database 时的已知问题</span><span class="sxs-lookup"><span data-stu-id="16da3-104">Known Issues When Connecting to a SQL Database</span></span>  
 <span data-ttu-id="16da3-105">以下是使用 [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] Native Client 连接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 时的一些已知问题：</span><span class="sxs-lookup"><span data-stu-id="16da3-105">The following are known issues when connecting to a [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client:</span></span>  
  
-   <span data-ttu-id="16da3-106">如果分阶段使用 `SQLBrowseConnect`，则使用 `SQLBrowseConnect` 建立的连接可能被拒绝。</span><span class="sxs-lookup"><span data-stu-id="16da3-106">A connection made with `SQLBrowseConnect` may be rejected if `SQLBrowseConnect` is used in stages.</span></span>  <span data-ttu-id="16da3-107">例如，如果在第一次调用中发送驱动程序名称，在第二次调用中发送服务器和凭据（用户名和密码），建立连接，然后在第三次调用中发送数据库名称和语言。</span><span class="sxs-lookup"><span data-stu-id="16da3-107">For example, if the driver name is sent in the first call, server and credentials (user and password) sent in the second call, establishing the connection, and a database name and a language in the third call.</span></span>  <span data-ttu-id="16da3-108">第三次调用将导致 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 发出 USE 语句来更改数据库。</span><span class="sxs-lookup"><span data-stu-id="16da3-108">The third call will cause [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client to issue a USE statement to change databases.</span></span> <span data-ttu-id="16da3-109">但是，在 [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] 中不支持 USE 语句，因此生成以下错误：</span><span class="sxs-lookup"><span data-stu-id="16da3-109">However, the USE statement is not supported in [!INCLUDE[ssSDS](../../../includes/sssds-md.md)], generating the following error:</span></span>  
  
    ```  
    [Microsoft][SQL Server Native Client 11.0][SQL Server]USE statement is not supported to switch between databases. Use a new connection to connect to a different Database.  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="16da3-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="16da3-110">See Also</span></span>  
 [<span data-ttu-id="16da3-111">使用 SQL Server Native Client 生成应用程序</span><span class="sxs-lookup"><span data-stu-id="16da3-111">Building Applications with SQL Server Native Client</span></span>](building-applications-with-sql-server-native-client.md)  
  
  
