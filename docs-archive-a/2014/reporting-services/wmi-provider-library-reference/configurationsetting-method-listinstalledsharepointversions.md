---
title: ListInstalledSharePointVersions 方法 (WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ListInstalledSharePointVersions method
ms.assetid: 8f0a5e9f-23f1-41e5-9a90-dfec19ef1df7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f0ceee23876461cf31cbd265ea39ae015ddcbc49
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581106"
---
# <a name="listinstalledsharepointversions-method-wmi"></a><span data-ttu-id="733a7-102">ListInstalledSharePointVersions 方法 (WMI)</span><span class="sxs-lookup"><span data-stu-id="733a7-102">ListInstalledSharePointVersions Method (WMI)</span></span>
  <span data-ttu-id="733a7-103">返回一组标记，表示与报表服务器安装在同一台计算机上的 Microsoft [!INCLUDE[winSPServ](../../includes/winspserv-md.md)]、 [!INCLUDE[offSPServ](../../includes/offspserv-md.md)]、 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]或 [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="733a7-103">Returns a set of tokens that represent the versions of Microsoft [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)], or [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] that are installed on the same computer as the report server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="733a7-104">语法</span><span class="sxs-lookup"><span data-stu-id="733a7-104">Syntax</span></span>  
  
```vb  
Public Sub ListInstalledSharePointVersions(ByRef VersionTokens() _  
    As String, ByRef Length As Int32, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void ListReportServersInDatabase (out string[] VersionTokens,   
    out Int32 Length, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="733a7-105">parameters</span><span class="sxs-lookup"><span data-stu-id="733a7-105">Parameters</span></span>  
 <span data-ttu-id="733a7-106">*VersionTokens[]*</span><span class="sxs-lookup"><span data-stu-id="733a7-106">*VersionTokens[]*</span></span>  
 <span data-ttu-id="733a7-107">[out] 一个包含表示 SharePoint 产品或技术的版本的标记的数组，该版本与安装的报表服务器兼容。</span><span class="sxs-lookup"><span data-stu-id="733a7-107">[out] An array that contains the tokens that represent the version of a SharePoint product or technology that is compatible with the installed report server.</span></span>  
  
 <span data-ttu-id="733a7-108">*长度*</span><span class="sxs-lookup"><span data-stu-id="733a7-108">*Length*</span></span>  
 <span data-ttu-id="733a7-109">[out] 版本标记数组的长度。</span><span class="sxs-lookup"><span data-stu-id="733a7-109">[out] The length of the version tokens array.</span></span>  
  
 <span data-ttu-id="733a7-110">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="733a7-110">*HRESULT*</span></span>  
 <span data-ttu-id="733a7-111">[out] 指示调用是成功还是失败的值。</span><span class="sxs-lookup"><span data-stu-id="733a7-111">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="733a7-112">返回值</span><span class="sxs-lookup"><span data-stu-id="733a7-112">Return Value</span></span>  
 <span data-ttu-id="733a7-113">返回 *HRESULT* ，指示方法调用是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="733a7-113">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="733a7-114">值 0 指示方法调用已成功。</span><span class="sxs-lookup"><span data-stu-id="733a7-114">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="733a7-115">非零值指示已发生错误。</span><span class="sxs-lookup"><span data-stu-id="733a7-115">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="733a7-116">备注</span><span class="sxs-lookup"><span data-stu-id="733a7-116">Remarks</span></span>  
 <span data-ttu-id="733a7-117">返回的每个标记都表示一个与当前安装的报表服务器兼容的 [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] 或 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="733a7-117">Each token that is returned represents a version of [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] or [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] that is compatible with the currently installed report server.</span></span> <span data-ttu-id="733a7-118">如果某个 SharePoint 特定版本兼容 SharePoint 的早期版本，则会返回每个 SharePoint 兼容版本的标记。</span><span class="sxs-lookup"><span data-stu-id="733a7-118">If a particular version of SharePoint is compatible with previous SharePoint versions, tokens for each compatible SharePoint version are returned.</span></span>  
  
 <span data-ttu-id="733a7-119">下表说明了返回的 SharePoint 标记。</span><span class="sxs-lookup"><span data-stu-id="733a7-119">The following is a table of the SharePoint tokens that are returned.</span></span>  
  
|<span data-ttu-id="733a7-120">**版本标记**</span><span class="sxs-lookup"><span data-stu-id="733a7-120">**Version Tokens**</span></span>|<span data-ttu-id="733a7-121">**说明**</span><span class="sxs-lookup"><span data-stu-id="733a7-121">**Description**</span></span>|  
|------------------------|---------------------|  
|<span data-ttu-id="733a7-122">WSS_V2_Compatible</span><span class="sxs-lookup"><span data-stu-id="733a7-122">WSS_V2_Compatible</span></span>|<span data-ttu-id="733a7-123">安装的 [!INCLUDE[winSPServ](../../includes/winspserv-md.md)]、 [!INCLUDE[winSPServ](../../includes/winspserv-md.md)]、 [!INCLUDE[offSPServ](../../includes/offspserv-md.md)]、 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]或 [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] 系统与 [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] 2.0 兼容。</span><span class="sxs-lookup"><span data-stu-id="733a7-123">A [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)], or [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] installation is installed that is compatible with [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] 2.0.</span></span>|  
|<span data-ttu-id="733a7-124">WSS_V3_Compatible</span><span class="sxs-lookup"><span data-stu-id="733a7-124">WSS_V3_Compatible</span></span>|<span data-ttu-id="733a7-125">安装的 [!INCLUDE[winSPServ](../../includes/winspserv-md.md)]、 [!INCLUDE[winSPServ](../../includes/winspserv-md.md)]、 [!INCLUDE[offSPServ](../../includes/offspserv-md.md)]、 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]或 [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] 系统与 [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] 3.0 兼容。</span><span class="sxs-lookup"><span data-stu-id="733a7-125">A [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)], or [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] installation is installed that is compatible with [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] 3.0.</span></span>|  
|<span data-ttu-id="733a7-126">WSS_V4_Compatible</span><span class="sxs-lookup"><span data-stu-id="733a7-126">WSS_V4_Compatible</span></span>|<span data-ttu-id="733a7-127">安装的 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] 或 [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] 系统与 Office 14 兼容。</span><span class="sxs-lookup"><span data-stu-id="733a7-127">A [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] or [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] installation is installed that is compatible with Office 14.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="733a7-128">要求</span><span class="sxs-lookup"><span data-stu-id="733a7-128">Requirements</span></span>  
 <span data-ttu-id="733a7-129">**命名空间：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="733a7-129">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="733a7-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="733a7-130">See Also</span></span>  
 [<span data-ttu-id="733a7-131">MSReportServer_ConfigurationSetting 成员</span><span class="sxs-lookup"><span data-stu-id="733a7-131">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
