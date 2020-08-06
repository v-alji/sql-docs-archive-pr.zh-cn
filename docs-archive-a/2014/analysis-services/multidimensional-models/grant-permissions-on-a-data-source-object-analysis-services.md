---
title: " (Analysis Services) 授予对数据源对象的权限 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.roledesignerdialog.datasources.f1
helpviewer_keywords:
- read/write permissions
- user access rights [Analysis Services], data sources
- security [Analysis Services], data sources
- connection strings [Analysis Services]
- data sources [Analysis Services], security
ms.assetid: b4e302d3-c93b-4383-aa4a-37d15c129830
author: minewiskan
ms.author: owend
ms.openlocfilehash: d0a7de676f5863187c2c137e056392a605af474f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690830"
---
# <a name="grant-permissions-on-a-data-source-object-analysis-services"></a><span data-ttu-id="90cd7-102">授予数据源对象的权限 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="90cd7-102">Grant permissions on a data source object (Analysis Services)</span></span>
  <span data-ttu-id="90cd7-103">通常，大多数 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 用户无需访问作为 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目基础的数据源。</span><span class="sxs-lookup"><span data-stu-id="90cd7-103">Typically, most users of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] do not require access to the data sources that underlie an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="90cd7-104">用户通常只查询 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中的数据。</span><span class="sxs-lookup"><span data-stu-id="90cd7-104">Users ordinarily just query the data within an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="90cd7-105">但是，在数据挖掘上下文中（如根据挖掘模型执行预测），用户必须将挖掘模型的已学习数据与用户提供的数据联接起来。</span><span class="sxs-lookup"><span data-stu-id="90cd7-105">However, in the context of data mining, such as performing predictions based on a mining model, a user has to join the learned data of a mining model with user-provided data.</span></span> <span data-ttu-id="90cd7-106">为了连接到包含用户提供数据的数据源，用户将使用包含 [OPENQUERY (DMX)](/sql/dmx/source-data-query-openquery) 或 [OPENROWSET (DMX)](/sql/dmx/source-data-query-openrowset) 子句的数据挖掘扩展插件 (DMX) 查询。</span><span class="sxs-lookup"><span data-stu-id="90cd7-106">To connect to the data source that contains the user-provided data, the user uses a Data Mining Extensions (DMX) query that contains either the [OPENQUERY &#40;DMX&#41;](/sql/dmx/source-data-query-openquery) and [OPENROWSET &#40;DMX&#41;](/sql/dmx/source-data-query-openrowset) clause.</span></span>  
  
 <span data-ttu-id="90cd7-107">若要执行连接到数据源的 DMX 查询，用户必须能访问 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库中的数据源对象。</span><span class="sxs-lookup"><span data-stu-id="90cd7-107">To execute a DMX query that connects to a data source, the user must have access to the data source object within the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="90cd7-108">默认情况下，只有数据库管理员或服务器管理员具有访问数据源对象的权限。</span><span class="sxs-lookup"><span data-stu-id="90cd7-108">By default, only Server Administrators or Database Administrators have access to data source objects.</span></span> <span data-ttu-id="90cd7-109">这意味着，除非管理员授予权限，否则用户将不能访问数据源对象。</span><span class="sxs-lookup"><span data-stu-id="90cd7-109">This means that a user cannot access a data source object unless an administrator grants permissions.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="90cd7-110">出于安全方面的考虑，系统禁止在 OPENROWSET 子句中使用公开连接字符串来提交 DMX 查询。</span><span class="sxs-lookup"><span data-stu-id="90cd7-110">For security reasons, the submission of DMX queries by using an open connection string in the OPENROWSET clause is disabled.</span></span>  
  
## <a name="set-read-permissions-to-a-data-source"></a><span data-ttu-id="90cd7-111">设置对数据源的读取权限</span><span class="sxs-lookup"><span data-stu-id="90cd7-111">Set Read permissions to a data source</span></span>  
 <span data-ttu-id="90cd7-112">可以使数据库角色无权访问数据源对象，也可以授予其读取权限。</span><span class="sxs-lookup"><span data-stu-id="90cd7-112">A database role can be granted either no access permissions on a data source object or read permissions.</span></span>  
  
1.  <span data-ttu-id="90cd7-113">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，连接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例，在对象资源管理器中展开相应数据库的“角色”\*\*\*\*，然后单击某个数据库角色（或创建一个新的数据库角色）。</span><span class="sxs-lookup"><span data-stu-id="90cd7-113">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], expand **Roles** for the appropriate database in Object explorer, and then click a database role (or create a new database role).</span></span>  
  
2.  <span data-ttu-id="90cd7-114">在“数据源访问”窗格 \*\*\*\* ，找到“数据源”列表中的数据源对象 \*\*\*\* ，然后在该数据源的“访问”列表 \*\*\*\* 中选择“读” \*\*\*\* 。</span><span class="sxs-lookup"><span data-stu-id="90cd7-114">In the **Data Source Access** pane, locate the data source object in the **Data Source** list, and then select the **Read** in the **Access** list for the data source.</span></span> <span data-ttu-id="90cd7-115">如果此选项不可用，请检查“常规” \*\*\*\* 面板，以查看是否已选择“完全控制”。</span><span class="sxs-lookup"><span data-stu-id="90cd7-115">If this option is unavailable, check the **General** pane to see if Full Control is selected.</span></span> <span data-ttu-id="90cd7-116">“完全控制”已在提供权限，你不能覆盖数据源上的权限。</span><span class="sxs-lookup"><span data-stu-id="90cd7-116">Full Control is already providing permission, you cannot override permissions on the data source.</span></span>  
  
## <a name="working-with-the-connection-string-used-by-a-data-source-object"></a><span data-ttu-id="90cd7-117">使用数据源对象使用的连接字符串</span><span class="sxs-lookup"><span data-stu-id="90cd7-117">Working With the Connection String Used by a Data Source Object</span></span>  
 <span data-ttu-id="90cd7-118">数据源对象包括用于连接到基础数据源的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="90cd7-118">The data source object contains the connection string that is used to connect to the underlying data source.</span></span> <span data-ttu-id="90cd7-119">此连接字符串可以指定以下内容之一：</span><span class="sxs-lookup"><span data-stu-id="90cd7-119">This connection string can specify one of the following:</span></span>  
  
-   <span data-ttu-id="90cd7-120">**指定用户名和密码**</span><span class="sxs-lookup"><span data-stu-id="90cd7-120">**Specify a user name and password**</span></span>  
  
     <span data-ttu-id="90cd7-121">如果数据源对象使用的连接字符串指定了用户名和密码，则可以创建多个数据源对象，每个对象都有不同的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="90cd7-121">If the connection string that a data source object uses specifies a user name and password, you may want to create multiple data source objects, each with different user accounts.</span></span> <span data-ttu-id="90cd7-122">通过创建多个数据源对象，可允许用户访问某些数据源对象，并可阻止用户访问其他数据源对象。</span><span class="sxs-lookup"><span data-stu-id="90cd7-122">Creating multiple data source objects lets users access certain data source objects and prevents those users from accessing other data source objects.</span></span> <span data-ttu-id="90cd7-123">其他这些数据源对象可由 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 自身使用，用于处理对象（如多维数据集和挖掘模型）。</span><span class="sxs-lookup"><span data-stu-id="90cd7-123">These other data source objects can be used by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] itself for processing objects, such as cubes and mining models.</span></span>  
  
-   <span data-ttu-id="90cd7-124">**指定 Windows 身份验证**</span><span class="sxs-lookup"><span data-stu-id="90cd7-124">**Specify Windows Authentication**</span></span>  
  
     <span data-ttu-id="90cd7-125">如果数据源对象使用的连接字符串指定了 Windows 身份验证，则 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 必须能够模拟客户端。</span><span class="sxs-lookup"><span data-stu-id="90cd7-125">If the connection string that a data source object uses specifies Windows Authentication, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] must be able to impersonate the client.</span></span> <span data-ttu-id="90cd7-126">如果数据源在远程计算机上，两台计算机必须使用 Kerberos 身份验证建立模拟信任，否则查询一般会失败。</span><span class="sxs-lookup"><span data-stu-id="90cd7-126">If the data source is on a remote computer, the two computers must be trusted for impersonation by using Kerberos authentication, or the query will typically fail.</span></span> <span data-ttu-id="90cd7-127">有关详细信息，请参阅 [Configure Analysis Services for Kerberos constrained delegation](../instances/configure-analysis-services-for-kerberos-constrained-delegation.md) 。</span><span class="sxs-lookup"><span data-stu-id="90cd7-127">See [Configure Analysis Services for Kerberos constrained delegation](../instances/configure-analysis-services-for-kerberos-constrained-delegation.md) for more information.</span></span>  
  
     <span data-ttu-id="90cd7-128">如果客户端不允许模拟（通过 OLE DB 和其他客户端组件中的“Impersonation Level”属性），则 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 将尝试匿名连接到基础数据源（大多数数据源不接受匿名连接）。</span><span class="sxs-lookup"><span data-stu-id="90cd7-128">If the client does not allow for impersonation (through the Impersonation Level property in OLE DB and other client components), [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will try to make an anonymous connection to the underlying data source.</span></span> <span data-ttu-id="90cd7-129">糯米连接到远程数据源很少成功，这是因为大多数数据源不接受匿名连接。）</span><span class="sxs-lookup"><span data-stu-id="90cd7-129">Anonymous connections to remote data sources rarely succeed, as most data sources do not accept anonymous connections).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90cd7-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="90cd7-130">See Also</span></span>  
 <span data-ttu-id="90cd7-131">[多维模型中的数据源](data-sources-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="90cd7-131">[Data Sources in Multidimensional Models](data-sources-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="90cd7-132">[连接字符串属性 &#40;Analysis Services&#41;](../instances/connection-string-properties-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="90cd7-132">[Connection String Properties &#40;Analysis Services&#41;](../instances/connection-string-properties-analysis-services.md) </span></span>  
 <span data-ttu-id="90cd7-133">[Analysis Services 支持的身份验证方法](../instances/authentication-methodologies-supported-by-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="90cd7-133">[Authentication methodologies supported by Analysis Services](../instances/authentication-methodologies-supported-by-analysis-services.md) </span></span>  
 <span data-ttu-id="90cd7-134">[授予对维度数据的自定义访问 &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="90cd7-134">[Grant custom access to dimension data &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md) </span></span>  
 <span data-ttu-id="90cd7-135">[&#40;Analysis Services 授予多维数据集或模型权限&#41;](grant-cube-or-model-permissions-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="90cd7-135">[Grant cube or model permissions &#40;Analysis Services&#41;](grant-cube-or-model-permissions-analysis-services.md) </span></span>  
 [<span data-ttu-id="90cd7-136">授予单元数据的自定义访问权限 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="90cd7-136">Grant custom access to cell data &#40;Analysis Services&#41;</span></span>](grant-custom-access-to-cell-data-analysis-services.md)  
  
  
