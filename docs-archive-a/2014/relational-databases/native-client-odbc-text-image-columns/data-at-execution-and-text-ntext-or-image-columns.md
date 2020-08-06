---
title: 执行时数据和 Text、ntext 或 Image 列 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- columns [ODBC]
- ODBC data types, image columns
- ODBC data types, text columns
- data-at-execution
- ODBC data-at-execution
- image columns [ODBC]
ms.assetid: 67ffb1a6-f38d-4712-ba64-96bdd41ec2b2
author: rothja
ms.author: jroth
ms.openlocfilehash: 404fade34862fe4705ec440eef7f466a9073250b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693818"
---
# <a name="data-at-execution-and-text-ntext-or-image-columns"></a><span data-ttu-id="4c618-102">执行时数据和 Text、ntext 或 Image 列</span><span class="sxs-lookup"><span data-stu-id="4c618-102">Data-at-Execution and Text, ntext, or Image Columns</span></span>
  <span data-ttu-id="4c618-103">使用 ODBC 执行时数据功能，应用程序能够对绑定列或参数使用非常大的数据量。</span><span class="sxs-lookup"><span data-stu-id="4c618-103">ODBC data-at-execution is a feature that enables applications to work with extremely large amounts of data on bound columns or parameters.</span></span> <span data-ttu-id="4c618-104">检索非常大的**text**、 **ntext**或**image**列时，应用程序可能无法简单地分配大型缓冲区，将列绑定到缓冲区，并提取行。</span><span class="sxs-lookup"><span data-stu-id="4c618-104">When retrieving very large **text**, **ntext**, or **image** columns, an application may not be able to simply allocate a huge buffer, bind the column into the buffer, and fetch the row.</span></span> <span data-ttu-id="4c618-105">更新非常大的**text**、 **ntext**或**image**列时，应用程序可能无法简单地分配大型缓冲区，将其绑定到 SQL 语句中的参数标记，然后执行该语句。</span><span class="sxs-lookup"><span data-stu-id="4c618-105">When updating very large **text**, **ntext**, or **image** columns, the application might not be able to simply allocate a huge buffer, bind it to a parameter marker in an SQL statement, and then execute the statement.</span></span> <span data-ttu-id="4c618-106">在这些情况下，应用程序必须将[SQLGetData](../native-client-odbc-api/sqlgetdata.md)或[SQLPutData](../native-client-odbc-api/sqlputdata.md)与它的执行时数据选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="4c618-106">In these cases, the application must use [SQLGetData](../native-client-odbc-api/sqlgetdata.md) or [SQLPutData](../native-client-odbc-api/sqlputdata.md) with its data-at-execution options.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c618-107">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4c618-107">See Also</span></span>  
 [<span data-ttu-id="4c618-108">管理 Text 和 Image 列</span><span class="sxs-lookup"><span data-stu-id="4c618-108">Managing Text and Image Columns</span></span>](managing-text-and-image-columns.md)  
  
  
