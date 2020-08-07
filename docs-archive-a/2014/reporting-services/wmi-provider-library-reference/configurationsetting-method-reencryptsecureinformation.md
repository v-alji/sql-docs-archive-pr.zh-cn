---
title: ReencryptSecureInformation 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- ReencryptSecureInformation (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- ReencryptSecureInformation method
ms.assetid: 8a487497-c207-45b2-8c92-87c58cc68716
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1a0c657b69d624df8895ae4d5a6d12277b011b24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588899"
---
# <a name="reencryptsecureinformation-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="1de0d-102">ReencryptSecureInformation 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="1de0d-102">ReencryptSecureInformation Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="1de0d-103">生成新的加密密钥，并使用新密钥对目录中的所有安全信息进行重新加密。</span><span class="sxs-lookup"><span data-stu-id="1de0d-103">Generates a new encryption key and re-encrypts all secure information in the catalog using this new key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1de0d-104">语法</span><span class="sxs-lookup"><span data-stu-id="1de0d-104">Syntax</span></span>  
  
```vb  
Public Sub ReencryptSecureInformation(ByRef HRESULT as Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void ReencryptSecureInformation (out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1de0d-105">parameters</span><span class="sxs-lookup"><span data-stu-id="1de0d-105">Parameters</span></span>  
 <span data-ttu-id="1de0d-106">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="1de0d-106">*HRESULT*</span></span>  
 <span data-ttu-id="1de0d-107">[out] 指示调用是成功还是失败的值。</span><span class="sxs-lookup"><span data-stu-id="1de0d-107">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
 <span data-ttu-id="1de0d-108">*ExtendedErrors[]*</span><span class="sxs-lookup"><span data-stu-id="1de0d-108">*ExtendedErrors[]*</span></span>  
 <span data-ttu-id="1de0d-109">[out] 一个字符串数组，包含此调用返回的其他错误。</span><span class="sxs-lookup"><span data-stu-id="1de0d-109">[out] A string array containing additional errors returned by the call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1de0d-110">返回值</span><span class="sxs-lookup"><span data-stu-id="1de0d-110">Return Value</span></span>  
 <span data-ttu-id="1de0d-111">返回 *HRESULT* ，指示方法调用是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="1de0d-111">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="1de0d-112">值 0 指示方法调用已成功。</span><span class="sxs-lookup"><span data-stu-id="1de0d-112">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="1de0d-113">非零值指示已发生错误。</span><span class="sxs-lookup"><span data-stu-id="1de0d-113">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1de0d-114">备注</span><span class="sxs-lookup"><span data-stu-id="1de0d-114">Remarks</span></span>  
 <span data-ttu-id="1de0d-115">ReencryptSecureInformation 方法允许管理员使用新密钥替换现有加密密钥。</span><span class="sxs-lookup"><span data-stu-id="1de0d-115">The ReencryptSecureInformation method allows the administrator to replace the existing encryption key with a new key.</span></span>  
  
 <span data-ttu-id="1de0d-116">调用此方法时，报表服务器会生成新的加密密钥，并遍历所有加密内容以使用新的加密密钥对其进行重新加密。</span><span class="sxs-lookup"><span data-stu-id="1de0d-116">When this method is invoked, the report server generates a new encryption key and iterates through all encrypted content to re-encrypt it with the new encryption key.</span></span>  
  
 <span data-ttu-id="1de0d-117">传递扩展插件可以其传递设置结构存储安全信息。</span><span class="sxs-lookup"><span data-stu-id="1de0d-117">Delivery extensions can store secured information in their delivery settings structures.</span></span> <span data-ttu-id="1de0d-118">调用 ReencryptSecureInformation 时，报表服务器会加载每个订阅和相应的传递扩展插件，以对关联设置中存储的信息进行重新加密。</span><span class="sxs-lookup"><span data-stu-id="1de0d-118">When ReencryptSecureInformation is called, the report server loads each subscription and the corresponding delivery extension to re-encrypt information stored in the associated settings.</span></span>  
  
 <span data-ttu-id="1de0d-119">如果此方法运行在扩展部署中的计算机上，则扩展部署中的每台计算机将都需要再次进行初始化。</span><span class="sxs-lookup"><span data-stu-id="1de0d-119">If this method is run on a computer in a scale-out deployment, each computer in the scale-out deployment will need to be initialized again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1de0d-120">要求</span><span class="sxs-lookup"><span data-stu-id="1de0d-120">Requirements</span></span>  
 <span data-ttu-id="1de0d-121">**命名空间：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1de0d-121">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1de0d-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1de0d-122">See Also</span></span>  
 [<span data-ttu-id="1de0d-123">MSReportServer_ConfigurationSetting 成员</span><span class="sxs-lookup"><span data-stu-id="1de0d-123">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
