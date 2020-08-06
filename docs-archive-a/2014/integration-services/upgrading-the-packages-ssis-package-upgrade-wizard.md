---
title: " (SSIS 包升级向导升级包) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.is.upgradewizard.upgradingpackage.f1
ms.assetid: cdb842e3-2e59-4ede-b127-be4fde46875c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d13228dabc1566b592733da4afd8ebde3671ee0d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578933"
---
# <a name="upgrading-the-packages-ssis-package-upgrade-wizard"></a><span data-ttu-id="d4855-102">升级包（SSIS 包升级向导）</span><span class="sxs-lookup"><span data-stu-id="d4855-102">Upgrading the Packages (SSIS Package Upgrade Wizard)</span></span>
  <span data-ttu-id="d4855-103">可以使用 **“升级包”** 页查看包升级的进度以及中断升级过程。</span><span class="sxs-lookup"><span data-stu-id="d4855-103">Use the **Upgrading the Packages** page to view the progress of package upgrade and to interrupt the upgrade process.</span></span> <span data-ttu-id="d4855-104">[!INCLUDE[ssIS](../includes/ssis-md.md)] 包升级向导会逐一升级所选包。</span><span class="sxs-lookup"><span data-stu-id="d4855-104">The [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Upgrade Wizard upgrades the selected packages one by one.</span></span>  
  
 <span data-ttu-id="d4855-105">**查看保存到 SQL Server 数据库或包存储区的升级包**</span><span class="sxs-lookup"><span data-stu-id="d4855-105">**To view upgraded packages that were saved to a SQL Server database or to the package store**</span></span>  
  
-   <span data-ttu-id="d4855-106">在 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]中的对象资源管理器中，连接到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]的本地实例，然后展开 **“已存储的包”** 节点查看已升级的包。</span><span class="sxs-lookup"><span data-stu-id="d4855-106">In [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], in Object Explorer, connect to the local instance of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], and then expand the **Stored Packages** node to see the packages that were upgraded.</span></span>  
  
 <span data-ttu-id="d4855-107">**查看通过 SQL Server Data Tools 升级的升级包**</span><span class="sxs-lookup"><span data-stu-id="d4855-107">**To view upgraded packages that were upgraded from SQL Server Data Tools**</span></span>  
  
-   <span data-ttu-id="d4855-108">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中的解决方案资源管理器中，打开 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目，然后展开 **“SSIS 包”** 节点查看已升级的包。</span><span class="sxs-lookup"><span data-stu-id="d4855-108">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], in Solution Explorer, open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, and then expand the **SSIS Packages** node to see the upgraded packages.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d4855-109">选项</span><span class="sxs-lookup"><span data-stu-id="d4855-109">Options</span></span>  
 <span data-ttu-id="d4855-110">**消息窗格**</span><span class="sxs-lookup"><span data-stu-id="d4855-110">**Message pane**</span></span>  
 <span data-ttu-id="d4855-111">在升级过程中显示进度消息和摘要信息。</span><span class="sxs-lookup"><span data-stu-id="d4855-111">Displays progress messages and summary information during the upgrade process.</span></span>  
  
 <span data-ttu-id="d4855-112">**Action**</span><span class="sxs-lookup"><span data-stu-id="d4855-112">**Action**</span></span>  
 <span data-ttu-id="d4855-113">查看升级中的操作。</span><span class="sxs-lookup"><span data-stu-id="d4855-113">View the actions in the upgrade.</span></span>  
  
 <span data-ttu-id="d4855-114">**Status**</span><span class="sxs-lookup"><span data-stu-id="d4855-114">**Status**</span></span>  
 <span data-ttu-id="d4855-115">查看每个操作的结果。</span><span class="sxs-lookup"><span data-stu-id="d4855-115">View the result of each action.</span></span>  
  
 <span data-ttu-id="d4855-116">**Message**</span><span class="sxs-lookup"><span data-stu-id="d4855-116">**Message**</span></span>  
 <span data-ttu-id="d4855-117">查看每个操作生成的错误消息。</span><span class="sxs-lookup"><span data-stu-id="d4855-117">View the error messages that each action generates.</span></span>  
  
 <span data-ttu-id="d4855-118">**Stop**</span><span class="sxs-lookup"><span data-stu-id="d4855-118">**Stop**</span></span>  
 <span data-ttu-id="d4855-119">停止包升级。</span><span class="sxs-lookup"><span data-stu-id="d4855-119">Stop the package upgrade.</span></span>  
  
 <span data-ttu-id="d4855-120">**Report**</span><span class="sxs-lookup"><span data-stu-id="d4855-120">**Report**</span></span>  
 <span data-ttu-id="d4855-121">选择希望如何处理包含包升级结果的报告：</span><span class="sxs-lookup"><span data-stu-id="d4855-121">Select what you want to do with the report that contains the results of the package upgrade:</span></span>  
  
-   <span data-ttu-id="d4855-122">联机查看报告。</span><span class="sxs-lookup"><span data-stu-id="d4855-122">View the report online.</span></span>  
  
-   <span data-ttu-id="d4855-123">将报告保存到文件中。</span><span class="sxs-lookup"><span data-stu-id="d4855-123">Save the report to a file.</span></span>  
  
-   <span data-ttu-id="d4855-124">将报告复制到剪贴板</span><span class="sxs-lookup"><span data-stu-id="d4855-124">Copy the report to the Clipboard</span></span>  
  
-   <span data-ttu-id="d4855-125">将报告作为电子邮件发送。</span><span class="sxs-lookup"><span data-stu-id="d4855-125">Send the report as an e-mail message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4855-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d4855-126">See Also</span></span>  
 [<span data-ttu-id="d4855-127">升级 Integration Services 包</span><span class="sxs-lookup"><span data-stu-id="d4855-127">Upgrade Integration Services Packages</span></span>](install-windows/upgrade-integration-services-packages.md)  
  
  
