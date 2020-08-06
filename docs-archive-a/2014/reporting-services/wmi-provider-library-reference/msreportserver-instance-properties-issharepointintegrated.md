---
title: IsSharePointIntegrated 属性 (WMI MSReportServer_Instance) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- IsSharePointIntegrated property
ms.assetid: e21d00ad-5d9a-4290-8d74-7eeeda39e1ed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d0c92ebe586d37053b47f90ca98c31b3068a7b91
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581088"
---
# <a name="issharepointintegrated-property-wmi-msreportserver_instance"></a><span data-ttu-id="ee741-102">IsSharePointIntegrated 属性 (WMI MSReportServer_Instance)</span><span class="sxs-lookup"><span data-stu-id="ee741-102">IsSharePointIntegrated Property (WMI MSReportServer_Instance)</span></span>
  <span data-ttu-id="ee741-103">指定报表服务器是否处于 SharePoint 集成模式。</span><span class="sxs-lookup"><span data-stu-id="ee741-103">Specifies whether the report server is in SharePoint integrated mode.</span></span> <span data-ttu-id="ee741-104">从 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 开始，此属性将始终返回 `False`，因为在 SharePoint 模式下，[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 实例为 SharePoint 共享服务，且不受 WMI 提供程序的控制。</span><span class="sxs-lookup"><span data-stu-id="ee741-104">Beginning in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], this property always returns `False` because in SharePoint mode, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instances are SharePoint shared services and are not controlled by WMI providers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee741-105">语法</span><span class="sxs-lookup"><span data-stu-id="ee741-105">Syntax</span></span>  
  
```vb  
Public Dim IsSharePointIntegrated As Boolean  
```  
  
```csharp  
public Boolean IsSharePointIntegrated;  
```  
  
## <a name="property-values"></a><span data-ttu-id="ee741-106">属性值</span><span class="sxs-lookup"><span data-stu-id="ee741-106">Property Values</span></span>  
 <span data-ttu-id="ee741-107">一个 `Boolean` 值，指示报表服务器是否处于 SharePoint 集成模式。</span><span class="sxs-lookup"><span data-stu-id="ee741-107">A `Boolean` value that indicates whether the report server is in SharePoint integrated mode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee741-108">要求</span><span class="sxs-lookup"><span data-stu-id="ee741-108">Requirements</span></span>  
 <span data-ttu-id="ee741-109">**命名空间：** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee741-109">**Namespace:** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee741-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ee741-110">See Also</span></span>  
 <span data-ttu-id="ee741-111">[MSReportServer_Instance 成员](msreportserver-instance-members.md) </span><span class="sxs-lookup"><span data-stu-id="ee741-111">[MSReportServer_Instance Members](msreportserver-instance-members.md) </span></span>  
 [<span data-ttu-id="ee741-112">MSReportServer_ConfigurationSetting 类</span><span class="sxs-lookup"><span data-stu-id="ee741-112">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
  
