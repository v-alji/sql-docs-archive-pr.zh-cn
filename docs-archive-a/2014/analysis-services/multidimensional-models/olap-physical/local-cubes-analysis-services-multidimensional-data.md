---
title: " (Analysis Services 多维数据) 的本地多维数据集 |Microsoft Docs"
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- cubes [Analysis Services], local
ms.assetid: e52e1515-35a7-4dc3-9bbf-736d176ba0c7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 75f02dd54992e9cc4f94d9845e0e25de5ed988f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589295"
---
# <a name="local-cubes-analysis-services---multidimensional-data"></a><span data-ttu-id="8d2ea-102">本地多维数据集（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="8d2ea-102">Local Cubes (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="8d2ea-103">若要创建、更新或删除本地多维数据集，必须编写并执行 ASSL 脚本或 AMO 程序。</span><span class="sxs-lookup"><span data-stu-id="8d2ea-103">To create, update or delete local cubes, you must write and execute either an ASSL script or an AMO program.</span></span>  
  
 <span data-ttu-id="8d2ea-104">本地多维数据集和本地挖掘模型允许在客户端工作站与网络的连接断开时对该工作站进行分析。</span><span class="sxs-lookup"><span data-stu-id="8d2ea-104">Local cubes and local mining models allow analysis on a client workstation while it is disconnected from the network.</span></span> <span data-ttu-id="8d2ea-105">例如，客户端应用程序可能调用 OLE DB for OLAP 9.0 访问接口 (MSOLAP.3)，该接口将加载本地多维数据集引擎以创建和查询本地多维数据集，如下图所示：</span><span class="sxs-lookup"><span data-stu-id="8d2ea-105">For example, a client application might call the OLE DB for OLAP 9.0 Provider (MSOLAP.3), which loads the local cube engine to create and query local cubes, as shown in the following illustration:</span></span>  
  
 <span data-ttu-id="8d2ea-106">![本地多维数据集和模型的客户端体系结构](../../../analysis-services/dev-guide/media/as-localcubearch9.gif "本地多维数据集和模型的客户端体系结构")</span><span class="sxs-lookup"><span data-stu-id="8d2ea-106">![Client architecture for local cubes and models](../../../analysis-services/dev-guide/media/as-localcubearch9.gif "Client architecture for local cubes and models")</span></span>  
  
 <span data-ttu-id="8d2ea-107">在与本地多维数据集进行交互时，ADMOD.NET 和 Analysis Management Objects (AMO) 也将加载本地多维数据集引擎。</span><span class="sxs-lookup"><span data-stu-id="8d2ea-107">ADMOD.NET and Analysis Management Objects (AMO) also load the local cube engine when interacting with local cubes.</span></span> <span data-ttu-id="8d2ea-108">只有一个进程可以访问本地多维数据集文件，这是因为本地多维数据集引擎建立到本地多维数据集的连接时将以独占方式锁定本地多维数据集文件。</span><span class="sxs-lookup"><span data-stu-id="8d2ea-108">Only a single process can access a local cube file, because the local cube engine exclusively locks a local cube file when it establishes a connection to the local cube.</span></span> <span data-ttu-id="8d2ea-109">对于一个进程，最多允许同时有五个连接。</span><span class="sxs-lookup"><span data-stu-id="8d2ea-109">With a process, up to five simultaneous connections are permitted.</span></span>  
  
 <span data-ttu-id="8d2ea-110">一个 .cub 文件可以包含多个多维数据集或数据挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="8d2ea-110">A .cub file may contain more than one cube or data mining model.</span></span> <span data-ttu-id="8d2ea-111">对本地多维数据集和数据挖掘模型的查询可通过本地多维数据集引擎处理，不需要连接到 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="8d2ea-111">Queries to the local cubes and data mining models are handled by the local cube engine and do not require a connection to an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8d2ea-112">不支持使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 和 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 来管理本地多维数据集。</span><span class="sxs-lookup"><span data-stu-id="8d2ea-112">The use of [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] to manage local cubes is not supported.</span></span>  
  
## <a name="local-cubes"></a><span data-ttu-id="8d2ea-113">本地多维数据集</span><span class="sxs-lookup"><span data-stu-id="8d2ea-113">Local Cubes</span></span>  
 <span data-ttu-id="8d2ea-114">可以从实例中的现有多维数据集 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 或从关系数据源创建和填充本地多维数据集。</span><span class="sxs-lookup"><span data-stu-id="8d2ea-114">A local cube can be created and populated from either an existing cube in an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance or from a relational data source.</span></span>  
  
|<span data-ttu-id="8d2ea-115">本地多维数据集的数据源</span><span class="sxs-lookup"><span data-stu-id="8d2ea-115">Source for data for local cube</span></span>|<span data-ttu-id="8d2ea-116">创建方法</span><span class="sxs-lookup"><span data-stu-id="8d2ea-116">Creation method</span></span>|  
|------------------------------------|---------------------|  
|<span data-ttu-id="8d2ea-117">基于服务器的多维数据集</span><span class="sxs-lookup"><span data-stu-id="8d2ea-117">Server-based cube</span></span>|<span data-ttu-id="8d2ea-118">您可以使用 CREATE GLOBAL CUBE 语句或 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 脚本语言 (ASSL) 脚本从基于服务器的多维数据集创建和填充多维数据集。</span><span class="sxs-lookup"><span data-stu-id="8d2ea-118">You can use either the CREATE GLOBAL CUBE statement or an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Scripting Language (ASSL) script to create and populate a cube from a server-based cube.</span></span> <span data-ttu-id="8d2ea-119">有关详细信息，请参阅[CREATE GLOBAL CUBE 语句 &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-global-cube)或[Analysis Services 脚本语言 &#40;ASSL&#41; 引用](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla)。</span><span class="sxs-lookup"><span data-stu-id="8d2ea-119">For more information, see [CREATE GLOBAL CUBE Statement  &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-global-cube) or [Analysis Services Scripting Language &#40;ASSL&#41; Reference](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla).</span></span>|  
|<span data-ttu-id="8d2ea-120">关系数据源</span><span class="sxs-lookup"><span data-stu-id="8d2ea-120">Relational data source</span></span>|<span data-ttu-id="8d2ea-121">可以使用 ASSL 脚本从 OLE DB 关系数据库创建和填充多维数据集。</span><span class="sxs-lookup"><span data-stu-id="8d2ea-121">You use an ASSL script to create and populate a cube from an OLE DB relational database.</span></span> <span data-ttu-id="8d2ea-122">若要使用 ASSL 创建本地多维数据集，只需连接到本地多维数据集文件 (\*.cub)，并以与针对 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 实例执行 ASSL 脚本创建服务器多维数据集的相同方式执行 ASSL 脚本。</span><span class="sxs-lookup"><span data-stu-id="8d2ea-122">To create a local cube using ASSL, you simply connect to a local cube file (\*.cub) and execute the ASSL script in the same manner as executing an ASSL script against an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance to create a server cube.</span></span> <span data-ttu-id="8d2ea-123">有关详细信息，请参阅[Analysis Services 脚本语言 &#40;ASSL&#41; 引用](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla)。</span><span class="sxs-lookup"><span data-stu-id="8d2ea-123">For more information, see [Analysis Services Scripting Language &#40;ASSL&#41; Reference](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla).</span></span>|  
  
 <span data-ttu-id="8d2ea-124">使用 REFRESH CUBE 语句可重新生成本地多维数据集并更新其数据。</span><span class="sxs-lookup"><span data-stu-id="8d2ea-124">Use the REFRESH CUBE statement to rebuild a local cube and update its data.</span></span> <span data-ttu-id="8d2ea-125">有关详细信息，请参阅[REFRESH CUBE 语句 &#40;MDX&#41;](/sql/mdx/mdx-data-definition-refresh-cube)。</span><span class="sxs-lookup"><span data-stu-id="8d2ea-125">For more information, see [REFRESH CUBE Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-refresh-cube).</span></span>  
  
### <a name="local-cubes-created-from-server-based-cubes"></a><span data-ttu-id="8d2ea-126">从基于服务器的多维数据集创建的本地多维数据集</span><span class="sxs-lookup"><span data-stu-id="8d2ea-126">Local Cubes Created from Server-based Cubes</span></span>  
 <span data-ttu-id="8d2ea-127">从基于服务器的多维数据集创建本地多维数据集时，应注意以下事项：</span><span class="sxs-lookup"><span data-stu-id="8d2ea-127">When creating local cubes created from server-based cubes, the following considerations apply:</span></span>  
  
-   <span data-ttu-id="8d2ea-128">不支持非重复计数度量值。</span><span class="sxs-lookup"><span data-stu-id="8d2ea-128">Distinct count measures are not supported.</span></span>  
  
-   <span data-ttu-id="8d2ea-129">添加度量值时，还必须至少包含一个与要添加的度量值相关的维度。</span><span class="sxs-lookup"><span data-stu-id="8d2ea-129">When you add a measure, you must also include at least one dimension that is related to the measure being added.</span></span> <span data-ttu-id="8d2ea-130">有关维度与度量值组的关系的详细信息，请参阅[维度关系](../../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)。</span><span class="sxs-lookup"><span data-stu-id="8d2ea-130">For more information about dimension relationships to measure groups, see [Dimension Relationships](../../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md).</span></span>  
  
-   <span data-ttu-id="8d2ea-131">添加父子层次结构时，将忽略父子层次结构的级别和筛选器，而将包括整个父子层次结构。</span><span class="sxs-lookup"><span data-stu-id="8d2ea-131">When you add a parent-child hierarchy, levels and filters on a parent-child hierarchy are ignored and the entire parent-child hierarchy is included.</span></span>  
  
-   <span data-ttu-id="8d2ea-132">不创建成员属性。</span><span class="sxs-lookup"><span data-stu-id="8d2ea-132">Member properties are not created.</span></span>  
  
-   <span data-ttu-id="8d2ea-133">包括半累加性度量值时，在帐户维度或时间维度上不允许进行切片。</span><span class="sxs-lookup"><span data-stu-id="8d2ea-133">When you include a semi-additive measure, no slices are permitted on either the Account or the Time dimension.</span></span>  
  
-   <span data-ttu-id="8d2ea-134">始终会具体化引用维度。</span><span class="sxs-lookup"><span data-stu-id="8d2ea-134">Reference dimensions are always materialized.</span></span>  
  
-   <span data-ttu-id="8d2ea-135">包含多对多维度时，适用以下规则：</span><span class="sxs-lookup"><span data-stu-id="8d2ea-135">When you include a many-to-many dimension, the following rules apply:</span></span>  
  
    -   <span data-ttu-id="8d2ea-136">不能对多对多维度进行切片。</span><span class="sxs-lookup"><span data-stu-id="8d2ea-136">You cannot slice the many-to-many dimension.</span></span>  
  
    -   <span data-ttu-id="8d2ea-137">必须从中间度量值组添加度量值。</span><span class="sxs-lookup"><span data-stu-id="8d2ea-137">You must add a measure from the intermediary measure group.</span></span>  
  
    -   <span data-ttu-id="8d2ea-138">不能对任何对于多对多关系中涉及的两个度量值组通用的维度进行切片。</span><span class="sxs-lookup"><span data-stu-id="8d2ea-138">You cannot slice any of the dimensions common to the two measure groups involved in the many-to-may relationship.</span></span>  
  
-   <span data-ttu-id="8d2ea-139">只有那些依赖于添加到本地多维数据集中的度量值和维度的计算成员、命名集和分配会显示在本地多维数据集中。</span><span class="sxs-lookup"><span data-stu-id="8d2ea-139">Only those calculated members, named sets, and assignments that rely upon measures and dimensions added to the local cube will appear in the local cube.</span></span> <span data-ttu-id="8d2ea-140">将自动排除无效计算成员、命名集和分配。</span><span class="sxs-lookup"><span data-stu-id="8d2ea-140">Invalid calculated members, named sets, and assignments will be automatically excluded.</span></span>  
  
### <a name="security"></a><span data-ttu-id="8d2ea-141">安全性</span><span class="sxs-lookup"><span data-stu-id="8d2ea-141">Security</span></span>  
 <span data-ttu-id="8d2ea-142">为了使用户能够从服务器多维数据集创建本地多维数据集，必须为用户授予对服务器多维数据集的**钻取和本地多维数据集**权限。</span><span class="sxs-lookup"><span data-stu-id="8d2ea-142">In order for a user to create a local cube from a server cube, the user must be granted **Drillthrough and Local Cube** permissions on the server cube.</span></span> <span data-ttu-id="8d2ea-143">有关详细信息，请参阅[&#40;Analysis Services&#41;授予多维数据集或模型权限](../../multidimensional-models/grant-cube-or-model-permissions-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="8d2ea-143">For more information, see [Grant cube or model permissions &#40;Analysis Services&#41;](../../multidimensional-models/grant-cube-or-model-permissions-analysis-services.md).</span></span>  
  
 <span data-ttu-id="8d2ea-144">使用诸如服务器多维数据集之类的角色无法确保本地多维数据集的安全。</span><span class="sxs-lookup"><span data-stu-id="8d2ea-144">Local cubes are not secured using roles like server cubes.</span></span> <span data-ttu-id="8d2ea-145">拥有对本地多维数据集文件的文件级访问权限的任何用户均可在此文件中查询多维数据集。</span><span class="sxs-lookup"><span data-stu-id="8d2ea-145">Anyone with file-level access to a local cube file can query cubes in it.</span></span> <span data-ttu-id="8d2ea-146">可以使用本地多维数据集文件的 `Encryption Password` 连接属性为本地多维数据集文件设置密码。</span><span class="sxs-lookup"><span data-stu-id="8d2ea-146">You can use the `Encryption Password` connection property on a local cube file to set a password on the local cube file.</span></span> <span data-ttu-id="8d2ea-147">如果为本地多维数据集文件设置密码，则与该本地多维数据集文件的所有连接都需要使用此密码才能查询该文件。</span><span class="sxs-lookup"><span data-stu-id="8d2ea-147">Setting a password on a local cube file requires all future connections to the local cube file to use this password in order to query the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d2ea-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8d2ea-148">See Also</span></span>  
 <span data-ttu-id="8d2ea-149">[&#40;MDX 创建全局多维数据集语句&#41;](/sql/mdx/mdx-data-definition-create-global-cube) </span><span class="sxs-lookup"><span data-stu-id="8d2ea-149">[CREATE GLOBAL CUBE Statement  &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-global-cube) </span></span>  
 <span data-ttu-id="8d2ea-150">[Analysis Services 脚本语言开发 &#40;ASSL&#41;](../scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md) </span><span class="sxs-lookup"><span data-stu-id="8d2ea-150">[Developing with Analysis Services Scripting Language &#40;ASSL&#41;](../scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md) </span></span>  
 [<span data-ttu-id="8d2ea-151">&#40;MDX&#41;刷新 CUBE 语句</span><span class="sxs-lookup"><span data-stu-id="8d2ea-151">REFRESH CUBE Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-data-definition-refresh-cube)  
  
  
