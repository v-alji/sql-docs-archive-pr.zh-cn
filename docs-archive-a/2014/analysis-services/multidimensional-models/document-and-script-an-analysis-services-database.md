---
title: 记录 Analysis Services 数据库并编写脚本 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- XML for Analysis, scripts
- XMLA, scripts
- scripts [Analysis Services], databases
- documenting databases
- databases [Analysis Services], documenting
- databases [Analysis Services], scripts
ms.assetid: 125044e2-8d36-4733-8743-8bb68ff9aa4e
author: minewiskan
ms.author: owend
ms.openlocfilehash: cfe008b0d6903d7d012eb57d41d6e50240202ec8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590392"
---
# <a name="document-and-script-an-analysis-services-database"></a><span data-ttu-id="de3cc-102">记录和编写 Analysis Services 数据库脚本</span><span class="sxs-lookup"><span data-stu-id="de3cc-102">Document and Script an Analysis Services Database</span></span>
  <span data-ttu-id="de3cc-103">在部署 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库后，可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 将数据库的元数据或数据库中包含的对象的元数据输出为 XML for Analysis (XMLA) 脚本。</span><span class="sxs-lookup"><span data-stu-id="de3cc-103">After an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database is deployed, you can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to output the metadata of the database, or of an object contained in the database, as an XML for Analysis (XMLA) script.</span></span> <span data-ttu-id="de3cc-104">可以将该脚本输出到一个新的 **“XMLA 查询编辑器”** 窗口、文件或剪贴板。</span><span class="sxs-lookup"><span data-stu-id="de3cc-104">You can output this script to a new **XMLA Query Editor** window, to a file, or to the Clipboard.</span></span> <span data-ttu-id="de3cc-105">有关 XMLA 的详细信息，请参阅[Analysis Services 脚本语言 &#40;ASSL&#41; 引用](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla)。</span><span class="sxs-lookup"><span data-stu-id="de3cc-105">For more information about XMLA, see [Analysis Services Scripting Language &#40;ASSL&#41; Reference](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla).</span></span>  
  
 <span data-ttu-id="de3cc-106">生成的 XMLA 脚本使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 脚本语言 (ASSL) 元素定义脚本包含的对象。</span><span class="sxs-lookup"><span data-stu-id="de3cc-106">The generated XMLA script uses [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Scripting Language (ASSL) elements to define the objects contained by the script.</span></span> <span data-ttu-id="de3cc-107">如果生成了 CREATE 脚本，则所生成的 XMLA 脚本包含一个 XMLA **Create** 命令和 ASSL 元素，它们可用于在实例上创建整个 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库结构。</span><span class="sxs-lookup"><span data-stu-id="de3cc-107">If you generated a CREATE script, the resulting XMLA script contains an XMLA **Create** command and ASSL elements that can be used to create the entire [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database structure on an instance.</span></span> <span data-ttu-id="de3cc-108">如果生成了一个 ALTER 脚本，则所生成的 XMLA 脚本包含一个 XMLA **Alter** 命令和 ASSL 元素，它们可用于将现有 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库的结构还原到创建脚本时数据库所处的状态。</span><span class="sxs-lookup"><span data-stu-id="de3cc-108">If you generated an ALTER script, the resulting XMLA script contains an XMLA **Alter** command and ASSL elements that can be used to restore the structure of an existing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database to the state of the database at the time the script was created.</span></span>  
  
 <span data-ttu-id="de3cc-109">可以通过多种方法使用从 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库生成的 XMLA 脚本，其中包括：</span><span class="sxs-lookup"><span data-stu-id="de3cc-109">You can use the generated XMLA script from an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database in many ways, including:</span></span>  
  
-   <span data-ttu-id="de3cc-110">维护一个备份脚本，通过该脚本可以重新创建所有数据库对象和权限。</span><span class="sxs-lookup"><span data-stu-id="de3cc-110">To maintain a backup script that allows you to recreate all the database objects and permissions.</span></span>  
  
-   <span data-ttu-id="de3cc-111">创建或更新数据库开发代码。</span><span class="sxs-lookup"><span data-stu-id="de3cc-111">To create or update database development code.</span></span>  
  
-   <span data-ttu-id="de3cc-112">从现有的架构创建一个测试或开发环境。</span><span class="sxs-lookup"><span data-stu-id="de3cc-112">To create a test or development environment from an existing schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de3cc-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="de3cc-113">See Also</span></span>  
 <span data-ttu-id="de3cc-114">[修改或删除 Analysis Services 数据库](modify-or-delete-an-analysis-services-database.md) </span><span class="sxs-lookup"><span data-stu-id="de3cc-114">[Modify or Delete an Analysis Services Database](modify-or-delete-an-analysis-services-database.md) </span></span>  
 <span data-ttu-id="de3cc-115">[&#40;XMLA&#41;更改元素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="de3cc-115">[Alter Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla) </span></span>  
 [<span data-ttu-id="de3cc-116">Create 元素 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="de3cc-116">Create Element &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla)  
  
  
