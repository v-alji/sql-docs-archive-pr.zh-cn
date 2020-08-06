---
title: " (XMLA) 的 XML 元素 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- XMLA, elements
- XML for Analysis, elements
- elements [XML for Analysis]
ms.assetid: 40ab2360-efb6-4ba6-bf23-e84964e51008
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5c1e5b046bfa57302baefc43a4da989be9c70e08
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589958"
---
# <a name="xml-elements-xmla"></a><span data-ttu-id="efd52-102">XML 元素 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="efd52-102">XML Elements (XMLA)</span></span>
  <span data-ttu-id="efd52-103">以下主题描述支持的各种 XML for Analysis (XMLA) 元素类别 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="efd52-103">The following topics describe the various XML for Analysis (XMLA) element categories supported by [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="efd52-104">本节内容</span><span class="sxs-lookup"><span data-stu-id="efd52-104">In This Section</span></span>  
  
|<span data-ttu-id="efd52-105">属性</span><span class="sxs-lookup"><span data-stu-id="efd52-105">Property</span></span>|<span data-ttu-id="efd52-106">说明</span><span class="sxs-lookup"><span data-stu-id="efd52-106">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="efd52-107">&#40;XMLA&#41;标头</span><span class="sxs-lookup"><span data-stu-id="efd52-107">Headers &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/xml-elements-headers)|<span data-ttu-id="efd52-108">介绍由应用程序或 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例为管理协议级别的功能在 SOAP 信封的 SOAP 标头里发送的那些元素。</span><span class="sxs-lookup"><span data-stu-id="efd52-108">Describes those elements sent in the SOAP header of a SOAP envelope, either by an application or by an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, to manage protocol-level features.</span></span>|  
|[<span data-ttu-id="efd52-109">XMLA &#40;方法&#41;</span><span class="sxs-lookup"><span data-stu-id="efd52-109">Methods &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods)|<span data-ttu-id="efd52-110">介绍应用程序为检索数据或元数据或为了对 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例进行操作而在 SOAP 信封里发送给该实例的最顶端元素。</span><span class="sxs-lookup"><span data-stu-id="efd52-110">Describes the topmost elements sent by an application in a SOAP envelope to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance to retrieve data or metadata, or to perform actions on the instance.</span></span>|  
|[<span data-ttu-id="efd52-111">命令 &#40;XMLA&#41;</span><span class="sxs-lookup"><span data-stu-id="efd52-111">Commands &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/xml-elements-commands)|<span data-ttu-id="efd52-112">介绍 XMLA 方法内为执行特定操作发送的元素。</span><span class="sxs-lookup"><span data-stu-id="efd52-112">Describes the elements sent within an XMLA method to perform a specific action.</span></span>|  
|[<span data-ttu-id="efd52-113">&#40;XMLA 的对象&#41;</span><span class="sxs-lookup"><span data-stu-id="efd52-113">Objects &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects)|<span data-ttu-id="efd52-114">介绍 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例为响应 XMLA 方法而在 SOAP 信封发送给应用程序的最顶端元素。</span><span class="sxs-lookup"><span data-stu-id="efd52-114">Describes the topmost elements received by an application in a SOAP envelope from an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance in response to an XMLA method.</span></span>|  
|[<span data-ttu-id="efd52-115">XMLA&#41;的属性 &#40;</span><span class="sxs-lookup"><span data-stu-id="efd52-115">Properties &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/xml-elements-properties)|<span data-ttu-id="efd52-116">介绍 XMLA 标头、方法、对象或命令的子元素。</span><span class="sxs-lookup"><span data-stu-id="efd52-116">Describes the child elements for XMLA headers, methods, objects, or commands.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="efd52-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="efd52-117">See Also</span></span>  
 <span data-ttu-id="efd52-118">[XML 数据类型 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-data-types/xml-data-types-xmla) </span><span class="sxs-lookup"><span data-stu-id="efd52-118">[XML Data Types &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-data-types/xml-data-types-xmla) </span></span>  
 [<span data-ttu-id="efd52-119">使用 Analysis Services 脚本语言 (ASSL) 开发</span><span class="sxs-lookup"><span data-stu-id="efd52-119">Developing with Analysis Services Scripting Language &#40;ASSL&#41;</span></span>](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)  
  
  
