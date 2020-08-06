---
title: SetUnattendedExecutionAccount 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SetUnattendedExecutionAccount (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetUnattendedExecutionAccount method
ms.assetid: 1ba6be6f-b05c-4ea0-af98-cd0780290b70
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 73cf4c633c51de1e3e6b878c66d73ee710e98df6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692182"
---
# <a name="setunattendedexecutionaccount-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="1c5f1-102">SetUnattendedExecutionAccount 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="1c5f1-102">SetUnattendedExecutionAccount Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="1c5f1-103">指定用于执行无人参与报表的帐户。</span><span class="sxs-lookup"><span data-stu-id="1c5f1-103">Specifies the account used to execute reports unattended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c5f1-104">语法</span><span class="sxs-lookup"><span data-stu-id="1c5f1-104">Syntax</span></span>  
  
```vb  
Public Sub SetUnattendedExecutionAccount(UserName as String, _  
    Password as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetUnattendedExecutionAccount (string UserName,   
    string Password, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c5f1-105">parameters</span><span class="sxs-lookup"><span data-stu-id="1c5f1-105">Parameters</span></span>  
 <span data-ttu-id="1c5f1-106">*UserName*</span><span class="sxs-lookup"><span data-stu-id="1c5f1-106">*UserName*</span></span>  
 <span data-ttu-id="1c5f1-107">用于无人参与执行的 Windows 帐户。</span><span class="sxs-lookup"><span data-stu-id="1c5f1-107">A Windows account to be used for unattended executions.</span></span>  
  
 <span data-ttu-id="1c5f1-108">*密码*</span><span class="sxs-lookup"><span data-stu-id="1c5f1-108">*Password*</span></span>  
 <span data-ttu-id="1c5f1-109">指定帐户的密码。</span><span class="sxs-lookup"><span data-stu-id="1c5f1-109">The password for the specified account.</span></span>  
  
 <span data-ttu-id="1c5f1-110">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="1c5f1-110">*HRESULT*</span></span>  
 <span data-ttu-id="1c5f1-111">[out] 指示调用是成功还是失败的值。</span><span class="sxs-lookup"><span data-stu-id="1c5f1-111">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1c5f1-112">返回值</span><span class="sxs-lookup"><span data-stu-id="1c5f1-112">Return Value</span></span>  
 <span data-ttu-id="1c5f1-113">返回 *HRESULT* ，指示方法调用是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="1c5f1-113">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="1c5f1-114">值 0 指示方法调用已成功。</span><span class="sxs-lookup"><span data-stu-id="1c5f1-114">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="1c5f1-115">非零值指示已发生错误。</span><span class="sxs-lookup"><span data-stu-id="1c5f1-115">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c5f1-116">备注</span><span class="sxs-lookup"><span data-stu-id="1c5f1-116">Remarks</span></span>  
 <span data-ttu-id="1c5f1-117">SetUnattendedExecutionAccount 方法不验证报表服务器是否可以指定用户身份登录。</span><span class="sxs-lookup"><span data-stu-id="1c5f1-117">The SetUnattendedExecutionAccount method does not verify whether the report server can log in as the specified user.</span></span>  
  
 <span data-ttu-id="1c5f1-118">不能使用 SetUnattendedExecutionAccount 方法在报表服务器 Windows 服务的上下文中运行无人参与的执行。</span><span class="sxs-lookup"><span data-stu-id="1c5f1-118">It is not possible to use the SetUnattendedExecutionAccount method to run unattended executions in the context of the report server Windows service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c5f1-119">要求</span><span class="sxs-lookup"><span data-stu-id="1c5f1-119">Requirements</span></span>  
 <span data-ttu-id="1c5f1-120">**命名空间：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c5f1-120">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c5f1-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1c5f1-121">See Also</span></span>  
 [<span data-ttu-id="1c5f1-122">MSReportServer_ConfigurationSetting 成员</span><span class="sxs-lookup"><span data-stu-id="1c5f1-122">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
