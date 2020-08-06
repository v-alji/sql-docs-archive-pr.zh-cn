---
title: 元数据发现 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: ec3c0f4f-f838-43ce-85f2-cf2761e2aac5
author: rothja
ms.author: jroth
ms.openlocfilehash: 571df9f21ab46a53c8aba7907039ce02afd6ad05
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688867"
---
# <a name="metadata-discovery"></a><span data-ttu-id="7f038-102">元数据发现</span><span class="sxs-lookup"><span data-stu-id="7f038-102">Metadata Discovery</span></span>
  <span data-ttu-id="7f038-103">中的元数据发现改进 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 允许 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 应用程序确保从执行查询返回的列或参数元数据与执行查询之前指定的元数据格式相同或与其兼容。</span><span class="sxs-lookup"><span data-stu-id="7f038-103">The metadata discovery improvement in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] allows [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client applications to ensure that column or parameter metadata returned from the execution of a query is identical to or compatible with the metadata format you specified before you executed the query.</span></span> <span data-ttu-id="7f038-104">如果执行查询后返回的元数据与执行该查询之前指定的元数据格式不兼容，您将会收到错误。</span><span class="sxs-lookup"><span data-stu-id="7f038-104">You will receive an error if the metadata returned after query execution is not compatible with the metadata format you specified before query execution.</span></span>  
  
 <span data-ttu-id="7f038-105">在 bcp 和 ODBC 函数以及 IBCPSession 和 IBCPSession2 接口中，您现在可以指定延迟读取（延迟的元数据发现）以避免对查询输出操作执行元数据发现。</span><span class="sxs-lookup"><span data-stu-id="7f038-105">In bcp and ODBC functions, and IBCPSession and IBCPSession2 interfaces, you can now specify a delayed read (delayed metadata discovery) to avoid metadata discovery for query out operations.</span></span> <span data-ttu-id="7f038-106">这样可以提高性能，并避免元数据发现失败。</span><span class="sxs-lookup"><span data-stu-id="7f038-106">This improves performance and eliminates metadata discovery failures.</span></span>  
  
 <span data-ttu-id="7f038-107">如果使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的 Native Client 开发应用程序 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] ，但连接到早于的服务器版本 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] ，则元数据发现功能将与服务器版本相对应。</span><span class="sxs-lookup"><span data-stu-id="7f038-107">If you develop an application using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] but connect to a server version earlier than [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], metadata discovery functionality will correspond to the version of the server.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f038-108">备注</span><span class="sxs-lookup"><span data-stu-id="7f038-108">Remarks</span></span>  
 <span data-ttu-id="7f038-109">[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 中增强了以下 bcp 函数，以提供改进的元数据发现：</span><span class="sxs-lookup"><span data-stu-id="7f038-109">The following bcp functions have been enhanced in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] to provide improved metadata discovery:</span></span>  
  
-   [<span data-ttu-id="7f038-110">bcp_columns</span><span class="sxs-lookup"><span data-stu-id="7f038-110">bcp_columns</span></span>](../../native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md)  
  
-   [<span data-ttu-id="7f038-111">bcp_control</span><span class="sxs-lookup"><span data-stu-id="7f038-111">bcp_control</span></span>](../../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)  
  
-   [<span data-ttu-id="7f038-112">bcp_getcolfmt</span><span class="sxs-lookup"><span data-stu-id="7f038-112">bcp_getcolfmt</span></span>](../../native-client-odbc-extensions-bulk-copy-functions/bcp-getcolfmt.md)  
  
-   [<span data-ttu-id="7f038-113">bcp_readfmt</span><span class="sxs-lookup"><span data-stu-id="7f038-113">bcp_readfmt</span></span>](../../native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md)  
  
-   [<span data-ttu-id="7f038-114">bcp_setcolfmt</span><span class="sxs-lookup"><span data-stu-id="7f038-114">bcp_setcolfmt</span></span>](../../native-client-odbc-extensions-bulk-copy-functions/bcp-setcolfmt.md)  
  
 <span data-ttu-id="7f038-115">使用[bcp_setbulkmode](../../native-client-odbc-extensions-bulk-copy-functions/bcp-setbulkmode.md)指定元数据格式时，您也会看到性能有所提高。</span><span class="sxs-lookup"><span data-stu-id="7f038-115">You will also see a performance improvement when specifying metadata format using [bcp_setbulkmode](../../native-client-odbc-extensions-bulk-copy-functions/bcp-setbulkmode.md).</span></span>  
  
 <span data-ttu-id="7f038-116">[bcp_control](../../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)提供了一个新的*eOption*来控制 bcp_readfmt 的行为： `BCPDELAYREADFMT` 。</span><span class="sxs-lookup"><span data-stu-id="7f038-116">[bcp_control](../../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) has a new *eOption* to control the behavior of bcp_readfmt: `BCPDELAYREADFMT`.</span></span>  
  
 <span data-ttu-id="7f038-117">[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 中增强了以下 ODBC 函数，以提供改进的元数据发现：</span><span class="sxs-lookup"><span data-stu-id="7f038-117">The following ODBC functions have been enhanced in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] to provide improved metadata discovery:</span></span>  
  
-   [<span data-ttu-id="7f038-118">SQLNumResultCols</span><span class="sxs-lookup"><span data-stu-id="7f038-118">SQLNumResultCols</span></span>](../../native-client-odbc-api/sqlnumresultcols.md)  
  
-   [<span data-ttu-id="7f038-119">SQLDescribeCol</span><span class="sxs-lookup"><span data-stu-id="7f038-119">SQLDescribeCol</span></span>](../../native-client-odbc-api/sqldescribecol.md)  
  
-   [<span data-ttu-id="7f038-120">SQLNumParams</span><span class="sxs-lookup"><span data-stu-id="7f038-120">SQLNumParams</span></span>](../../native-client-odbc-api/sqlnumparams.md)  
  
-   [<span data-ttu-id="7f038-121">SQLDescribeParam</span><span class="sxs-lookup"><span data-stu-id="7f038-121">SQLDescribeParam</span></span>](../../native-client-odbc-api/sqldescribeparam.md)  
  
 <span data-ttu-id="7f038-122">[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 中增强了以下 OLE DB 成员函数，以提供改进的元数据发现：</span><span class="sxs-lookup"><span data-stu-id="7f038-122">The following OLE DB member functions have been enhanced in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] to provide improved metadata discovery:</span></span>  
  
-   <span data-ttu-id="7f038-123">IColumnsInfo::GetColumnInfo</span><span class="sxs-lookup"><span data-stu-id="7f038-123">IColumnsInfo::GetColumnInfo</span></span>  
  
-   <span data-ttu-id="7f038-124">IColumnsRowset::GetColumnsRowset</span><span class="sxs-lookup"><span data-stu-id="7f038-124">IColumnsRowset::GetColumnsRowset</span></span>  
  
-   <span data-ttu-id="7f038-125">ICommandWithParameters::GetParameterInfo（有关详细信息，请参阅 [ICommandWithParameters](../../native-client-ole-db-interfaces/icommandwithparameters.md)）</span><span class="sxs-lookup"><span data-stu-id="7f038-125">ICommandWithParameters::GetParameterInfo (see [ICommandWithParameters](../../native-client-ole-db-interfaces/icommandwithparameters.md) for more information)</span></span>  
  
 <span data-ttu-id="7f038-126">使用 IBCPSession::BCPSetBulkMode 指定元数据格式时，也会看到性能改进</span><span class="sxs-lookup"><span data-stu-id="7f038-126">You will also see a performance improvement when specifying metadata format using IBCPSession::BCPSetBulkMode</span></span>  
  
 <span data-ttu-id="7f038-127">由于 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中新增了两个存储过程，[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client 中的元数据发现功能才得以改进：</span><span class="sxs-lookup"><span data-stu-id="7f038-127">The improved metadata discovery in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client is possible because of the addition of two stored procedures in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]:</span></span>  
  
-   <span data-ttu-id="7f038-128">sp_describe_first_result_set</span><span class="sxs-lookup"><span data-stu-id="7f038-128">sp_describe_first_result_set</span></span>  
  
-   <span data-ttu-id="7f038-129">sp_describe_undeclared_parameters</span><span class="sxs-lookup"><span data-stu-id="7f038-129">sp_describe_undeclared_parameters</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f038-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7f038-130">See Also</span></span>  
 [<span data-ttu-id="7f038-131">SQL Server Native Client 功能</span><span class="sxs-lookup"><span data-stu-id="7f038-131">SQL Server Native Client Features</span></span>](sql-server-native-client-features.md)  
  
  
