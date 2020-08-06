---
title: 跨版本兼容性 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), cross-version compatibility
ms.assetid: 5f14850b-b85c-41e2-8116-6f5b3f5e0856
author: rothja
ms.author: jroth
ms.openlocfilehash: af434713946f5c568ee71644a7403f9496a8c16f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589556"
---
# <a name="cross-version-compatibility"></a><span data-ttu-id="000d8-102">跨版本兼容性</span><span class="sxs-lookup"><span data-stu-id="000d8-102">Cross-Version Compatibility</span></span>
  <span data-ttu-id="000d8-103">如果期望让早于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 客户端或服务器实例处理表值参数，则会发生跨版本冲突。</span><span class="sxs-lookup"><span data-stu-id="000d8-103">Cross-version conflicts can occur when client or server instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] earlier than [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] are expected to process table-valued parameters.</span></span>  
  
 <span data-ttu-id="000d8-104">通常，表值参数功能仅对连接到 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]（或更高版本）服务器的 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 客户端（使用 SQL Server Native Client 10.0）或更高版本可用。</span><span class="sxs-lookup"><span data-stu-id="000d8-104">In general, table-valued parameter functionality is only available to [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] clients (using SQL Server Native Client 10.0) or later that are connected to [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (or later) servers.</span></span> <span data-ttu-id="000d8-105">仅当连接到 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (或更高版本) 服务器时，才会显示目录函数结果集中的新列。</span><span class="sxs-lookup"><span data-stu-id="000d8-105">New columns in catalog function result sets will only be present when connected to a [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (or later) server.</span></span>  
  
 <span data-ttu-id="000d8-106">如果用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 的更早版本编译的客户端应用程序执行了期望表值参数的语句，则服务器将通过数据转换错误检测到此情况，并且 ODBC 将以 SQLSTATE 07006 和消息“受限制的数据类型属性冲突”返回该错误。</span><span class="sxs-lookup"><span data-stu-id="000d8-106">If a client application compiled with an earlier version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client executes statements that expect table-valued parameters, the server detects this condition through a data conversion error, and ODBC returns this as a SQLSTATE 07006 and the message "Restricted data type attribute violation".</span></span>  
  
 <span data-ttu-id="000d8-107">如果使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native client 10.0 或更高版本编译的客户端应用程序在连接到早于的服务器实例时尝试使用表值 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 参数 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，则 Native client 将检测到此情况，并且 SQLBindCol、SQLBindParameter、SQLSetDescFields 和 SQLSetDescRec 调用将失败，并出现 SQLSTATE 07006 和消息 "受限制的数据类型属性冲突 (此连接的 SQL Server 版本不支持) " 表值参数。</span><span class="sxs-lookup"><span data-stu-id="000d8-107">If a client application that was compiled with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 10.0 or later tries to use table-valued parameters when connected to a server instance earlier than [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client will detect this, and SQLBindCol, SQLBindParameter, SQLSetDescFields, and SQLSetDescRec calls will fail with SQLSTATE 07006 and the message "Restricted data type attribute violation (the version of SQL Server for this connection does not support table-valued parameters)".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="000d8-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="000d8-108">See Also</span></span>  
 [<span data-ttu-id="000d8-109">ODBC&#41;&#40;表值参数</span><span class="sxs-lookup"><span data-stu-id="000d8-109">Table-Valued Parameters &#40;ODBC&#41;</span></span>](table-valued-parameters-odbc.md)  
  
  
