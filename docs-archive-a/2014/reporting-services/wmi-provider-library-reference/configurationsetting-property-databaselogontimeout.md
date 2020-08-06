---
title: DatabaseLogonTimeout 属性 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- DatabaseLogonTimeout Property
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DatabaseLogonTimeout property
ms.assetid: 4a65162c-33de-485e-8fd3-2bd6bff8bf8d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4920f5ef2282478f4d12a19b0806cf6ff9632cac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692168"
---
# <a name="databaselogontimeout-property-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="e42f0-102">DatabaseLogonTimeout 属性 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="e42f0-102">DatabaseLogonTimeout Property (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="e42f0-103">指定尝试登录到报表服务器数据库失败前等待的秒数。</span><span class="sxs-lookup"><span data-stu-id="e42f0-103">Specifies the number of seconds to wait before an attempt to log on to the report server database fails.</span></span> <span data-ttu-id="e42f0-104">值 **0** 指示无限期的等待时间。</span><span class="sxs-lookup"><span data-stu-id="e42f0-104">A value of **0** indicates an infinite wait time.</span></span> <span data-ttu-id="e42f0-105">只读。</span><span class="sxs-lookup"><span data-stu-id="e42f0-105">Read only.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e42f0-106">语法</span><span class="sxs-lookup"><span data-stu-id="e42f0-106">Syntax</span></span>  
  
```vb  
Public Dim DatabaseLogonTimeout As Int32  
```  
  
```csharp  
public Int32 DatabaseLogonTimeout;  
```  
  
## <a name="property-values"></a><span data-ttu-id="e42f0-107">属性值</span><span class="sxs-lookup"><span data-stu-id="e42f0-107">Property Values</span></span>  
 <span data-ttu-id="e42f0-108">一个表示秒数的 32 位带符号整数对象。</span><span class="sxs-lookup"><span data-stu-id="e42f0-108">A 32-bit signed integer object that represents the number of seconds.</span></span>  
  
## <a name="example-code"></a><span data-ttu-id="e42f0-109">示例代码</span><span class="sxs-lookup"><span data-stu-id="e42f0-109">Example Code</span></span>  
 [<span data-ttu-id="e42f0-110">MSReportServer_ConfigurationSetting 类</span><span class="sxs-lookup"><span data-stu-id="e42f0-110">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a><span data-ttu-id="e42f0-111">要求</span><span class="sxs-lookup"><span data-stu-id="e42f0-111">Requirements</span></span>  
 <span data-ttu-id="e42f0-112">**命名空间：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e42f0-112">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e42f0-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e42f0-113">See Also</span></span>  
 [<span data-ttu-id="e42f0-114">MSReportServer_ConfigurationSetting 成员</span><span class="sxs-lookup"><span data-stu-id="e42f0-114">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
