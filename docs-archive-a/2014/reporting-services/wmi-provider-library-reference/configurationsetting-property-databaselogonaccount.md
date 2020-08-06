---
title: DatabaseLogonAccount 属性 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- DatabaseLogonAccount
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DatabaseLogonAccount property
ms.assetid: 55f2863f-1ac1-4519-b512-e7f11c0ea5ea
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6f9e844ff1d1447bd5abfefad8e82939575c7f47
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692172"
---
# <a name="databaselogonaccount-property-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="9272c-102">DatabaseLogonAccount 属性 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="9272c-102">DatabaseLogonAccount Property (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="9272c-103">指定报表服务器连接到报表服务器数据库时使用的登录帐户。</span><span class="sxs-lookup"><span data-stu-id="9272c-103">Specifies the logon account that the report server uses when connecting to the report server database.</span></span> <span data-ttu-id="9272c-104">只读。</span><span class="sxs-lookup"><span data-stu-id="9272c-104">Read only.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9272c-105">语法</span><span class="sxs-lookup"><span data-stu-id="9272c-105">Syntax</span></span>  
  
```vb  
Public Dim DatabaseLogonAccount As String  
```  
  
```csharp  
public string DatabaseLogonAccount;  
```  
  
## <a name="property-values"></a><span data-ttu-id="9272c-106">属性值</span><span class="sxs-lookup"><span data-stu-id="9272c-106">Property Values</span></span>  
 <span data-ttu-id="9272c-107">表示登录帐户名的 `String` 对象。</span><span class="sxs-lookup"><span data-stu-id="9272c-107">A `String` object that represents the logon account name.</span></span>  
  
## <a name="example-code"></a><span data-ttu-id="9272c-108">示例代码</span><span class="sxs-lookup"><span data-stu-id="9272c-108">Example Code</span></span>  
 [<span data-ttu-id="9272c-109">MSReportServer_ConfigurationSetting 类</span><span class="sxs-lookup"><span data-stu-id="9272c-109">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
## <a name="remarks"></a><span data-ttu-id="9272c-110">备注</span><span class="sxs-lookup"><span data-stu-id="9272c-110">Remarks</span></span>  
 <span data-ttu-id="9272c-111">此属性的有效值将因 [DatabaseLogonType](configurationsetting-property-databaselogontype.md) 属性的值而异。</span><span class="sxs-lookup"><span data-stu-id="9272c-111">Valid values for this property will vary depending on the value of the [DatabaseLogonType](configurationsetting-property-databaselogontype.md) property.</span></span>  
  
 <span data-ttu-id="9272c-112">如果[DatabaseLogonType](configurationsetting-property-databaselogontype.md)属性设置为，则忽略此属性 `2 (Service)` 。</span><span class="sxs-lookup"><span data-stu-id="9272c-112">This property is ignored if the [DatabaseLogonType](configurationsetting-property-databaselogontype.md) property is set to `2 (Service)`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9272c-113">要求</span><span class="sxs-lookup"><span data-stu-id="9272c-113">Requirements</span></span>  
 <span data-ttu-id="9272c-114">**命名空间：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9272c-114">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9272c-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9272c-115">See Also</span></span>  
 [<span data-ttu-id="9272c-116">MSReportServer_ConfigurationSetting 成员</span><span class="sxs-lookup"><span data-stu-id="9272c-116">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
