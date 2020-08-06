---
title: 使用具有强名称的自定义程序集 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- AllowPartiallyTrustedCallersAttribute attribute
- strong-named custom assemblies [Reporting Services]
- strong names [Reporting Services]
- assemblies [Reporting Services], strong names
- custom assemblies [Reporting Services], strong-named
ms.assetid: ca9f19d7-6e86-46f2-b9ad-9bf807eaa52e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5e685ecda39e0487eb4b469920820fa6e4a10daa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577404"
---
# <a name="using-strong-named-custom-assemblies"></a><span data-ttu-id="9130b-102">使用具有强名称的自定义程序集</span><span class="sxs-lookup"><span data-stu-id="9130b-102">Using Strong-Named Custom Assemblies</span></span>
  <span data-ttu-id="9130b-103">强名称标识程序集，它包括程序集的文本名称、由四个部分组成的版本号、区域性信息（如果提供）、公钥以及存储在程序集的清单中的数字签名。</span><span class="sxs-lookup"><span data-stu-id="9130b-103">A strong name identifies an assembly and includes the assembly's text name, four-part version number, culture information (if provided), a public key, and a digital signature stored in the assembly's manifest.</span></span> <span data-ttu-id="9130b-104">强名称针对公共语言运行时 (CLR) 唯一标识程序集并确保二进制完整性。</span><span class="sxs-lookup"><span data-stu-id="9130b-104">A strong name uniquely identifies an assembly to the common language runtime (CLR) and ensures binary integrity.</span></span>  
  
## <a name="using-allowpartiallytrustedcallersattribute"></a><span data-ttu-id="9130b-105">使用 AllowPartiallyTrustedCallersAttribute</span><span class="sxs-lookup"><span data-stu-id="9130b-105">Using AllowPartiallyTrustedCallersAttribute</span></span>  
 <span data-ttu-id="9130b-106">要将具有强名称的程序集用于报表，必须允许部分受信任的代码使用程序集的 AllowPartiallyTrustedCallers 属性调用具有强名称的程序集\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9130b-106">To use strong-named assemblies with reports, you must allow your strong-named assembly to be called by partially trusted code using the assembly's **AllowPartiallyTrustedCallers** attribute.</span></span> <span data-ttu-id="9130b-107">可以使用 AllowPartiallyTrustedCallersAttribute 以允许报表设计器或报表服务器在报表表达式中调用具有强名称的程序集\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9130b-107">You can use **AllowPartiallyTrustedCallersAttribute** to allow strong-named assemblies to be called by Report Designer or the report server in report expressions.</span></span> <span data-ttu-id="9130b-108">若要允许部分受信任的代码调用具有强名称的程序集，请将以下程序集级别属性添加到程序集属性文件。</span><span class="sxs-lookup"><span data-stu-id="9130b-108">To allow partially trusted code to call strong-named assemblies, add the following assembly-level attribute to your assembly attribute file.</span></span>  
  
```vb  
<assembly:AllowPartiallyTrustedCallers>  
```  
  
```csharp  
[assembly:AllowPartiallyTrustedCallers]  
```  
  
 <span data-ttu-id="9130b-109">AllowPartiallyTrustedCallersAttribute 仅当被具有强名称的程序集在程序集级别应用时才生效\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9130b-109">**AllowPartiallyTrustedCallersAttribute** is effective only when applied by a strong-named assembly at the assembly level.</span></span> <span data-ttu-id="9130b-110">有关在程序集级别应用属性的详细信息，请参阅 SDK 文档中的 "应用属性" [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="9130b-110">For more information about applying attributes at the assembly level, see "Applying Attributes" in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="9130b-111">当存在 AllowPartiallyTrustedCallersAttribute 时，将阻止默认的 FullTrustLinkDemand 安全检查，同时可以从任何其他部分受信任的程序集调用该程序集\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9130b-111">When **AllowPartiallyTrustedCallersAttribute** is present, the default **FullTrustLinkDemand** security checks are prevented, making the assembly callable from any other partially trusted assembly.</span></span> <span data-ttu-id="9130b-112">所有安全检查（包括类级别或方法级别的声明性安全属性）都必须显式声明。</span><span class="sxs-lookup"><span data-stu-id="9130b-112">All security checks, including class-level or method-level declarative security attributes, must be explicitly stated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9130b-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9130b-113">See Also</span></span>  
 [<span data-ttu-id="9130b-114">将自定义程序集用于报表</span><span class="sxs-lookup"><span data-stu-id="9130b-114">Using Custom Assemblies with Reports</span></span>](using-custom-assemblies-with-reports.md)  
  
  
