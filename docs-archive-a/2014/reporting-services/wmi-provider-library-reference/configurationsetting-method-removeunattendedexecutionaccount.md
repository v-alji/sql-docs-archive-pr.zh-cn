---
title: " (WMI MSReportServer_ConfigurationSetting) 的 RemoveUnattendedExecutionAccount 方法 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- RemoveUnattendedExecutionAccount (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- RemoveUnattendedExecutionAccount method
ms.assetid: 77e371c1-7c26-44f9-9119-7c8dc838db32
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: efe0523c9aa13315399c043367ef05a63da46e91
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691033"
---
# <a name="removeunattendedexecutionaccount-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="78a3a-102">RemoveUnattendedExecutionAccount 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="78a3a-102">RemoveUnattendedExecutionAccount Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="78a3a-103">从报表服务器配置文件中删除无人参与的执行帐户条目。</span><span class="sxs-lookup"><span data-stu-id="78a3a-103">Deletes the unattended execution account entry from the report server configuration file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78a3a-104">语法</span><span class="sxs-lookup"><span data-stu-id="78a3a-104">Syntax</span></span>  
  
```vb  
Public Sub RemoveUnattendedExecutionAccount(ByRef HRESULT as Int32)  
```  
  
```csharp  
public void RemoveUnattendedExecutionAccount (out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78a3a-105">parameters</span><span class="sxs-lookup"><span data-stu-id="78a3a-105">Parameters</span></span>  
 <span data-ttu-id="78a3a-106">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="78a3a-106">*HRESULT*</span></span>  
 <span data-ttu-id="78a3a-107">[out] 指示调用是成功还是失败的值。</span><span class="sxs-lookup"><span data-stu-id="78a3a-107">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="78a3a-108">返回值</span><span class="sxs-lookup"><span data-stu-id="78a3a-108">Return Value</span></span>  
 <span data-ttu-id="78a3a-109">返回 *HRESULT* ，指示方法调用是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="78a3a-109">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="78a3a-110">值 0 指示方法调用已成功。</span><span class="sxs-lookup"><span data-stu-id="78a3a-110">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="78a3a-111">非零值指示已发生错误。</span><span class="sxs-lookup"><span data-stu-id="78a3a-111">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78a3a-112">要求</span><span class="sxs-lookup"><span data-stu-id="78a3a-112">Requirements</span></span>  
 <span data-ttu-id="78a3a-113">**命名空间：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78a3a-113">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78a3a-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="78a3a-114">See Also</span></span>  
 [<span data-ttu-id="78a3a-115">MSReportServer_ConfigurationSetting 成员</span><span class="sxs-lookup"><span data-stu-id="78a3a-115">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
