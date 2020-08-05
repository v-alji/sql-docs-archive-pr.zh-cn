---
title: ISSCommandWithParameters::GetParameterProperties (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSCommandWithParameters::GetParameterProperties (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- GetParameterProperties method
ms.assetid: 7f4cc5ea-d028-4fe5-9192-bd153ab3c26c
author: rothja
ms.author: jroth
ms.openlocfilehash: 2160c93748375a4aa3bee3d530d441182204134a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580231"
---
# <a name="isscommandwithparametersgetparameterproperties-ole-db"></a><span data-ttu-id="83675-102">ISSCommandWithParameters::GetParameterProperties (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="83675-102">ISSCommandWithParameters::GetParameterProperties (OLE DB)</span></span>
  <span data-ttu-id="83675-103">返回 SSPARAMPROPS 属性集结构的数组，每个 UDT 或 XML 参数对应一个 SSPARAMPROPS 属性集。</span><span class="sxs-lookup"><span data-stu-id="83675-103">Returns an array of SSPARAMPROPS property set structures, one SSPARAMPROPS property set for each UDT or XML parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83675-104">语法</span><span class="sxs-lookup"><span data-stu-id="83675-104">Syntax</span></span>  
  
```  
  
HRESULT GetParameterProperties(  
DB_UPARAMS *pcParams,  
SSPARAMPROPS **prgParamProperties);  
```  
  
## <a name="arguments"></a><span data-ttu-id="83675-105">参数</span><span class="sxs-lookup"><span data-stu-id="83675-105">Arguments</span></span>  
 <span data-ttu-id="83675-106">pcParams[out][in]\*\*</span><span class="sxs-lookup"><span data-stu-id="83675-106">*pcParams*[out][in]</span></span>  
 <span data-ttu-id="83675-107">一个指向内存的指针，该内存包含 prgParamProperties 中返回的 SSPARAMPROPS 结构数量\*\*。</span><span class="sxs-lookup"><span data-stu-id="83675-107">A pointer to memory that contains the number of SSPARAMPROPS structures returned in *prgParamProperties*.</span></span>  
  
 <span data-ttu-id="83675-108">prgParamProperties[out]\*\*</span><span class="sxs-lookup"><span data-stu-id="83675-108">*prgParamProperties*[out]</span></span>  
 <span data-ttu-id="83675-109">指向内存中将返回 SSPARAMPROPS 结构数组的位置的指针。</span><span class="sxs-lookup"><span data-stu-id="83675-109">A pointer to memory in which an array of SSPARAMPROPS structures is returned.</span></span> <span data-ttu-id="83675-110">提供程序为结构分配内存并返回此内存的地址;当使用者不再需要结构时，将使用**IMalloc：： Free**释放此内存。</span><span class="sxs-lookup"><span data-stu-id="83675-110">The provider allocates memory for the structures and returns the address to this memory; the consumer releases this memory with **IMalloc::Free** when it no longer needs the structures.</span></span> <span data-ttu-id="83675-111">在调用**IMalloc：： Free** for *prgParamProperties*之前，使用者还必须调用每个 DBPROP 结构的*vValue*属性的**VariantClear** ，以防止在变体包含引用类型 (例如 BSTR）的情况下发生内存泄漏。 ) 如果在输出中*pcParams*为零或发生除 DB_E_ERRORSOCCURRED 之外的错误，则访问接口不会分配任何内存，并确保*prgParamProperties*在输出时为 null 指针。</span><span class="sxs-lookup"><span data-stu-id="83675-111">Before calling **IMalloc::Free** for *prgParamProperties*, the consumer must also call **VariantClear** for the *vValue* property of each DBPROP structure in order to prevent a memory leak in cases where the variant contains a reference type (such as a BSTR.) If *pcParams* is zero on output or an error other than DB_E_ERRORSOCCURRED occurs, the provider does not allocate any memory and ensures that *prgParamProperties* is a null pointer on output.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="83675-112">返回代码值</span><span class="sxs-lookup"><span data-stu-id="83675-112">Return Code Values</span></span>  
 <span data-ttu-id="83675-113">**GetParameterProperties**方法返回与 Core OLE DB **ICommandProperties：： GetProperties**方法相同的错误代码，但不能引发 DB_S_ERRORSOCCURRED 和 DB_E_ERRORSOCCURED。</span><span class="sxs-lookup"><span data-stu-id="83675-113">The **GetParameterProperties** method returns the same error codes as the core OLE DB **ICommandProperties::GetProperties** method, except that DB_S_ERRORSOCCURRED and DB_E_ERRORSOCCURED cannot be raised.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83675-114">备注</span><span class="sxs-lookup"><span data-stu-id="83675-114">Remarks</span></span>  
 <span data-ttu-id="83675-115">对于**GetParameterInfo**， **ISSCommandWithParameters：： GetParameterProperties**的行为一致。</span><span class="sxs-lookup"><span data-stu-id="83675-115">**ISSCommandWithParameters::GetParameterProperties** behaves consistently with respect to **GetParameterInfo**.</span></span> <span data-ttu-id="83675-116">如果未调用[ISSCommandWithParameters：： SetParameterProperties](isscommandwithparameters-setparameterproperties-ole-db.md)或**SetParameterInfo** cParams 等于零，则**GetParameterInfo**将派生参数信息并返回 this。</span><span class="sxs-lookup"><span data-stu-id="83675-116">If [ISSCommandWithParameters::SetParameterProperties](isscommandwithparameters-setparameterproperties-ole-db.md) or **SetParameterInfo** have not been called or have been called with cParams equal to zero, **GetParameterInfo** derives parameter information and returns this.</span></span> <span data-ttu-id="83675-117">如果已为至少一个参数调用了**ISSCommandWithParameters：： SetParameterProperties**或**SetParameterInfo** ，则**ISSCommandWithParameters：： GetParameterProperties**仅返回已调用**ISSCommandWithParameters：： SetParameterProperties**的那些参数的属性。</span><span class="sxs-lookup"><span data-stu-id="83675-117">If **ISSCommandWithParameters::SetParameterProperties** or **SetParameterInfo** have been called for at least one parameter, **ISSCommandWithParameters::GetParameterProperties** returns properties only for those parameters for which **ISSCommandWithParameters::SetParameterProperties** has been called.</span></span> <span data-ttu-id="83675-118">如果在**ISSCommandWithParameters：： GetParameterProperties**或**GetParameterInfo**后调用**ISSCommandWithParameters：： SetParameterProperties** ，则对**ISSCommandWithParameters：： GetParameterProperties**的后续调用将返回为其调用**ISSCommandWithParameters：： SetParameterProperties**的那些参数的重写值。</span><span class="sxs-lookup"><span data-stu-id="83675-118">If **ISSCommandWithParameters::SetParameterProperties** is called after **ISSCommandWithParameters::GetParameterProperties** or **GetParameterInfo**, subsequent calls to **ISSCommandWithParameters::GetParameterProperties** return the overridden values for those parameters for which **ISSCommandWithParameters::SetParameterProperties** has been called.</span></span>  
  
 <span data-ttu-id="83675-119">SSPARAMPROPS 结构的定义如下所示：</span><span class="sxs-lookup"><span data-stu-id="83675-119">The SSPARAMPROPS structure is defined as follows:</span></span>  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
|<span data-ttu-id="83675-120">成员</span><span class="sxs-lookup"><span data-stu-id="83675-120">Member</span></span>|<span data-ttu-id="83675-121">描述</span><span class="sxs-lookup"><span data-stu-id="83675-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="83675-122">iOrdinal\*\*</span><span class="sxs-lookup"><span data-stu-id="83675-122">*iOrdinal*</span></span>|<span data-ttu-id="83675-123">所传递参数的序号。</span><span class="sxs-lookup"><span data-stu-id="83675-123">The ordinal of the passed parameter.</span></span>|  
|<span data-ttu-id="83675-124">cPropertySets\*\*</span><span class="sxs-lookup"><span data-stu-id="83675-124">*cPropertySets*</span></span>|<span data-ttu-id="83675-125">rgPropertySets 中 DBPROPSET 结构的数量\*\*。</span><span class="sxs-lookup"><span data-stu-id="83675-125">The number of DBPROPSET structures in *rgPropertySets*.</span></span>|  
|<span data-ttu-id="83675-126">rgPropertySets\*\*</span><span class="sxs-lookup"><span data-stu-id="83675-126">*rgPropertySets*</span></span>|<span data-ttu-id="83675-127">指向内存中将返回 DBPROPSET 结构数组的位置的指针。</span><span class="sxs-lookup"><span data-stu-id="83675-127">A pointer to memory in which to return an array of DBPROPSET structures.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="83675-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="83675-128">See Also</span></span>  
 [<span data-ttu-id="83675-129">ISSCommandWithParameters &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="83675-129">ISSCommandWithParameters &#40;OLE DB&#41;</span></span>](isscommandwithparameters-ole-db.md)  
  
  
