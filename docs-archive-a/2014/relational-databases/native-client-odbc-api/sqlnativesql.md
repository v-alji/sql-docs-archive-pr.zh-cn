---
title: SQLNativeSql |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLNativeSql function
ms.assetid: 2d999fec-9e22-4514-ad5f-22a64b82f95b
author: rothja
ms.author: jroth
ms.openlocfilehash: 433b086dc36a79cb82868edebac9f0a4814c21fe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590763"
---
# <a name="sqlnativesql"></a><span data-ttu-id="63be0-102">SQLNativeSql</span><span class="sxs-lookup"><span data-stu-id="63be0-102">SQLNativeSql</span></span>
  <span data-ttu-id="63be0-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驱动程序在不访问服务器的情况下满足**SQLNativeSql**请求。</span><span class="sxs-lookup"><span data-stu-id="63be0-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver satisfies **SQLNativeSql** requests without visiting the server.</span></span> <span data-ttu-id="63be0-104">该函数有效地测试 SQL 语句的语法。</span><span class="sxs-lookup"><span data-stu-id="63be0-104">The function efficiently tests the syntax of SQL statements.</span></span> <span data-ttu-id="63be0-105">语法检查无法确定 SQL 语句中表达式的标识符或结果是否有效，并且 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **SQLNativeSql**返回的本机 SQL 可能无法运行。</span><span class="sxs-lookup"><span data-stu-id="63be0-105">Syntax checking does not determine if identifiers or the results of expressions in the SQL statements are valid, and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native SQL returned by **SQLNativeSql** can fail to run.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63be0-106">另请参阅</span><span class="sxs-lookup"><span data-stu-id="63be0-106">See Also</span></span>  
 <span data-ttu-id="63be0-107">[SQLNativeSql 函数](https://go.microsoft.com/fwlink/?LinkID=59358) </span><span class="sxs-lookup"><span data-stu-id="63be0-107">[SQLNativeSql Function](https://go.microsoft.com/fwlink/?LinkID=59358) </span></span>  
 [<span data-ttu-id="63be0-108">ODBC API 实现细节</span><span class="sxs-lookup"><span data-stu-id="63be0-108">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
