---
title: DatabaseLogonType 属性 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- DatabaseLogonType
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DatabaseLogonType property
ms.assetid: 6b592582-4c35-4029-ab86-982fff47d8d6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3bb5a4149c29fb7532b7140a2616dd856e6db2b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692167"
---
# <a name="databaselogontype-property-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="20517-102">DatabaseLogonType 属性 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="20517-102">DatabaseLogonType Property (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="20517-103">指定报表服务器是使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 服务帐户、Windows 用户帐户还是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名访问报表服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="20517-103">Specifies whether the report server uses a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows service account, a Windows user account, or a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to access the report server database.</span></span> <span data-ttu-id="20517-104">只读。</span><span class="sxs-lookup"><span data-stu-id="20517-104">Read-only.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20517-105">语法</span><span class="sxs-lookup"><span data-stu-id="20517-105">Syntax</span></span>  
  
```vb  
Public Dim DatabaseLogonType As Integer  
```  
  
```csharp  
public int DatabaseLogonType;  
```  
  
## <a name="property-values"></a><span data-ttu-id="20517-106">属性值</span><span class="sxs-lookup"><span data-stu-id="20517-106">Property Values</span></span>  
 <span data-ttu-id="20517-107">表示登录类型的 `integer` 对象。</span><span class="sxs-lookup"><span data-stu-id="20517-107">An `integer` object that represents the login type.</span></span>  
  
## <a name="example-code"></a><span data-ttu-id="20517-108">示例代码</span><span class="sxs-lookup"><span data-stu-id="20517-108">Example Code</span></span>  
 [<span data-ttu-id="20517-109">MSReportServer_ConfigurationSetting 类</span><span class="sxs-lookup"><span data-stu-id="20517-109">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
## <a name="remarks"></a><span data-ttu-id="20517-110">备注</span><span class="sxs-lookup"><span data-stu-id="20517-110">Remarks</span></span>  
 <span data-ttu-id="20517-111">值为：</span><span class="sxs-lookup"><span data-stu-id="20517-111">Values are:</span></span>  
  
-   <span data-ttu-id="20517-112">0 表示 Windows 登录</span><span class="sxs-lookup"><span data-stu-id="20517-112">0 for Windows login</span></span>  
  
-   <span data-ttu-id="20517-113">1 表示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录</span><span class="sxs-lookup"><span data-stu-id="20517-113">1 for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login</span></span>  
  
-   <span data-ttu-id="20517-114">2 表示以服务身份登录</span><span class="sxs-lookup"><span data-stu-id="20517-114">2 to log in as a service</span></span>  
  
 <span data-ttu-id="20517-115">如果指定 0 (Windows)，则必须将 [DatabaseLogonAccount](configurationsetting-property-databaselogonaccount.md) 属性中的值设置为相应的有效 Windows 用户帐户。</span><span class="sxs-lookup"><span data-stu-id="20517-115">If you specify 0 (Windows), you must set the value in the [DatabaseLogonAccount](configurationsetting-property-databaselogonaccount.md) property to a corresponding a valid Windows user account.</span></span>  
  
 <span data-ttu-id="20517-116">如果指定 1 (SQL Server)，请确保 [DatabaseLogonAccount](configurationsetting-property-databaselogonaccount.md) 的值与有效的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名对应。</span><span class="sxs-lookup"><span data-stu-id="20517-116">If you specify 1 (SQL Server), make sure the value of the [DatabaseLogonAccount](configurationsetting-property-databaselogonaccount.md) corresponds to a valid [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span>  
  
 <span data-ttu-id="20517-117">如果指定 2（Windows 服务），则报表服务器使用 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 帐户和 Windows 服务帐户来访问报表服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="20517-117">If you specify 2 (Windows service), the report server uses an [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] account and the Windows service account to access the report server database.</span></span> <span data-ttu-id="20517-118">DatabaseLogonAccount 属性被忽略。</span><span class="sxs-lookup"><span data-stu-id="20517-118">The DatabaseLogonAccount property is ignored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20517-119">要求</span><span class="sxs-lookup"><span data-stu-id="20517-119">Requirements</span></span>  
 <span data-ttu-id="20517-120">**命名空间：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20517-120">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20517-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="20517-121">See Also</span></span>  
 [<span data-ttu-id="20517-122">MSReportServer_ConfigurationSetting 成员</span><span class="sxs-lookup"><span data-stu-id="20517-122">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
