---
title: DisplayName 属性 (SqlService 类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- DisplayName Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- DisplayName property
ms.assetid: 49c408aa-6eb4-45cd-8d5c-60f065f24f5c
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 147fc298d6d263caf1e4ad6852d4b02f86911572
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692316"
---
# <a name="displayname-property-sqlservice-class"></a><span data-ttu-id="e98c3-102">DisplayName 属性（SqlService 类）</span><span class="sxs-lookup"><span data-stu-id="e98c3-102">DisplayName Property (SqlService Class)</span></span>
  <span data-ttu-id="e98c3-103">获取服务的显示名称。</span><span class="sxs-lookup"><span data-stu-id="e98c3-103">Gets the display name of the service.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e98c3-104">语法</span><span class="sxs-lookup"><span data-stu-id="e98c3-104">Syntax</span></span>  
  
```  
  
object  
.DisplayName [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="e98c3-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="e98c3-105">Parts</span></span>  
 <span data-ttu-id="e98c3-106">对象</span><span class="sxs-lookup"><span data-stu-id="e98c3-106">*object*</span></span>  
 <span data-ttu-id="e98c3-107">一个表示服务的 [SqlService 类](sqlservice-class.md) 对象。</span><span class="sxs-lookup"><span data-stu-id="e98c3-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="e98c3-108">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="e98c3-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="e98c3-109">一个指定服务的显示名称的字符串值。</span><span class="sxs-lookup"><span data-stu-id="e98c3-109">A string value that specifies the display name of the service.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e98c3-110">备注</span><span class="sxs-lookup"><span data-stu-id="e98c3-110">Remarks</span></span>  
 <span data-ttu-id="e98c3-111">此字符串的最大长度为 256 个字符。</span><span class="sxs-lookup"><span data-stu-id="e98c3-111">This string has a maximum length of 256 characters.</span></span> <span data-ttu-id="e98c3-112">此名称在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 配置管理器中是区分大小写的。</span><span class="sxs-lookup"><span data-stu-id="e98c3-112">The name is case-preserved in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="e98c3-113">但是，显示名称比较始终不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="e98c3-113">However, display name comparisons are always case-insensitive.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e98c3-114">示例</span><span class="sxs-lookup"><span data-stu-id="e98c3-114">Example</span></span>  
  
```  
mysqlservice.DisplayName = "Atdisk"  
```  
  
## <a name="see-also"></a><span data-ttu-id="e98c3-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e98c3-115">See Also</span></span>  
 <span data-ttu-id="e98c3-116">[启动和停止服务](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="e98c3-116">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
