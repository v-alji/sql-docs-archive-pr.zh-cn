---
title: 创建 SQL Server 索引 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- CreateIndex function
- constraints [OLE DB]
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
- adding indexes
ms.assetid: 6239d440-2818-4b98-bb79-732dced41952
author: rothja
ms.author: jroth
ms.openlocfilehash: 3693355eec7a290c03658c10db500161aa52062d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692874"
---
# <a name="creating-sql-server-indexes"></a><span data-ttu-id="448dc-102">创建 SQL Server 索引</span><span class="sxs-lookup"><span data-stu-id="448dc-102">Creating SQL Server Indexes</span></span>
  <span data-ttu-id="448dc-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序公开**IIndexDefinition：： CreateIndex**函数，允许使用者定义表的新索引 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="448dc-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **IIndexDefinition::CreateIndex** function, allowing consumers to define new indexes on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables.</span></span>  
  
 <span data-ttu-id="448dc-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序将表索引创建为索引或约束。</span><span class="sxs-lookup"><span data-stu-id="448dc-104">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider creates table indexes as either indexes or constraints.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="448dc-105">向表所有者、数据库所有者和某些管理角色的成员提供约束创建特权。</span><span class="sxs-lookup"><span data-stu-id="448dc-105">gives constraint-creation privilege to the table owner, database owner, and members of certain administrative roles.</span></span> <span data-ttu-id="448dc-106">默认情况下，只有表所有者才能对表创建索引。</span><span class="sxs-lookup"><span data-stu-id="448dc-106">By default, only the table owner can create an index on a table.</span></span> <span data-ttu-id="448dc-107">因此，CreateIndex 的成功或失败不仅取决于应用程序用户的访问权限，还取决于所创建索引的类型\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="448dc-107">Therefore, the success or failure of **CreateIndex** depends not only on the application user's access rights but also on the type of index created.</span></span>  
  
 <span data-ttu-id="448dc-108">在 pTableID 参数的 uName 联合的 pwszName 成员中，使用者将表名指定为 Unicode 字符串\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="448dc-108">Consumers specify the table name as a Unicode character string in the *pwszName* member of the *uName* union in the *pTableID* parameter.</span></span> <span data-ttu-id="448dc-109">pTableID 的 eKind 成员必须是 DBKIND_NAME\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="448dc-109">The *eKind* member of *pTableID* must be DBKIND_NAME.</span></span>  
  
 <span data-ttu-id="448dc-110">*PIndexID*参数可以为 NULL，如果是，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序为索引创建唯一名称。</span><span class="sxs-lookup"><span data-stu-id="448dc-110">The *pIndexID* parameter can be NULL, and if it is, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider creates a unique name for the index.</span></span> <span data-ttu-id="448dc-111">通过在 ppIndexID 参数中指定一个指向 DBID 的有效指针，使用者可以捕获索引的名称\*\*。</span><span class="sxs-lookup"><span data-stu-id="448dc-111">The consumer can capture the name of the index by specifying a valid pointer to a DBID in the *ppIndexID* parameter.</span></span>  
  
 <span data-ttu-id="448dc-112">在 pIndexID 参数的 uName 联合的 pwszName 成员中，使用者可以将索引名称指定为 Unicode 字符串\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="448dc-112">The consumer can specify the index name as a Unicode character string in the *pwszName* member of the *uName* union of the *pIndexID* parameter.</span></span> <span data-ttu-id="448dc-113">pIndexID 的 eKind 成员必须是 DBKIND_NAME\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="448dc-113">The *eKind* member of *pIndexID* must be DBKIND_NAME.</span></span>  
  
 <span data-ttu-id="448dc-114">使用者按名称指定参与索引的一个或多个列。</span><span class="sxs-lookup"><span data-stu-id="448dc-114">The consumer specifies the column or columns participating in the index by name.</span></span> <span data-ttu-id="448dc-115">对于在 CreateIndex 中使用的每个 DBINDEXCOLUMNDESC 结构，pColumnID 的 eKind 成员必须为 DBKIND_NAME\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="448dc-115">For each DBINDEXCOLUMNDESC structure used in **CreateIndex**, the *eKind* member of the *pColumnID* must be DBKIND_NAME.</span></span> <span data-ttu-id="448dc-116">在 pColumnID 的 uName 联合的 pwszName 成员中，列名指定为 Unicode 字符串\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="448dc-116">The name of the column is specified as a Unicode character string in the *pwszName* member of the *uName* union in the *pColumnID*.</span></span>  
  
 <span data-ttu-id="448dc-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序，并 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支持对索引中的值进行升序排序。</span><span class="sxs-lookup"><span data-stu-id="448dc-117">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] support ascending order on values in the index.</span></span> <span data-ttu-id="448dc-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]如果使用者在任何 DBINDEXCOLUMNDESC 结构中指定 DBINDEX_COL_ORDER_DESC，则 Native Client OLE DB 提供程序将返回 E_INVALIDARG。</span><span class="sxs-lookup"><span data-stu-id="448dc-118">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns E_INVALIDARG if the consumer specifies DBINDEX_COL_ORDER_DESC in any DBINDEXCOLUMNDESC structure.</span></span>  
  
 <span data-ttu-id="448dc-119">CreateIndex 对索引属性的解释如下\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="448dc-119">**CreateIndex** interprets index properties as follows.</span></span>  
  
|<span data-ttu-id="448dc-120">属性 ID</span><span class="sxs-lookup"><span data-stu-id="448dc-120">Property ID</span></span>|<span data-ttu-id="448dc-121">说明</span><span class="sxs-lookup"><span data-stu-id="448dc-121">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="448dc-122">DBPROP_INDEX_AUTOUPDATE</span><span class="sxs-lookup"><span data-stu-id="448dc-122">DBPROP_INDEX_AUTOUPDATE</span></span>|<span data-ttu-id="448dc-123">R/W：读取/写入</span><span class="sxs-lookup"><span data-stu-id="448dc-123">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="448dc-124">默认值：无</span><span class="sxs-lookup"><span data-stu-id="448dc-124">Default: None</span></span><br /><br /> <span data-ttu-id="448dc-125">说明： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序不支持此属性。</span><span class="sxs-lookup"><span data-stu-id="448dc-125">Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not support this property.</span></span> <span data-ttu-id="448dc-126">尝试在 CreateIndex 中设置此属性将导致出现 DB_S_ERRORSOCCURRED 返回值\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="448dc-126">Attempts to set the property in **CreateIndex** cause a DB_S_ERRORSOCCURRED return value.</span></span> <span data-ttu-id="448dc-127">此属性结构的 dwStatus 成员指示 DBPROPSTATUS_BADVALUE\*\*。</span><span class="sxs-lookup"><span data-stu-id="448dc-127">The *dwStatus* member of the property structure indicates DBPROPSTATUS_BADVALUE.</span></span>|  
|<span data-ttu-id="448dc-128">DBPROP_INDEX_CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="448dc-128">DBPROP_INDEX_CLUSTERED</span></span>|<span data-ttu-id="448dc-129">R/W：读取/写入</span><span class="sxs-lookup"><span data-stu-id="448dc-129">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="448dc-130">默认值：VARIANT_FALSE</span><span class="sxs-lookup"><span data-stu-id="448dc-130">Default: VARIANT_FALSE</span></span><br /><br /> <span data-ttu-id="448dc-131">说明：控制索引聚类分析。</span><span class="sxs-lookup"><span data-stu-id="448dc-131">Description: Controls index clustering.</span></span><br /><br /> <span data-ttu-id="448dc-132">VARIANT_TRUE： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序尝试对表创建聚集索引 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="448dc-132">VARIANT_TRUE: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider attempts to create a clustered index on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="448dc-133">支持对任何表最多创建一个聚集索引。</span><span class="sxs-lookup"><span data-stu-id="448dc-133">supports at most one clustered index on any table.</span></span><br /><br /> <span data-ttu-id="448dc-134">VARIANT_FALSE： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序尝试对表创建非聚集索引 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="448dc-134">VARIANT_FALSE: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider attempts to create a nonclustered index on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>|  
|<span data-ttu-id="448dc-135">DBPROP_INDEX_FILLFACTOR</span><span class="sxs-lookup"><span data-stu-id="448dc-135">DBPROP_INDEX_FILLFACTOR</span></span>|<span data-ttu-id="448dc-136">R/W：读取/写入</span><span class="sxs-lookup"><span data-stu-id="448dc-136">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="448dc-137">默认值：0</span><span class="sxs-lookup"><span data-stu-id="448dc-137">Default: 0</span></span><br /><br /> <span data-ttu-id="448dc-138">说明：指定用于存储的索引页所占的百分比。</span><span class="sxs-lookup"><span data-stu-id="448dc-138">Description: Specifies the percentage of an index page used for storage.</span></span> <span data-ttu-id="448dc-139">有关详细信息，请参阅[创建索引](/sql/t-sql/statements/create-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="448dc-139">For more information, see [CREATE INDEX](/sql/t-sql/statements/create-index-transact-sql).</span></span><br /><br /> <span data-ttu-id="448dc-140">变量类型为 VT_I4。</span><span class="sxs-lookup"><span data-stu-id="448dc-140">The type of the variant is VT_I4.</span></span> <span data-ttu-id="448dc-141">该值必须大于或等于 1 且小于或等于 100。</span><span class="sxs-lookup"><span data-stu-id="448dc-141">The value must be greater than or equal to 1 and less than or equal to 100.</span></span>|  
|<span data-ttu-id="448dc-142">DBPROP_INDEX_INITIALIZE</span><span class="sxs-lookup"><span data-stu-id="448dc-142">DBPROP_INDEX_INITIALIZE</span></span>|<span data-ttu-id="448dc-143">R/W：读取/写入</span><span class="sxs-lookup"><span data-stu-id="448dc-143">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="448dc-144">默认值：无</span><span class="sxs-lookup"><span data-stu-id="448dc-144">Default: None</span></span><br /><br /> <span data-ttu-id="448dc-145">说明： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序不支持此属性。</span><span class="sxs-lookup"><span data-stu-id="448dc-145">Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not support this property.</span></span> <span data-ttu-id="448dc-146">尝试在 CreateIndex 中设置此属性将导致出现 DB_S_ERRORSOCCURRED 返回值\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="448dc-146">Attempts to set the property in **CreateIndex** cause a DB_S_ERRORSOCCURRED return value.</span></span> <span data-ttu-id="448dc-147">此属性结构的 dwStatus 成员指示 DBPROPSTATUS_BADVALUE\*\*。</span><span class="sxs-lookup"><span data-stu-id="448dc-147">The *dwStatus* member of the property structure indicates DBPROPSTATUS_BADVALUE.</span></span>|  
|<span data-ttu-id="448dc-148">DBPROP_INDEX_NULLCOLLATION</span><span class="sxs-lookup"><span data-stu-id="448dc-148">DBPROP_INDEX_NULLCOLLATION</span></span>|<span data-ttu-id="448dc-149">R/W：读取/写入</span><span class="sxs-lookup"><span data-stu-id="448dc-149">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="448dc-150">默认值：无</span><span class="sxs-lookup"><span data-stu-id="448dc-150">Default: None</span></span><br /><br /> <span data-ttu-id="448dc-151">说明： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序不支持此属性。</span><span class="sxs-lookup"><span data-stu-id="448dc-151">Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not support this property.</span></span> <span data-ttu-id="448dc-152">尝试在 CreateIndex 中设置此属性将导致出现 DB_S_ERRORSOCCURRED 返回值\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="448dc-152">Attempts to set the property in **CreateIndex** cause a DB_S_ERRORSOCCURRED return value.</span></span> <span data-ttu-id="448dc-153">此属性结构的 dwStatus 成员指示 DBPROPSTATUS_BADVALUE\*\*。</span><span class="sxs-lookup"><span data-stu-id="448dc-153">The *dwStatus* member of the property structure indicates DBPROPSTATUS_BADVALUE.</span></span>|  
|<span data-ttu-id="448dc-154">DBPROP_INDEX_NULLS</span><span class="sxs-lookup"><span data-stu-id="448dc-154">DBPROP_INDEX_NULLS</span></span>|<span data-ttu-id="448dc-155">R/W：读取/写入</span><span class="sxs-lookup"><span data-stu-id="448dc-155">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="448dc-156">默认值：无</span><span class="sxs-lookup"><span data-stu-id="448dc-156">Default: None</span></span><br /><br /> <span data-ttu-id="448dc-157">说明： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序不支持此属性。</span><span class="sxs-lookup"><span data-stu-id="448dc-157">Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not support this property.</span></span> <span data-ttu-id="448dc-158">尝试在 CreateIndex 中设置此属性将导致出现 DB_S_ERRORSOCCURRED 返回值\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="448dc-158">Attempts to set the property in **CreateIndex** cause a DB_S_ERRORSOCCURRED return value.</span></span> <span data-ttu-id="448dc-159">此属性结构的 dwStatus 成员指示 DBPROPSTATUS_BADVALUE\*\*。</span><span class="sxs-lookup"><span data-stu-id="448dc-159">The *dwStatus* member of the property structure indicates DBPROPSTATUS_BADVALUE.</span></span>|  
|<span data-ttu-id="448dc-160">DBPROP_INDEX_PRIMARYKEY</span><span class="sxs-lookup"><span data-stu-id="448dc-160">DBPROP_INDEX_PRIMARYKEY</span></span>|<span data-ttu-id="448dc-161">R/W：读取/写入</span><span class="sxs-lookup"><span data-stu-id="448dc-161">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="448dc-162">默认值：VARIANT_FALSE 说明：将该索引创建为引用完整性 PRIMARY KEY 约束。</span><span class="sxs-lookup"><span data-stu-id="448dc-162">Default: VARIANT_FALSE Description: Creates the index as a referential integrity, PRIMARY KEY constraint.</span></span><br /><br /> <span data-ttu-id="448dc-163">VARIANT_TRUE：创建该索引是为了支持表的 PRIMARY KEY 约束。</span><span class="sxs-lookup"><span data-stu-id="448dc-163">VARIANT_TRUE: The index is created to support the PRIMARY KEY constraint of the table.</span></span> <span data-ttu-id="448dc-164">列必须不可为 Null。</span><span class="sxs-lookup"><span data-stu-id="448dc-164">The columns must be nonnullable.</span></span><br /><br /> <span data-ttu-id="448dc-165">VARIANT_FALSE：该索引不作为表中行值的 PRIMARY KEY 约束使用。</span><span class="sxs-lookup"><span data-stu-id="448dc-165">VARIANT_FALSE: The index is not used as a PRIMARY KEY constraint for row values in the table.</span></span>|  
|<span data-ttu-id="448dc-166">DBPROP_INDEX_SORTBOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="448dc-166">DBPROP_INDEX_SORTBOOKMARKS</span></span>|<span data-ttu-id="448dc-167">R/W：读取/写入</span><span class="sxs-lookup"><span data-stu-id="448dc-167">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="448dc-168">默认值：无</span><span class="sxs-lookup"><span data-stu-id="448dc-168">Default: None</span></span><br /><br /> <span data-ttu-id="448dc-169">说明： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序不支持此属性。</span><span class="sxs-lookup"><span data-stu-id="448dc-169">Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not support this property.</span></span> <span data-ttu-id="448dc-170">尝试在 CreateIndex 中设置此属性将导致出现 DB_S_ERRORSOCCURRED 返回值\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="448dc-170">Attempts to set the property in **CreateIndex** cause a DB_S_ERRORSOCCURRED return value.</span></span> <span data-ttu-id="448dc-171">此属性结构的 dwStatus 成员指示 DBPROPSTATUS_BADVALUE\*\*。</span><span class="sxs-lookup"><span data-stu-id="448dc-171">The *dwStatus* member of the property structure indicates DBPROPSTATUS_BADVALUE.</span></span>|  
|<span data-ttu-id="448dc-172">DBPROP_INDEX_TEMPINDEX</span><span class="sxs-lookup"><span data-stu-id="448dc-172">DBPROP_INDEX_TEMPINDEX</span></span>|<span data-ttu-id="448dc-173">R/W：读取/写入</span><span class="sxs-lookup"><span data-stu-id="448dc-173">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="448dc-174">默认值：无</span><span class="sxs-lookup"><span data-stu-id="448dc-174">Default: None</span></span><br /><br /> <span data-ttu-id="448dc-175">说明： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序不支持此属性。</span><span class="sxs-lookup"><span data-stu-id="448dc-175">Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not support this property.</span></span> <span data-ttu-id="448dc-176">尝试在 CreateIndex 中设置此属性将导致出现 DB_S_ERRORSOCCURRED 返回值\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="448dc-176">Attempts to set the property in **CreateIndex** cause a DB_S_ERRORSOCCURRED return value.</span></span> <span data-ttu-id="448dc-177">此属性结构的 dwStatus 成员指示 DBPROPSTATUS_BADVALUE\*\*。</span><span class="sxs-lookup"><span data-stu-id="448dc-177">The *dwStatus* member of the property structure indicates DBPROPSTATUS_BADVALUE.</span></span>|  
|<span data-ttu-id="448dc-178">DBPROP_INDEX_TYPE</span><span class="sxs-lookup"><span data-stu-id="448dc-178">DBPROP_INDEX_TYPE</span></span>|<span data-ttu-id="448dc-179">R/W：读取/写入</span><span class="sxs-lookup"><span data-stu-id="448dc-179">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="448dc-180">默认值：无</span><span class="sxs-lookup"><span data-stu-id="448dc-180">Default: None</span></span><br /><br /> <span data-ttu-id="448dc-181">说明： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序不支持此属性。</span><span class="sxs-lookup"><span data-stu-id="448dc-181">Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not support this property.</span></span> <span data-ttu-id="448dc-182">尝试在 CreateIndex 中设置此属性将导致出现 DB_S_ERRORSOCCURRED 返回值\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="448dc-182">Attempts to set the property in **CreateIndex** cause a DB_S_ERRORSOCCURRED return value.</span></span> <span data-ttu-id="448dc-183">此属性结构的 dwStatus 成员指示 DBPROPSTATUS_BADVALUE\*\*。</span><span class="sxs-lookup"><span data-stu-id="448dc-183">The *dwStatus* member of the property structure indicates DBPROPSTATUS_BADVALUE.</span></span>|  
|<span data-ttu-id="448dc-184">DBPROP_INDEX_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="448dc-184">DBPROP_INDEX_UNIQUE</span></span>|<span data-ttu-id="448dc-185">R/W：读取/写入</span><span class="sxs-lookup"><span data-stu-id="448dc-185">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="448dc-186">默认值：VARIANT_FALSE</span><span class="sxs-lookup"><span data-stu-id="448dc-186">Default: VARIANT_FALSE</span></span><br /><br /> <span data-ttu-id="448dc-187">说明：对参与的一个或多个列将该索引创建为 UNIQUE 约束。</span><span class="sxs-lookup"><span data-stu-id="448dc-187">Description: Creates the index as a UNIQUE constraint on the participating column or columns.</span></span><br /><br /> <span data-ttu-id="448dc-188">VARIANT_TRUE：该索引用于唯一约束表中的行值。</span><span class="sxs-lookup"><span data-stu-id="448dc-188">VARIANT_TRUE: The index is used to uniquely constrain row values in the table.</span></span><br /><br /> <span data-ttu-id="448dc-189">VARIANT_FALSE：该索引不对行值进行唯一约束。</span><span class="sxs-lookup"><span data-stu-id="448dc-189">VARIANT_FALSE: The index does not uniquely constrain row values.</span></span>|  
  
 <span data-ttu-id="448dc-190">在特定于访问接口的属性集中 DBPROPSET_SQLSERVERINDEX， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序定义以下数据源信息属性。</span><span class="sxs-lookup"><span data-stu-id="448dc-190">In the provider-specific property set DBPROPSET_SQLSERVERINDEX, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider defines the following data source information property.</span></span>  
  
|<span data-ttu-id="448dc-191">属性 ID</span><span class="sxs-lookup"><span data-stu-id="448dc-191">Property ID</span></span>|<span data-ttu-id="448dc-192">说明</span><span class="sxs-lookup"><span data-stu-id="448dc-192">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="448dc-193">SSPROP_INDEX_XML</span><span class="sxs-lookup"><span data-stu-id="448dc-193">SSPROP_INDEX_XML</span></span>|<span data-ttu-id="448dc-194">类型：VT_BOOL (R/W)</span><span class="sxs-lookup"><span data-stu-id="448dc-194">Type: VT_BOOL (R/W)</span></span><br /><br /> <span data-ttu-id="448dc-195">默认值：VARIANT_FALSE</span><span class="sxs-lookup"><span data-stu-id="448dc-195">Default: VARIANT_FALSE</span></span><br /><br /> <span data-ttu-id="448dc-196">说明：当使用 IIndexDefinition::CreateIndex 将此属性指定为值 VARIANT_TRUE 时，将导致创建与被索引的列对应的主 xml 索引。</span><span class="sxs-lookup"><span data-stu-id="448dc-196">Description: When this property is specified with a value of VARIANT_TRUE with IIndexDefinition::CreateIndex, it results in a primary xml index being created corresponding to the column being indexed.</span></span> <span data-ttu-id="448dc-197">如果此属性为 VARIANT_TRUE，则 cIndexColumnDescs 应为 1，否则将会出错。</span><span class="sxs-lookup"><span data-stu-id="448dc-197">If this property is VARIANT_TRUE, cIndexColumnDescs should be 1, otherwise it is an error.</span></span>|  
  
 <span data-ttu-id="448dc-198">本示例创建了一个主键索引：</span><span class="sxs-lookup"><span data-stu-id="448dc-198">This example creates a primary key index:</span></span>  
  
```  
// This CREATE TABLE statement shows the referential integrity and   
// PRIMARY KEY constraint on the OrderDetails table that will be created   
// by the following example code.  
//  
// CREATE TABLE OrderDetails  
// (  
//    OrderID      int      NOT NULL  
//    ProductID   int      NOT NULL  
//        CONSTRAINT PK_OrderDetails  
//        PRIMARY KEY CLUSTERED (OrderID, ProductID),  
//    UnitPrice   money      NOT NULL,  
//    Quantity   int      NOT NULL,  
//    Discount   decimal(2,2)   NOT NULL  
//        DEFAULT 0  
// )  
//  
HRESULT CreatePrimaryKey  
    (  
    IIndexDefinition* pIIndexDefinition  
    )  
    {  
    HRESULT             hr = S_OK;  
  
    DBID                dbidTable;  
    DBID                dbidIndex;  
    const ULONG         nCols = 2;  
    ULONG               nCol;  
    const ULONG         nProps = 2;  
    ULONG               nProp;  
  
    DBINDEXCOLUMNDESC   dbidxcoldesc[nCols];  
    DBPROP              dbpropIndex[nProps];  
    DBPROPSET           dbpropset;  
  
    DBID*               pdbidIndexOut = NULL;  
  
    // Set up identifiers for the table and index.  
    dbidTable.eKind = DBKIND_NAME;  
    dbidTable.uName.pwszName = L"OrderDetails";  
  
    dbidIndex.eKind = DBKIND_NAME;  
    dbidIndex.uName.pwszName = L"PK_OrderDetails";  
  
    // Set up column identifiers.  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        dbidxcoldesc[nCol].pColumnID = new DBID;  
        dbidxcoldesc[nCol].pColumnID->eKind = DBKIND_NAME;  
  
        dbidxcoldesc[nCol].eIndexColOrder = DBINDEX_COL_ORDER_ASC;  
        }  
    dbidxcoldesc[0].pColumnID->uName.pwszName = L"OrderID";  
    dbidxcoldesc[1].pColumnID->uName.pwszName = L"ProductID";  
  
    // Set properties for the index. The index is clustered,  
    // PRIMARY KEY.  
    for (nProp = 0; nProp < nProps; nProp++)  
        {  
        dbpropIndex[nProp].dwOptions = DBPROPOPTIONS_REQUIRED;  
        dbpropIndex[nProp].colid = DB_NULLID;  
  
        VariantInit(&(dbpropIndex[nProp].vValue));  
  
        dbpropIndex[nProp].vValue.vt = VT_BOOL;  
        }  
    dbpropIndex[0].dwPropertyID = DBPROP_INDEX_CLUSTERED;  
    dbpropIndex[0].vValue.boolVal = VARIANT_TRUE;  
  
    dbpropIndex[1].dwPropertyID = DBPROP_INDEX_PRIMARYKEY;  
    dbpropIndex[1].vValue.boolVal = VARIANT_TRUE;  
  
    dbpropset.rgProperties = dbpropIndex;  
    dbpropset.cProperties = nProps;  
    dbpropset.guidPropertySet = DBPROPSET_INDEX;  
  
    hr = pIIndexDefinition->CreateIndex(&dbidTable, &dbidIndex, nCols,  
        dbidxcoldesc, 1, &dbpropset, &pdbidIndexOut);  
  
    // Clean up dynamically allocated DBIDs.  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        delete dbidxcoldesc[nCol].pColumnID;  
        }  
  
    return (hr);  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="448dc-199">另请参阅</span><span class="sxs-lookup"><span data-stu-id="448dc-199">See Also</span></span>  
 [<span data-ttu-id="448dc-200">表和索引</span><span class="sxs-lookup"><span data-stu-id="448dc-200">Tables and Indexes</span></span>](../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)  
  
  
