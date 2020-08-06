---
title: GetReportServerUrls 方法 (WMI MSReportServer_Instance) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- GetReportServerUrls method
ms.assetid: 4865e32c-0114-465a-be8c-be223a7bc09e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f36a5ba10c05276cffabc155e5289d675db8dae7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690335"
---
# <a name="getreportserverurls-method-wmi-msreportserver_instance"></a><span data-ttu-id="25765-102">GetReportServerUrls 方法 (WMI MSReportServer_Instance)</span><span class="sxs-lookup"><span data-stu-id="25765-102">GetReportServerUrls Method (WMI MSReportServer_Instance)</span></span>
  <span data-ttu-id="25765-103">返回可用于访问报表服务器和报表管理器的 URL 列表。</span><span class="sxs-lookup"><span data-stu-id="25765-103">Returns a list of URLs users can use to access the report server and report manager.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25765-104">语法</span><span class="sxs-lookup"><span data-stu-id="25765-104">Syntax</span></span>  
  
```vb  
Public Sub GetReportServerUrls (ByRef ApplicationName() As String, ByRef URLs()_  
    As String, ByRef Length As Int32, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GetReportServerUrls(out string[] applicationName,   
    out string[] URLs, out int length, out int HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25765-105">parameters</span><span class="sxs-lookup"><span data-stu-id="25765-105">Parameters</span></span>  
 <span data-ttu-id="25765-106">*ApplicationName[]*</span><span class="sxs-lookup"><span data-stu-id="25765-106">*ApplicationName[]*</span></span>  
 <span data-ttu-id="25765-107">一个包含安装的应用程序的数组。</span><span class="sxs-lookup"><span data-stu-id="25765-107">An array that contains the applications that are installed.</span></span> <span data-ttu-id="25765-108">值为 `ReportServerWebService` 或 `ReportManager`。</span><span class="sxs-lookup"><span data-stu-id="25765-108">Values are either `ReportServerWebService` or `ReportManager`.</span></span>  
  
 <span data-ttu-id="25765-109">*URLs[]*</span><span class="sxs-lookup"><span data-stu-id="25765-109">*URLs[]*</span></span>  
 <span data-ttu-id="25765-110">一个包含已成功注册的 URL 的数组。</span><span class="sxs-lookup"><span data-stu-id="25765-110">An array that contains the successfully registered Urls.</span></span>  
  
 <span data-ttu-id="25765-111">*长度*</span><span class="sxs-lookup"><span data-stu-id="25765-111">*Length*</span></span>  
 <span data-ttu-id="25765-112">一个包含返回数组的长度的整数值。</span><span class="sxs-lookup"><span data-stu-id="25765-112">An integer value that contains the length of the arrays returned.</span></span>  
  
 <span data-ttu-id="25765-113">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="25765-113">*HRESULT*</span></span>  
 <span data-ttu-id="25765-114">一个指示成功或错误代码的值。</span><span class="sxs-lookup"><span data-stu-id="25765-114">A value that indicates success or an error code.</span></span>  
  
## <a name="return-values"></a><span data-ttu-id="25765-115">返回值</span><span class="sxs-lookup"><span data-stu-id="25765-115">Return Values</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25765-116">备注</span><span class="sxs-lookup"><span data-stu-id="25765-116">Remarks</span></span>  
 <span data-ttu-id="25765-117">可通过 InvokeMethod 函数调用由 WMI 管理对象公开的方法。</span><span class="sxs-lookup"><span data-stu-id="25765-117">Methods exposed by WMI management objects are called through the InvokeMethod function.</span></span> <span data-ttu-id="25765-118">有关详细信息，请参阅 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework WMI 文档中的“Executing Methods on Management Objects”（对管理对象执行方法）。</span><span class="sxs-lookup"><span data-stu-id="25765-118">For more information, please see "Executing Methods on Management Objects" in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework WMI documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25765-119">要求</span><span class="sxs-lookup"><span data-stu-id="25765-119">Requirements</span></span>  
 <span data-ttu-id="25765-120">**命名空间：** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25765-120">**Namespace:** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25765-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="25765-121">See Also</span></span>  
 [<span data-ttu-id="25765-122">MSReportServer_ConfigurationSetting 成员</span><span class="sxs-lookup"><span data-stu-id="25765-122">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
