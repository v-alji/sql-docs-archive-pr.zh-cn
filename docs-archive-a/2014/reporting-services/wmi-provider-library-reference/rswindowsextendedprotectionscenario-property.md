---
title: " (WMI MSReportServer_ConfigurationSetting) 的 RSWindowsExtendedProtectionScenario 属性 |Microsoft Docs"
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5ac7ab80-9adf-4f65-abfa-fedf53b082b5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 84e14d056cc0352b0d1d85bc12c9c873a1b89ced
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691031"
---
# <a name="rswindowsextendedprotectionscenario-property-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="2808b-102">RSWindowsExtendedProtectionScenario 属性 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="2808b-102">RSWindowsExtendedProtectionScenario Property (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="2808b-103">返回一个字符串值，该值指示报表服务器配置为允许的扩展保护方案。</span><span class="sxs-lookup"><span data-stu-id="2808b-103">Returns a string value that indicates the extended protection scenario the report server is configured to allow.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2808b-104">语法</span><span class="sxs-lookup"><span data-stu-id="2808b-104">Syntax</span></span>  
  
```vb  
Public Dim RSWindowsExtendedProtectionScenario As String  
```  
  
```csharp  
public string RSWindowsExtendedProtectionScenario;  
```  
  
## <a name="remarks"></a><span data-ttu-id="2808b-105">备注</span><span class="sxs-lookup"><span data-stu-id="2808b-105">Remarks</span></span>  
 <span data-ttu-id="2808b-106">返回一个字符串值，该值指示报表服务器配置为允许的扩展保护方案。</span><span class="sxs-lookup"><span data-stu-id="2808b-106">Returns a string value that indicates the extended protection scenario the report server is configured to allow.</span></span> <span data-ttu-id="2808b-107">如果 WMI 提供程序连接到的报表服务器不支持扩展保护，则返回“”（空字符串）。</span><span class="sxs-lookup"><span data-stu-id="2808b-107">If the report server that the WMI provider is connected to does not support extended protection, "" (empty string) is returned.</span></span>  
  
 <span data-ttu-id="2808b-108">下表显示有效值：</span><span class="sxs-lookup"><span data-stu-id="2808b-108">The following list shows valid values:</span></span>  
  
 `"Any | Proxy | Direct"`  
  
## <a name="example-code"></a><span data-ttu-id="2808b-109">示例代码</span><span class="sxs-lookup"><span data-stu-id="2808b-109">Example Code</span></span>  
 [<span data-ttu-id="2808b-110">MSReportServer_ConfigurationSetting 类</span><span class="sxs-lookup"><span data-stu-id="2808b-110">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
## <a name="see-also"></a><span data-ttu-id="2808b-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2808b-111">See Also</span></span>  
 <span data-ttu-id="2808b-112">[RSWindowsExtendedProtectionLevel 属性 (WMI MSReportServer_ConfigurationSetting)](rswindowsextendedprotectionlevel-property.md) </span><span class="sxs-lookup"><span data-stu-id="2808b-112">[RSWindowsExtendedProtectionLevel Property &#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionlevel-property.md) </span></span>  
 <span data-ttu-id="2808b-113">[SetExtendedProtectionSettings 方法 (WMI MSReportServer_ConfigurationSetting)](configurationsetting-method-setextendedprotectionsettings.md) </span><span class="sxs-lookup"><span data-stu-id="2808b-113">[SetExtendedProtectionSettings Method &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-setextendedprotectionsettings.md) </span></span>  
 <span data-ttu-id="2808b-114">[Reporting Services 针对验证的扩展保护](../security/extended-protection-for-authentication-with-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="2808b-114">[Extended Protection for Authentication with Reporting Services](../security/extended-protection-for-authentication-with-reporting-services.md) </span></span>  
 [<span data-ttu-id="2808b-115">RSReportServer Configuration File</span><span class="sxs-lookup"><span data-stu-id="2808b-115">RSReportServer Configuration File</span></span>](../report-server/rsreportserver-config-configuration-file.md)  
  
  
