---
title: InitializeReportServer 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- InitializeReportServer (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- InitializeReportServer method
ms.assetid: 0304acc2-1fd7-437b-94d9-1c1073dd3ca4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c6a8e44a98320ca2c9add6a1b6eef9362eef7731
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581110"
---
# <a name="initializereportserver-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="4061d-102">InitializeReportServer 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="4061d-102">InitializeReportServer Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="4061d-103">初始化指定的报表服务实例。</span><span class="sxs-lookup"><span data-stu-id="4061d-103">Initializes the specified report service instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4061d-104">语法</span><span class="sxs-lookup"><span data-stu-id="4061d-104">Syntax</span></span>  
  
```vb  
Public Sub InitializeReportServer(ByVal InstallationID As String, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void InitializeReportServer(string InstallationID,   
    out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4061d-105">parameters</span><span class="sxs-lookup"><span data-stu-id="4061d-105">Parameters</span></span>  
 <span data-ttu-id="4061d-106">*InstallationID*</span><span class="sxs-lookup"><span data-stu-id="4061d-106">*InstallationID*</span></span>  
 <span data-ttu-id="4061d-107">用于在加密密钥返回之前对其进行加密的字符串。</span><span class="sxs-lookup"><span data-stu-id="4061d-107">A string used to encrypt the encryption key before it is returned.</span></span>  
  
 <span data-ttu-id="4061d-108">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="4061d-108">*HRESULT*</span></span>  
 <span data-ttu-id="4061d-109">[out] 指示调用是成功还是失败的值。</span><span class="sxs-lookup"><span data-stu-id="4061d-109">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
 <span data-ttu-id="4061d-110">*ExtendedErrors[]*</span><span class="sxs-lookup"><span data-stu-id="4061d-110">*ExtendedErrors[]*</span></span>  
 <span data-ttu-id="4061d-111">[out] 一个字符串数组，包含此调用返回的其他错误。</span><span class="sxs-lookup"><span data-stu-id="4061d-111">[out] A string array containing additional errors returned by the call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4061d-112">返回值</span><span class="sxs-lookup"><span data-stu-id="4061d-112">Return Value</span></span>  
 <span data-ttu-id="4061d-113">返回 *HRESULT* ，指示方法调用是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="4061d-113">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="4061d-114">值 0 指示方法调用已成功。</span><span class="sxs-lookup"><span data-stu-id="4061d-114">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="4061d-115">非零值指示已发生错误。</span><span class="sxs-lookup"><span data-stu-id="4061d-115">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4061d-116">备注</span><span class="sxs-lookup"><span data-stu-id="4061d-116">Remarks</span></span>  
 <span data-ttu-id="4061d-117">调用此方法时，将使用由 *InstallationID*标识的报表服务器的公钥，对访问该报表服务器数据库安全信息的加密密钥进行加密。</span><span class="sxs-lookup"><span data-stu-id="4061d-117">When this method is called, the encryption key that accesses the report server database secure information is encrypted using the public key of the report server identified by *InstallationID*.</span></span>  
  
 <span data-ttu-id="4061d-118">指定报表服务器的公钥必须在先前已写入报表服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="4061d-118">The specified report server's public key must have previously been written into the report server database.</span></span>  
  
 <span data-ttu-id="4061d-119">必须对已能访问安全信息的报表服务器调用 *InitializeReportServer* 方法，以便此方法可以解密加密密钥。</span><span class="sxs-lookup"><span data-stu-id="4061d-119">The *InitializeReportServer* method must be called against a report server that already has access to the secure information so that it can decrypt the encryption key.</span></span> <span data-ttu-id="4061d-120">然后，所产生的已加密的加密密钥将存储在报表服务器数据库中。</span><span class="sxs-lookup"><span data-stu-id="4061d-120">The resulting encrypted encryption key is then stored in the report server database.</span></span>  
  
 <span data-ttu-id="4061d-121">如果在调用 InitializeReportServer 方法时，Report Server 的[IsInitialized](configurationsetting-property-isinitialized.md)属性设置为 `true` ，则该方法将返回 success，而不会尝试对加密密钥进行加密。</span><span class="sxs-lookup"><span data-stu-id="4061d-121">If the report server's [IsInitialized](configurationsetting-property-isinitialized.md) property is set to `true` when the InitializeReportServer method is called, the method returns success without trying to encrypt the encryption key.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4061d-122">要求</span><span class="sxs-lookup"><span data-stu-id="4061d-122">Requirements</span></span>  
 <span data-ttu-id="4061d-123">**命名空间：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4061d-123">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4061d-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4061d-124">See Also</span></span>  
 [<span data-ttu-id="4061d-125">MSReportServer_ConfigurationSetting 成员</span><span class="sxs-lookup"><span data-stu-id="4061d-125">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
