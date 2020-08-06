---
title: 安全属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- security [Analysis Services], properties
- SecurityPackageList property
- BuiltinAdminsAreServerAdmins property
- DisableClientImpersonation property
- ErrorMessageMode property
- RequiredProtectionLevel property
- ServiceAccountIsServerAdmin property
- RequireClientAuthentication property
ms.assetid: 2fc7fe10-0cbb-49ac-aa8c-8ec3f7a7705f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 20133554835803908a340c5369eb66e86b119d72
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586002"
---
# <a name="security-properties"></a><span data-ttu-id="8e662-102">安全属性</span><span class="sxs-lookup"><span data-stu-id="8e662-102">Security Properties</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="8e662-103">支持下表中列出的安全服务器属性。</span><span class="sxs-lookup"><span data-stu-id="8e662-103">supports the security server properties listed in the following table.</span></span> <span data-ttu-id="8e662-104">有关更多服务器属性以及如何设置这些属性的详细信息，请参阅 [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="8e662-104">For more information about additional server properties and how to set them, see [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).</span></span>  
  
 <span data-ttu-id="8e662-105">**适用于：** 多维和表格服务器模式</span><span class="sxs-lookup"><span data-stu-id="8e662-105">**Applies to:** Multidimensional and Tabular server mode</span></span>  
  
## <a name="properties"></a><span data-ttu-id="8e662-106">属性</span><span class="sxs-lookup"><span data-stu-id="8e662-106">Properties</span></span>  
 `RequireClientAuthentication`  
 <span data-ttu-id="8e662-107">一个布尔值属性，指示是否需要客户端身份验证。</span><span class="sxs-lookup"><span data-stu-id="8e662-107">A Boolean property that indicates whether client authentication is required.</span></span>  
  
 <span data-ttu-id="8e662-108">该属性的默认值为 True，指示需要客户端身份验证。</span><span class="sxs-lookup"><span data-stu-id="8e662-108">The default value for this property is True, which indicates that client authentication is required.</span></span>  
  
 `SecurityPackageList`  
 <span data-ttu-id="8e662-109">字符串属性，它包含服务器用于进行客户端身份验证的 SSPI 包的列表，该列表以逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="8e662-109">A string property that contains a comma-separated list of SSPI packages used by server for client authentication.</span></span>  
  
 `DisableClientImpersonation`  
 <span data-ttu-id="8e662-110">指示是否禁用客户端模拟（例如，通过存储过程）的布尔值属性。</span><span class="sxs-lookup"><span data-stu-id="8e662-110">A Boolean property that indicates whether client impersonation (for example, from stored procedures) is disabled.</span></span>  
  
 <span data-ttu-id="8e662-111">该属性的默认值为 False，指示启用客户端模拟。</span><span class="sxs-lookup"><span data-stu-id="8e662-111">The default value for this property is False, which indicates that client impersonation is enabled.</span></span>  
  
 `BuiltinAdminsAreServerAdmins`  
 <span data-ttu-id="8e662-112">指示本地计算机管理员组的成员是否为 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 管理员的布尔值属性。</span><span class="sxs-lookup"><span data-stu-id="8e662-112">A Boolean property that indicates whether members of the local machine administrators group are [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] administrators.</span></span>  
  
 `ServiceAccountIsServerAdmin`  
 <span data-ttu-id="8e662-113">指示服务帐户是否为服务器管理员的布尔值属性。</span><span class="sxs-lookup"><span data-stu-id="8e662-113">A Boolean property that indicates whether the service account is a server administrator.</span></span>  
  
 <span data-ttu-id="8e662-114">该属性的默认值为 True，指示服务帐户为服务器管理员。</span><span class="sxs-lookup"><span data-stu-id="8e662-114">The default value for this property is True, which indicates that the service account is a server administrator.</span></span>  
  
 `ErrorMessageMode`  
 <span data-ttu-id="8e662-115">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="8e662-115">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataProtection\ RequiredProtectionLevel`  
 <span data-ttu-id="8e662-116">有符号 32 位整数属性，用于定义所有客户端请求所需的保护级别。</span><span class="sxs-lookup"><span data-stu-id="8e662-116">A signed 32-bit integer property that defines the required protection level for all client requests.</span></span> <span data-ttu-id="8e662-117">该属性具有下表所列的值之一。</span><span class="sxs-lookup"><span data-stu-id="8e662-117">This property has one of the values listed in the following table.</span></span>  
  
|<span data-ttu-id="8e662-118">值</span><span class="sxs-lookup"><span data-stu-id="8e662-118">Value</span></span>|<span data-ttu-id="8e662-119">说明</span><span class="sxs-lookup"><span data-stu-id="8e662-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8e662-120">*0*</span><span class="sxs-lookup"><span data-stu-id="8e662-120">*0*</span></span>|<span data-ttu-id="8e662-121">无，允许使用明文。</span><span class="sxs-lookup"><span data-stu-id="8e662-121">None, clear text allowed.</span></span>|  
|<span data-ttu-id="8e662-122">*1*</span><span class="sxs-lookup"><span data-stu-id="8e662-122">*1*</span></span>|<span data-ttu-id="8e662-123">（默认值）需要加密，没有明文日志记录。</span><span class="sxs-lookup"><span data-stu-id="8e662-123">(Default) Encryption required, no clear-text logging.</span></span>|  
|<span data-ttu-id="8e662-124">*2*</span><span class="sxs-lookup"><span data-stu-id="8e662-124">*2*</span></span>|<span data-ttu-id="8e662-125">允许进行明文请求，但只带有签名（保护效果弱于加密）。</span><span class="sxs-lookup"><span data-stu-id="8e662-125">Clear-text requests allowed but only with signatures (weaker protection than encryption).</span></span>|  
  
 `AdministrativeDataProtection\ RequiredProtectionLevel`  
 <span data-ttu-id="8e662-126">这是一项高级属性，除非有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技术支持的指导，否则不应更改此属性。</span><span class="sxs-lookup"><span data-stu-id="8e662-126">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e662-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8e662-127">See Also</span></span>  
 <span data-ttu-id="8e662-128">[在 Analysis Services 中配置服务器属性](server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="8e662-128">[Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="8e662-129">确定 Analysis Services 实例的服务器模式</span><span class="sxs-lookup"><span data-stu-id="8e662-129">Determine the Server Mode of an Analysis Services Instance</span></span>](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
