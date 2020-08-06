---
title: PropertyValType 属性 (ServerNetworkProtocolProperty 类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- PropertyValType Property (ServerNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- PropertyValType property
ms.assetid: fbd42e8e-0642-4a19-b3c8-6ce88345145f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: be6c42fbaa36080ec8144d95abb045a3b4328057
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692815"
---
# <a name="propertyvaltype-property-servernetworkprotocolproperty-class"></a><span data-ttu-id="a85ae-102">PropertyValType 属性（ServerNetworkProtocolProperty 类）</span><span class="sxs-lookup"><span data-stu-id="a85ae-102">PropertyValType Property (ServerNetworkProtocolProperty Class)</span></span>
  <span data-ttu-id="a85ae-103">获取存储在所引用属性中的值的数据类型。</span><span class="sxs-lookup"><span data-stu-id="a85ae-103">Gets the data type of the value stored in the referenced property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a85ae-104">语法</span><span class="sxs-lookup"><span data-stu-id="a85ae-104">Syntax</span></span>  
  
```  
  
object  
.PropertyValType [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="a85ae-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="a85ae-105">Parts</span></span>  
 <span data-ttu-id="a85ae-106">对象</span><span class="sxs-lookup"><span data-stu-id="a85ae-106">*object*</span></span>  
 <span data-ttu-id="a85ae-107">一个表示实例上的网络协议属性的[ServerNetworkProtocolProperty 类](servernetworkprotocolproperty-class.md)对象 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a85ae-107">A [ServerNetworkProtocolProperty Class](servernetworkprotocolproperty-class.md) object that represents an attribute of the network protocol on the instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="a85ae-108">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="a85ae-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="a85ae-109">一个指定属性值的数据类型的 `uint32` 值。</span><span class="sxs-lookup"><span data-stu-id="a85ae-109">A `uint32` value that specifies the data type of the property value.</span></span> <span data-ttu-id="a85ae-110">如果是字符串值类型，则返回 0；如果是数值类型，则返回 1。</span><span class="sxs-lookup"><span data-stu-id="a85ae-110">It returns 0 for a string value and 1 for a numerical type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a85ae-111">备注</span><span class="sxs-lookup"><span data-stu-id="a85ae-111">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a85ae-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a85ae-112">See Also</span></span>  
 <span data-ttu-id="a85ae-113">[配置服务器网络协议和网络库](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="a85ae-113">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
