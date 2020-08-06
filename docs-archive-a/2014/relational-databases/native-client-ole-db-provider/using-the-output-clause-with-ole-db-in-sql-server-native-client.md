---
title: 将 OUTPUT 子句与 SQL Server Native Client 中的 OLE DB 一起使用 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 53deeb99-c088-4fde-844b-b2d91d6de1eb
author: rothja
ms.author: jroth
ms.openlocfilehash: a425ec6269040c72836571b8fa8b51bba4ed8c32
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692366"
---
# <a name="using-the-output-clause-with-ole-db-in-sql-server-native-client"></a><span data-ttu-id="e7062-102">在 SQL Server Native Client 中对 OLE DB 使用 OUTPUT 子句</span><span class="sxs-lookup"><span data-stu-id="e7062-102">Using the OUTPUT Clause with OLE DB in SQL Server Native Client</span></span>
  <span data-ttu-id="e7062-103">如果在 INSERT、UPDATE、DELETE 或 MERGE 命令中使用 OUTPUT 子句，则无法获得受影响的行数。</span><span class="sxs-lookup"><span data-stu-id="e7062-103">If you use an OUTPUT clause in an INSERT, UPDATE, DELETE, or MERGE command, the count of affected rows is not available.</span></span> <span data-ttu-id="e7062-104">应用程序必须对 OUTPUT 子句所返回的行集中的行数进行计数。</span><span class="sxs-lookup"><span data-stu-id="e7062-104">The application must count the number of rows in the rowset that is returned by the OUTPUT clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7062-105">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e7062-105">See Also</span></span>  
 [<span data-ttu-id="e7062-106">创建 SQL Server Native Client OLE DB 访问接口应用程序</span><span class="sxs-lookup"><span data-stu-id="e7062-106">Creating a SQL Server Native Client OLE DB Provider Application</span></span>](creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
  
