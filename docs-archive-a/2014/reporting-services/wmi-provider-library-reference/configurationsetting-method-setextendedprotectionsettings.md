---
title: SetExtendedProtectionSettings 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2d8e7232-42f4-41b6-98eb-c856f6c85d8c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ee937747b74bcf8d53012721b4be5bfca04185df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692188"
---
# <a name="setextendedprotectionsettings-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="b83b6-102">SetExtendedProtectionSettings 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="b83b6-102">SetExtendedProtectionSettings Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="b83b6-103">SetExtendedProtectionSettings 方法用于设置 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置文件 RSReportServer.config 中的 RSWindowsExtendedProtectionLevel 和 RSWindowsExtendedProtectionScenario 属性。</span><span class="sxs-lookup"><span data-stu-id="b83b6-103">The SetExtendedProtectionSettings method is used to set the RSWindowsExtendedProtectionLevel and the RSWindowsExtendedProtectionScenario properties in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] configuration file RSReportServer.config.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b83b6-104">语法</span><span class="sxs-lookup"><span data-stu-id="b83b6-104">Syntax</span></span>  
  
```vb  
Public Sub SetExtendedProtectionSettings( _  
        ByVal ExtendedProtectionLevel As String, _  
        ByVal ExtendedProtectionScenario As String, _  
        ByRef Warnings() As String, _  
        ByRef Length As Int32, _  
        ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetExtendedProtectionSettings(  
            string ExtendedProtectionLevel,  
            string ExtendedProtectionScenario,  
            out string[] Warnings,  
            out Int32 Length,  
            out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b83b6-105">parameters</span><span class="sxs-lookup"><span data-stu-id="b83b6-105">Parameters</span></span>  
 <span data-ttu-id="b83b6-106">*ExtendedProtectionLevel*</span><span class="sxs-lookup"><span data-stu-id="b83b6-106">*ExtendedProtectionLevel*</span></span>  
 <span data-ttu-id="b83b6-107">设置 RSRreportserver.config 文件中的 RSWindowsExtendedProtectionLevel。</span><span class="sxs-lookup"><span data-stu-id="b83b6-107">Sets the RSWindowsExtendedProtectionLevel in the RSRreportserver.config file.</span></span> <span data-ttu-id="b83b6-108">必需值不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="b83b6-108">The required value is not case sensitive.</span></span>  
  
 <span data-ttu-id="b83b6-109">下表显示有效值：</span><span class="sxs-lookup"><span data-stu-id="b83b6-109">The following list shows valid values:</span></span>  
  
 `"Off | Allow | Require"`  
  
 <span data-ttu-id="b83b6-110">*ExtendedProtectionScenario*</span><span class="sxs-lookup"><span data-stu-id="b83b6-110">*ExtendedProtectionScenario*</span></span>  
 <span data-ttu-id="b83b6-111">设置 RSReportserver.config 文件中的 RSWindowsExtendedProtectionScenario。</span><span class="sxs-lookup"><span data-stu-id="b83b6-111">Sets the RSWindowsExtendedProtectionScenario in the RSReportserver.config file.</span></span> <span data-ttu-id="b83b6-112">必需值不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="b83b6-112">The required value is not case sensitive.</span></span>  
  
 <span data-ttu-id="b83b6-113">下表显示有效值：</span><span class="sxs-lookup"><span data-stu-id="b83b6-113">The following list shows valid values:</span></span>  
  
 `"Any" | "Proxy" | "Direct"`  
  
## <a name="remarks"></a><span data-ttu-id="b83b6-114">备注</span><span class="sxs-lookup"><span data-stu-id="b83b6-114">Remarks</span></span>  
 <span data-ttu-id="b83b6-115">当 RSReportServer.config 文件中的 AuthenticationTypes 包括 RSWindowNTLM、RSWindowsNegotiate 或 RSWindowsKerberos 时，应用 RSWindowsExtendedProtectionLevel 和 RSWindowsExtendedProtectionScenario 属性。</span><span class="sxs-lookup"><span data-stu-id="b83b6-115">The RSWindowsExtendedProtectionLevel and the RSWindowsExtendedProtectionScenario properties apply when the AuthenticationTypes in the RSReportServer.config file include RSWindowNTLM, RSWindowsNegotiate, or RSWindowsKerberos.</span></span> <span data-ttu-id="b83b6-116">设置这些属性将影响用户和客户端软件如何在报表服务器上进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="b83b6-116">Setting these properties affects how users and client software authenticate with a report server.</span></span> <span data-ttu-id="b83b6-117">建议你在将 ExtendedProtectionLevel 设置为 `Allow` 或 `Require` 前阅读有关扩展保护的文档。</span><span class="sxs-lookup"><span data-stu-id="b83b6-117">It is recommended that you read the documentation for extended protection before setting ExtendedProtectionLevel to either `Allow` or `Require`.</span></span>  
  
 <span data-ttu-id="b83b6-118">要设置 ExtendedProtectionLevel，用户必须是报表服务器上 BUILTIN\Administrators 组的成员。</span><span class="sxs-lookup"><span data-stu-id="b83b6-118">To set the ExtendedProtectionLevel, the user must be a member of the BUILTIN\Administrators group on the report server.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b83b6-119">要求</span><span class="sxs-lookup"><span data-stu-id="b83b6-119">Requirements</span></span>  
 <span data-ttu-id="b83b6-120">**命名空间：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b83b6-120">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b83b6-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b83b6-121">See Also</span></span>  
 <span data-ttu-id="b83b6-122">[RSWindowsExtendedProtectionScenario 属性 (WMI MSReportServer_ConfigurationSetting)](rswindowsextendedprotectionscenario-property.md) </span><span class="sxs-lookup"><span data-stu-id="b83b6-122">[RSWindowsExtendedProtectionScenario Property &#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionscenario-property.md) </span></span>  
 <span data-ttu-id="b83b6-123">[RSWindowsExtendedProtectionLevel 属性 (WMI MSReportServer_ConfigurationSetting)](rswindowsextendedprotectionlevel-property.md) </span><span class="sxs-lookup"><span data-stu-id="b83b6-123">[RSWindowsExtendedProtectionLevel Property &#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionlevel-property.md) </span></span>  
 <span data-ttu-id="b83b6-124">[Reporting Services 针对验证的扩展保护](../security/extended-protection-for-authentication-with-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="b83b6-124">[Extended Protection for Authentication with Reporting Services](../security/extended-protection-for-authentication-with-reporting-services.md) </span></span>  
 [<span data-ttu-id="b83b6-125">RSReportServer Configuration File</span><span class="sxs-lookup"><span data-stu-id="b83b6-125">RSReportServer Configuration File</span></span>](../report-server/rsreportserver-config-configuration-file.md)  
  
  
