---
title: SetServiceAccountPassword 方法 (SqlService 类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetServiceAccountPassword Method (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetServiceAccountPassword method
ms.assetid: e577a1ac-985c-4799-bb38-9393efc3def2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e7a83a6d3686b2ec2df98ae79b4c9d3347f621ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687596"
---
# <a name="setserviceaccountpassword-method-sqlservice-class"></a><span data-ttu-id="1e4b0-102">SetServiceAccountPassword 方法（SqlService 类）</span><span class="sxs-lookup"><span data-stu-id="1e4b0-102">SetServiceAccountPassword Method (SqlService Class)</span></span>
  <span data-ttu-id="1e4b0-103">修改引用的服务运行时使用的帐户的密码。</span><span class="sxs-lookup"><span data-stu-id="1e4b0-103">Modifies the password for the account that the referenced service runs under.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e4b0-104">语法</span><span class="sxs-lookup"><span data-stu-id="1e4b0-104">Syntax</span></span>  
  
```  
  
object  
.SetServiceAccountPassword(  
AccountOldPassword , ServiceStartPassword  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="1e4b0-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="1e4b0-105">Parts</span></span>  
 <span data-ttu-id="1e4b0-106">对象</span><span class="sxs-lookup"><span data-stu-id="1e4b0-106">*object*</span></span>  
 <span data-ttu-id="1e4b0-107">一个表示服务的 [SqlService 类](sqlservice-class.md) 对象。</span><span class="sxs-lookup"><span data-stu-id="1e4b0-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="1e4b0-108">参数</span><span class="sxs-lookup"><span data-stu-id="1e4b0-108">Parameters</span></span>  
 <span data-ttu-id="1e4b0-109">*AccountOldPassword*</span><span class="sxs-lookup"><span data-stu-id="1e4b0-109">*AccountOldPassword*</span></span>  
 <span data-ttu-id="1e4b0-110">一个指定帐户的现有密码的字符串值。</span><span class="sxs-lookup"><span data-stu-id="1e4b0-110">A string value that specifies the existing password for the account.</span></span>  
  
 <span data-ttu-id="1e4b0-111">*ServiceStartPassword*</span><span class="sxs-lookup"><span data-stu-id="1e4b0-111">*ServiceStartPassword*</span></span>  
 <span data-ttu-id="1e4b0-112">一个指定帐户的新密码的字符串值。</span><span class="sxs-lookup"><span data-stu-id="1e4b0-112">A string value that specifies the new password for the account.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="1e4b0-113">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="1e4b0-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="1e4b0-114">一个 `uint32` 值，如果服务已成功修改，则为 0；如果不支持请求，则为 1；其他任何数字表示出现错误。</span><span class="sxs-lookup"><span data-stu-id="1e4b0-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e4b0-115">备注</span><span class="sxs-lookup"><span data-stu-id="1e4b0-115">Remarks</span></span>  
  
