---
title: IsSharePointIntegrated 属性 (WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- IsSharePointIntegrated property
ms.assetid: c548fed8-5e04-4faf-8b10-b37c86178056
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a1f3f38c23546ddf4dfb52c2a3af7c122af10cbd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588898"
---
# <a name="issharepointintegrated-property-wmi"></a><span data-ttu-id="3da4d-102">IsSharePointIntegrated 属性 (WMI)</span><span class="sxs-lookup"><span data-stu-id="3da4d-102">IsSharePointIntegrated Property (WMI)</span></span>
  <span data-ttu-id="3da4d-103">指定报表服务器是否处于 SharePoint 集成模式。</span><span class="sxs-lookup"><span data-stu-id="3da4d-103">Specifies whether the report server is in SharePoint integrated mode.</span></span> <span data-ttu-id="3da4d-104">从 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 开始，此属性将始终返回 `False`，因为在 SharePoint 模式下，[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 实例为 SharePoint 共享服务，且不受 WMI 提供程序的控制。</span><span class="sxs-lookup"><span data-stu-id="3da4d-104">Beginning in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], this property always returns `False` because in SharePoint mode, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instances are SharePoint shared services and are not controlled by WMI providers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3da4d-105">语法</span><span class="sxs-lookup"><span data-stu-id="3da4d-105">Syntax</span></span>  
  
```vb  
Public Dim IsSharePointIntegrated As Boolean  
```  
  
```csharp  
public Boolean IsSharePointIntegrated;  
```  
  
## <a name="property-values"></a><span data-ttu-id="3da4d-106">属性值</span><span class="sxs-lookup"><span data-stu-id="3da4d-106">Property Values</span></span>  
 <span data-ttu-id="3da4d-107">一个 `Boolean` 对象，指示报表服务器是否处于 SharePoint 集成模式。</span><span class="sxs-lookup"><span data-stu-id="3da4d-107">A `Boolean` object that indicates whether the report server is in SharePoint integrated mode.</span></span>  
  
## <a name="example-code"></a><span data-ttu-id="3da4d-108">示例代码</span><span class="sxs-lookup"><span data-stu-id="3da4d-108">Example Code</span></span>  
 [<span data-ttu-id="3da4d-109">MSReportServer_ConfigurationSetting 类</span><span class="sxs-lookup"><span data-stu-id="3da4d-109">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a><span data-ttu-id="3da4d-110">要求</span><span class="sxs-lookup"><span data-stu-id="3da4d-110">Requirements</span></span>  
 <span data-ttu-id="3da4d-111">**命名空间：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3da4d-111">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3da4d-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3da4d-112">See Also</span></span>  
 [<span data-ttu-id="3da4d-113">MSReportServer_ConfigurationSetting 成员</span><span class="sxs-lookup"><span data-stu-id="3da4d-113">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
