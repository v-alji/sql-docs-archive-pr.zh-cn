---
title: OLE DB API 对日期和时间增强功能的支持 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, date/time improvements
ms.assetid: e65c9253-bd99-4dc3-9cb8-7613f754c966
author: rothja
ms.author: jroth
ms.openlocfilehash: cdb17f0d2104373ea797ff9403cc417dfaa3d868
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589549"
---
# <a name="ole-db-api-support-for-date-and-time-enhancements"></a><span data-ttu-id="3874f-102">OLE DB API 对日期和时间增强功能的支持</span><span class="sxs-lookup"><span data-stu-id="3874f-102">OLE DB API Support for Date and Time Enhancements</span></span>
  <span data-ttu-id="3874f-103">以下 OLE DB API 支持日期/时间增强功能。</span><span class="sxs-lookup"><span data-stu-id="3874f-103">The following OLE DB APIs support enhanced date/time features.</span></span>  
  
|<span data-ttu-id="3874f-104">函数</span><span class="sxs-lookup"><span data-stu-id="3874f-104">Function</span></span>|<span data-ttu-id="3874f-105">说明</span><span class="sxs-lookup"><span data-stu-id="3874f-105">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="3874f-106">IAccessor::CreateAccessor</span><span class="sxs-lookup"><span data-stu-id="3874f-106">IAccessor::CreateAccessor</span></span>|<span data-ttu-id="3874f-107">DBBINDING 结构中添加了一个标志，用于支持应用程序区分 `datetime`、`datetime2` 和 `smalldatetime` 的值。</span><span class="sxs-lookup"><span data-stu-id="3874f-107">A flag is added in the DBBINDING structure to enable applications to discriminate between `datetime`, `datetime2`, and `smalldatetime` values.</span></span> <span data-ttu-id="3874f-108">有关详细信息，请参阅[参数和行集元数据](metadata-parameter-and-rowset.md)。</span><span class="sxs-lookup"><span data-stu-id="3874f-108">For more information, see [Parameter and Rowset Metadata](metadata-parameter-and-rowset.md).</span></span>|  
|<span data-ttu-id="3874f-109">IBCPSession::BCPColFmt</span><span class="sxs-lookup"><span data-stu-id="3874f-109">IBCPSession::BCPColFmt</span></span>|<span data-ttu-id="3874f-110">有关详细信息，请参阅[&#40;OLE DB 和 ODBC&#41;的增强日期和时间类型的大容量复制更改](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="3874f-110">For more information, see [Bulk Copy Changes for Enhanced Date and Time Types &#40;OLE DB and ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).</span></span>|  
|<span data-ttu-id="3874f-111">ICommandWithParameters::GetParameterInfo</span><span class="sxs-lookup"><span data-stu-id="3874f-111">ICommandWithParameters::GetParameterInfo</span></span>|<span data-ttu-id="3874f-112">有关详细信息，请参阅[参数和行集元数据](metadata-parameter-and-rowset.md)。</span><span class="sxs-lookup"><span data-stu-id="3874f-112">For more information, see[Parameter and Rowset Metadata](metadata-parameter-and-rowset.md).</span></span>|  
|<span data-ttu-id="3874f-113">ICommandWithParameters::SetParameterinfo</span><span class="sxs-lookup"><span data-stu-id="3874f-113">ICommandWithParameters::SetParameterinfo</span></span>|<span data-ttu-id="3874f-114">有关详细信息，请参阅[参数和行集元数据](metadata-parameter-and-rowset.md)。</span><span class="sxs-lookup"><span data-stu-id="3874f-114">For more information, see[Parameter and Rowset Metadata](metadata-parameter-and-rowset.md).</span></span>|  
|<span data-ttu-id="3874f-115">IColumnsRowset::GetColumnsRowset</span><span class="sxs-lookup"><span data-stu-id="3874f-115">IColumnsRowset::GetColumnsRowset</span></span>|<span data-ttu-id="3874f-116">有关详细信息，请参阅[参数和行集元数据](metadata-parameter-and-rowset.md)。</span><span class="sxs-lookup"><span data-stu-id="3874f-116">For more information, see[Parameter and Rowset Metadata](metadata-parameter-and-rowset.md).</span></span>|  
|<span data-ttu-id="3874f-117">IColumnsInfo::GetColumnInfo</span><span class="sxs-lookup"><span data-stu-id="3874f-117">IColumnsInfo::GetColumnInfo</span></span>|<span data-ttu-id="3874f-118">有关详细信息，请参阅[参数和行集元数据](metadata-parameter-and-rowset.md)。</span><span class="sxs-lookup"><span data-stu-id="3874f-118">For more information, see[Parameter and Rowset Metadata](metadata-parameter-and-rowset.md).</span></span>|  
|<span data-ttu-id="3874f-119">IDBSchemaRowset::GetRowset</span><span class="sxs-lookup"><span data-stu-id="3874f-119">IDBSchemaRowset::GetRowset</span></span>|<span data-ttu-id="3874f-120">若要详细了解受影响的架构行集，请参阅[日期和时间与架构行集](../native-client-ole-db-rowsets/rowsets.md)。</span><span class="sxs-lookup"><span data-stu-id="3874f-120">For details of the affected schema rowsets, see[Date and Time and Schema Rowsets](../native-client-ole-db-rowsets/rowsets.md).</span></span>|  
|<span data-ttu-id="3874f-121">IRowsetFastLoad</span><span class="sxs-lookup"><span data-stu-id="3874f-121">IRowsetFastLoad</span></span>|<span data-ttu-id="3874f-122">此接口支持新的日期/时间类型，但对其接口没有任何更改。</span><span class="sxs-lookup"><span data-stu-id="3874f-122">This interface supports the new date/time types, but there is no change to its interface.</span></span>|  
|<span data-ttu-id="3874f-123">ITableDefinition::CreateTable</span><span class="sxs-lookup"><span data-stu-id="3874f-123">ITableDefinition::CreateTable</span></span>|<span data-ttu-id="3874f-124">有关详细信息，请参阅[针对 OLE DB 日期和时间改进的数据类型支持](data-type-support-for-ole-db-date-and-time-improvements.md)。</span><span class="sxs-lookup"><span data-stu-id="3874f-124">For more information, see [Data Type Support for OLE DB Date and Time Improvements](data-type-support-for-ole-db-date-and-time-improvements.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3874f-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3874f-125">See Also</span></span>  
 [<span data-ttu-id="3874f-126">日期和时间改进 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="3874f-126">Date and Time Improvements &#40;OLE DB&#41;</span></span>](date-and-time-improvements-ole-db.md)  
  
  
