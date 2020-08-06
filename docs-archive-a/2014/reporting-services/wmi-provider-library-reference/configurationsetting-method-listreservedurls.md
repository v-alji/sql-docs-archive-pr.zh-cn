---
title: ListReservedURLs 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ListReservedURLs method
ms.assetid: 32335af1-5eae-4420-a0ef-b1e8a3267166
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7639741adb0c756961c4c6b63a3bffb627c4a89c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581101"
---
# <a name="listreservedurls-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="ed5c9-102">ListReservedURLs 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="ed5c9-102">ListReservedURLs Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="ed5c9-103">列出为报表服务器上所有应用程序保留的 URL。</span><span class="sxs-lookup"><span data-stu-id="ed5c9-103">Lists URLs reserved for all applications on the report server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed5c9-104">语法</span><span class="sxs-lookup"><span data-stu-id="ed5c9-104">Syntax</span></span>  
  
```vb  
Public Sub ListReservedUrls(ByRef Application() as String, ByRef UrlString() as String, _  
    ByRef Account() as String, ByRef AccountSID() as String, _  
    ByRef length() as Int32, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void ListReservedUrls(out string[] Application, out string[] UrlString,  
        out string[] Account, out string[] AccountSID,  
        out int[] Length, out int[] HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed5c9-105">parameters</span><span class="sxs-lookup"><span data-stu-id="ed5c9-105">Parameters</span></span>  
 <span data-ttu-id="ed5c9-106">*Application[]*</span><span class="sxs-lookup"><span data-stu-id="ed5c9-106">*Application[]*</span></span>  
 <span data-ttu-id="ed5c9-107">[out] 具有 URL 预留的应用程序。</span><span class="sxs-lookup"><span data-stu-id="ed5c9-107">[out] The applications that have URL reservations.</span></span>  
  
 <span data-ttu-id="ed5c9-108">*UrlString[]*</span><span class="sxs-lookup"><span data-stu-id="ed5c9-108">*UrlString[]*</span></span>  
 <span data-ttu-id="ed5c9-109">[out] 已保留的 URL。</span><span class="sxs-lookup"><span data-stu-id="ed5c9-109">[out] The URLs that are reserved.</span></span>  
  
 <span data-ttu-id="ed5c9-110">*Account[]*</span><span class="sxs-lookup"><span data-stu-id="ed5c9-110">*Account[]*</span></span>  
 <span data-ttu-id="ed5c9-111">[out] 与 URL 预留的帐户关联的帐户名。</span><span class="sxs-lookup"><span data-stu-id="ed5c9-111">[out] The account names associated with the account for the URL reservations.</span></span>  
  
 <span data-ttu-id="ed5c9-112">*AccountSID[]*</span><span class="sxs-lookup"><span data-stu-id="ed5c9-112">*AccountSID[]*</span></span>  
 <span data-ttu-id="ed5c9-113">[out] 与 URL 预留的帐户关联的帐户 SID。</span><span class="sxs-lookup"><span data-stu-id="ed5c9-113">[out] The account SIDs associated with the account for the URL reservations.</span></span>  
  
 <span data-ttu-id="ed5c9-114">*长度*</span><span class="sxs-lookup"><span data-stu-id="ed5c9-114">*Length*</span></span>  
 <span data-ttu-id="ed5c9-115">[out] 该方法返回的数组长度。</span><span class="sxs-lookup"><span data-stu-id="ed5c9-115">[out] The length of the arrays returned by the method.</span></span>  
  
 <span data-ttu-id="ed5c9-116">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="ed5c9-116">*HRESULT*</span></span>  
 <span data-ttu-id="ed5c9-117">[out] 指示调用是成功还是失败的值。</span><span class="sxs-lookup"><span data-stu-id="ed5c9-117">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ed5c9-118">返回值</span><span class="sxs-lookup"><span data-stu-id="ed5c9-118">Return Value</span></span>  
 <span data-ttu-id="ed5c9-119">返回 *HRESULT* ，指示方法调用是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="ed5c9-119">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="ed5c9-120">值 0 指示方法调用已成功；错误代码指示调用未成功。</span><span class="sxs-lookup"><span data-stu-id="ed5c9-120">A value of 0 indicates that the method call was successful; an error code indicates the call was not successful.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed5c9-121">备注</span><span class="sxs-lookup"><span data-stu-id="ed5c9-121">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed5c9-122">要求</span><span class="sxs-lookup"><span data-stu-id="ed5c9-122">Requirements</span></span>  
 <span data-ttu-id="ed5c9-123">**命名空间：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed5c9-123">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed5c9-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ed5c9-124">See Also</span></span>  
 [<span data-ttu-id="ed5c9-125">MSReportServer_ConfigurationSetting 成员</span><span class="sxs-lookup"><span data-stu-id="ed5c9-125">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
