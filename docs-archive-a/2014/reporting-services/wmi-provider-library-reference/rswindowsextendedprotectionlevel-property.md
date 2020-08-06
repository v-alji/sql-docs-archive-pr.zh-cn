---
title: " (WMI MSReportServer_ConfigurationSetting) 的 RSWindowsExtendedProtectionLevel 属性 |Microsoft Docs"
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 162ffe86-69c3-49d2-b9ed-49d097c05551
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 02ff3bad42ae25adf6cfa563944d89bac2c600e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581087"
---
# <a name="rswindowsextendedprotectionlevel-property-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="e7c0a-102">RSWindowsExtendedProtectionLevel 属性 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="e7c0a-102">RSWindowsExtendedProtectionLevel Property (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="e7c0a-103">返回一个字符串值，该值指示配置报表服务器所支持的保护级别。</span><span class="sxs-lookup"><span data-stu-id="e7c0a-103">Returns a string value that indicates the level of protection the report server is configured to support.</span></span> <span data-ttu-id="e7c0a-104">此属性为只读。</span><span class="sxs-lookup"><span data-stu-id="e7c0a-104">This property is read-only.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7c0a-105">语法</span><span class="sxs-lookup"><span data-stu-id="e7c0a-105">Syntax</span></span>  
  
```vb  
Public Dim RSWindowsExtendedProtectionLevel As String  
```  
  
```csharp  
public string RSWindowsExtendedProtectionLevel;  
```  
  
## <a name="remarks"></a><span data-ttu-id="e7c0a-106">备注</span><span class="sxs-lookup"><span data-stu-id="e7c0a-106">Remarks</span></span>  
 <span data-ttu-id="e7c0a-107">返回一个字符串值，该值指示配置报表服务器所支持的保护级别。</span><span class="sxs-lookup"><span data-stu-id="e7c0a-107">Returns a string value that indicates the level of protection the report server is configured to support.</span></span> <span data-ttu-id="e7c0a-108">如果 WMI 提供程序连接到的报表服务器不支持扩展保护，则返回“”（空字符串）。</span><span class="sxs-lookup"><span data-stu-id="e7c0a-108">If the report server that the WMI provider is connected to does not support extended protection, "" (empty string) is returned.</span></span> <span data-ttu-id="e7c0a-109">下表显示有效值：</span><span class="sxs-lookup"><span data-stu-id="e7c0a-109">The following list shows valid values:</span></span>  
  
 `"Off" | "Allow" | "Require"`  
  
## <a name="example-code"></a><span data-ttu-id="e7c0a-110">示例代码</span><span class="sxs-lookup"><span data-stu-id="e7c0a-110">Example Code</span></span>  
 [<span data-ttu-id="e7c0a-111">MSReportServer_ConfigurationSetting 类</span><span class="sxs-lookup"><span data-stu-id="e7c0a-111">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
## <a name="see-also"></a><span data-ttu-id="e7c0a-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e7c0a-112">See Also</span></span>  
 <span data-ttu-id="e7c0a-113">[RSWindowsExtendedProtectionScenario 属性 (WMI MSReportServer_ConfigurationSetting)](rswindowsextendedprotectionscenario-property.md) </span><span class="sxs-lookup"><span data-stu-id="e7c0a-113">[RSWindowsExtendedProtectionScenario Property &#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionscenario-property.md) </span></span>  
 <span data-ttu-id="e7c0a-114">[SetExtendedProtectionSettings 方法 (WMI MSReportServer_ConfigurationSetting)](configurationsetting-method-setextendedprotectionsettings.md) </span><span class="sxs-lookup"><span data-stu-id="e7c0a-114">[SetExtendedProtectionSettings Method &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-setextendedprotectionsettings.md) </span></span>  
 <span data-ttu-id="e7c0a-115">[Reporting Services 针对验证的扩展保护](../security/extended-protection-for-authentication-with-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="e7c0a-115">[Extended Protection for Authentication with Reporting Services](../security/extended-protection-for-authentication-with-reporting-services.md) </span></span>  
 [<span data-ttu-id="e7c0a-116">RSReportServer Configuration File</span><span class="sxs-lookup"><span data-stu-id="e7c0a-116">RSReportServer Configuration File</span></span>](../report-server/rsreportserver-config-configuration-file.md)  
  
  
