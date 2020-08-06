---
title: SQLSetEnvAttr |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLSetEnvAttr function
ms.assetid: d4114571-feca-4330-b2e4-7bfd1050b812
author: rothja
ms.author: jroth
ms.openlocfilehash: f0dbd4d01de9ca769c46a93f810f0149f5b86981
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590741"
---
# <a name="sqlsetenvattr"></a><span data-ttu-id="ec1df-102">SQLSetEnvAttr</span><span class="sxs-lookup"><span data-stu-id="ec1df-102">SQLSetEnvAttr</span></span>
  <span data-ttu-id="ec1df-103">[Odbc 程序员参考](https://go.microsoft.com/fwlink/?LinkId=45250)定义了 odbc 驱动程序应如何从写入 odbc 2 的应用程序解释**SQLSetEnvAttr**属性规范。*x*或 ODBC 3。*x* API。</span><span class="sxs-lookup"><span data-stu-id="ec1df-103">The [ODBC Programmer's Reference](https://go.microsoft.com/fwlink/?LinkId=45250) defines how ODBC drivers should interpret the **SQLSetEnvAttr** attribute specifications from applications written to either the ODBC 2.*x* or ODBC 3.*x* API.</span></span> <span data-ttu-id="ec1df-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驱动程序符合这些规则。</span><span class="sxs-lookup"><span data-stu-id="ec1df-104">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver complies with those rules.</span></span>  
  
 <span data-ttu-id="ec1df-105">**SQLSetEnvAttr**控制的属性之一是是否要使用连接池。</span><span class="sxs-lookup"><span data-stu-id="ec1df-105">One of the attributes controlled by **SQLSetEnvAttr** is whether connection pooling is to be used.</span></span> <span data-ttu-id="ec1df-106">如果连接池与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驱动程序一起使用，则在使用[SQLDriverConnect](sqldriverconnect.md)或**SQLConnect**连接时， *DriverCompletion*参数必须设置为 SQL_DRIVER_NOPROMPT。</span><span class="sxs-lookup"><span data-stu-id="ec1df-106">If connection pooling is used with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver, the *DriverCompletion* parameter must be set to SQL_DRIVER_NOPROMPT when connecting with either [SQLDriverConnect](sqldriverconnect.md) or **SQLConnect**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec1df-107">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ec1df-107">See Also</span></span>  
 <span data-ttu-id="ec1df-108">[SQLSetEnvAttr 函数](https://go.microsoft.com/fwlink/?LinkId=59369) </span><span class="sxs-lookup"><span data-stu-id="ec1df-108">[SQLSetEnvAttr Function](https://go.microsoft.com/fwlink/?LinkId=59369) </span></span>  
 [<span data-ttu-id="ec1df-109">ODBC API 实现细节</span><span class="sxs-lookup"><span data-stu-id="ec1df-109">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
