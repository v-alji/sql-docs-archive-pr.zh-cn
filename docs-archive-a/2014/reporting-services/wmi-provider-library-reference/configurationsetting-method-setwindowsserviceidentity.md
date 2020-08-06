---
title: SetWindowsServiceIdentity 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SetWindowsServiceIdentity (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetWindowsServiceIdentity method
ms.assetid: 9bbc734c-9e69-48c2-8bec-8abe7c6cc987
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 15d1b7fa5fc6d69a963785cdaf976c80623c47f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692174"
---
# <a name="setwindowsserviceidentity-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="f256c-102">SetWindowsServiceIdentity 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="f256c-102">SetWindowsServiceIdentity Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="f256c-103">将报表服务器 Windows 服务作为指定的 Windows 用户运行，并授予此帐户足够的文件系统权限以允许操作报表服务器。</span><span class="sxs-lookup"><span data-stu-id="f256c-103">Makes the Report Server Windows service run as a specified Windows user, and grants this account sufficient file system permissions to allow the report server to operate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f256c-104">语法</span><span class="sxs-lookup"><span data-stu-id="f256c-104">Syntax</span></span>  
  
```vb  
Public Sub SetWindowsServiceIdentity(UseBuiltInAccount as Boolean, _  
    Account as String, Password as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetWindowsServiceIdentity(boolean UseBuiltInAccount,   
    string Account, string Password, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f256c-105">parameters</span><span class="sxs-lookup"><span data-stu-id="f256c-105">Parameters</span></span>  
 <span data-ttu-id="f256c-106">*UseBuiltInAccount*</span><span class="sxs-lookup"><span data-stu-id="f256c-106">*UseBuiltInAccount*</span></span>  
 <span data-ttu-id="f256c-107">指示指定的帐户是否是内置 Windows 帐户。</span><span class="sxs-lookup"><span data-stu-id="f256c-107">Indicates whether the specified account is a built-in Windows account.</span></span>  
  
 <span data-ttu-id="f256c-108">*帐户*</span><span class="sxs-lookup"><span data-stu-id="f256c-108">*Account*</span></span>  
 <span data-ttu-id="f256c-109">要用于运行 Windows 服务的 Windows 帐户，格式为“DOMAIN\alias”。</span><span class="sxs-lookup"><span data-stu-id="f256c-109">The Windows account to use to run the Windows service, in the format "DOMAIN\alias".</span></span>  
  
 <span data-ttu-id="f256c-110">*密码*</span><span class="sxs-lookup"><span data-stu-id="f256c-110">*Password*</span></span>  
 <span data-ttu-id="f256c-111">帐户的密码。</span><span class="sxs-lookup"><span data-stu-id="f256c-111">The password for the account.</span></span>  
  
 <span data-ttu-id="f256c-112">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="f256c-112">*HRESULT*</span></span>  
 <span data-ttu-id="f256c-113">[out] 指示调用是成功还是失败的值。</span><span class="sxs-lookup"><span data-stu-id="f256c-113">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f256c-114">返回值</span><span class="sxs-lookup"><span data-stu-id="f256c-114">Return Value</span></span>  
 <span data-ttu-id="f256c-115">返回 *HRESULT* ，指示方法调用是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="f256c-115">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="f256c-116">值 0 指示方法调用已成功。</span><span class="sxs-lookup"><span data-stu-id="f256c-116">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="f256c-117">非零值指示已发生错误。</span><span class="sxs-lookup"><span data-stu-id="f256c-117">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f256c-118">备注</span><span class="sxs-lookup"><span data-stu-id="f256c-118">Remarks</span></span>  
 <span data-ttu-id="f256c-119">当*UseBuiltInAccount*参数设置为 `true` 并且 Report Server 在 MICROSOFT [!INCLUDE[win2kfamily](../../includes/win2kfamily-md.md)] 或 Windows XP 上运行时，将忽略*Name*、 *Domain*和*Password*参数的值，并使用本地系统帐户。</span><span class="sxs-lookup"><span data-stu-id="f256c-119">When the *UseBuiltInAccount* parameter is set to `true` and the report server is running on Microsoft [!INCLUDE[win2kfamily](../../includes/win2kfamily-md.md)] or Windows XP, the value of the *Name*, *Domain*, and *Password* parameters are ignored and the Local system account is used.</span></span>  
  
 <span data-ttu-id="f256c-120">如果将*UseBuiltInAccount*参数设置为 `true` 并且 Report Server 在 Windows server 2003 上运行，则将忽略*Domain*和*Password*属性，并且名称字段必须包含 "builtin\system" 或 "Builtin\System" 或 "Builtin\LocalService"。</span><span class="sxs-lookup"><span data-stu-id="f256c-120">When the *UseBuiltInAccount* parameter is set to `true` and the report server is running on Windows Server 2003, the *Domain* and *Password* properties are ignored, and the name field must contain either "Builtin\NetworkService" or "Builtin\System" or "Builtin\LocalService".</span></span>  
  
 <span data-ttu-id="f256c-121">SetWindowsServiceIdentity 方法可对报表服务器安装目录中的文件和文件夹设置文件权限。</span><span class="sxs-lookup"><span data-stu-id="f256c-121">The SetWindowsServiceIdentity method sets file permissions on files and folders in the report server installation directory.</span></span>  
  
 <span data-ttu-id="f256c-122">*帐户*参数中指定的帐户需要 `LogonAsService` Windows 中的权限。</span><span class="sxs-lookup"><span data-stu-id="f256c-122">The account specified in the *Account* parameter requires `LogonAsService` rights in Windows.</span></span> <span data-ttu-id="f256c-123">该方法可将此权限授予指定的帐户。</span><span class="sxs-lookup"><span data-stu-id="f256c-123">The method grants this right to the specified account.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f256c-124">要求</span><span class="sxs-lookup"><span data-stu-id="f256c-124">Requirements</span></span>  
 <span data-ttu-id="f256c-125">**命名空间：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f256c-125">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f256c-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f256c-126">See Also</span></span>  
 [<span data-ttu-id="f256c-127">MSReportServer_ConfigurationSetting 成员</span><span class="sxs-lookup"><span data-stu-id="f256c-127">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
