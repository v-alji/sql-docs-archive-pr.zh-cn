---
title: 配置 two digit year cutoff 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- two digit year cutoff option
- four-digit years [SQL Server]
ms.assetid: d94e81b6-f2e6-47ef-b497-ec3d827a1646
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c31c1d87c8b743132dd90d495f73ef711dc1f813
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580359"
---
# <a name="configure-the-two-digit-year-cutoff-server-configuration-option"></a><span data-ttu-id="e3b04-102">配置两位数年份截止服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="e3b04-102">Configure the two digit year cutoff Server Configuration Option</span></span>
  <span data-ttu-id="e3b04-103">本主题说明了如何使用 **或** 在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中配置 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] “两位数年份截止” [!INCLUDE[tsql](../../includes/tsql-md.md)]服务器配置选项。</span><span class="sxs-lookup"><span data-stu-id="e3b04-103">This topic describes how to configure the **two digit year cutoff** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="e3b04-104">**“两位数年份截止”** 选项从 1753 到 9999 之间指定一个整数来表示缩略形式的年份，以将两位数的年份解释为四位数的年份。</span><span class="sxs-lookup"><span data-stu-id="e3b04-104">The **two digit year cutoff** option specifies an integer from 1753 to 9999 that represents the cutoff year for interpreting two-digit years as four-digit years.</span></span> <span data-ttu-id="e3b04-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 默认的时间范围是 1950-2049，表示截止年份为 2049。</span><span class="sxs-lookup"><span data-stu-id="e3b04-105">The default time span for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is 1950-2049, which represents a cutoff year of 2049.</span></span> <span data-ttu-id="e3b04-106">这说明 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将两位数年份 49 解释为 2049 年，将两位数年份 50 解释为 1950 年，而将两位数年份 99 解释为 1999 年。</span><span class="sxs-lookup"><span data-stu-id="e3b04-106">This means that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interprets a two-digit year of 49 as 2049, a two-digit year of 50 as 1950, and a two-digit year of 99 as 1999.</span></span> <span data-ttu-id="e3b04-107">若要维护向后兼容性，请将设置保持为默认值。</span><span class="sxs-lookup"><span data-stu-id="e3b04-107">To maintain backward compatibility, leave the setting at the default value.</span></span>  
  
 <span data-ttu-id="e3b04-108">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="e3b04-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e3b04-109">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="e3b04-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e3b04-110">建议</span><span class="sxs-lookup"><span data-stu-id="e3b04-110">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="e3b04-111">安全性</span><span class="sxs-lookup"><span data-stu-id="e3b04-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e3b04-112">**若要配置两位数年份截止选项，请使用：**</span><span class="sxs-lookup"><span data-stu-id="e3b04-112">**To configure the two digit year cutoff option, using:**</span></span>  
  
     [<span data-ttu-id="e3b04-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e3b04-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="e3b04-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e3b04-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="e3b04-115">**跟进：** [在配置“两位数年份截止”选项之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="e3b04-115">**Follow Up:**  [After you configure the two digit year cutoff option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e3b04-116">开始之前</span><span class="sxs-lookup"><span data-stu-id="e3b04-116">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="e3b04-117">建议</span><span class="sxs-lookup"><span data-stu-id="e3b04-117">Recommendations</span></span>  
  
-   <span data-ttu-id="e3b04-118">此选项是一个高级选项，仅应由有经验的数据库管理员或认证的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技术人员更改。</span><span class="sxs-lookup"><span data-stu-id="e3b04-118">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="e3b04-119">OLE 自动化对象使用 2030 作为两位数年份截止。</span><span class="sxs-lookup"><span data-stu-id="e3b04-119">OLE Automation objects use 2030 as the two-digit cutoff year.</span></span> <span data-ttu-id="e3b04-120">可以使用 **“两位数年份截止”** 选项使 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和客户端应用程序之间的日期值保持一致。</span><span class="sxs-lookup"><span data-stu-id="e3b04-120">You can use the **two digit year cutoff** option to provide consistency in date values between [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and client applications.</span></span> <span data-ttu-id="e3b04-121">然而，为了在使用日期时避免含糊歧义，请在日期中使用 4 位数字的年份。</span><span class="sxs-lookup"><span data-stu-id="e3b04-121">However, to avoid ambiguity with dates, use four-digit years in your data.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e3b04-122">Security</span><span class="sxs-lookup"><span data-stu-id="e3b04-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e3b04-123">权限</span><span class="sxs-lookup"><span data-stu-id="e3b04-123">Permissions</span></span>  
 <span data-ttu-id="e3b04-124">默认情况下，所有用户都具备不带参数或仅带第一个参数的 **sp_configure** 的执行权限。</span><span class="sxs-lookup"><span data-stu-id="e3b04-124">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="e3b04-125">若要执行带两个参数的 **sp_configure** 以更改配置选项或运行 RECONFIGURE 语句，则用户必须具备 ALTER SETTINGS 服务器级别的权限。</span><span class="sxs-lookup"><span data-stu-id="e3b04-125">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="e3b04-126">ALTER SETTINGS 权限由 **sysadmin** 和 **serveradmin** 固定服务器角色隐式持有。</span><span class="sxs-lookup"><span data-stu-id="e3b04-126">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e3b04-127">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e3b04-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-two-digit-year-cutoff-option"></a><span data-ttu-id="e3b04-128">配置两位数年份截止选项</span><span class="sxs-lookup"><span data-stu-id="e3b04-128">To configure the two digit year cutoff option</span></span>  
  
1.  <span data-ttu-id="e3b04-129">在对象资源管理器中，右键单击服务器并选择 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="e3b04-129">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="e3b04-130">单击 **“杂项服务器设置”** 节点。</span><span class="sxs-lookup"><span data-stu-id="e3b04-130">Click the **Misc server settings** node.</span></span>  
  
3.  <span data-ttu-id="e3b04-131">在 **“两位数年份支持”** 下的 **“在输入两位数的年份时**， **将其解释为介于下面范围内的年份”** 框中，键入或选择作为时间范围的结束年份的值。</span><span class="sxs-lookup"><span data-stu-id="e3b04-131">Under **Two digit year support**, in the **When a two digit year is entered**, **interpret it as a year between** box, type or select a value that is the ending year of the time span.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e3b04-132">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e3b04-132">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-two-digit-year-cutoff-option"></a><span data-ttu-id="e3b04-133">配置两位数年份截止选项</span><span class="sxs-lookup"><span data-stu-id="e3b04-133">To configure the two digit year cutoff option</span></span>  
  
1.  <span data-ttu-id="e3b04-134">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e3b04-134">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e3b04-135">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="e3b04-135">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e3b04-136">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="e3b04-136">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="e3b04-137">此示例说明如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 将 `two digit year cutoff` 选项的值设置为 `2030`。</span><span class="sxs-lookup"><span data-stu-id="e3b04-137">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `two digit year cutoff` option to `2030`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'two digit year cutoff', 2030 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="e3b04-138">有关详细信息，请参阅 [服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md)版本的组合自动配置的最大工作线程数。</span><span class="sxs-lookup"><span data-stu-id="e3b04-138">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-two-digit-year-cutoff-option"></a><a name="FollowUp"></a> <span data-ttu-id="e3b04-139">跟进：在配置“两位数年份截止”选项之后</span><span class="sxs-lookup"><span data-stu-id="e3b04-139">Follow Up: After you configure the two digit year cutoff option</span></span>  
 <span data-ttu-id="e3b04-140">该设置将立即生效，无需重新启动服务器。</span><span class="sxs-lookup"><span data-stu-id="e3b04-140">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3b04-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e3b04-141">See Also</span></span>  
 <span data-ttu-id="e3b04-142">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e3b04-142">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="e3b04-143">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e3b04-143">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="e3b04-144">RECONFIGURE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e3b04-144">RECONFIGURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
