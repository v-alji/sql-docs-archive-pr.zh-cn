---
title: DeleteEncryptedInformation 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- DeleteEncryptedInformation (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DeleteEncryptedInformation method
ms.assetid: c14ed187-bdd9-4304-88e3-72072f03c21b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d00dc3e90816cd04c84f124cdc3d25a9ac122bba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581121"
---
# <a name="deleteencryptedinformation-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="b6d57-102">DeleteEncryptedInformation 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="b6d57-102">DeleteEncryptedInformation Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="b6d57-103">从报表服务器数据库删除加密信息。</span><span class="sxs-lookup"><span data-stu-id="b6d57-103">Deletes the encrypted information from the report server database.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6d57-104">语法</span><span class="sxs-lookup"><span data-stu-id="b6d57-104">Syntax</span></span>  
  
```vb  
Public Sub DeleteEncryptedInformation(ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void DeleteEncryptedInformation(out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6d57-105">parameters</span><span class="sxs-lookup"><span data-stu-id="b6d57-105">Parameters</span></span>  
 <span data-ttu-id="b6d57-106">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="b6d57-106">*HRESULT*</span></span>  
 <span data-ttu-id="b6d57-107">[out] 指示调用是成功还是失败的值。</span><span class="sxs-lookup"><span data-stu-id="b6d57-107">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
 <span data-ttu-id="b6d57-108">*ExtendedErrors[]*</span><span class="sxs-lookup"><span data-stu-id="b6d57-108">*ExtendedErrors[]*</span></span>  
 <span data-ttu-id="b6d57-109">[out] 一个字符串数组，包含此调用返回的其他错误。</span><span class="sxs-lookup"><span data-stu-id="b6d57-109">[out] A string array containing additional errors returned by the call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b6d57-110">返回值</span><span class="sxs-lookup"><span data-stu-id="b6d57-110">Return Value</span></span>  
 <span data-ttu-id="b6d57-111">返回 *HRESULT* ，指示方法调用是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="b6d57-111">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="b6d57-112">值 0 指示方法调用已成功。</span><span class="sxs-lookup"><span data-stu-id="b6d57-112">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="b6d57-113">非零值指示已发生错误。</span><span class="sxs-lookup"><span data-stu-id="b6d57-113">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6d57-114">备注</span><span class="sxs-lookup"><span data-stu-id="b6d57-114">Remarks</span></span>  
 <span data-ttu-id="b6d57-115">调用此方法后，将删除以下数据：</span><span class="sxs-lookup"><span data-stu-id="b6d57-115">When this method is invoked, the following data is deleted:</span></span>  
  
-   <span data-ttu-id="b6d57-116">加密的数据源信息，包括用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="b6d57-116">Data source information that is encrypted, including user name and password.</span></span>  
  
-   <span data-ttu-id="b6d57-117">使用传递扩展插件接口加密的订阅数据。</span><span class="sxs-lookup"><span data-stu-id="b6d57-117">Subscription data that is encrypted using the delivery extension interfaces.</span></span>  
  
-   <span data-ttu-id="b6d57-118">报表服务器数据库密钥表中的所有信息。</span><span class="sxs-lookup"><span data-stu-id="b6d57-118">All the information from the keys table in the report server database.</span></span>  
  
 <span data-ttu-id="b6d57-119">调用此方法后，用户必须初始化使用报表服务器数据库的每台计算机。</span><span class="sxs-lookup"><span data-stu-id="b6d57-119">After this method is invoked, the user must initialize each computer that uses the report server database.</span></span>  
  
 <span data-ttu-id="b6d57-120">调用 DeleteEncryptedInformation 方法不会影响报表服务器配置文件。</span><span class="sxs-lookup"><span data-stu-id="b6d57-120">Calling the DeleteEncryptedInformation method does not affect the report server configuration file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6d57-121">要求</span><span class="sxs-lookup"><span data-stu-id="b6d57-121">Requirements</span></span>  
 <span data-ttu-id="b6d57-122">**命名空间：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6d57-122">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6d57-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b6d57-123">See Also</span></span>  
 [<span data-ttu-id="b6d57-124">MSReportServer_ConfigurationSetting 成员</span><span class="sxs-lookup"><span data-stu-id="b6d57-124">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
