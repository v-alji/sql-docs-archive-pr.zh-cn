---
title: 为 OLE DB 表值参数更改的架构行集 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- schema rowsets [OLE DB]
- table-valued parameters (OLE DB), schema rowsets changed for (OLE DB)
ms.assetid: 581e3ead-53db-44da-8718-f3fc4b5108f1
author: rothja
ms.author: jroth
ms.openlocfilehash: e09d5127f332c8b6cc948be3eeb74e600bb856f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692878"
---
# <a name="schema-rowsets-changed-for-ole-db-table-valued-parameters"></a><span data-ttu-id="aa1b9-102">为 OLE DB 表值参数更改的架构行集</span><span class="sxs-lookup"><span data-stu-id="aa1b9-102">Schema Rowsets Changed for OLE DB Table-Valued Parameters</span></span>
  <span data-ttu-id="aa1b9-103">以下为已更改或添加以支持表值参数的架构行集。</span><span class="sxs-lookup"><span data-stu-id="aa1b9-103">The following are the schema rowsets that have been changed or added to support table-valued parameters.</span></span>  
  
|<span data-ttu-id="aa1b9-104">架构行集</span><span class="sxs-lookup"><span data-stu-id="aa1b9-104">Schema rowset</span></span>|<span data-ttu-id="aa1b9-105">说明</span><span class="sxs-lookup"><span data-stu-id="aa1b9-105">Description</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="aa1b9-106">DBSCHEMA_PROCEDURE_PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="aa1b9-106">DBSCHEMA_PROCEDURE_PARAMETERS</span></span>|<span data-ttu-id="aa1b9-107">在名为 SS_TYPE_CATALOG_NAME 和 SS_TYPE_SCHEMANAME 的行集末尾添加了两个新列。</span><span class="sxs-lookup"><span data-stu-id="aa1b9-107">Two new columns were added at the end of the rowset named SS_TYPE_CATALOG_NAME and SS_TYPE_SCHEMANAME.</span></span> <span data-ttu-id="aa1b9-108">这些列可供将来的类型重用。</span><span class="sxs-lookup"><span data-stu-id="aa1b9-108">These columns could be re-used for future types.</span></span> <span data-ttu-id="aa1b9-109">TYPE_NAME 和 LOCAL_TYPE_NAME 列将包含表值参数 TABLE 类型的名称。</span><span class="sxs-lookup"><span data-stu-id="aa1b9-109">The TYPE_NAME and LOCAL_TYPE_NAME columns will contain the name of the table-valued parameter TABLE type.</span></span> <span data-ttu-id="aa1b9-110">DATA_TYPE 列将具有表值参数的值 DBTYPE_TABLE = 143。</span><span class="sxs-lookup"><span data-stu-id="aa1b9-110">The DATA_TYPE column will have value DBTYPE_TABLE = 143 for table-valued parameters.</span></span>|  
|<span data-ttu-id="aa1b9-111">DBSCHEMA_TABLE_TYPES</span><span class="sxs-lookup"><span data-stu-id="aa1b9-111">DBSCHEMA_TABLE_TYPES</span></span>|<span data-ttu-id="aa1b9-112">添加了此行集以支持表值参数。</span><span class="sxs-lookup"><span data-stu-id="aa1b9-112">This rowset was added to support table-valued parameters.</span></span> <span data-ttu-id="aa1b9-113">此行集与 DBSCHEMA_TABLES 基本相同，不同的是它仅为表类型而非表、视图或同义词返回元数据。</span><span class="sxs-lookup"><span data-stu-id="aa1b9-113">It is identical to DBSCHEMA_TABLES, except that it returns metadata only for table types, rather than for tables, views, or synonyms.</span></span> <span data-ttu-id="aa1b9-114">TABLE_TYPE 列将具有值“TABLE TYPE”。</span><span class="sxs-lookup"><span data-stu-id="aa1b9-114">The TABLE_TYPE column will have the value 'TABLE TYPE'.</span></span>|  
|<span data-ttu-id="aa1b9-115">DBSCHEMA_TABLE_TYPE_PRIMARY_KEYS</span><span class="sxs-lookup"><span data-stu-id="aa1b9-115">DBSCHEMA_TABLE_TYPE_PRIMARY_KEYS</span></span>|<span data-ttu-id="aa1b9-116">添加了此行集以支持表值参数。</span><span class="sxs-lookup"><span data-stu-id="aa1b9-116">This rowset was added to support table-valued parameters.</span></span> <span data-ttu-id="aa1b9-117">此行集与 DBSCHEMA_PRIMARY_KEYS 基本相同，不同的是它只为表类型而非表返回主键元数据。</span><span class="sxs-lookup"><span data-stu-id="aa1b9-117">It is identical to DBSCHEMA_PRIMARY_KEYS, except that it returns primary keys metadata only for table types, rather than for tables.</span></span>|  
|<span data-ttu-id="aa1b9-118">DBSCHEMA_TABLE_TYPE_COLUMNS</span><span class="sxs-lookup"><span data-stu-id="aa1b9-118">DBSCHEMA_TABLE_TYPE_COLUMNS</span></span>|<span data-ttu-id="aa1b9-119">添加了此行集以支持表值参数。</span><span class="sxs-lookup"><span data-stu-id="aa1b9-119">This rowset was added to support table-valued parameters.</span></span> <span data-ttu-id="aa1b9-120">此行集与 DBSCHEMA_COLUMNS 基本相同，不同的是它仅为表类型而非表、视图或同义词返回列元数据。</span><span class="sxs-lookup"><span data-stu-id="aa1b9-120">It is identical to DBSCHEMA_COLUMNS, except that it returns column metadata only for table types, rather than for tables, views, or synonyms.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aa1b9-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aa1b9-121">See Also</span></span>  
 <span data-ttu-id="aa1b9-122">[表值参数 &#40;OLE DB&#41;](table-valued-parameters-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="aa1b9-122">[Table-Valued Parameters &#40;OLE DB&#41;](table-valued-parameters-ole-db.md) </span></span>  
 [<span data-ttu-id="aa1b9-123">使用表值参数 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="aa1b9-123">Use Table-Valued Parameters &#40;OLE DB&#41;</span></span>](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
