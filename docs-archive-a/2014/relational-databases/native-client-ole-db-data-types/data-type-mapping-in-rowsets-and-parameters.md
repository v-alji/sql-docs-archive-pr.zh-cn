---
title: 行集和参数中的数据类型映射 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- mapping data types [OLE DB]
- DBTYPE_SQLVARIANT data type
- SQL Server Native Client OLE DB provider, data types
- rowsets [OLE DB], data type mapping
- data types [OLE DB]
- GetColumnInfo function
- parameters [OLE DB]
- SSPROP_ALLOWNATIVEVARIANT property
- GetParameterInfo function
- OLE DB, data types
ms.assetid: 3d831ff8-3b79-4698-b2c1-2b5dd2f8235c
author: rothja
ms.author: jroth
ms.openlocfilehash: 83923eb611ddc7baedc38c70b23c2ff5e17556d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589553"
---
# <a name="data-type-mapping-in-rowsets-and-parameters"></a><span data-ttu-id="166a3-102">行集和参数中的数据类型映射</span><span class="sxs-lookup"><span data-stu-id="166a3-102">Data Type Mapping in Rowsets and Parameters</span></span>
  <span data-ttu-id="166a3-103">在行集和作为参数值的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 情况下，Native Client OLE DB 提供程序 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用以下 OLE DB 定义的数据类型来表示数据，这些数据类型在函数**IColumnsInfo：： GetColumnInfo**和**ICommandWithParameters：： GetParameterInfo**中报告。</span><span class="sxs-lookup"><span data-stu-id="166a3-103">In rowsets and as parameter values, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider represents [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data by using the following OLE DB defined data types, reported in the functions **IColumnsInfo::GetColumnInfo** and **ICommandWithParameters::GetParameterInfo**.</span></span>  
  
|<span data-ttu-id="166a3-104">SQL Server 数据类型</span><span class="sxs-lookup"><span data-stu-id="166a3-104">SQL Server data type</span></span>|<span data-ttu-id="166a3-105">OLE DB 数据类型</span><span class="sxs-lookup"><span data-stu-id="166a3-105">OLE DB data type</span></span>|  
|--------------------------|----------------------|  
|<span data-ttu-id="166a3-106">**bigint**</span><span class="sxs-lookup"><span data-stu-id="166a3-106">**bigint**</span></span>|<span data-ttu-id="166a3-107">DBTYPE_I8</span><span class="sxs-lookup"><span data-stu-id="166a3-107">DBTYPE_I8</span></span>|  
|<span data-ttu-id="166a3-108">**binary**</span><span class="sxs-lookup"><span data-stu-id="166a3-108">**binary**</span></span>|<span data-ttu-id="166a3-109">DBTYPE_BYTES</span><span class="sxs-lookup"><span data-stu-id="166a3-109">DBTYPE_BYTES</span></span>|  
|<span data-ttu-id="166a3-110">**bit**</span><span class="sxs-lookup"><span data-stu-id="166a3-110">**bit**</span></span>|<span data-ttu-id="166a3-111">DBTYPE_BOOL</span><span class="sxs-lookup"><span data-stu-id="166a3-111">DBTYPE_BOOL</span></span>|  
|<span data-ttu-id="166a3-112">**char**</span><span class="sxs-lookup"><span data-stu-id="166a3-112">**char**</span></span>|<span data-ttu-id="166a3-113">DBTYPE_STR</span><span class="sxs-lookup"><span data-stu-id="166a3-113">DBTYPE_STR</span></span>|  
|<span data-ttu-id="166a3-114">**datetime**</span><span class="sxs-lookup"><span data-stu-id="166a3-114">**datetime**</span></span>|<span data-ttu-id="166a3-115">DBTYPE_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="166a3-115">DBTYPE_DBTIMESTAMP</span></span>|  
|<span data-ttu-id="166a3-116">**datetime2**</span><span class="sxs-lookup"><span data-stu-id="166a3-116">**datetime2**</span></span>|<span data-ttu-id="166a3-117">DBTYPE_DBTIME2</span><span class="sxs-lookup"><span data-stu-id="166a3-117">DBTYPE_DBTIME2</span></span>|  
|<span data-ttu-id="166a3-118">**decimal**</span><span class="sxs-lookup"><span data-stu-id="166a3-118">**decimal**</span></span>|<span data-ttu-id="166a3-119">DBTYPE_NUMERIC</span><span class="sxs-lookup"><span data-stu-id="166a3-119">DBTYPE_NUMERIC</span></span>|  
|<span data-ttu-id="166a3-120">**float**</span><span class="sxs-lookup"><span data-stu-id="166a3-120">**float**</span></span>|<span data-ttu-id="166a3-121">DBTYPE_R8</span><span class="sxs-lookup"><span data-stu-id="166a3-121">DBTYPE_R8</span></span>|  
|<span data-ttu-id="166a3-122">**图像**</span><span class="sxs-lookup"><span data-stu-id="166a3-122">**image**</span></span>|<span data-ttu-id="166a3-123">DBTYPE_BYTES</span><span class="sxs-lookup"><span data-stu-id="166a3-123">DBTYPE_BYTES</span></span>|  
|<span data-ttu-id="166a3-124">**int**</span><span class="sxs-lookup"><span data-stu-id="166a3-124">**int**</span></span>|<span data-ttu-id="166a3-125">DBTYPE_I4</span><span class="sxs-lookup"><span data-stu-id="166a3-125">DBTYPE_I4</span></span>|  
|<span data-ttu-id="166a3-126">**money**</span><span class="sxs-lookup"><span data-stu-id="166a3-126">**money**</span></span>|<span data-ttu-id="166a3-127">DBTYPE_CY</span><span class="sxs-lookup"><span data-stu-id="166a3-127">DBTYPE_CY</span></span>|  
|<span data-ttu-id="166a3-128">**nchar**</span><span class="sxs-lookup"><span data-stu-id="166a3-128">**nchar**</span></span>|<span data-ttu-id="166a3-129">DBTYPE_WSTR</span><span class="sxs-lookup"><span data-stu-id="166a3-129">DBTYPE_WSTR</span></span>|  
|<span data-ttu-id="166a3-130">**ntext**</span><span class="sxs-lookup"><span data-stu-id="166a3-130">**ntext**</span></span>|<span data-ttu-id="166a3-131">DBTYPE_WSTR</span><span class="sxs-lookup"><span data-stu-id="166a3-131">DBTYPE_WSTR</span></span>|  
|<span data-ttu-id="166a3-132">**numeric**</span><span class="sxs-lookup"><span data-stu-id="166a3-132">**numeric**</span></span>|<span data-ttu-id="166a3-133">DBTYPE_NUMERIC</span><span class="sxs-lookup"><span data-stu-id="166a3-133">DBTYPE_NUMERIC</span></span>|  
|<span data-ttu-id="166a3-134">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="166a3-134">**nvarchar**</span></span>|<span data-ttu-id="166a3-135">DBTYPE_WSTR</span><span class="sxs-lookup"><span data-stu-id="166a3-135">DBTYPE_WSTR</span></span>|  
|<span data-ttu-id="166a3-136">**real**</span><span class="sxs-lookup"><span data-stu-id="166a3-136">**real**</span></span>|<span data-ttu-id="166a3-137">DBTYPE_R4</span><span class="sxs-lookup"><span data-stu-id="166a3-137">DBTYPE_R4</span></span>|  
|<span data-ttu-id="166a3-138">**smalldatetime**</span><span class="sxs-lookup"><span data-stu-id="166a3-138">**smalldatetime**</span></span>|<span data-ttu-id="166a3-139">DBTYPE_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="166a3-139">DBTYPE_DBTIMESTAMP</span></span>|  
|<span data-ttu-id="166a3-140">**smallint**</span><span class="sxs-lookup"><span data-stu-id="166a3-140">**smallint**</span></span>|<span data-ttu-id="166a3-141">DBTYPE_I2</span><span class="sxs-lookup"><span data-stu-id="166a3-141">DBTYPE_I2</span></span>|  
|<span data-ttu-id="166a3-142">**smallmoney**</span><span class="sxs-lookup"><span data-stu-id="166a3-142">**smallmoney**</span></span>|<span data-ttu-id="166a3-143">DBTYPE_CY</span><span class="sxs-lookup"><span data-stu-id="166a3-143">DBTYPE_CY</span></span>|  
|<span data-ttu-id="166a3-144">**sql_variant**</span><span class="sxs-lookup"><span data-stu-id="166a3-144">**sql_variant**</span></span>|<span data-ttu-id="166a3-145">DBTYPE_VARIANT、DBTYPE_SQLVARIANT</span><span class="sxs-lookup"><span data-stu-id="166a3-145">DBTYPE_VARIANT, DBTYPE_SQLVARIANT</span></span>|  
|<span data-ttu-id="166a3-146">**sysname**</span><span class="sxs-lookup"><span data-stu-id="166a3-146">**sysname**</span></span>|<span data-ttu-id="166a3-147">DBTYPE_WSTR</span><span class="sxs-lookup"><span data-stu-id="166a3-147">DBTYPE_WSTR</span></span>|  
|<span data-ttu-id="166a3-148">**text**</span><span class="sxs-lookup"><span data-stu-id="166a3-148">**text**</span></span>|<span data-ttu-id="166a3-149">DBTYPE_STR</span><span class="sxs-lookup"><span data-stu-id="166a3-149">DBTYPE_STR</span></span>|  
|<span data-ttu-id="166a3-150">**timestamp**</span><span class="sxs-lookup"><span data-stu-id="166a3-150">**timestamp**</span></span>|<span data-ttu-id="166a3-151">DBTYPE_BYTES</span><span class="sxs-lookup"><span data-stu-id="166a3-151">DBTYPE_BYTES</span></span>|  
|<span data-ttu-id="166a3-152">**tinyint**</span><span class="sxs-lookup"><span data-stu-id="166a3-152">**tinyint**</span></span>|<span data-ttu-id="166a3-153">DBTYPE_UI1</span><span class="sxs-lookup"><span data-stu-id="166a3-153">DBTYPE_UI1</span></span>|  
|<span data-ttu-id="166a3-154">**UDT**</span><span class="sxs-lookup"><span data-stu-id="166a3-154">**UDT**</span></span>|<span data-ttu-id="166a3-155">DBTYPE_UDT</span><span class="sxs-lookup"><span data-stu-id="166a3-155">DBTYPE_UDT</span></span>|  
|<span data-ttu-id="166a3-156">**uniqueidentifier**</span><span class="sxs-lookup"><span data-stu-id="166a3-156">**uniqueidentifier**</span></span>|<span data-ttu-id="166a3-157">DBTYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="166a3-157">DBTYPE_GUID</span></span>|  
|<span data-ttu-id="166a3-158">**varbinary**</span><span class="sxs-lookup"><span data-stu-id="166a3-158">**varbinary**</span></span>|<span data-ttu-id="166a3-159">DBTYPE_BYTES</span><span class="sxs-lookup"><span data-stu-id="166a3-159">DBTYPE_BYTES</span></span>|  
|<span data-ttu-id="166a3-160">**varchar**</span><span class="sxs-lookup"><span data-stu-id="166a3-160">**varchar**</span></span>|<span data-ttu-id="166a3-161">DBTYPE_STR</span><span class="sxs-lookup"><span data-stu-id="166a3-161">DBTYPE_STR</span></span>|  
|<span data-ttu-id="166a3-162">**XML**</span><span class="sxs-lookup"><span data-stu-id="166a3-162">**XML**</span></span>|<span data-ttu-id="166a3-163">DBTYPE_XML</span><span class="sxs-lookup"><span data-stu-id="166a3-163">DBTYPE_XML</span></span>|  
  
 <span data-ttu-id="166a3-164">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序支持使用者请求的数据转换，如图所示。</span><span class="sxs-lookup"><span data-stu-id="166a3-164">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports consumer-requested data conversions as shown in the illustration.</span></span>  
  
 <span data-ttu-id="166a3-165">sql_variant 对象可以保留除 text、ntext、image、varchar(max)、nvarchar(max)、varbinary(max)、xml、timestamp 和 Microsoft .NET Framework 公共语言运行时 (CLR) 用户定义类型以外的任意 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型的数据\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="166a3-165">The **sql_variant** objects can hold data of any [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type except text, ntext, image, varchar(max), nvarchar(max), varbinary(max), xml, timestamp, and Microsoft .NET Framework common language runtime (CLR) user-defined types.</span></span> <span data-ttu-id="166a3-166">另外，sql_variant 数据实例还不能将 sql_variant 作为其基础的基本数据类型。</span><span class="sxs-lookup"><span data-stu-id="166a3-166">An instance of sql_variant data also cannot have sql_variant as its underlying base data type.</span></span> <span data-ttu-id="166a3-167">例如，列中的某些行可能包含 smallint 值，而其他某些行可能包含 float 值，剩余的行则包含 char/nchar 值\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="166a3-167">For example, the column can contain **smallint** values for some rows, **float** values for other rows, and **char**/**nchar** values in the remainder.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="166a3-168">**Sql_variant**的数据类型类似于 Microsoft Visual Basic？？中的变量数据类型。</span><span class="sxs-lookup"><span data-stu-id="166a3-168">The **sql_variant** data type is similar to the Variant data type in Microsoft Visual Basic??</span></span> <span data-ttu-id="166a3-169">DBTYPE_VARIANT，请 DBTYPE_SQLVARIANT OLEDB。</span><span class="sxs-lookup"><span data-stu-id="166a3-169">and the DBTYPE_VARIANT, DBTYPE_SQLVARIANT in OLEDB.</span></span>  
  
 <span data-ttu-id="166a3-170">当提取 sql_variant 数据作为 DBTYPE_VARIANT 时，该数据被放置到缓冲区的 VARIANT 结构中  。</span><span class="sxs-lookup"><span data-stu-id="166a3-170">When **sql_variant** data is fetched as DBTYPE_VARIANT, it is put in a VARIANT structure in the buffer.</span></span> <span data-ttu-id="166a3-171">但 VARIANT 结构中的子类型可能无法映射为 sql_variant 数据类型中定义的子类型  。</span><span class="sxs-lookup"><span data-stu-id="166a3-171">But the subtypes in the VARIANT structure may not map to subtypes defined in the **sql_variant** data type.</span></span> <span data-ttu-id="166a3-172">然后，必须提取 sql_variant 数据作为 DBTYPE_SQLVARIANT，以使所有子类型匹配  。</span><span class="sxs-lookup"><span data-stu-id="166a3-172">The **sql_variant** data must then be fetched as DBTYPE_SQLVARIANT in order for all the subtypes to match.</span></span>  
  
## <a name="dbtype_sqlvariant-data-type"></a><span data-ttu-id="166a3-173">DBTYPE_SQLVARIANT 数据类型</span><span class="sxs-lookup"><span data-stu-id="166a3-173">DBTYPE_SQLVARIANT Data Type</span></span>  
 <span data-ttu-id="166a3-174">为了支持**sql_variant**数据类型， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序公开了一种称为 DBTYPE_SQLVARIANT 的特定于提供程序的数据类型。</span><span class="sxs-lookup"><span data-stu-id="166a3-174">To support the **sql_variant** data type, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes a provider-specific data type called DBTYPE_SQLVARIANT.</span></span> <span data-ttu-id="166a3-175">当提取 sql_variant 数据作为 DBTYPE_SQLVARIANT 时，该数据存储到特定于访问接口的 SSVARIANT 结构中  。</span><span class="sxs-lookup"><span data-stu-id="166a3-175">When **sql_variant** data is fetched in as DBTYPE_SQLVARIANT, it is stored in a provider-specific SSVARIANT structure.</span></span> <span data-ttu-id="166a3-176">SSVARIANT 结构包含与 sql_variant 数据类型的子类型匹配的所有子类型  。</span><span class="sxs-lookup"><span data-stu-id="166a3-176">The SSVARIANT structure contains all of the subtypes that match the subtypes of the **sql_variant** data type.</span></span>  
  
 <span data-ttu-id="166a3-177">此外，还必须将 SSPROP_ALLOWNATIVEVARIANT 会话属性设置为 TRUE。</span><span class="sxs-lookup"><span data-stu-id="166a3-177">The session property SSPROP_ALLOWNATIVEVARIANT must also be set to TRUE.</span></span>  
  
## <a name="provider-specific-property-ssprop_allownativevariant"></a><span data-ttu-id="166a3-178">特定于访问接口的 SSPROP_ALLOWNATIVEVARIANT 属性</span><span class="sxs-lookup"><span data-stu-id="166a3-178">Provider-Specific Property SSPROP_ALLOWNATIVEVARIANT</span></span>  
 <span data-ttu-id="166a3-179">提取数据时，您可以显式指定应为列或参数返回的数据类型。</span><span class="sxs-lookup"><span data-stu-id="166a3-179">In fetching data, you can specify explicitly what kind of data type should be returned for a column or for a parameter.</span></span> <span data-ttu-id="166a3-180">还可以使用 IColumnsInfo 获取列信息，并将该信息用于绑定  。</span><span class="sxs-lookup"><span data-stu-id="166a3-180">**IColumnsInfo** can also be used to get the column information and use that to do the binding.</span></span> <span data-ttu-id="166a3-181">当使用 IColumnsInfo 获取列信息以用于绑定目的时，如果 SSPROP_ALLOWNATIVEVARIANT 会话属性为 FALSE（默认值），则为 sql_variant 列返回 DBTYPE_VARIANT   。</span><span class="sxs-lookup"><span data-stu-id="166a3-181">When **IColumnsInfo** is used to obtain column information for binding purposes, if the SSPROP_ALLOWNATIVEVARIANT session property is FALSE (default value), DBTYPE_VARIANT is returned for **sql_variant** columns.</span></span> <span data-ttu-id="166a3-182">如果 SSPROP_ALLOWNATIVEVARIANT 属性为 FALSE，则不支持 DBTYPE_SQLVARIANT。</span><span class="sxs-lookup"><span data-stu-id="166a3-182">If SSPROP_ALLOWNATIVEVARIANT property is FALSE DBTYPE_SQLVARIANT is not supported.</span></span> <span data-ttu-id="166a3-183">如果 SSPROP_ALLOWNATIVEVARIANT 属性设置为 TRUE，列类型将作为 DBTYPE_SQLVARIANT 返回，在这种情况下，缓冲区将保留 SSVARIANT 结构。</span><span class="sxs-lookup"><span data-stu-id="166a3-183">If SSPROP_ALLOWNATIVEVARIANT property is set to TRUE, the column type is returned as DBTYPE_SQLVARIANT, in which case the buffer will hold the SSVARIANT structure.</span></span> <span data-ttu-id="166a3-184">在提取 sql_variant 数据作为 DBTYPE_SQLVARIANT 时，必须将 SSPROP_ALLOWNATIVEVARIANT 会话属性设置为 TRUE  。</span><span class="sxs-lookup"><span data-stu-id="166a3-184">In fetching **sql_variant** data as DBTYPE_SQLVARIANT, the session property SSPROP_ALLOWNATIVEVARIANT must be set to TRUE.</span></span>  
  
 <span data-ttu-id="166a3-185">SSPROP_ALLOWNATIVEVARIANT 属性是特定于访问接口的 DBPROPSET_SQLSERVERSESSION 属性集的一部分，因此，该属性是一个会话属性。</span><span class="sxs-lookup"><span data-stu-id="166a3-185">SSPROP_ALLOWNATIVEVARIANT property is part of the provider-specific DBPROPSET_SQLSERVERSESSION property set, and is a session property.</span></span>  
  
 <span data-ttu-id="166a3-186">DBTYPE_VARIANT 适用于所有其他 OLE DB 访问接口。</span><span class="sxs-lookup"><span data-stu-id="166a3-186">DBTYPE_VARIANT applies to all other OLE DB providers.</span></span>  
  
## <a name="ssprop_allownativevariant"></a><span data-ttu-id="166a3-187">SSPROP_ALLOWNATIVEVARIANT</span><span class="sxs-lookup"><span data-stu-id="166a3-187">SSPROP_ALLOWNATIVEVARIANT</span></span>  
 <span data-ttu-id="166a3-188">SSPROP_ALLOWNATIVEVARIANT 是一个会话属性，并且是 DBPROPSET_SQLSERVERSESSION 属性集的一部分。</span><span class="sxs-lookup"><span data-stu-id="166a3-188">SSPROP_ALLOWNATIVEVARIANT is a session property and is part of DBPROPSET_SQLSERVERSESSION  property set.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="166a3-189">SSPROP_ALLOWNATIVEVARIANT</span><span class="sxs-lookup"><span data-stu-id="166a3-189">SSPROP_ALLOWNATIVEVARIANT</span></span>|<span data-ttu-id="166a3-190">类型：VT_BOOL</span><span class="sxs-lookup"><span data-stu-id="166a3-190">Type: VT_BOOL</span></span><br /><br /> <span data-ttu-id="166a3-191">R/W：读/写</span><span class="sxs-lookup"><span data-stu-id="166a3-191">R/W: Read/Write</span></span><br /><br /> <span data-ttu-id="166a3-192">默认值：VARIANT_FALSE</span><span class="sxs-lookup"><span data-stu-id="166a3-192">Default: VARIANT_FALSE</span></span><br /><br /> <span data-ttu-id="166a3-193">说明：确定提取的数据是作为 DBTYPE_VARIANT 还是作为 DBTYPE_SQLVARIANT。</span><span class="sxs-lookup"><span data-stu-id="166a3-193">Description: Determines if the data fetched in is as DBTYPE_VARIANT or DBTYPE_SQLVARIANT.</span></span><br /><br /> <span data-ttu-id="166a3-194">VARIANT_TRUE：列类型作为 DBTYPE_SQLVARIANT 返回，这种情况下缓冲区将保留 SSVARIANT 结构。</span><span class="sxs-lookup"><span data-stu-id="166a3-194">VARIANT_TRUE: Column type is returned as DBTYPE_SQLVARIANT in which case the buffer will hold SSVARIANT structure.</span></span><br /><br /> <span data-ttu-id="166a3-195">VARIANT_FALSE：列类型作为 DBTYPE_VARIANT 返回，且缓冲区将具有 VARIANT 结构。</span><span class="sxs-lookup"><span data-stu-id="166a3-195">VARIANT_FALSE: Column type is returned as DBTYPE_VARIANT and the buffer will have VARIANT structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="166a3-196">另请参阅</span><span class="sxs-lookup"><span data-stu-id="166a3-196">See Also</span></span>  
 [<span data-ttu-id="166a3-197">数据类型 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="166a3-197">Data Types &#40;OLE DB&#41;</span></span>](data-types-ole-db.md)  
  
  
