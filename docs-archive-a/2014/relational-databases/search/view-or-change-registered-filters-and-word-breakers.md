---
title: 查看或更改注册的筛选器和断字符 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], word breakers
- full-text search [SQL Server], filters
- filters [full-text search]
- word breakers [full-text search]
ms.assetid: f88c54df-b1aa-4701-807f-dc92c32363fd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 79ad7f1f7df15fed21a132bbe253adc7185d8c06
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688781"
---
# <a name="view-or-change-registered-filters-and-word-breakers"></a><span data-ttu-id="509c3-102">查看或更改注册的筛选器和断字符</span><span class="sxs-lookup"><span data-stu-id="509c3-102">View or Change Registered Filters and Word Breakers</span></span>
  <span data-ttu-id="509c3-103">在系统上安装或卸载了任何断字符或筛选器后，所做的更改并不会在服务器实例上自动生效。</span><span class="sxs-lookup"><span data-stu-id="509c3-103">After any word breakers or filters are installed or uninstalled on a system, the changes do not automatically take effect on server instances.</span></span> <span data-ttu-id="509c3-104">本主题介绍在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的实例上如何查看当前注册的断字符或筛选器，以及如何注册新安装的断字符和筛选器。</span><span class="sxs-lookup"><span data-stu-id="509c3-104">This topic describes how to view the currently registered word breaker or filters and how to register newly installed word breakers and filters on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
### <a name="to-view-a-list-of-languages-whose-word-breakers-are-currently-registered"></a><span data-ttu-id="509c3-105">查看其断字符当前已注册的语言的列表</span><span class="sxs-lookup"><span data-stu-id="509c3-105">To view a list of languages whose word breakers are currently registered</span></span>  
  
1.  <span data-ttu-id="509c3-106">请使用 [sys.fulltext_languages](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql) 目录视图，如下所示：</span><span class="sxs-lookup"><span data-stu-id="509c3-106">Use the [sys.fulltext_languages](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql) catalog view, as follows:</span></span>  
  
    ```  
    SELECT * FROM sys.fulltext_languages;   
    ```  
  
### <a name="to-view-a-list-of-the-filters-that-are-currently-registered"></a><span data-ttu-id="509c3-107">查看当前已注册的筛选器的列表</span><span class="sxs-lookup"><span data-stu-id="509c3-107">To view a list of the filters that are currently registered</span></span>  
  
1.  <span data-ttu-id="509c3-108">请使用 [sp_help_fulltext_system_components](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql) 系统存储过程，如下所示：</span><span class="sxs-lookup"><span data-stu-id="509c3-108">Use the [sp_help_fulltext_system_components](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql) system stored procedure, as follows:</span></span>  
  
    ```  
    EXEC sp_help_fulltext_system_components 'filter';    
    ```  
  
### <a name="to-register-newly-installed-word-breakers-and-filters"></a><span data-ttu-id="509c3-109">注册新安装的断字符和筛选器</span><span class="sxs-lookup"><span data-stu-id="509c3-109">To register newly installed word breakers and filters</span></span>  
  
1.  <span data-ttu-id="509c3-110">按如下方式使用 [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql) 系统存储过程更新语言列表：</span><span class="sxs-lookup"><span data-stu-id="509c3-110">Use the [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql) system stored procedure to update the list of languages, as follows:</span></span>  
  
    ```  
    exec sp_fulltext_service 'update_languages';   
    ```  
  
### <a name="to-unregister-uninstalled-word-breakers-and-filters"></a><span data-ttu-id="509c3-111">撤消注册已卸载的断字符和筛选器</span><span class="sxs-lookup"><span data-stu-id="509c3-111">To unregister uninstalled word breakers and filters</span></span>  
  
1.  <span data-ttu-id="509c3-112">按如下方式使用 **sp_fulltext_service** 更新语言列表：</span><span class="sxs-lookup"><span data-stu-id="509c3-112">Use the **sp_fulltext_service** to update the list of languages, as follows:</span></span>  
  
    ```  
    exec sp_fulltext_service 'update_languages'  
    ```  
  
2.  <span data-ttu-id="509c3-113">按如下方式使用 **sp_fulltext_service** 重新启动筛选器后台程序宿主进程 (fdhost.exe)：</span><span class="sxs-lookup"><span data-stu-id="509c3-113">Use the **sp_fulltext_service** to restart the filter daemon host processes (fdhost.exe), as follows:</span></span>  
  
    ```  
    exec sp_fulltext_service 'restart_all_fdhosts';  
    ```  
  
### <a name="to-replace-existing-word-breakers-or-filters-when-installing-new-ones"></a><span data-ttu-id="509c3-114">安装新断字符或筛选器时替换现有的断字符或筛选器</span><span class="sxs-lookup"><span data-stu-id="509c3-114">To replace existing word breakers or filters when installing new ones</span></span>  
  
1.  <span data-ttu-id="509c3-115">准备安装包含新的断字符或筛选器的 DLL 文件时，请验证其文件名是否不同于已在您的服务器实例上安装的任何现有 DLL 文件的文件名。</span><span class="sxs-lookup"><span data-stu-id="509c3-115">When preparing to install a DLL file that contains new word breakers or filters, verify that it has a different filename from any of the existing DLL files installed on your server instance.</span></span>  
  
2.  <span data-ttu-id="509c3-116">将新的 DLL 文件复制到包含该服务器实例的标准 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DLL 文件的目录内。</span><span class="sxs-lookup"><span data-stu-id="509c3-116">Copy the new DLL file into the directory containing the standard [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DLL files for the server instance.</span></span> <span data-ttu-id="509c3-117">默认位置为：</span><span class="sxs-lookup"><span data-stu-id="509c3-117">The default location is:</span></span>  
  
     <span data-ttu-id="509c3-118">C:\Program Files\Microsoft SQL Server\MSSQL.*instance_name*\MSSQL\Binn</span><span class="sxs-lookup"><span data-stu-id="509c3-118">C:\Program Files\Microsoft SQL Server\MSSQL.*instance_name*\MSSQL\Binn</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="509c3-119">强烈建议您仅加载经过签名和验证的组件。</span><span class="sxs-lookup"><span data-stu-id="509c3-119">We highly recommend that you load only signed and verified components.</span></span> <span data-ttu-id="509c3-120">并且，建议您以可能的最低特权运行 FDHOST Launcher (MSSQLFDLauncher) 服务。</span><span class="sxs-lookup"><span data-stu-id="509c3-120">Also, we recommend that you run the FDHOST Launcher (MSSQLFDLauncher) Service with the least possible privileges.</span></span>  
  
3.  <span data-ttu-id="509c3-121">安装新的断字符或筛选器。</span><span class="sxs-lookup"><span data-stu-id="509c3-121">Install the new word breaker or filters.</span></span>  
  
     <span data-ttu-id="509c3-122">**安装并加载 Microsoft Filter Pack IFilter**</span><span class="sxs-lookup"><span data-stu-id="509c3-122">**To install and load Microsoft Filter Pack IFilters**</span></span>  
  
    -   [<span data-ttu-id="509c3-123">如何将 Microsoft Filter Pack IFilter 注册到 SQL Server</span><span class="sxs-lookup"><span data-stu-id="509c3-123">How to register Microsoft Filter Pack IFilters with SQL Server</span></span>](https://go.microsoft.com/fwlink/?LinkId=130439)  
  
4.  <span data-ttu-id="509c3-124">按如下方式使用 **sp_fulltext_service** 加载服务器实例中新安装的断字符和筛选器：</span><span class="sxs-lookup"><span data-stu-id="509c3-124">Use **sp_fulltext_service** to load newly installed word breakers and filters in the server instance, as follows:</span></span>  
  
    ```  
    EXEC sp_fulltext_service @action='load_os_resources', @value=1;  
    ```  
  
5.  <span data-ttu-id="509c3-125">按如下方式使用 **sp_fulltext_service** 更新语言列表：</span><span class="sxs-lookup"><span data-stu-id="509c3-125">Use **sp_fulltext_service** to update the list of languages, as follows:</span></span>  
  
    ```  
    EXEC sp_fulltext_service 'update_languages';  
    ```  
  
6.  <span data-ttu-id="509c3-126">按如下方式使用 **sp_fulltext_service** 重新启动筛选器后台程序宿主进程 (fdhost.exe)：</span><span class="sxs-lookup"><span data-stu-id="509c3-126">Restart the filter daemon host processes (fdhost.exe), using **sp_fulltext_service** as follows:</span></span>  
  
    ```  
    EXEC sp_fulltext_service 'restart_all_fdhosts';   
    ```  
  
## <a name="see-also"></a><span data-ttu-id="509c3-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="509c3-127">See Also</span></span>  
 <span data-ttu-id="509c3-128">[设置用于全文筛选器后台程序启动器的服务帐户](set-the-service-account-for-the-full-text-filter-daemon-launcher.md) </span><span class="sxs-lookup"><span data-stu-id="509c3-128">[Set the Service Account for the Full-text Filter Daemon Launcher](set-the-service-account-for-the-full-text-filter-daemon-launcher.md) </span></span>  
 <span data-ttu-id="509c3-129">[配置和管理搜索筛选器](configure-and-manage-filters-for-search.md) </span><span class="sxs-lookup"><span data-stu-id="509c3-129">[Configure and Manage Filters for Search](configure-and-manage-filters-for-search.md) </span></span>  
 [<span data-ttu-id="509c3-130">配置和管理断字符和词干分析器以便搜索</span><span class="sxs-lookup"><span data-stu-id="509c3-130">Configure and Manage Word Breakers and Stemmers for Search</span></span>](configure-and-manage-word-breakers-and-stemmers-for-search.md)  
  
  
