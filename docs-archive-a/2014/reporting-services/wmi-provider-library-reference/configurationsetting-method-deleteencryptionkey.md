---
title: DeleteEncryptionKey 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- DeleteEncryptionKey (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DeleteEncryptionKey method
ms.assetid: ed2f25b6-6a63-468d-9279-a577ca01b096
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0e302659615bd620b3b0ed802b83aafc4e9506d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581114"
---
# <a name="deleteencryptionkey-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="5492e-102">DeleteEncryptionKey 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="5492e-102">DeleteEncryptionKey Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="5492e-103">从报表服务器数据库删除加密密钥。</span><span class="sxs-lookup"><span data-stu-id="5492e-103">Deletes the encryption keys from the report server database.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5492e-104">语法</span><span class="sxs-lookup"><span data-stu-id="5492e-104">Syntax</span></span>  
  
```vb  
Public Sub DeleteEncryptionKeys(ByVal InstallationID As String, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void DeleteEncryptionKeys(string InstallationID, out Int32 HRESULT,   
    out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5492e-105">parameters</span><span class="sxs-lookup"><span data-stu-id="5492e-105">Parameters</span></span>  
 <span data-ttu-id="5492e-106">*InstallationID*</span><span class="sxs-lookup"><span data-stu-id="5492e-106">*InstallationID*</span></span>  
 <span data-ttu-id="5492e-107">位于报表服务器数据库的密钥表中的报表服务器安装 ID。</span><span class="sxs-lookup"><span data-stu-id="5492e-107">The installation ID of a report server that is in the keys table of the report server database.</span></span>  
  
 <span data-ttu-id="5492e-108">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="5492e-108">*HRESULT*</span></span>  
 <span data-ttu-id="5492e-109">[out] 指示调用是成功还是失败的值。</span><span class="sxs-lookup"><span data-stu-id="5492e-109">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
 <span data-ttu-id="5492e-110">*ExtendedErrors[]*</span><span class="sxs-lookup"><span data-stu-id="5492e-110">*ExtendedErrors[]*</span></span>  
 <span data-ttu-id="5492e-111">[out] 一个字符串数组，包含此调用返回的其他错误。</span><span class="sxs-lookup"><span data-stu-id="5492e-111">[out] A string array containing additional errors returned by the call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5492e-112">返回值</span><span class="sxs-lookup"><span data-stu-id="5492e-112">Return Value</span></span>  
 <span data-ttu-id="5492e-113">返回 HRESULT，指示方法调用是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="5492e-113">Returns an HRESULT indicating success or failure of the method call.</span></span> <span data-ttu-id="5492e-114">值 0 指示方法调用已成功。</span><span class="sxs-lookup"><span data-stu-id="5492e-114">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="5492e-115">非零值指示已发生错误。</span><span class="sxs-lookup"><span data-stu-id="5492e-115">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5492e-116">备注</span><span class="sxs-lookup"><span data-stu-id="5492e-116">Remarks</span></span>  
 <span data-ttu-id="5492e-117">*DeleteEncryptionKey* 方法用于从密钥表中删除可访问报表服务器数据库中安全信息的任何报表服务器的条目。</span><span class="sxs-lookup"><span data-stu-id="5492e-117">The *DeleteEncryptionKey* method deletes entries from the keys table for any report servers that have access to the secure information in the report server database.</span></span> <span data-ttu-id="5492e-118">如果指定的 *InstallationID* 参数与该数据库中的安装 ID 不对应，该方法将返回错误。</span><span class="sxs-lookup"><span data-stu-id="5492e-118">If the *InstallationID* parameter specified does not correspond to an installation ID in the database, the method returns an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5492e-119">要求</span><span class="sxs-lookup"><span data-stu-id="5492e-119">Requirements</span></span>  
 <span data-ttu-id="5492e-120">**命名空间：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5492e-120">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5492e-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5492e-121">See Also</span></span>  
 [<span data-ttu-id="5492e-122">MSReportServer_ConfigurationSetting 成员</span><span class="sxs-lookup"><span data-stu-id="5492e-122">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
