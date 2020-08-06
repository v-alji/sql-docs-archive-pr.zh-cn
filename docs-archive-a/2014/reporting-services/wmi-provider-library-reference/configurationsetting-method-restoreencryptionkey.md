---
title: RestoreEncryptionKey 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- RestoreEncryptionKey (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- RestoreEncryptionKey method
ms.assetid: 37e949f5-15af-4858-848a-f482ee94fcd9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e67478541bab615a6d441ae273ed3385a8654203
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692194"
---
# <a name="restoreencryptionkey-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="69b39-102">RestoreEncryptionKey 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="69b39-102">RestoreEncryptionKey Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="69b39-103">将指定的加密密钥重新应用于报表服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="69b39-103">Reapplies the specified encryption key to the report server database.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69b39-104">语法</span><span class="sxs-lookup"><span data-stu-id="69b39-104">Syntax</span></span>  
  
```vb  
Public Sub RestoreEncryptionKey(ByRef KeyFile() As Integer, _  
    ByRef Length As Int32, ByVal Password As String, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void RestoreEncryptionKey(out Byte[] KeyFile, out Int32 Length,   
            string Password, out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69b39-105">parameters</span><span class="sxs-lookup"><span data-stu-id="69b39-105">Parameters</span></span>  
 <span data-ttu-id="69b39-106">*KeyFile[]*</span><span class="sxs-lookup"><span data-stu-id="69b39-106">*KeyFile[]*</span></span>  
 <span data-ttu-id="69b39-107">[out] 包含已加密的加密密钥的数组。</span><span class="sxs-lookup"><span data-stu-id="69b39-107">[out] An array containing the encrypted encryption key.</span></span>  
  
 <span data-ttu-id="69b39-108">*长度*</span><span class="sxs-lookup"><span data-stu-id="69b39-108">*Length*</span></span>  
 <span data-ttu-id="69b39-109">[out] 该方法返回的数组长度。</span><span class="sxs-lookup"><span data-stu-id="69b39-109">[out] The length of the array returned by the method.</span></span>  
  
 <span data-ttu-id="69b39-110">*密码*</span><span class="sxs-lookup"><span data-stu-id="69b39-110">*Password*</span></span>  
 <span data-ttu-id="69b39-111">用于对加密密钥进行加密的字符串。</span><span class="sxs-lookup"><span data-stu-id="69b39-111">A string used to encrypt the encryption key.</span></span>  
  
 <span data-ttu-id="69b39-112">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="69b39-112">*HRESULT*</span></span>  
 <span data-ttu-id="69b39-113">[out] 指示调用是成功还是失败的值。</span><span class="sxs-lookup"><span data-stu-id="69b39-113">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
 <span data-ttu-id="69b39-114">*ExtendedErrors[]*</span><span class="sxs-lookup"><span data-stu-id="69b39-114">*ExtendedErrors[]*</span></span>  
 <span data-ttu-id="69b39-115">[out] 一个字符串数组，包含此调用返回的其他错误。</span><span class="sxs-lookup"><span data-stu-id="69b39-115">[out] A string array containing additional errors returned by the call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="69b39-116">返回值</span><span class="sxs-lookup"><span data-stu-id="69b39-116">Return Value</span></span>  
 <span data-ttu-id="69b39-117">返回 *HRESULT* ，指示方法调用是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="69b39-117">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="69b39-118">值 0 指示方法调用已成功。</span><span class="sxs-lookup"><span data-stu-id="69b39-118">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="69b39-119">非零值指示已发生错误。</span><span class="sxs-lookup"><span data-stu-id="69b39-119">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69b39-120">备注</span><span class="sxs-lookup"><span data-stu-id="69b39-120">Remarks</span></span>  
 <span data-ttu-id="69b39-121">如果报表服务器数据库中已经存在报表服务器的条目，则删除它。</span><span class="sxs-lookup"><span data-stu-id="69b39-121">If an entry already exists for the report server in the report server database, it is deleted.</span></span> <span data-ttu-id="69b39-122">然后，使用指定的加密密钥和报表服务器的公钥创建新条目。</span><span class="sxs-lookup"><span data-stu-id="69b39-122">The new entry is then created using the specified encryption key and the report server's public key.</span></span>  
  
 <span data-ttu-id="69b39-123">在调用清除加密密钥列表的 [DeleteEncryptionKey](configurationsetting-method-deleteencryptionkey.md) 方法之后调用该方法最有效。</span><span class="sxs-lookup"><span data-stu-id="69b39-123">The method is most effective when called after the [DeleteEncryptionKey](configurationsetting-method-deleteencryptionkey.md) method, which clears the list of encryption keys.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69b39-124">要求</span><span class="sxs-lookup"><span data-stu-id="69b39-124">Requirements</span></span>  
 <span data-ttu-id="69b39-125">**命名空间：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69b39-125">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69b39-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="69b39-126">See Also</span></span>  
 [<span data-ttu-id="69b39-127">MSReportServer_ConfigurationSetting 成员</span><span class="sxs-lookup"><span data-stu-id="69b39-127">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
