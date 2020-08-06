---
title: Analysis Services 脚本语言开发 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Analysis Services Scripting Language
- ASSL
ms.assetid: ce9aca4d-b7ad-451e-bb7f-20c2b0c03f29
author: minewiskan
ms.author: owend
ms.openlocfilehash: fbb64c120e67d5b4ac12e7bd77f0e0c4e5736757
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587054"
---
# <a name="developing-with-analysis-services-scripting-language-assl"></a><span data-ttu-id="53fd9-102">使用 Analysis Services 脚本语言 (ASSL) 开发</span><span class="sxs-lookup"><span data-stu-id="53fd9-102">Developing with Analysis Services Scripting Language (ASSL)</span></span>
  <span data-ttu-id="53fd9-103">Analysis Services 脚本语言 (ASSL) 是对 XMLA 的扩展，该语言添加了对象定义语言和命令语言，用来在服务器上直接创建和管理 Analysis Services 结构。</span><span class="sxs-lookup"><span data-stu-id="53fd9-103">Analysis Services Scripting Language (ASSL) is an extension to XMLA that adds an object definition language and command language for creating and managing Analysis Services structures directly on the server.</span></span> <span data-ttu-id="53fd9-104">您可以在自定义应用程序中使用 ASSL 通过 XMLA 协议与 Analysis Services 通信。</span><span class="sxs-lookup"><span data-stu-id="53fd9-104">You can use ASSL in custom application to communicate with Analysis Services over the XMLA protocol.</span></span> <span data-ttu-id="53fd9-105">ASSL 由两个部分组成：</span><span class="sxs-lookup"><span data-stu-id="53fd9-105">ASSL is made up of two parts:</span></span>  
  
-   <span data-ttu-id="53fd9-106">数据定义语言 (DDL)（也称为对象定义语言）定义并说明 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 实例以及该实例所包含的数据库和数据库对象。</span><span class="sxs-lookup"><span data-stu-id="53fd9-106">A Data Definition Language (DDL), or object definition language, defines and describes an instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], as well as the databases and database objects that the instance contains.</span></span>  
  
-   <span data-ttu-id="53fd9-107">向 Analysis Services 实例发送操作命令（如 `Create`、`Alter` 或 `Process`）的命令语言。</span><span class="sxs-lookup"><span data-stu-id="53fd9-107">A command language that sends action commands, such as `Create`, `Alter`, or `Process`, to an instance of Analysis Services.</span></span> <span data-ttu-id="53fd9-108">[XML for Analysis &#40;XMLA&#41; 参考](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference)中讨论了此命令语言。</span><span class="sxs-lookup"><span data-stu-id="53fd9-108">This command language is discussed in the [XML for Analysis  &#40;XMLA&#41; Reference](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference).</span></span>  
  
 <span data-ttu-id="53fd9-109">若要查看描述 [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)] 中的多维解决方案的 ASSL，可以在项目级别使用 View Code 命令。</span><span class="sxs-lookup"><span data-stu-id="53fd9-109">To view the ASSL that describes a multidimensional solution in [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)], you can use the View Code command at the project level.</span></span> <span data-ttu-id="53fd9-110">您还可以在 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] 中使用 XMLA 查询编辑器创建或编辑 ASSL 脚本。</span><span class="sxs-lookup"><span data-stu-id="53fd9-110">You can also create or edit ASSL script in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] using the XMLA query editor.</span></span> <span data-ttu-id="53fd9-111">生成的脚本可用于管理服务器上的对象或在服务器上运行命令。</span><span class="sxs-lookup"><span data-stu-id="53fd9-111">The scripts you build can be used to manage objects or run commands on the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53fd9-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="53fd9-112">See Also</span></span>  
 <span data-ttu-id="53fd9-113">[ASSL 对象和对象特征](assl-objects-and-object-characteristics.md) </span><span class="sxs-lookup"><span data-stu-id="53fd9-113">[ASSL Objects and Object Characteristics](assl-objects-and-object-characteristics.md) </span></span>  
 <span data-ttu-id="53fd9-114">[ASSL XML 约定](assl-xml-conventions.md) </span><span class="sxs-lookup"><span data-stu-id="53fd9-114">[ASSL XML Conventions](assl-xml-conventions.md) </span></span>  
 [<span data-ttu-id="53fd9-115">数据源和绑定（SSAS 多维）</span><span class="sxs-lookup"><span data-stu-id="53fd9-115">Data Sources and Bindings &#40;SSAS Multidimensional&#41;</span></span>](../data-sources-and-bindings-ssas-multidimensional.md)  
  
  
