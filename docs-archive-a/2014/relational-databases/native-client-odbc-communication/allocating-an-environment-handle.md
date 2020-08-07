---
title: 分配环境句柄 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, environment handles
- ODBC applications, connections
- handles [SQL Server Native Client]
- environment handles [SQLNCLI]
ms.assetid: 15c1b428-ea6d-4672-894c-f0e289e2da3f
author: rothja
ms.author: jroth
ms.openlocfilehash: 1c655b5e9a406c3e1881c9dd199a92666377918f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587801"
---
# <a name="allocating-an-environment-handle"></a><span data-ttu-id="ef6bc-102">分配环境句柄</span><span class="sxs-lookup"><span data-stu-id="ef6bc-102">Allocating an Environment Handle</span></span>
  <span data-ttu-id="ef6bc-103">在应用程序可以调用任何 ODBC 函数之前，它必须初始化 ODBC 环境并分配环境句柄。</span><span class="sxs-lookup"><span data-stu-id="ef6bc-103">Before an application can call any ODBC function, it must initialize the ODBC environment and allocate an environment handle.</span></span> <span data-ttu-id="ef6bc-104">这是全局上下文句柄，并且是 ODBC 中其他句柄的占位符。</span><span class="sxs-lookup"><span data-stu-id="ef6bc-104">This is the global context handle and placeholder for the other handles in ODBC.</span></span> <span data-ttu-id="ef6bc-105">为此，可调用**SQLAllocHandle** ，并将*HandleType*参数设置为 SQL_HANDLE_ENV 并将*将 inputhandle*设置为 SQL_NULL_HANDLE。</span><span class="sxs-lookup"><span data-stu-id="ef6bc-105">You do this by calling **SQLAllocHandle** with the *HandleType* parameter set to SQL_HANDLE_ENV and *InputHandle* set to SQL_NULL_HANDLE.</span></span>  
  
 <span data-ttu-id="ef6bc-106">分配环境句柄之后，应用程序必须设置环境属性以指示它将使用哪一个版本的 ODBC 函数调用。</span><span class="sxs-lookup"><span data-stu-id="ef6bc-106">After allocating the environment handle, the application must set environment attributes to indicate which version of ODBC function calls it will be using.</span></span> <span data-ttu-id="ef6bc-107">使用 ODBC 3。*x*函数调用[SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md) ，并将*特性*参数设置为 SQL_ATTR_ODBC_VERSION，将*将 valueptr*设置为 SQL_OV_ODBC3。</span><span class="sxs-lookup"><span data-stu-id="ef6bc-107">To use the ODBC 3.*x* functions, call [SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md) with the *Attribute* parameter set to SQL_ATTR_ODBC_VERSION and *ValuePtr* set to SQL_OV_ODBC3.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef6bc-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ef6bc-108">See Also</span></span>  
 [<span data-ttu-id="ef6bc-109">与 SQL Server &#40;ODBC&#41;通信</span><span class="sxs-lookup"><span data-stu-id="ef6bc-109">Communicating with SQL Server &#40;ODBC&#41;</span></span>](communicating-with-sql-server-odbc.md)  
  
  
