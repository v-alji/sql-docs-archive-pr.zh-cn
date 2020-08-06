---
title: ListReportServersInDatabase 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- ListReportServersInDatabase (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- ListReportServersInDatabase method
ms.assetid: a4bf5968-c46f-484f-a510-65e2dde65a0d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9eaea72c0737124d89c86b55281326073597fb38
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581103"
---
# <a name="listreportserversindatabase-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="c7a20-102">ListReportServersInDatabase 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="c7a20-102">ListReportServersInDatabase Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="c7a20-103">返回报表服务器数据库中存在的报表服务器安装列表，无论这些安装是否具有访问安全信息的权限都同样如此。</span><span class="sxs-lookup"><span data-stu-id="c7a20-103">Returns the list of report server installations that are present in the report server database, regardless of whether they have access to secure information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7a20-104">语法</span><span class="sxs-lookup"><span data-stu-id="c7a20-104">Syntax</span></span>  
  
```vb  
Public Sub ListReportServersInDatabase(ByRef MachineNames() As String, _  
    ByRef InstanceNames() As String, ByRef InstallationIDs() As String, _  
    ByRef IsInitialized() As Boolean, ByRef Length As Int32, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void ListReportServersInDatabase (out string[] MachineNames,   
    out string[] InstanceNames, out string[] InstallationIDs,   
    out Boolean[] IsInitialized,out Int32 Length, out Int32 HRESULT,    
    out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7a20-105">parameters</span><span class="sxs-lookup"><span data-stu-id="c7a20-105">Parameters</span></span>  
 <span data-ttu-id="c7a20-106">*MachineNames[]*</span><span class="sxs-lookup"><span data-stu-id="c7a20-106">*MachineNames[]*</span></span>  
 <span data-ttu-id="c7a20-107">[out] 一个数组，包含数据库中存在的各个报表服务器安装的计算机名称。</span><span class="sxs-lookup"><span data-stu-id="c7a20-107">[out] An array containing the machine names for the report server installations in the database.</span></span>  
  
 <span data-ttu-id="c7a20-108">*InstanceNames[]*</span><span class="sxs-lookup"><span data-stu-id="c7a20-108">*InstanceNames[]*</span></span>  
 <span data-ttu-id="c7a20-109">[out] 一个数组，包含数据库中存在的各个报表服务器安装的实例名称。</span><span class="sxs-lookup"><span data-stu-id="c7a20-109">[out] An array containing the instance names of each of the report server installations in the database.</span></span>  
  
 <span data-ttu-id="c7a20-110">*InstallationIDs[]*</span><span class="sxs-lookup"><span data-stu-id="c7a20-110">*InstallationIDs[]*</span></span>  
 <span data-ttu-id="c7a20-111">[out] 一个数组，包含数据库中存在的各个报表服务器安装的安装 ID。</span><span class="sxs-lookup"><span data-stu-id="c7a20-111">[out] An array containing the installation IDs of each report server installation in the database.</span></span>  
  
 <span data-ttu-id="c7a20-112">*IsInitialized[]*</span><span class="sxs-lookup"><span data-stu-id="c7a20-112">*IsInitialized[]*</span></span>  
 <span data-ttu-id="c7a20-113">[out] 一个数组，包含数据库中存在的各个报表服务器安装的初始化状态。</span><span class="sxs-lookup"><span data-stu-id="c7a20-113">[out] An array containing initialization status for each report server installation in the database.</span></span>  
  
 <span data-ttu-id="c7a20-114">*长度*</span><span class="sxs-lookup"><span data-stu-id="c7a20-114">*Length*</span></span>  
 <span data-ttu-id="c7a20-115">[out] 该方法返回的数组长度。</span><span class="sxs-lookup"><span data-stu-id="c7a20-115">[out] The length of the arrays returned by the method.</span></span> <span data-ttu-id="c7a20-116">所有返回数组的长度都相同。</span><span class="sxs-lookup"><span data-stu-id="c7a20-116">All returned arrays have the same length.</span></span>  
  
 <span data-ttu-id="c7a20-117">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="c7a20-117">*HRESULT*</span></span>  
 <span data-ttu-id="c7a20-118">[out] 指示调用是成功还是失败的值。</span><span class="sxs-lookup"><span data-stu-id="c7a20-118">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
 <span data-ttu-id="c7a20-119">*ExtendedErrors[]*</span><span class="sxs-lookup"><span data-stu-id="c7a20-119">*ExtendedErrors[]*</span></span>  
 <span data-ttu-id="c7a20-120">[out] 一个字符串数组，包含此调用返回的其他错误。</span><span class="sxs-lookup"><span data-stu-id="c7a20-120">[out] A string array containing additional errors returned by the call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c7a20-121">返回值</span><span class="sxs-lookup"><span data-stu-id="c7a20-121">Return Value</span></span>  
 <span data-ttu-id="c7a20-122">返回 *HRESULT* ，指示方法调用是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="c7a20-122">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="c7a20-123">值 0 指示方法调用已成功。</span><span class="sxs-lookup"><span data-stu-id="c7a20-123">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="c7a20-124">非零值指示已发生错误。</span><span class="sxs-lookup"><span data-stu-id="c7a20-124">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7a20-125">备注</span><span class="sxs-lookup"><span data-stu-id="c7a20-125">Remarks</span></span>  
 <span data-ttu-id="c7a20-126">ListReportServersInDatabase 用于列出报表服务器数据库中存在的报表服务器安装（无论这些安装是否具有访问安全信息的权限），并返回一组包含每一安装相关信息的匹配数组。</span><span class="sxs-lookup"><span data-stu-id="c7a20-126">ListReportServersInDatabase lists the report server installations that are present in the report server database, regardless of whether they have access to secure information, and returns a matched set of arrays containing information about each installation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7a20-127">要求</span><span class="sxs-lookup"><span data-stu-id="c7a20-127">Requirements</span></span>  
 <span data-ttu-id="c7a20-128">**命名空间：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7a20-128">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7a20-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c7a20-129">See Also</span></span>  
 [<span data-ttu-id="c7a20-130">MSReportServer_ConfigurationSetting 成员</span><span class="sxs-lookup"><span data-stu-id="c7a20-130">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
