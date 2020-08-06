---
title: ISSCommandWithParameters::SetParameterProperties (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSCommandWithParameters::SetParameterProperties (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- SetParameterProperties method
ms.assetid: 4cd0281a-a2a0-43df-8e46-eb478b64cb4b
author: rothja
ms.author: jroth
ms.openlocfilehash: 4bf8e5cde9885a5d9b55d84c6384b76aecf50b8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687836"
---
# <a name="isscommandwithparameterssetparameterproperties-ole-db"></a><span data-ttu-id="74560-102">ISSCommandWithParameters::SetParameterProperties (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="74560-102">ISSCommandWithParameters::SetParameterProperties (OLE DB)</span></span>
  <span data-ttu-id="74560-103">按照序号基于每个参数设置参数属性，或者通过指定 SSPARAMPROPS 结构数组来设置大容量参数属性。</span><span class="sxs-lookup"><span data-stu-id="74560-103">Sets the parameter properties on a per parameter basis by ordinal, or sets bulk parameter properties by specifying an array of SSPARAMPROPS structures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74560-104">语法</span><span class="sxs-lookup"><span data-stu-id="74560-104">Syntax</span></span>  
  
```  
  
HRESULT SetParameterProperties(  
DB_UPARAMS cParams,   
SSPARAMPROPS rgParamProperties[]);  
```  
  
## <a name="arguments"></a><span data-ttu-id="74560-105">参数</span><span class="sxs-lookup"><span data-stu-id="74560-105">Arguments</span></span>  
 <span data-ttu-id="74560-106">cParams[in]\*\*</span><span class="sxs-lookup"><span data-stu-id="74560-106">*cParams*[in]</span></span>  
 <span data-ttu-id="74560-107">rgParamProperties 数组中 SSPARAMPROPS 结构的数量\*\*。</span><span class="sxs-lookup"><span data-stu-id="74560-107">The number of SSPARAMPROPS structures in the *rgParamProperties* array.</span></span> <span data-ttu-id="74560-108">如果此数为零， `ISSCommandWithParameters::SetParameterProperties` 则将删除可能已为命令中的任何参数指定的所有属性。</span><span class="sxs-lookup"><span data-stu-id="74560-108">If this number is zero, `ISSCommandWithParameters::SetParameterProperties` will delete all properties that might have been specified for any parameters in the command.</span></span>  
  
 <span data-ttu-id="74560-109">rgParamProperties[in]\*\*</span><span class="sxs-lookup"><span data-stu-id="74560-109">*rgParamProperties*[in]</span></span>  
 <span data-ttu-id="74560-110">要设置的 SSPARAMPROPS 结构数组。</span><span class="sxs-lookup"><span data-stu-id="74560-110">An array of SSPARAMPROPS structures to be set.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="74560-111">返回代码值</span><span class="sxs-lookup"><span data-stu-id="74560-111">Return Code Values</span></span>  
 <span data-ttu-id="74560-112">`ISSCommandWithParameters::SetParameterProperties`方法返回与 core OLE DB **ICommandProperties：： SetProperties**方法相同的错误代码。</span><span class="sxs-lookup"><span data-stu-id="74560-112">The `ISSCommandWithParameters::SetParameterProperties` method returns the same error codes as the core OLE DB **ICommandProperties::SetProperties** method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74560-113">备注</span><span class="sxs-lookup"><span data-stu-id="74560-113">Remarks</span></span>  
 <span data-ttu-id="74560-114">使用此方法设置参数属性的方法是按顺序在每个参数基础上使用，也可以在 `ISSCommandWithParameters::SetParameterProperties` 从属性数组生成 SSPARAMPROPS 后使用单个调用。</span><span class="sxs-lookup"><span data-stu-id="74560-114">Setting parameter properties with this method is allowed on a per parameter basis by ordinal, or with a single `ISSCommandWithParameters::SetParameterProperties` call once the SSPARAMPROPS has been built from the property array.</span></span>  
  
 <span data-ttu-id="74560-115">在调用方法之前，必须调用**SetParameterInfo**方法 `ISSCommandWithParameters::SetParameterProperties` 。</span><span class="sxs-lookup"><span data-stu-id="74560-115">The **SetParameterInfo** method must be called before calling the `ISSCommandWithParameters::SetParameterProperties` method.</span></span> <span data-ttu-id="74560-116">调用 `SetParameterProperties(0, NULL)` 可清除所有指定的参数属性，而调用 `SetParameterInfo(0,NULL,NULL)` 则会清除所有参数信息（包括可能与某个参数相关的任何属性）。</span><span class="sxs-lookup"><span data-stu-id="74560-116">Calling `SetParameterProperties(0, NULL)` clears all specified parameter properties, while calling `SetParameterInfo(0,NULL,NULL)` clears all the parameter info including any properties that might be associated with a parameter.</span></span>  
  
 <span data-ttu-id="74560-117">调用 `ISSCommandWithParameters::SetParameterProperties` 以指定参数的属性，该参数的类型不是 DBTYPE_XML 或 DBTYPE_UDT 返回 DB_E_ERRORSOCCURRED 或 DB_S_ERRORSOCCURRED，并使用 DBPROPSTATUS_NOTSET 标记该参数包含在 SSPARAMPROPS 中的所有 dbprop 的*dwStatus*字段。</span><span class="sxs-lookup"><span data-stu-id="74560-117">Calling `ISSCommandWithParameters::SetParameterProperties` to specify properties for a parameter which is not of type DBTYPE_XML or DBTYPE_UDT returns DB_E_ERRORSOCCURRED or DB_S_ERRORSOCCURRED and marks the *dwStatus* field of all DBPROPs contained in SSPARAMPROPS for that parameter with DBPROPSTATUS_NOTSET.</span></span> <span data-ttu-id="74560-118">应当遍历 SSPARAMPROPS 中包含的每个 DBPROPSET 的 DBPROP 数组，以检测 DB_E_ERRORSOCCURRED 或 DB_S_ERRORSOCCURRED 引用了哪些参数。</span><span class="sxs-lookup"><span data-stu-id="74560-118">The DBPROP array of each DBPROPSET contained in SSPARAMPROPS should be traversed to detect which parameter the DB_E_ERRORSOCCURRED or DB_S_ERRORSOCCURRED refers to.</span></span>  
  
 <span data-ttu-id="74560-119">如果 `ISSCommandWithParameters::SetParameterProperties` 调用以指定参数信息尚未使用**SetParameterInfo**设置的参数的属性，则提供程序将返回 E_UNEXPECTED，并返回以下错误消息：</span><span class="sxs-lookup"><span data-stu-id="74560-119">If `ISSCommandWithParameters::SetParameterProperties` is called to specify the properties of parameters whose parameter info have not been set yet with **SetParameterInfo**, the provider returns E_UNEXPECTED with the following error message:</span></span>  
  
 <span data-ttu-id="74560-120">在没有先调用 SetParameterInfo 方法的情况下，不能为指定参数调用 SetParameterProperties 方法。</span><span class="sxs-lookup"><span data-stu-id="74560-120">SetParameterProperties method cannot be called for the specified parameters without first calling SetParameterInfo method.</span></span> <span data-ttu-id="74560-121">在设置参数属性之前，必须首先设置参数信息。</span><span class="sxs-lookup"><span data-stu-id="74560-121">The parameter information must be set before setting the parameter properties.</span></span>  
  
 <span data-ttu-id="74560-122">如果对的调用 `ISSCommandWithParameters::SetParameterProperties` 包含某些参数信息已设置的参数，而某些参数尚未设置参数信息，则 SSPARAMPROPS 属性集的 DBPROPSET 中的 dwStatus 属性将返回 DBSTATUS_NOTSET。</span><span class="sxs-lookup"><span data-stu-id="74560-122">If the call to `ISSCommandWithParameters::SetParameterProperties` contains some parameters where the parameter info has been set, and some parameters where the parameter info has not been set, the dwStatus properties in the DBPROPSET of the SSPARAMPROPS property set will return with DBSTATUS_NOTSET.</span></span>  
  
 <span data-ttu-id="74560-123">SSPARAMPROPS 结构的定义如下所示：</span><span class="sxs-lookup"><span data-stu-id="74560-123">The SSPARAMPROPS structure is defined as follows:</span></span>  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
 <span data-ttu-id="74560-124">自 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 起，借助数据库引擎中的改进，ISSCommandWithParameters::SetParameterProperties 可以获取预期结果的更准确描述。</span><span class="sxs-lookup"><span data-stu-id="74560-124">Improvements in the database engine starting with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] allow ISSCommandWithParameters::SetParameterProperties to obtain more accurate descriptions of the expected results.</span></span> <span data-ttu-id="74560-125">这些更准确的结果可能与旧版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中 ISSCommandWithParameters::SetParameterProperties 返回的值有所不同。</span><span class="sxs-lookup"><span data-stu-id="74560-125">These more accurate results may differ from the values returned by ISSCommandWithParameters::SetParameterProperties in previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="74560-126">有关详细信息，请参阅[元数据发现](../native-client/features/metadata-discovery.md)。</span><span class="sxs-lookup"><span data-stu-id="74560-126">For more information, see [Metadata Discovery](../native-client/features/metadata-discovery.md).</span></span>  
  
|<span data-ttu-id="74560-127">成员</span><span class="sxs-lookup"><span data-stu-id="74560-127">Member</span></span>|<span data-ttu-id="74560-128">描述</span><span class="sxs-lookup"><span data-stu-id="74560-128">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="74560-129">iOrdinal\*\*</span><span class="sxs-lookup"><span data-stu-id="74560-129">*iOrdinal*</span></span>|<span data-ttu-id="74560-130">所传递参数的序号。</span><span class="sxs-lookup"><span data-stu-id="74560-130">The ordinal of the passed parameter.</span></span>|  
|<span data-ttu-id="74560-131">cPropertySets\*\*</span><span class="sxs-lookup"><span data-stu-id="74560-131">*cPropertySets*</span></span>|<span data-ttu-id="74560-132">rgPropertySets 中 DBPROPSET 结构的数量\*\*。</span><span class="sxs-lookup"><span data-stu-id="74560-132">The number of DBPROPSET structures in *rgPropertySets*.</span></span>|  
|<span data-ttu-id="74560-133">rgPropertySets\*\*</span><span class="sxs-lookup"><span data-stu-id="74560-133">*rgPropertySets*</span></span>|<span data-ttu-id="74560-134">指向内存中将返回 DBPROPSET 结构数组的位置的指针。</span><span class="sxs-lookup"><span data-stu-id="74560-134">A pointer to memory in which to return an array of DBPROPSET structures.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="74560-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="74560-135">See Also</span></span>  
 [<span data-ttu-id="74560-136">ISSCommandWithParameters &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="74560-136">ISSCommandWithParameters &#40;OLE DB&#41;</span></span>](isscommandwithparameters-ole-db.md)  
  
  
