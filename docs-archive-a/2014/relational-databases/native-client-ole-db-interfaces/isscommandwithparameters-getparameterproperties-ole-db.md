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
# <a name="isscommandwithparametersgetparameterproperties-ole-db"></a>ISSCommandWithParameters::GetParameterProperties (OLE DB)
  返回 SSPARAMPROPS 属性集结构的数组，每个 UDT 或 XML 参数对应一个 SSPARAMPROPS 属性集。  
  
## <a name="syntax"></a>语法  
  
```  
  
HRESULT GetParameterProperties(  
DB_UPARAMS *pcParams,  
SSPARAMPROPS **prgParamProperties);  
```  
  
## <a name="arguments"></a>参数  
 pcParams[out][in]**  
 一个指向内存的指针，该内存包含 prgParamProperties 中返回的 SSPARAMPROPS 结构数量**。  
  
 prgParamProperties[out]**  
 指向内存中将返回 SSPARAMPROPS 结构数组的位置的指针。 提供程序为结构分配内存并返回此内存的地址;当使用者不再需要结构时，将使用**IMalloc：： Free**释放此内存。 在调用**IMalloc：： Free** for *prgParamProperties*之前，使用者还必须调用每个 DBPROP 结构的*vValue*属性的**VariantClear** ，以防止在变体包含引用类型 (例如 BSTR）的情况下发生内存泄漏。 ) 如果在输出中*pcParams*为零或发生除 DB_E_ERRORSOCCURRED 之外的错误，则访问接口不会分配任何内存，并确保*prgParamProperties*在输出时为 null 指针。  
  
## <a name="return-code-values"></a>返回代码值  
 **GetParameterProperties**方法返回与 Core OLE DB **ICommandProperties：： GetProperties**方法相同的错误代码，但不能引发 DB_S_ERRORSOCCURRED 和 DB_E_ERRORSOCCURED。  
  
## <a name="remarks"></a>备注  
 对于**GetParameterInfo**， **ISSCommandWithParameters：： GetParameterProperties**的行为一致。 如果未调用[ISSCommandWithParameters：： SetParameterProperties](isscommandwithparameters-setparameterproperties-ole-db.md)或**SetParameterInfo** cParams 等于零，则**GetParameterInfo**将派生参数信息并返回 this。 如果已为至少一个参数调用了**ISSCommandWithParameters：： SetParameterProperties**或**SetParameterInfo** ，则**ISSCommandWithParameters：： GetParameterProperties**仅返回已调用**ISSCommandWithParameters：： SetParameterProperties**的那些参数的属性。 如果在**ISSCommandWithParameters：： GetParameterProperties**或**GetParameterInfo**后调用**ISSCommandWithParameters：： SetParameterProperties** ，则对**ISSCommandWithParameters：： GetParameterProperties**的后续调用将返回为其调用**ISSCommandWithParameters：： SetParameterProperties**的那些参数的重写值。  
  
 SSPARAMPROPS 结构的定义如下所示：  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
|成员|描述|  
|------------|-----------------|  
|iOrdinal**|所传递参数的序号。|  
|cPropertySets**|rgPropertySets 中 DBPROPSET 结构的数量**。|  
|rgPropertySets**|指向内存中将返回 DBPROPSET 结构数组的位置的指针。|  
  
## <a name="see-also"></a>另请参阅  
 [ISSCommandWithParameters &#40;OLE DB&#41;](isscommandwithparameters-ole-db.md)  
  
  
