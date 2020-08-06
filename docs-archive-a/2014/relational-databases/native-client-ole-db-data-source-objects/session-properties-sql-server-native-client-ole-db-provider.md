---
title: 会话属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- sessions [OLE DB]
- SQL Server Native Client OLE DB provider, sessions
ms.assetid: 2498fbad-b3db-4bea-8fc6-fef5317d3eba
author: rothja
ms.author: jroth
ms.openlocfilehash: 99f2bc6def0f470f653446c87216c3e854b2f819
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578186"
---
# <a name="session-properties"></a><span data-ttu-id="2a672-102">会话属性</span><span class="sxs-lookup"><span data-stu-id="2a672-102">Session Properties</span></span>
  <span data-ttu-id="2a672-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序按如下方式解释 OLE DB 的会话属性。</span><span class="sxs-lookup"><span data-stu-id="2a672-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider interprets OLE DB session properties as follows.</span></span>  
  
|<span data-ttu-id="2a672-104">属性 ID</span><span class="sxs-lookup"><span data-stu-id="2a672-104">Property ID</span></span>|<span data-ttu-id="2a672-105">说明</span><span class="sxs-lookup"><span data-stu-id="2a672-105">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="2a672-106">DBPROP_SESS_AUTOCOMMITISOLEVELS</span><span class="sxs-lookup"><span data-stu-id="2a672-106">DBPROP_SESS_AUTOCOMMITISOLEVELS</span></span>|<span data-ttu-id="2a672-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序支持所有的自动提交事务隔离级别，但 DBPROPVAL_TI_CHAOS 的混乱级别除外。</span><span class="sxs-lookup"><span data-stu-id="2a672-107">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports all autocommit transaction isolation levels with the exception of the chaos level DBPROPVAL_TI_CHAOS.</span></span>|  
  
 <span data-ttu-id="2a672-108">在特定于访问接口的属性集中 DBPROPSET_SQLSERVERSESSION， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序定义以下附加的会话属性。</span><span class="sxs-lookup"><span data-stu-id="2a672-108">In the provider-specific property set DBPROPSET_SQLSERVERSESSION, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider defines the following additional session property.</span></span>  
  
|<span data-ttu-id="2a672-109">属性 ID</span><span class="sxs-lookup"><span data-stu-id="2a672-109">Property ID</span></span>|<span data-ttu-id="2a672-110">说明</span><span class="sxs-lookup"><span data-stu-id="2a672-110">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="2a672-111">SSPROP_QUOTEDCATALOGNAMES</span><span class="sxs-lookup"><span data-stu-id="2a672-111">SSPROP_QUOTEDCATALOGNAMES</span></span>|<span data-ttu-id="2a672-112">键入：VT_BOOL</span><span class="sxs-lookup"><span data-stu-id="2a672-112">Type: VT_BOOL</span></span><br /><br /> <span data-ttu-id="2a672-113">R/W：读取/写入</span><span class="sxs-lookup"><span data-stu-id="2a672-113">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="2a672-114">默认值：VARIANT_FALSE</span><span class="sxs-lookup"><span data-stu-id="2a672-114">Default: VARIANT_FALSE</span></span><br /><br /> <span data-ttu-id="2a672-115">说明：在 CATALOG 限制中允许带引号的标识符。</span><span class="sxs-lookup"><span data-stu-id="2a672-115">Description: Quoted identifiers allowed in CATALOG restriction.</span></span><br /><br /> <span data-ttu-id="2a672-116">VARIANT_TRUE：对提供分布式查询支持的架构行集的目录限制识别带引号的标识符。</span><span class="sxs-lookup"><span data-stu-id="2a672-116">VARIANT_TRUE: Quoted identifiers are recognized for a catalog restriction for the schema rowsets that supply distributed query support.</span></span><br /><br /> <span data-ttu-id="2a672-117">VARIANT_FALSE：对提供分布式查询支持的架构行集的目录限制不识别带引号的标识符。</span><span class="sxs-lookup"><span data-stu-id="2a672-117">VARIANT_FALSE: Quoted identifiers are not recognized for a catalog restriction for the schema rowsets that supply distributed query support.</span></span><br /><br /> <span data-ttu-id="2a672-118">有关提供分布式查询支持的架构行集的详细信息，请参阅[架构行集中的分布式查询支持](../native-client/ole-db/schema-rowsets-distributed-query-support.md)。</span><span class="sxs-lookup"><span data-stu-id="2a672-118">For more information about schema rowsets that supply distributed query support, see [Distributed Query Support in Schema Rowsets](../native-client/ole-db/schema-rowsets-distributed-query-support.md).</span></span>|  
|<span data-ttu-id="2a672-119">SSPROP_ALLOWNATIVEVARIANT</span><span class="sxs-lookup"><span data-stu-id="2a672-119">SSPROP_ALLOWNATIVEVARIANT</span></span>|<span data-ttu-id="2a672-120">键入：VT_BOOL</span><span class="sxs-lookup"><span data-stu-id="2a672-120">Type: VT_BOOL</span></span><br /><br /> <span data-ttu-id="2a672-121">R/W：读/写</span><span class="sxs-lookup"><span data-stu-id="2a672-121">R/W: Read/Write</span></span><br /><br /> <span data-ttu-id="2a672-122">默认值：VARIANT_FALSE</span><span class="sxs-lookup"><span data-stu-id="2a672-122">Default: VARIANT_FALSE</span></span><br /><br /> <span data-ttu-id="2a672-123">说明：确定提取的数据是作为 DBTYPE_VARIANT 还是作为 DBTYPE_SQLVARIANT。</span><span class="sxs-lookup"><span data-stu-id="2a672-123">Description: Determines if the data fetched in is as DBTYPE_VARIANT or DBTYPE_SQLVARIANT.</span></span><br /><br /> <span data-ttu-id="2a672-124">VARIANT_TRUE：列类型作为 DBTYPE_SQLVARIANT 返回，这种情况下缓冲区将保留 SSVARIANT 结构。</span><span class="sxs-lookup"><span data-stu-id="2a672-124">VARIANT_TRUE: Column type is returned as DBTYPE_SQLVARIANT in which case the buffer will hold SSVARIANT structure.</span></span><br /><br /> <span data-ttu-id="2a672-125">VARIANT_FALSE：列类型作为 DBTYPE_VARIANT 返回，且缓冲区将具有 VARIANT 结构。</span><span class="sxs-lookup"><span data-stu-id="2a672-125">VARIANT_FALSE: Column type is returned as DBTYPE_VARIANT and the buffer will have VARIANT structure.</span></span>|  
|<span data-ttu-id="2a672-126">SSPROP_ASYNCH_BULKCOPY</span><span class="sxs-lookup"><span data-stu-id="2a672-126">SSPROP_ASYNCH_BULKCOPY</span></span>|<span data-ttu-id="2a672-127">若要使用异步模式，请在调用 BCPExec 方法之前，将特定于提供程序的会话属性 SSPROP_ASYNCH_BULKCOPY 设置为 VARIANT_TRUE。</span><span class="sxs-lookup"><span data-stu-id="2a672-127">To use asynchronous mode, set the provider specific session property SSPROP_ASYNCH_BULKCOPY to VARIANT_TRUE before calling the BCPExec method.</span></span> <span data-ttu-id="2a672-128">此属性位于 DBPROPSET_SQLSERVERSESSION 属性集中。</span><span class="sxs-lookup"><span data-stu-id="2a672-128">This property is available in the DBPROPSET_SQLSERVERSESSION property set.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2a672-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2a672-129">See Also</span></span>  
 [<span data-ttu-id="2a672-130">数据源对象 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="2a672-130">Data Source Objects &#40;OLE DB&#41;</span></span>](data-source-objects-ole-db.md)  
  
  
