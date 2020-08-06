---
title: 数据库属性（“事务日志传送”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.logshipping.f1
ms.assetid: 72c4e539-fe11-4d57-b977-65b418d5916f
author: stevestein
ms.author: sstein
ms.openlocfilehash: dd36b3bc56bcd48c53871c9bc1e334d72c80ac78
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693951"
---
# <a name="database-properties-transaction-log-shipping-page"></a><span data-ttu-id="db97e-102">数据库属性（“事务日志传送”页）</span><span class="sxs-lookup"><span data-stu-id="db97e-102">Database Properties (Transaction Log Shipping Page)</span></span>
  <span data-ttu-id="db97e-103">使用此页可以配置和修改数据库的日志传送属性。</span><span class="sxs-lookup"><span data-stu-id="db97e-103">Use this page to configure and modify the properties of log shipping for a database.</span></span>  
  
 <span data-ttu-id="db97e-104">有关日志传送概念的说明，请参阅 [关于日志传送 (SQL Server)](../../database-engine/log-shipping/about-log-shipping-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="db97e-104">For an explanation of log shipping concepts, see [About Log Shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="db97e-105">选项</span><span class="sxs-lookup"><span data-stu-id="db97e-105">Options</span></span>  
 <span data-ttu-id="db97e-106">**将此数据库启用为日志传送配置中的主数据库**</span><span class="sxs-lookup"><span data-stu-id="db97e-106">**Enable this as a primary database in a log shipping configuration**</span></span>  
 <span data-ttu-id="db97e-107">将此数据库启用为日志传送的主数据库。</span><span class="sxs-lookup"><span data-stu-id="db97e-107">Enables this database as a log shipping primary database.</span></span> <span data-ttu-id="db97e-108">请选中该选项，然后再配置此页上的剩余选项。</span><span class="sxs-lookup"><span data-stu-id="db97e-108">Select it and then configure the remaining options on this page.</span></span> <span data-ttu-id="db97e-109">如果清除此复选框，则将删除此数据库的日志传送配置。</span><span class="sxs-lookup"><span data-stu-id="db97e-109">If you clear this check box, the log shipping configuration will be dropped for this database.</span></span>  
  
 <span data-ttu-id="db97e-110">**备份设置**</span><span class="sxs-lookup"><span data-stu-id="db97e-110">**Backup Settings**</span></span>  
 <span data-ttu-id="db97e-111">单击“备份设置”可以配置备份计划、位置、警报和存档参数。</span><span class="sxs-lookup"><span data-stu-id="db97e-111">Click **Backup Settings** to configure backup schedule, location, alert, and archiving parameters.</span></span>  
  
 <span data-ttu-id="db97e-112">**备份计划**</span><span class="sxs-lookup"><span data-stu-id="db97e-112">**Backup schedule**</span></span>  
 <span data-ttu-id="db97e-113">显示当前为主数据库选择的备份计划。</span><span class="sxs-lookup"><span data-stu-id="db97e-113">Shows the currently selected backup schedule for the primary database.</span></span> <span data-ttu-id="db97e-114">单击 **“备份设置”** 可修改这些设置。</span><span class="sxs-lookup"><span data-stu-id="db97e-114">Click **Backup Settings** to modify these settings.</span></span>  
  
 <span data-ttu-id="db97e-115">**上次备份创建时间**</span><span class="sxs-lookup"><span data-stu-id="db97e-115">**Last backup created**</span></span>  
 <span data-ttu-id="db97e-116">指示上次对主数据库进行事务日志备份的时间和日期。</span><span class="sxs-lookup"><span data-stu-id="db97e-116">Indicates the time and date of the last transaction log backup of the primary database.</span></span>  
  
 <span data-ttu-id="db97e-117">**辅助服务器实例和数据库**</span><span class="sxs-lookup"><span data-stu-id="db97e-117">**Secondary server instances and databases**</span></span>  
 <span data-ttu-id="db97e-118">列出当前为此主数据库配置的辅助服务器和数据库。</span><span class="sxs-lookup"><span data-stu-id="db97e-118">Lists the currently configured secondary servers and databases for this primary database.</span></span> <span data-ttu-id="db97e-119">突出显示某个数据库，然后单击 **“...”** 可以修改与该辅助数据库相关联的参数。</span><span class="sxs-lookup"><span data-stu-id="db97e-119">Highlight a database, and then click **...** to modify the parameters associated with that secondary database.</span></span>  
  
 <span data-ttu-id="db97e-120">**添加**</span><span class="sxs-lookup"><span data-stu-id="db97e-120">**Add**</span></span>  
 <span data-ttu-id="db97e-121">单击“添加”可以向此主数据库的日志传送配置中添加辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="db97e-121">Click **Add** to add a secondary database to the log shipping configuration for this primary database.</span></span>  
  
 <span data-ttu-id="db97e-122">**删除**</span><span class="sxs-lookup"><span data-stu-id="db97e-122">**Remove**</span></span>  
 <span data-ttu-id="db97e-123">从此日志传送配置中删除所选数据库。</span><span class="sxs-lookup"><span data-stu-id="db97e-123">Removes a selected database from this log shipping configuration.</span></span> <span data-ttu-id="db97e-124">首先选择该数据库，再单击 **“删除”** 。</span><span class="sxs-lookup"><span data-stu-id="db97e-124">Select the database first and then click **Remove**.</span></span>  
  
 <span data-ttu-id="db97e-125">**使用监视服务器实例**</span><span class="sxs-lookup"><span data-stu-id="db97e-125">**Use a monitor server instance**</span></span>  
 <span data-ttu-id="db97e-126">为此日志传送配置设置监视服务器实例。</span><span class="sxs-lookup"><span data-stu-id="db97e-126">Sets up a monitor server instance for this log shipping configuration.</span></span> <span data-ttu-id="db97e-127">选中 **“使用监视服务器实例”** 复选框，再单击 **“设置”** 可以指定监视服务器实例。</span><span class="sxs-lookup"><span data-stu-id="db97e-127">Select the **Use a monitor server instance** check box and then click **Settings** to specify the monitor server instance.</span></span>  
  
 <span data-ttu-id="db97e-128">**监视服务器实例**</span><span class="sxs-lookup"><span data-stu-id="db97e-128">**Monitor server instance**</span></span>  
 <span data-ttu-id="db97e-129">指示当前为该日志传送配置设置的监视服务器实例。</span><span class="sxs-lookup"><span data-stu-id="db97e-129">Indicates the currently configured monitor server instance for this log shipping configuration.</span></span>  
  
 <span data-ttu-id="db97e-130">**设置**</span><span class="sxs-lookup"><span data-stu-id="db97e-130">**Settings**</span></span>  
 <span data-ttu-id="db97e-131">为日志传送配置设置监视服务器实例。</span><span class="sxs-lookup"><span data-stu-id="db97e-131">Configures the monitor server instance for a log shipping configuration.</span></span> <span data-ttu-id="db97e-132">单击 **“设置”** 可以配置此监视服务器实例。</span><span class="sxs-lookup"><span data-stu-id="db97e-132">Click **Settings** to configure this monitor server instance.</span></span>  
  
 <span data-ttu-id="db97e-133">**编写配置脚本**</span><span class="sxs-lookup"><span data-stu-id="db97e-133">**Script Configuration**</span></span>  
 <span data-ttu-id="db97e-134">生成一个脚本，使用所选参数配置日志传送功能。</span><span class="sxs-lookup"><span data-stu-id="db97e-134">Generates a script for configuring log shipping with the parameters you have selected.</span></span> <span data-ttu-id="db97e-135">单击 **“编写配置脚本”** ，然后为该脚本选择输出目标。</span><span class="sxs-lookup"><span data-stu-id="db97e-135">Click **Script Configuration**, and then choose an output destination for the script.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="db97e-136">在编写辅助数据库的脚本设置之前，必须调用 **“辅助数据库设置”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="db97e-136">Before scripting settings for a secondary database, you must invoke the **Secondary Database Settings** dialog box.</span></span> <span data-ttu-id="db97e-137">通过调用该对话框，用户可以连接到辅助服务器，并且可以检索生成该脚本所需的辅助数据库的当前设置。</span><span class="sxs-lookup"><span data-stu-id="db97e-137">Invoking this dialog box connects you to the secondary server and retrieves the current settings of the secondary database that are needed to generate the script.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db97e-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="db97e-138">See Also</span></span>  
 <span data-ttu-id="db97e-139">[日志传送存储过程 (Transact-SQL)](/sql/relational-databases/system-stored-procedures/log-shipping-stored-procedures-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="db97e-139">[Log Shipping Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/log-shipping-stored-procedures-transact-sql) </span></span>  
 [<span data-ttu-id="db97e-140">日志传送表 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="db97e-140">Log Shipping Tables &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-tables/log-shipping-tables-transact-sql)  
  
  
