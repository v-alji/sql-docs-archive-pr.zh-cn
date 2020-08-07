---
title: GetDatabaseVersionDisplayName 方法 (WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- GetDatabaseVersionDisplayName method
ms.assetid: e1286424-7043-4f12-a7ad-1cf69e81baa4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8b39ce39a4f26964c148631c903869b0234e2b9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581107"
---
# <a name="getdatabaseversiondisplayname-method-wmi"></a><span data-ttu-id="d2f5d-102">GetDatabaseVersionDisplayName 方法 (WMI)</span><span class="sxs-lookup"><span data-stu-id="d2f5d-102">GetDatabaseVersionDisplayName Method (WMI)</span></span>
  <span data-ttu-id="d2f5d-103">获取给定报表服务器数据库版本字符串的显示名称。</span><span class="sxs-lookup"><span data-stu-id="d2f5d-103">Gets the display name for a given report server database version string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2f5d-104">语法</span><span class="sxs-lookup"><span data-stu-id="d2f5d-104">Syntax</span></span>  
  
```vb  
Public Sub GetDatabaseVersionDisplayName(Version As String, DisplayName As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GetDatabaseVersionDisplayName(string Version, string DisplayName, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2f5d-105">parameters</span><span class="sxs-lookup"><span data-stu-id="d2f5d-105">Parameters</span></span>  
 <span data-ttu-id="d2f5d-106">*版本*</span><span class="sxs-lookup"><span data-stu-id="d2f5d-106">*Version*</span></span>  
 <span data-ttu-id="d2f5d-107">包含报表服务器数据库的版本字符串的字符串。</span><span class="sxs-lookup"><span data-stu-id="d2f5d-107">A string that contains the version string for a report server database.</span></span>  
  
 <span data-ttu-id="d2f5d-108">*DisplayName*</span><span class="sxs-lookup"><span data-stu-id="d2f5d-108">*DisplayName*</span></span>  
 <span data-ttu-id="d2f5d-109">[out] 包含与所提供版本相对应的显示名称的字符串。</span><span class="sxs-lookup"><span data-stu-id="d2f5d-109">[out] A string that contains the display name that corresponds to the version supplied.</span></span>  
  
 <span data-ttu-id="d2f5d-110">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="d2f5d-110">*HRESULT*</span></span>  
 <span data-ttu-id="d2f5d-111">[out] 指示调用是成功还是失败的值。</span><span class="sxs-lookup"><span data-stu-id="d2f5d-111">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2f5d-112">备注</span><span class="sxs-lookup"><span data-stu-id="d2f5d-112">Remarks</span></span>  
 <span data-ttu-id="d2f5d-113">下表显示的是从数据库版本到显示字符串的映射。</span><span class="sxs-lookup"><span data-stu-id="d2f5d-113">The following table shows the mapping from database version to display string.</span></span>  
  
|<span data-ttu-id="d2f5d-114">**版本**</span><span class="sxs-lookup"><span data-stu-id="d2f5d-114">**Release**</span></span>|`Version`|<span data-ttu-id="d2f5d-115">**显示名称**</span><span class="sxs-lookup"><span data-stu-id="d2f5d-115">**Display Name**</span></span>|  
|-----------------|-----------------|----------------------|  
|<span data-ttu-id="d2f5d-116">RS 2005 SP2</span><span class="sxs-lookup"><span data-stu-id="d2f5d-116">RS 2005 SP2</span></span>|<span data-ttu-id="d2f5d-117">@DBVersion = 'C.0.8.54'</span><span class="sxs-lookup"><span data-stu-id="d2f5d-117">@DBVersion = 'C.0.8.54'</span></span>|<span data-ttu-id="d2f5d-118">SQL Server 2005 SP2</span><span class="sxs-lookup"><span data-stu-id="d2f5d-118">SQL Server 2005 SP2</span></span>|  
|<span data-ttu-id="d2f5d-119">RS 2005 SP1</span><span class="sxs-lookup"><span data-stu-id="d2f5d-119">RS 2005 SP1</span></span>|<span data-ttu-id="d2f5d-120">@DBVersion = 'C.0.8.43'</span><span class="sxs-lookup"><span data-stu-id="d2f5d-120">@DBVersion = 'C.0.8.43'</span></span>|<span data-ttu-id="d2f5d-121">SQL Server 2005 SP1</span><span class="sxs-lookup"><span data-stu-id="d2f5d-121">SQL Server 2005 SP1</span></span>|  
|<span data-ttu-id="d2f5d-122">RS 2005 RTM</span><span class="sxs-lookup"><span data-stu-id="d2f5d-122">RS 2005 RTM</span></span>|<span data-ttu-id="d2f5d-123">@DBVersion = 'C.0.8.40'</span><span class="sxs-lookup"><span data-stu-id="d2f5d-123">@DBVersion = 'C.0.8.40'</span></span>|<span data-ttu-id="d2f5d-124">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="d2f5d-124">SQL Server 2005</span></span>|  
|<span data-ttu-id="d2f5d-125">RS 2000 SP2</span><span class="sxs-lookup"><span data-stu-id="d2f5d-125">RS 2000 SP2</span></span>|<span data-ttu-id="d2f5d-126">@DBVersion = 'C.0.6.54'</span><span class="sxs-lookup"><span data-stu-id="d2f5d-126">@DBVersion = 'C.0.6.54'</span></span>|<span data-ttu-id="d2f5d-127">SQL Server 2000 SP2</span><span class="sxs-lookup"><span data-stu-id="d2f5d-127">SQL Server 2000 SP2</span></span>|  
|<span data-ttu-id="d2f5d-128">RS 2000 SP1</span><span class="sxs-lookup"><span data-stu-id="d2f5d-128">RS 2000 SP1</span></span>|<span data-ttu-id="d2f5d-129">@DBVersion = 'C.0.6.51'</span><span class="sxs-lookup"><span data-stu-id="d2f5d-129">@DBVersion = 'C.0.6.51'</span></span>|<span data-ttu-id="d2f5d-130">SQL Server 2000 SP1</span><span class="sxs-lookup"><span data-stu-id="d2f5d-130">SQL Server 2000 SP1</span></span>|  
|<span data-ttu-id="d2f5d-131">RS 2000 RTM</span><span class="sxs-lookup"><span data-stu-id="d2f5d-131">RS 2000 RTM</span></span>|<span data-ttu-id="d2f5d-132">@DBVersion = 'C.0.6.43'</span><span class="sxs-lookup"><span data-stu-id="d2f5d-132">@DBVersion = 'C.0.6.43'</span></span>|<span data-ttu-id="d2f5d-133">SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="d2f5d-133">SQL Server 2000</span></span>|  
|<span data-ttu-id="d2f5d-134">修补程序</span><span class="sxs-lookup"><span data-stu-id="d2f5d-134">Hotfix</span></span>||<span data-ttu-id="d2f5d-135">最接近的适用版本</span><span class="sxs-lookup"><span data-stu-id="d2f5d-135">Closest applicable version</span></span>|  
  
 <span data-ttu-id="d2f5d-136">如果版本早于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2000，返回的 HRESULT 为 ACT_E_BAD_VERSION\*\*。</span><span class="sxs-lookup"><span data-stu-id="d2f5d-136">For a *Version* prior to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2000 an HRESULT of ACT_E_BAD_VERSION is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d2f5d-137">返回值</span><span class="sxs-lookup"><span data-stu-id="d2f5d-137">Return Value</span></span>  
 <span data-ttu-id="d2f5d-138">返回 *HRESULT* ，指示方法调用是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="d2f5d-138">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="d2f5d-139">值 0 指示方法调用已成功。</span><span class="sxs-lookup"><span data-stu-id="d2f5d-139">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="d2f5d-140">非零值指示已发生错误。</span><span class="sxs-lookup"><span data-stu-id="d2f5d-140">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2f5d-141">要求</span><span class="sxs-lookup"><span data-stu-id="d2f5d-141">Requirements</span></span>  
 <span data-ttu-id="d2f5d-142">**命名空间：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2f5d-142">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2f5d-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d2f5d-143">See Also</span></span>  
 [<span data-ttu-id="d2f5d-144">MSReportServer_ConfigurationSetting 成员</span><span class="sxs-lookup"><span data-stu-id="d2f5d-144">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
