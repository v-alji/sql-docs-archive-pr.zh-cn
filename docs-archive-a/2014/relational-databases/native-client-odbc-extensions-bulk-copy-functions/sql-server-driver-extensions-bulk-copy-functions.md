---
title: 大容量复制函数 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], functions
- ODBC, bulk copy operations
- functions [ODBC]
ms.assetid: 6526b892-1d58-4f55-8335-f09887f6ea02
author: rothja
ms.author: jroth
ms.openlocfilehash: 02dba8cf4d510d2ec5f20e600302bb692c749f97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587797"
---
# <a name="bulk-copy-functions"></a><span data-ttu-id="282a0-102">大容量复制函数</span><span class="sxs-lookup"><span data-stu-id="282a0-102">Bulk Copy Functions</span></span>
  <span data-ttu-id="282a0-103">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序的特定于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的大容量复制 API 扩展，客户端应用程序可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表中快速添加或提取数据行。</span><span class="sxs-lookup"><span data-stu-id="282a0-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-specific bulk-copy API extension of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver allows client applications to rapidly add data rows to, or extract data rows from, a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="282a0-104">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 时，您可以在 SQLNCLI11.LIB 和 SQLNCLI.H 中引用大容量复制函数 (BCP)。</span><span class="sxs-lookup"><span data-stu-id="282a0-104">When using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, you can reference the bulk copy functions (BCP) in SQLNCLI11.LIB and SQLNCLI.H.</span></span>  
  
 <span data-ttu-id="282a0-105">使用 BCP API 函数调用的应用程序应与随该应用程序使用的驱动程序 (.dll) 提供的库 (.lib) 建立链接。</span><span class="sxs-lookup"><span data-stu-id="282a0-105">An application that uses BCP API function calls should link with the library (.lib) that shipped with the driver (.dll) used by the application.</span></span> <span data-ttu-id="282a0-106">BCP 应用程序不应链接到多个驱动程序库。</span><span class="sxs-lookup"><span data-stu-id="282a0-106">A BCP application should not link with more than one driver library.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="282a0-107">本节内容</span><span class="sxs-lookup"><span data-stu-id="282a0-107">In This Section</span></span>  
  
-   [<span data-ttu-id="282a0-108">bcp_batch</span><span class="sxs-lookup"><span data-stu-id="282a0-108">bcp_batch</span></span>](bcp-batch.md)  
  
-   [<span data-ttu-id="282a0-109">bcp_bind</span><span class="sxs-lookup"><span data-stu-id="282a0-109">bcp_bind</span></span>](bcp-bind.md)  
  
-   [<span data-ttu-id="282a0-110">bcp_colfmt</span><span class="sxs-lookup"><span data-stu-id="282a0-110">bcp_colfmt</span></span>](bcp-colfmt.md)  
  
-   [<span data-ttu-id="282a0-111">bcp_collen</span><span class="sxs-lookup"><span data-stu-id="282a0-111">bcp_collen</span></span>](bcp-collen.md)  
  
-   [<span data-ttu-id="282a0-112">bcp_colptr</span><span class="sxs-lookup"><span data-stu-id="282a0-112">bcp_colptr</span></span>](bcp-colptr.md)  
  
-   [<span data-ttu-id="282a0-113">bcp_columns</span><span class="sxs-lookup"><span data-stu-id="282a0-113">bcp_columns</span></span>](bcp-columns.md)  
  
-   [<span data-ttu-id="282a0-114">bcp_control</span><span class="sxs-lookup"><span data-stu-id="282a0-114">bcp_control</span></span>](bcp-control.md)  
  
-   [<span data-ttu-id="282a0-115">bcp_done</span><span class="sxs-lookup"><span data-stu-id="282a0-115">bcp_done</span></span>](bcp-done.md)  
  
-   [<span data-ttu-id="282a0-116">bcp_exec</span><span class="sxs-lookup"><span data-stu-id="282a0-116">bcp_exec</span></span>](bcp-exec.md)  
  
-   [<span data-ttu-id="282a0-117">bcp_getcolfmt</span><span class="sxs-lookup"><span data-stu-id="282a0-117">bcp_getcolfmt</span></span>](bcp-getcolfmt.md)  
  
-   [<span data-ttu-id="282a0-118">bcp_gettypename</span><span class="sxs-lookup"><span data-stu-id="282a0-118">bcp_gettypename</span></span>](bcp-gettypename.md)  
  
-   [<span data-ttu-id="282a0-119">bcp_init</span><span class="sxs-lookup"><span data-stu-id="282a0-119">bcp_init</span></span>](bcp-init.md)  
  
-   [<span data-ttu-id="282a0-120">bcp_moretext</span><span class="sxs-lookup"><span data-stu-id="282a0-120">bcp_moretext</span></span>](bcp-moretext.md)  
  
-   [<span data-ttu-id="282a0-121">bcp_readfmt</span><span class="sxs-lookup"><span data-stu-id="282a0-121">bcp_readfmt</span></span>](bcp-readfmt.md)  
  
-   [<span data-ttu-id="282a0-122">bcp_sendrow</span><span class="sxs-lookup"><span data-stu-id="282a0-122">bcp_sendrow</span></span>](bcp-sendrow.md)  
  
-   [<span data-ttu-id="282a0-123">bcp_setbulkmode</span><span class="sxs-lookup"><span data-stu-id="282a0-123">bcp_setbulkmode</span></span>](bcp-setbulkmode.md)  
  
-   [<span data-ttu-id="282a0-124">bcp_setcolfmt</span><span class="sxs-lookup"><span data-stu-id="282a0-124">bcp_setcolfmt</span></span>](bcp-setcolfmt.md)  
  
-   [<span data-ttu-id="282a0-125">bcp_writefmt</span><span class="sxs-lookup"><span data-stu-id="282a0-125">bcp_writefmt</span></span>](bcp-writefmt.md)  
  
## <a name="see-also"></a><span data-ttu-id="282a0-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="282a0-126">See Also</span></span>  
 <span data-ttu-id="282a0-127">[SQL Server 驱动程序扩展](../../database-engine/dev-guide/sql-server-driver-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="282a0-127">[SQL Server Driver Extensions](../../database-engine/dev-guide/sql-server-driver-extensions.md) </span></span>  
 [<span data-ttu-id="282a0-128">&#40;ODBC&#41;执行大容量复制操作</span><span class="sxs-lookup"><span data-stu-id="282a0-128">Performing Bulk Copy Operations &#40;ODBC&#41;</span></span>](../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
  
