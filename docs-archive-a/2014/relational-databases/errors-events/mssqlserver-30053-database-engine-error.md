---
title: MSSQLSERVER_30053 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
ms.assetid: 8ad23889-e243-4bd7-bc3e-150403399d89
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 02d6262f93ef3dbbc9834053f864046b4dca30f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586735"
---
# <a name="mssqlserver_30053"></a><span data-ttu-id="7ac37-102">MSSQLSERVER_30053</span><span class="sxs-lookup"><span data-stu-id="7ac37-102">MSSQLSERVER_30053</span></span>
    
## <a name="details"></a><span data-ttu-id="7ac37-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="7ac37-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7ac37-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="7ac37-104">Product Name</span></span>|<span data-ttu-id="7ac37-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="7ac37-105">SQL Server</span></span>|  
|<span data-ttu-id="7ac37-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="7ac37-106">Event ID</span></span>|<span data-ttu-id="7ac37-107">30053</span><span class="sxs-lookup"><span data-stu-id="7ac37-107">30053</span></span>|  
|<span data-ttu-id="7ac37-108">事件源</span><span class="sxs-lookup"><span data-stu-id="7ac37-108">Event Source</span></span>|<span data-ttu-id="7ac37-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="7ac37-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="7ac37-110">组件</span><span class="sxs-lookup"><span data-stu-id="7ac37-110">Component</span></span>|<span data-ttu-id="7ac37-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="7ac37-111">SQLEngine</span></span>|  
|<span data-ttu-id="7ac37-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="7ac37-112">Symbolic Name</span></span>|<span data-ttu-id="7ac37-113">FTXT_QUERY_E_WORDBREAKINGTIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7ac37-113">FTXT_QUERY_E_WORDBREAKINGTIMEOUT</span></span>|  
|<span data-ttu-id="7ac37-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="7ac37-114">Message Text</span></span>|<span data-ttu-id="7ac37-115">全文查询字符串出现断字超时。</span><span class="sxs-lookup"><span data-stu-id="7ac37-115">Word breaking timed out for the full-text query string.</span></span> <span data-ttu-id="7ac37-116">如果断字器长时间处理全文查询字符串或服务器上有大量查询正在运行，则会发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="7ac37-116">This can happen if the wordbreaker took a long time to process the full-text query string, or if a large number of queries are running on the server.</span></span> <span data-ttu-id="7ac37-117">请在负荷较轻的情况下再次尝试运行此查询。</span><span class="sxs-lookup"><span data-stu-id="7ac37-117">Try running the query again under a lighter load.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7ac37-118">说明</span><span class="sxs-lookup"><span data-stu-id="7ac37-118">Explanation</span></span>  
 <span data-ttu-id="7ac37-119">在以下情况下会发生断字超时错误：</span><span class="sxs-lookup"><span data-stu-id="7ac37-119">A word-breaking timeout error can occur in the following situations:</span></span>  
  
-   <span data-ttu-id="7ac37-120">查询语言的断字符配置不正确；例如，其注册表设置不正确。</span><span class="sxs-lookup"><span data-stu-id="7ac37-120">The word breaker for the query language is configured incorrectly; for example, its registry settings are incorrect.</span></span>  
  
-   <span data-ttu-id="7ac37-121">特定查询字符串的断字符工作不正常。</span><span class="sxs-lookup"><span data-stu-id="7ac37-121">The word breaker malfunctions for a specific query string.</span></span>  
  
-   <span data-ttu-id="7ac37-122">断字符为特定查询字符串返回过多数据。</span><span class="sxs-lookup"><span data-stu-id="7ac37-122">The word breaker returns too much data for a specific query string.</span></span> <span data-ttu-id="7ac37-123">过多的数据将被视为潜在的缓冲区溢出攻击，并会关闭承载断字服务的筛选器后台进程 (fdhost.exe)。</span><span class="sxs-lookup"><span data-stu-id="7ac37-123">Excess data is treated as a potential buffer overrun attack, and shuts down the filter daemon process (fdhost.exe), which hosts the word-breaking services.</span></span>  
  
-   <span data-ttu-id="7ac37-124">筛选器后台进程配置不正确。</span><span class="sxs-lookup"><span data-stu-id="7ac37-124">The filter daemon process configuration is incorrect.</span></span>  
  
     <span data-ttu-id="7ac37-125">最常见的配置问题是密码过期或阻止筛选器后台帐户登录的域策略。</span><span class="sxs-lookup"><span data-stu-id="7ac37-125">The most common configuration problems are password expiration or a domain policy that prevents the filter daemon account from logging on.</span></span>  
  
-   <span data-ttu-id="7ac37-126">服务器实例上运行的查询工作负荷很重；例如，断字器长时间处理全文查询字符串或服务器上有大量查询正在运行。</span><span class="sxs-lookup"><span data-stu-id="7ac37-126">A very heavy query workload is running on the server instance; for example, the word-breaker took a long time to process the full-text query string, or a large number of queries are running on the server.</span></span> <span data-ttu-id="7ac37-127">请注意，此原因发生的可能性最低。</span><span class="sxs-lookup"><span data-stu-id="7ac37-127">Note that this is the least likely cause.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7ac37-128">用户操作</span><span class="sxs-lookup"><span data-stu-id="7ac37-128">User Action</span></span>  
 <span data-ttu-id="7ac37-129">针对超时的可能原因选择适当的用户操作，如下所示：</span><span class="sxs-lookup"><span data-stu-id="7ac37-129">Select the user action that is appropriate to the probable cause of the timeout, as follows:</span></span>  
  
|<span data-ttu-id="7ac37-130">可能的原因</span><span class="sxs-lookup"><span data-stu-id="7ac37-130">Probable cause</span></span>|<span data-ttu-id="7ac37-131">用户操作</span><span class="sxs-lookup"><span data-stu-id="7ac37-131">User action</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="7ac37-132">查询语言的断字符配置不正确。</span><span class="sxs-lookup"><span data-stu-id="7ac37-132">The word breaker for the query language is configured incorrectly.</span></span>|<span data-ttu-id="7ac37-133">如果使用的是第三方断字符，则该断字符在操作系统中的注册可能不正确。</span><span class="sxs-lookup"><span data-stu-id="7ac37-133">If you are using a third-party word breaker it might be incorrectly registered with the operating system.</span></span> <span data-ttu-id="7ac37-134">在这种情况下，请重新注册断字符。</span><span class="sxs-lookup"><span data-stu-id="7ac37-134">In this case, re-register the word breaker.</span></span> <span data-ttu-id="7ac37-135">有关详细信息，请参阅[将搜索功能所使用的断字符还原到以前的版本](../search/revert-the-word-breakers-used-by-search-to-the-previous-version.md)。</span><span class="sxs-lookup"><span data-stu-id="7ac37-135">For more information, see [Revert the Word Breakers Used by Search to the Previous Version](../search/revert-the-word-breakers-used-by-search-to-the-previous-version.md).</span></span>|  
|<span data-ttu-id="7ac37-136">特定查询字符串的断字符工作不正常。</span><span class="sxs-lookup"><span data-stu-id="7ac37-136">The word breaker malfunctions for a specific query string.</span></span>|<span data-ttu-id="7ac37-137">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支持断字符，请与 Microsoft 客户服务与支持部门联系。</span><span class="sxs-lookup"><span data-stu-id="7ac37-137">If the word breaker is supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], contact Microsoft Customer Service and Support.</span></span>|  
|<span data-ttu-id="7ac37-138">断字符为特定查询字符串返回过多数据。</span><span class="sxs-lookup"><span data-stu-id="7ac37-138">The word breaker returns too much data for a specific query string.</span></span>|<span data-ttu-id="7ac37-139">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支持断字符，请与 Microsoft 客户服务与支持部门联系。</span><span class="sxs-lookup"><span data-stu-id="7ac37-139">If the word breaker is supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], contact Microsoft Customer Service and Support.</span></span>|  
|<span data-ttu-id="7ac37-140">筛选器后台进程配置不正确。</span><span class="sxs-lookup"><span data-stu-id="7ac37-140">The filter daemon process configuration is incorrect.</span></span>|<span data-ttu-id="7ac37-141">请确保使用的是当前密码，并且域策略不会阻止筛选器后台帐户登录。</span><span class="sxs-lookup"><span data-stu-id="7ac37-141">Ensure that you are using the current password and that a domain policy is not preventing the filter daemon account from logging on.</span></span>|  
|<span data-ttu-id="7ac37-142">服务器实例上运行的查询工作负荷很重。</span><span class="sxs-lookup"><span data-stu-id="7ac37-142">A very heavy query workload is running on the server instance.</span></span>|<span data-ttu-id="7ac37-143">请在负荷较轻的情况下再次尝试运行此查询。</span><span class="sxs-lookup"><span data-stu-id="7ac37-143">Try running the query again under a lighter load.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7ac37-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7ac37-144">See Also</span></span>  
 <span data-ttu-id="7ac37-145">[设置全文筛选器后台程序启动器的服务帐户](../search/set-the-service-account-for-the-full-text-filter-daemon-launcher.md) </span><span class="sxs-lookup"><span data-stu-id="7ac37-145">[Set the Service Account for the Full-text Filter Daemon Launcher](../search/set-the-service-account-for-the-full-text-filter-daemon-launcher.md) </span></span>  
 <span data-ttu-id="7ac37-146">[全文搜索](../search/full-text-search.md) </span><span class="sxs-lookup"><span data-stu-id="7ac37-146">[Full-Text Search](../search/full-text-search.md) </span></span>  
 <span data-ttu-id="7ac37-147">[sp_help_fulltext_system_components &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7ac37-147">[sp_help_fulltext_system_components &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql) </span></span>  
 <span data-ttu-id="7ac37-148">[配置和管理断字符和词干分析器以便搜索](../search/configure-and-manage-word-breakers-and-stemmers-for-search.md) </span><span class="sxs-lookup"><span data-stu-id="7ac37-148">[Configure and Manage Word Breakers and Stemmers for Search](../search/configure-and-manage-word-breakers-and-stemmers-for-search.md) </span></span>  
 [<span data-ttu-id="7ac37-149">配置和管理搜索筛选器</span><span class="sxs-lookup"><span data-stu-id="7ac37-149">Configure and Manage Filters for Search</span></span>](../search/configure-and-manage-filters-for-search.md)  
  
  
