---
title: " (ODBC) 执行大容量复制操作 |Microsoft Docs"
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC]
- ODBC, bulk copy operations
- minimally logged operations [SQL Server Native Client]
- bulk copy [ODBC], about bulk copy
ms.assetid: 5c793405-487c-4f52-88b8-0091d529afb3
author: rothja
ms.author: jroth
ms.openlocfilehash: f2647ebca703eab46d7be0e1cfc2490a65384ee6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693301"
---
# <a name="performing-bulk-copy-operations-odbc"></a><span data-ttu-id="18785-102">执行大容量复制操作 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="18785-102">Performing Bulk Copy Operations (ODBC)</span></span>
  <span data-ttu-id="18785-103">ODBC 标准不直接支持 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 大容量复制操作。</span><span class="sxs-lookup"><span data-stu-id="18785-103">The ODBC standard does not directly support [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bulk copy operations.</span></span> <span data-ttu-id="18785-104">连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本 7.0 或更高版本的实例时，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序支持执行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 大容量复制操作的 DB-Library 函数。</span><span class="sxs-lookup"><span data-stu-id="18785-104">When connected to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 7.0 or later, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver supports the DB-Library functions that perform [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bulk copy operations.</span></span> <span data-ttu-id="18785-105">这个特定于驱动程序的扩展为使用大容量复制函数的现有 DB-Library 应用程序提供了容易实现的升级路径。</span><span class="sxs-lookup"><span data-stu-id="18785-105">This driver-specific extension provides an easy upgrade path for existing DB-Library applications that use bulk copy functions.</span></span> <span data-ttu-id="18785-106">专用的大容量复制支持包含在以下文件中：</span><span class="sxs-lookup"><span data-stu-id="18785-106">The specialized bulk copy support is in the following files:</span></span>  
  
-   <span data-ttu-id="18785-107">sqlncli.h</span><span class="sxs-lookup"><span data-stu-id="18785-107">sqlncli.h</span></span>  
  
     <span data-ttu-id="18785-108">包括用于大容量复制函数的函数原型和常量定义。</span><span class="sxs-lookup"><span data-stu-id="18785-108">Includes function prototypes and constant definitions for bulk copy functions.</span></span> <span data-ttu-id="18785-109">必须在执行大容量复制操作的 ODBC 应用程序中包括 sqlncli.h，并且在编译应用程序时必须将其放在应用程序的 include 路径中。</span><span class="sxs-lookup"><span data-stu-id="18785-109">sqlncli.h must be included in the ODBC application performing bulk copy operations and must be in the application's include path when it is compiled.</span></span>  
  
-   <span data-ttu-id="18785-110">sqlncli11.lib</span><span class="sxs-lookup"><span data-stu-id="18785-110">sqlncli11.lib</span></span>  
  
     <span data-ttu-id="18785-111">必须放在链接器的库路径中，并将其指定为要链接的文件。</span><span class="sxs-lookup"><span data-stu-id="18785-111">Must be in the library path of the linker and specified as a file to be linked.</span></span> <span data-ttu-id="18785-112">sqlncli11.lib 随 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序一起分发。</span><span class="sxs-lookup"><span data-stu-id="18785-112">sqlncli11.lib is distributed with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span>  
  
-   <span data-ttu-id="18785-113">sqlncli11.dll</span><span class="sxs-lookup"><span data-stu-id="18785-113">sqlncli11.dll</span></span>  
  
     <span data-ttu-id="18785-114">在执行时必须存在。</span><span class="sxs-lookup"><span data-stu-id="18785-114">Must be present at execution time.</span></span> <span data-ttu-id="18785-115">sqlncli11.dll 随 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序一起分发。</span><span class="sxs-lookup"><span data-stu-id="18785-115">sqlncli11.dll is distributed with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="18785-116">ODBC **SQLBulkOperations**函数与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 大容量复制函数没有关系。</span><span class="sxs-lookup"><span data-stu-id="18785-116">The ODBC **SQLBulkOperations** function has no relationship to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bulk copy functions.</span></span> <span data-ttu-id="18785-117">应用程序必须使用特定于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的大容量复制函数，才能执行大容量复制操作。</span><span class="sxs-lookup"><span data-stu-id="18785-117">Applications must use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-specific bulk-copy functions to perform bulk copy operations.</span></span>  
  
## <a name="minimally-logging-bulk-copies"></a><span data-ttu-id="18785-118">按最小方式记录大容量复制</span><span class="sxs-lookup"><span data-stu-id="18785-118">Minimally Logging Bulk Copies</span></span>  
 <span data-ttu-id="18785-119">使用完整恢复模式，将在事务日志中完整记录大容量加载所执行的所有行插入操作。</span><span class="sxs-lookup"><span data-stu-id="18785-119">With the Full Recovery model, all row-insert operations performed by bulk load are fully logged in the transaction log.</span></span> <span data-ttu-id="18785-120">对于大型数据加载，这会导致事务日志被迅速填充。</span><span class="sxs-lookup"><span data-stu-id="18785-120">For large data loads, this can cause the transaction log to fill rapidly.</span></span> <span data-ttu-id="18785-121">在某些情况下，按最小方式记录是可能的。</span><span class="sxs-lookup"><span data-stu-id="18785-121">Under certain conditions, minimally logging is possible.</span></span> <span data-ttu-id="18785-122">按最小方式记录将减少大容量加载操作填充日志空间的可能性，并且比完整记录更有效。</span><span class="sxs-lookup"><span data-stu-id="18785-122">Minimal logging reduces the possibility of a bulk load operation filling the log space and is also more efficient than full logging.</span></span>  
  
 <span data-ttu-id="18785-123">有关使用最小日志记录的信息，请参阅[批量导入中最小日志记录的先决条件](../import-export/prerequisites-for-minimal-logging-in-bulk-import.md)。</span><span class="sxs-lookup"><span data-stu-id="18785-123">For information on using minimal logging, see [Prerequisites for Minimal Logging in Bulk Import](../import-export/prerequisites-for-minimal-logging-in-bulk-import.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="18785-124">备注</span><span class="sxs-lookup"><span data-stu-id="18785-124">Remarks</span></span>  
 <span data-ttu-id="18785-125">在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 或更高版本中使用 bcp.exe 时，可能在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 之前未出现错误的情形下出现错误。</span><span class="sxs-lookup"><span data-stu-id="18785-125">When using bcp.exe in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later, you might see errors in situations where there were no errors prior to [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="18785-126">这是因为在更高版本中 bcp.exe 不再执行隐式的数据类型转换。</span><span class="sxs-lookup"><span data-stu-id="18785-126">This is because in the later versions, bcp.exe no longer performs implicit data type conversion.</span></span> <span data-ttu-id="18785-127">在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 之前，如果目标表有 money 数据类型，则 bcp.exe 会将数字数据转换为 money 数据类型。</span><span class="sxs-lookup"><span data-stu-id="18785-127">Prior to [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], bcp.exe converted numeric data to a money data type, if the target table had a money data type.</span></span> <span data-ttu-id="18785-128">但是，在这种情况下，bcp.exe 只是截断额外的字段。</span><span class="sxs-lookup"><span data-stu-id="18785-128">However, in that situation, bcp.exe simply truncated extra fields.</span></span> <span data-ttu-id="18785-129">从 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 开始，如果文件和目标表的数据类型不匹配，那么，只要有任何数据必须在截断后才能适合放到目标表中，则 bcp.exe 将引发错误。</span><span class="sxs-lookup"><span data-stu-id="18785-129">Beginning in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], if data types do not match between the file and the target table, bcp.exe will raise an error if there is any data that would have to be truncated to fit into the target table.</span></span> <span data-ttu-id="18785-130">若要解决该错误，请修复数据，使其与目标数据类型匹配。</span><span class="sxs-lookup"><span data-stu-id="18785-130">To resolve this error, fix the data to match the target data type.</span></span> <span data-ttu-id="18785-131">另外，也可以选择使用在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以前的版本中的 bcp.exe。</span><span class="sxs-lookup"><span data-stu-id="18785-131">Optionally, use bcp.exe from a release prior to [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="18785-132">本节内容</span><span class="sxs-lookup"><span data-stu-id="18785-132">In This Section</span></span>  
  
-   [<span data-ttu-id="18785-133">使用数据文件和格式化文件</span><span class="sxs-lookup"><span data-stu-id="18785-133">Using Data Files and Format Files</span></span>](using-data-files-and-format-files.md)  
  
-   [<span data-ttu-id="18785-134">从程序变量执行大容量复制</span><span class="sxs-lookup"><span data-stu-id="18785-134">Bulk Copying from Program Variables</span></span>](bulk-copying-from-program-variables.md)  
  
-   [<span data-ttu-id="18785-135">管理大容量复制的批大小</span><span class="sxs-lookup"><span data-stu-id="18785-135">Managing Bulk Copy Batch Sizes</span></span>](managing-bulk-copy-batch-sizes.md)  
  
-   [<span data-ttu-id="18785-136">大容量复制文本和图像数据</span><span class="sxs-lookup"><span data-stu-id="18785-136">Bulk Copying Text and Image Data</span></span>](bulk-copying-text-and-image-data.md)  
  
-   [<span data-ttu-id="18785-137">从 DB-Library 转换到 ODBC 大容量复制</span><span class="sxs-lookup"><span data-stu-id="18785-137">Converting from DB-Library to ODBC Bulk Copy</span></span>](converting-from-db-library-to-odbc-bulk-copy.md)  
  
## <a name="see-also"></a><span data-ttu-id="18785-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="18785-138">See Also</span></span>  
 <span data-ttu-id="18785-139">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="18785-139">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span></span>  
 [<span data-ttu-id="18785-140">批量导入和导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="18785-140">Bulk Import and Export of Data &#40;SQL Server&#41;</span></span>](../import-export/bulk-import-and-export-of-data-sql-server.md)  
  
  
