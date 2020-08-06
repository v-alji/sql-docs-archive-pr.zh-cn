---
title: 使用 XMLA 部署模型解决方案 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- XML scripts [Analysis Services]
- scripts [Analysis Services], deployment
- deploying [Analysis Services], XML scripts
- Analysis Services deployments, XML scripts
ms.assetid: a8cb1837-fcac-4730-bea4-a72cf94d9f7c
author: minewiskan
ms.author: owend
ms.openlocfilehash: b78490c5ab6ad3ba5e52bb82d4be254e3f5f102b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693540"
---
# <a name="deploy-model-solutions-using-xmla"></a><span data-ttu-id="051ba-102">使用 XMLA 部署模型解决方案</span><span class="sxs-lookup"><span data-stu-id="051ba-102">Deploy Model Solutions Using XMLA</span></span>
  <span data-ttu-id="051ba-103">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中， **“编写数据库脚本为”** 命令的 **“CREATE 到”** 选项用于创建整个 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库或其中一个构成对象的 XML 脚本。</span><span class="sxs-lookup"><span data-stu-id="051ba-103">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], the **CREATE To** option of the **Script Database As** command creates an XML script of an entire [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database or one of its constituent objects.</span></span> <span data-ttu-id="051ba-104">然后，生成的脚本可以在另一台计算机上运行来重新创建 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库的架构（元数据）。</span><span class="sxs-lookup"><span data-stu-id="051ba-104">The resulting script can then be run on another computer to recreate the schema (metadata) of the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="051ba-105">脚本生成整个数据库，而且当使用脚本时，没有用于增量更新已部署对象的机制。</span><span class="sxs-lookup"><span data-stu-id="051ba-105">The script generates the entire database, and there is no mechanism for incrementally updating already deployed objects when using the script.</span></span> <span data-ttu-id="051ba-106">运行脚本并部署数据库之后，必须对新创建的数据库进行处理，然后用户才能浏览该数据库。</span><span class="sxs-lookup"><span data-stu-id="051ba-106">After running the script and deploying the database, the newly created database must be processed before users can browse it.</span></span>  
  
 <span data-ttu-id="051ba-107">有关“编写数据库脚本为”\*\*\*\* 命令的详细信息，请参阅[记录和编写 Analysis Services 数据库脚本](document-and-script-an-analysis-services-database.md)。</span><span class="sxs-lookup"><span data-stu-id="051ba-107">For more information about the **Script Database As** command, see [Document and Script an Analysis Services Database](document-and-script-an-analysis-services-database.md).</span></span>  
  
## <a name="modifying-object-properties-in-the-xml-script"></a><span data-ttu-id="051ba-108">在 XML 脚本中修改对象属性</span><span class="sxs-lookup"><span data-stu-id="051ba-108">Modifying Object Properties in the XML Script</span></span>  
 <span data-ttu-id="051ba-109">当使用“编写数据库脚本为”\*\*\*\* 命令时，不能修改数据库对象的特定属性（如数据库名称、数据源连接字符串以及安全设置）。</span><span class="sxs-lookup"><span data-stu-id="051ba-109">When using the **Script Database As** command, you cannot modify specific properties (such as the database name, data source connection strings, and security settings) of the database objects.</span></span> <span data-ttu-id="051ba-110">这些属性必须当脚本生成后在脚本中手动修改，或者当运行脚本后在已部署的数据库中修改。</span><span class="sxs-lookup"><span data-stu-id="051ba-110">These properties must either be manually modified in the script after the script has been generated or modified in the deployed database after running the script.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="051ba-111">如果在用于数据源的连接字符串中指定密码或出于模拟目的而指定密码，则此密码不包含在 XML 脚本中。</span><span class="sxs-lookup"><span data-stu-id="051ba-111">The XML script will not contain the password if this is specified in either the connection string for a data source or for impersonation purposes.</span></span> <span data-ttu-id="051ba-112">在这种情况下，由于处理时需要密码，因此必须在执行 XML 脚本之前将该密码手动添加到此脚本中，或者在执行 XML 脚本后添加该密码。</span><span class="sxs-lookup"><span data-stu-id="051ba-112">Since the password is required for processing purposes in this scenario, you will either need to add this manually to the XML script before it executes or add it after the XML script executes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="051ba-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="051ba-113">See Also</span></span>  
 <span data-ttu-id="051ba-114">[使用部署向导部署模型解决方案](deploy-model-solutions-using-the-deployment-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="051ba-114">[Deploy Model Solutions Using the Deployment Wizard](deploy-model-solutions-using-the-deployment-wizard.md) </span></span>  
 [<span data-ttu-id="051ba-115">同步 Analysis Services 数据库</span><span class="sxs-lookup"><span data-stu-id="051ba-115">Synchronize Analysis Services Databases</span></span>](synchronize-analysis-services-databases.md)  
  
  
