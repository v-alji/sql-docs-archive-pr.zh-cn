---
title: GetAdminSiteUrl 方法 (WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- GetAdminSiteUrl method
ms.assetid: fbc5bf3c-120c-4aec-a4f2-f5391bd415f6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cae1a6f7e363ddce8c47c00eb5ef25fc832e59c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581108"
---
# <a name="getadminsiteurl-method-wmi"></a><span data-ttu-id="04d00-102">GetAdminSiteUrl 方法 (WMI)</span><span class="sxs-lookup"><span data-stu-id="04d00-102">GetAdminSiteUrl Method (WMI)</span></span>
  <span data-ttu-id="04d00-103">获取集成报表服务器的 Microsoft [!INCLUDE[winSPServ](../../includes/winspserv-md.md)]、 [!INCLUDE[offSPServ](../../includes/offspserv-md.md)]、 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]或 [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] 场管理中心网站的绝对 URL。</span><span class="sxs-lookup"><span data-stu-id="04d00-103">Gets the absolute URL for the Central Administration Web site for the Microsoft [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)], or [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] farm that the report server is integrated with.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04d00-104">语法</span><span class="sxs-lookup"><span data-stu-id="04d00-104">Syntax</span></span>  
  
```vb  
Public Sub GetAdminSiteUrl(ByRef AdminSiteUrl as String, _  
ByRef HRESULT as Int32)  
```  
  
```csharp  
public void GetAdminSiteUrl(out string AdminSiteUrl, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04d00-105">parameters</span><span class="sxs-lookup"><span data-stu-id="04d00-105">Parameters</span></span>  
 <span data-ttu-id="04d00-106">*AdminSiteUrl*</span><span class="sxs-lookup"><span data-stu-id="04d00-106">*AdminSiteUrl*</span></span>  
 <span data-ttu-id="04d00-107">[out] 一个字符串，包含集成报表服务器的 SharePoint 场管理中心网站的绝对 URL。</span><span class="sxs-lookup"><span data-stu-id="04d00-107">[out] A string that contains the absolute URL for the Central Administration Web site for the SharePoint farm that the report server is integrated with.</span></span>  
  
 <span data-ttu-id="04d00-108">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="04d00-108">*HRESULT*</span></span>  
 <span data-ttu-id="04d00-109">[out] 指示调用是成功还是失败的值。</span><span class="sxs-lookup"><span data-stu-id="04d00-109">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="04d00-110">返回值</span><span class="sxs-lookup"><span data-stu-id="04d00-110">Return Value</span></span>  
 <span data-ttu-id="04d00-111">返回 *HRESULT* ，指示方法调用是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="04d00-111">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="04d00-112">值 0 指示方法调用已成功。</span><span class="sxs-lookup"><span data-stu-id="04d00-112">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="04d00-113">非零值指示已发生错误。</span><span class="sxs-lookup"><span data-stu-id="04d00-113">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04d00-114">要求</span><span class="sxs-lookup"><span data-stu-id="04d00-114">Requirements</span></span>  
 <span data-ttu-id="04d00-115">**命名空间：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04d00-115">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04d00-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="04d00-116">See Also</span></span>  
 [<span data-ttu-id="04d00-117">MSReportServer_ConfigurationSetting 方法</span><span class="sxs-lookup"><span data-stu-id="04d00-117">MSReportServer_ConfigurationSetting Methods</span></span>](msreportserver-configurationsetting-methods.md)  
  
  
