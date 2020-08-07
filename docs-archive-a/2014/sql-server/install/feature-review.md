---
title: 功能评审 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 1e2b22b8-5811-4f50-875b-685f3ddbd1ee
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 8e258ac763d8c5e057f8dcdb6f740aacb4fef1c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588879"
---
# <a name="feature-review"></a><span data-ttu-id="c4286-102">查看功能</span><span class="sxs-lookup"><span data-stu-id="c4286-102">Feature Review</span></span>
  <span data-ttu-id="c4286-103">“查看功能”页是已准备好并且将在完成映像步骤结束时配置并完成的功能的只读列表。</span><span class="sxs-lookup"><span data-stu-id="c4286-103">The Feature Review page is a read-only list of features that have been prepared and will be configured and completed at the end of the complete image step.</span></span> <span data-ttu-id="c4286-104">该功能列表在准备映像步骤中选择，并且在完成映像步骤中无法修改。</span><span class="sxs-lookup"><span data-stu-id="c4286-104">The feature list is selected during the prepare image step and cannot be modified during complete image step.</span></span> <span data-ttu-id="c4286-105">除了显示的功能外，已准备实例还包括 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Writer 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client。</span><span class="sxs-lookup"><span data-stu-id="c4286-105">In addition to the features displayed, a prepared instance also includes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Writer, and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
 <span data-ttu-id="c4286-106">在完成了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的已准备实例的配置后，可以添加在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的已准备实例中未包括的其他功能。</span><span class="sxs-lookup"><span data-stu-id="c4286-106">You can add other features not included in the prepared instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance after you have completed the configuration of the prepared instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="c4286-107">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="c4286-107">UI element list</span></span>  
  
|<span data-ttu-id="c4286-108">组件组</span><span class="sxs-lookup"><span data-stu-id="c4286-108">Component Group</span></span>|<span data-ttu-id="c4286-109">组件和功能</span><span class="sxs-lookup"><span data-stu-id="c4286-109">Components and features</span></span>|  
|---------------------|-----------------------------|  
|[!INCLUDE[ssDE](../../includes/ssde-md.md)] <span data-ttu-id="c4286-110">服务</span><span class="sxs-lookup"><span data-stu-id="c4286-110">Services</span></span>|<span data-ttu-id="c4286-111">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 是用于存储、处理和保护数据的核心服务。</span><span class="sxs-lookup"><span data-stu-id="c4286-111">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] is the core service for storing, processing, and securing data.</span></span> <span data-ttu-id="c4286-112">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]中包括以下组件：</span><span class="sxs-lookup"><span data-stu-id="c4286-112">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] includes the following components:</span></span><br /><br /> <span data-ttu-id="c4286-113">复制：（可选）复制是一组技术，用于将数据和数据库对象从一个数据库复制和分发到另一个数据库，然后在数据库之间进行同步以维护一致性。</span><span class="sxs-lookup"><span data-stu-id="c4286-113">Replication: (Optional) Replication is a set of technologies for copying and distributing data and database objects from one database to another and then synchronizing between databases to maintain consistency.</span></span><br /><br /> <span data-ttu-id="c4286-114">全文搜索：（可选）全文搜索提供了针对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表中基于纯字符的数据发出全文查询的功能。</span><span class="sxs-lookup"><span data-stu-id="c4286-114">Full-Text Search: (Optional) Full-Text Search provides functionality to issue full-text queries against plain character-based data in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables.</span></span><br /><br /> [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)]<span data-ttu-id="c4286-115">（可选）：[!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) 是一种数据清理解决方案，使您能够发现您的数据源中不一致和不正确的数据，并提供自动且交互式方法来清理数据。</span><span class="sxs-lookup"><span data-stu-id="c4286-115">(Optional): [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) is a data-cleansing solution that enables you to discover inconsistent and incorrect data in your data source, and provides automated and interactive ways to cleanse the data.</span></span>|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="c4286-116">包括用于创建、管理和部署表格报表、矩阵报表、图形报表以及自由格式报表的服务器和客户端组件。</span><span class="sxs-lookup"><span data-stu-id="c4286-116">includes server and client components for creating, managing, and deploying tabular, matrix, graphical, and free-form reports.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="c4286-117">还是一个可用于开发报表应用程序的可扩展平台。</span><span class="sxs-lookup"><span data-stu-id="c4286-117">is also an extensible platform that you can use to develop report applications.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c4286-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c4286-118">See Also</span></span>  
 [<span data-ttu-id="c4286-119">使用 SysPrep 安装 SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="c4286-119">Install SQL Server 2014 Using SysPrep</span></span>](../../database-engine/install-windows/install-sql-server-using-sysprep.md)  
  
  
