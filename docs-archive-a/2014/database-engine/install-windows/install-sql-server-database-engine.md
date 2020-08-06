---
title: 关于 SQL Server 数据库引擎 |Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], installing
ms.assetid: d0876e7f-aa52-4dd7-bd5c-029e2ffded5f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 93e3d7a749fe6be47cc84d43509a6f378476b2ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690026"
---
# <a name="about-the-sql-server-database-engine"></a><span data-ttu-id="14df1-102">关于 SQL Server 数据库引擎</span><span class="sxs-lookup"><span data-stu-id="14df1-102">About the SQL Server Database Engine</span></span>
  <span data-ttu-id="14df1-103">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件是用于存储、处理数据和保证数据安全的核心服务。</span><span class="sxs-lookup"><span data-stu-id="14df1-103">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] component of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is the core service for storing, processing, and securing data.</span></span> <span data-ttu-id="14df1-104">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 提供受控的访问和快速事务处理，以满足企业中要求极高、大量使用数据的应用程序的要求。</span><span class="sxs-lookup"><span data-stu-id="14df1-104">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] provides controlled access and rapid transaction processing to meet the requirements of the most demanding data consuming applications in your enterprise.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="14df1-105">支持在同一台计算机上最多存在 50 个 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="14df1-105">supports up to 50 instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] on a single computer.</span></span> <span data-ttu-id="14df1-106">若要创建典型 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装，请参阅安装[向导中的安装 SQL Server 2014 &#40;安装&#41;](install-sql-server-from-the-installation-wizard-setup.md)。</span><span class="sxs-lookup"><span data-stu-id="14df1-106">To create a typical [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation, see [Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](install-sql-server-from-the-installation-wizard-setup.md).</span></span>  
  
 <span data-ttu-id="14df1-107">**重要提示** 对于本地安装，必须以管理员身份运行安装程序。</span><span class="sxs-lookup"><span data-stu-id="14df1-107">**Important** For local installations, you must run Setup as an administrator.</span></span> <span data-ttu-id="14df1-108">如果从远程共享安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，则必须使用对远程共享具有读取和执行权限的域帐户。</span><span class="sxs-lookup"><span data-stu-id="14df1-108">If you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from a remote share, you must use a domain account that has read and execute permissions on the remote share.</span></span>  
  
 <span data-ttu-id="14df1-109">在 **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装向导的“要安装的组件”页上选择** 数据库引擎” [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 时，将安装下列功能：</span><span class="sxs-lookup"><span data-stu-id="14df1-109">The following features are installed when you select **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database Engine** on the Components to Install page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard:</span></span>  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   <span data-ttu-id="14df1-110">复制 - 是一个可选组件</span><span class="sxs-lookup"><span data-stu-id="14df1-110">Replication - is an optional component</span></span>  
  
-   <span data-ttu-id="14df1-111">全文搜索 - 是一个可选组件</span><span class="sxs-lookup"><span data-stu-id="14df1-111">Full-Text Search - is an optional component</span></span>  
  
-   <span data-ttu-id="14df1-112">Data Quality Services - 一个可选组件</span><span class="sxs-lookup"><span data-stu-id="14df1-112">Data Quality Services - is an optional component</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="14df1-113">在此版本中，在安装程序中选中“Data Quality Services”复选框不会安装 Data Quality Services (DQS) 服务器。</span><span class="sxs-lookup"><span data-stu-id="14df1-113">In this release, selecting the **Data Quality Services** check box in setup does not install the Data Quality Services (DQS) server.</span></span> <span data-ttu-id="14df1-114">您必须执行其他安装后步骤以安装 DQS 服务器。</span><span class="sxs-lookup"><span data-stu-id="14df1-114">You will have to perform additional steps post installation to install DQS server.</span></span> <span data-ttu-id="14df1-115">有关详细信息，请参阅 [Install Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md)。</span><span class="sxs-lookup"><span data-stu-id="14df1-115">For more information, see [Install Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md).</span></span>  
  
 <span data-ttu-id="14df1-116">下列附加功能是许多典型用户应用场景的可选项：</span><span class="sxs-lookup"><span data-stu-id="14df1-116">The following additional features are options for many typical user scenarios:</span></span>  
  
-   <span data-ttu-id="14df1-117">数据质量客户端</span><span class="sxs-lookup"><span data-stu-id="14df1-117">Data Quality Client</span></span>  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
-   <span data-ttu-id="14df1-118">连接组件</span><span class="sxs-lookup"><span data-stu-id="14df1-118">Connectivity components</span></span>  
  
-   <span data-ttu-id="14df1-119">编程模型</span><span class="sxs-lookup"><span data-stu-id="14df1-119">Programming models</span></span>  
  
-   <span data-ttu-id="14df1-120">管理工具</span><span class="sxs-lookup"><span data-stu-id="14df1-120">Management tools</span></span>  
  
-   [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]  
  
-   <span data-ttu-id="14df1-121">文档组件</span><span class="sxs-lookup"><span data-stu-id="14df1-121">Documentation components</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="14df1-122">默认情况下，不会将示例数据库和示例代码作为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装程序的一部分进行安装。</span><span class="sxs-lookup"><span data-stu-id="14df1-122">By default, sample databases and sample code are not installed as part of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup.</span></span> <span data-ttu-id="14df1-123">若要安装示例数据库和示例代码，请参阅 [CodePlex 网站](https://go.microsoft.com/fwlink/?LinkId=87843)。</span><span class="sxs-lookup"><span data-stu-id="14df1-123">To install sample databases and sample code, see the [CodePlex Web site](https://go.microsoft.com/fwlink/?LinkId=87843).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14df1-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="14df1-124">See Also</span></span>  
 <span data-ttu-id="14df1-125">[SQL Server 2014 的各个版本支持的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span><span class="sxs-lookup"><span data-stu-id="14df1-125">[Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span></span>  
 <span data-ttu-id="14df1-126">[SQL Server 2014 的版本和组件](../../sql-server/editions-and-components-of-sql-server-2016.md) </span><span class="sxs-lookup"><span data-stu-id="14df1-126">[Editions and Components of SQL Server 2014](../../sql-server/editions-and-components-of-sql-server-2016.md) </span></span>  
 <span data-ttu-id="14df1-127">[计划 SQL Server 安装](../../sql-server/install/planning-a-sql-server-installation.md) </span><span class="sxs-lookup"><span data-stu-id="14df1-127">[Planning a SQL Server Installation](../../sql-server/install/planning-a-sql-server-installation.md) </span></span>  
 <span data-ttu-id="14df1-128">[高可用性解决方案 (SQL Server)](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="14df1-128">[High Availability Solutions &#40;SQL Server&#41;](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md) </span></span>  
 [<span data-ttu-id="14df1-129">使用安装向导 &#40;安装程序升级到 SQL Server 2014&#41;</span><span class="sxs-lookup"><span data-stu-id="14df1-129">Upgrade to SQL Server 2014 Using the Installation Wizard &#40;Setup&#41;</span></span>](upgrade-sql-server-using-the-installation-wizard-setup.md)  
  
  
