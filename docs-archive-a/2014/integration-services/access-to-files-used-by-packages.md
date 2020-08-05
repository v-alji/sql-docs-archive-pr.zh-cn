---
title: 对包使用的文件的访问 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS packages, security
- packages [Integration Services], security
- configuration files [Integration Services]
- checkpoint files
- Integration Services packages, security
- logs [Integration Services], security
- files [Integration Services], security
- SQL Server Integration Services packages, security
ms.assetid: 2e3ddea9-5289-4289-a70e-11c018f34977
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8db9511c91c9f229b7002f5b16cf077910a4ccf0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579022"
---
# <a name="access-to-files-used-by-packages"></a><span data-ttu-id="7582b-102">对包使用的文件的访问</span><span class="sxs-lookup"><span data-stu-id="7582b-102">Access to Files Used by Packages</span></span>
  <span data-ttu-id="7582b-103">包保护级别不保护存储在包以外的文件。</span><span class="sxs-lookup"><span data-stu-id="7582b-103">The package protection level does not protect files that are stored outside the package.</span></span> <span data-ttu-id="7582b-104">这些文件包括下面的文件：</span><span class="sxs-lookup"><span data-stu-id="7582b-104">These files include the following:</span></span>  
  
-   <span data-ttu-id="7582b-105">配置文件</span><span class="sxs-lookup"><span data-stu-id="7582b-105">Configuration files</span></span>  
  
-   <span data-ttu-id="7582b-106">检查点文件</span><span class="sxs-lookup"><span data-stu-id="7582b-106">Checkpoint files</span></span>  
  
-   <span data-ttu-id="7582b-107">日志文件</span><span class="sxs-lookup"><span data-stu-id="7582b-107">Log files</span></span>  
  
 <span data-ttu-id="7582b-108">这些文件必须单独进行保护，尤其是在它们包括敏感的信息时。</span><span class="sxs-lookup"><span data-stu-id="7582b-108">These files must be protected separately, especially if they include sensitive information.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="7582b-109">配置文件</span><span class="sxs-lookup"><span data-stu-id="7582b-109">Configuration Files</span></span>  
 <span data-ttu-id="7582b-110">如果配置中有敏感的信息，例如登录名和密码信息，则应当考虑将配置保存到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]，或使用访问控制列表 (ACL) 来限制对存储文件的位置或文件夹的访问，并只允许访问某些帐户。</span><span class="sxs-lookup"><span data-stu-id="7582b-110">If you have sensitive information in a configuration, such as login and password information, you should consider saving the configuration to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], or use an access control list (ACL) to restrict access to the location or folder where you store the files and allow access only to certain accounts.</span></span> <span data-ttu-id="7582b-111">通常，可以向允许其运行包的帐户以及负责管理包和排除包的故障的帐户授予访问权，这些权限可能包括检查配置、检查点和日志文件的内容。</span><span class="sxs-lookup"><span data-stu-id="7582b-111">Typically, you would grant access to the accounts that you permit to run packages, and to the accounts that manage and troubleshoot packages, which may include reviewing the contents of configuration, checkpoint, and log files.</span></span> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="7582b-112">提供了更安全的存储方式，因为它在服务器和数据库级别提供保护。</span><span class="sxs-lookup"><span data-stu-id="7582b-112">provides the more secure storage because it offers protection at the server and database levels.</span></span> <span data-ttu-id="7582b-113">若要将配置保存到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]，请使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 配置类型。</span><span class="sxs-lookup"><span data-stu-id="7582b-113">To save configurations to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], you use the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] configuration type.</span></span> <span data-ttu-id="7582b-114">若要保存到文件系统，请使用 XML 配置类型。</span><span class="sxs-lookup"><span data-stu-id="7582b-114">To save to the file system, you use the XML configuration type.</span></span>  
  
 <span data-ttu-id="7582b-115">有关详细信息，请参阅 [包配置](../../2014/integration-services/package-configurations.md)、 [创建包配置](../../2014/integration-services/create-package-configurations.md)和 [有关 SQL Server 安装的安全注意事项](../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)。</span><span class="sxs-lookup"><span data-stu-id="7582b-115">For more information, see [Package Configurations](../../2014/integration-services/package-configurations.md), [Create Package Configurations](../../2014/integration-services/create-package-configurations.md), and [Security Considerations for a SQL Server Installation](../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md).</span></span>  
  
## <a name="checkpoint-files"></a><span data-ttu-id="7582b-116">检查点文件</span><span class="sxs-lookup"><span data-stu-id="7582b-116">Checkpoint Files</span></span>  
 <span data-ttu-id="7582b-117">同样，如果包所使用的检查点文件包含敏感信息，则应使用访问控制列表 (ACL) 来保证文件存储位置或所在文件夹的安全。</span><span class="sxs-lookup"><span data-stu-id="7582b-117">Similarly, if the checkpoint file that the package uses includes sensitive information, you should use an access control list (ACL) to secure the location or folder where you store the file.</span></span> <span data-ttu-id="7582b-118">检查点文件用于保存有关包进度的当前状态信息和变量的当前值。</span><span class="sxs-lookup"><span data-stu-id="7582b-118">Checkpoint files save current state information on the progress of the package as well as the current values of variables.</span></span> <span data-ttu-id="7582b-119">例如，包中可能包含含有电话号码的自定义变量。</span><span class="sxs-lookup"><span data-stu-id="7582b-119">For example, the package may include a custom variable that contains a telephone number.</span></span> <span data-ttu-id="7582b-120">有关详细信息，请参阅 [通过使用检查点重新启动包](packages/restart-packages-by-using-checkpoints.md)。</span><span class="sxs-lookup"><span data-stu-id="7582b-120">For more information, see [Restart Packages by Using Checkpoints](packages/restart-packages-by-using-checkpoints.md).</span></span>  
  
## <a name="log-files"></a><span data-ttu-id="7582b-121">日志文件</span><span class="sxs-lookup"><span data-stu-id="7582b-121">Log Files</span></span>  
 <span data-ttu-id="7582b-122">写入文件系统的日志项也应使用访问控制列表 (ACL) 进行保护。</span><span class="sxs-lookup"><span data-stu-id="7582b-122">Log entries that are written to the file system should also be secured using an access control list (ACL).</span></span> <span data-ttu-id="7582b-123">日志项也可存储在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 表中，受 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 安全机制的保护。</span><span class="sxs-lookup"><span data-stu-id="7582b-123">Log entries can also be stored in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tables and protected by [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] security.</span></span> <span data-ttu-id="7582b-124">日志项可能包含敏感信息。例如，如果包中包含构造 SQL 语句的执行 SQL 任务，而所构造的 SQL 语句又引用电话号码，则对应于该 SQL 语句的日志项就会包含电话号码。</span><span class="sxs-lookup"><span data-stu-id="7582b-124">Log entries may include sensitive information, For example, if the package contains an Execute SQL task that constructs an SQL statement that refers to a telephone number, the log entry for the SQL statement includes the telephone number.</span></span> <span data-ttu-id="7582b-125">SQL 语句还可能泄漏数据库中有关表和列名的私有信息。</span><span class="sxs-lookup"><span data-stu-id="7582b-125">The SQL statement may also reveal private information about table and column names in databases.</span></span> <span data-ttu-id="7582b-126">有关详细信息，请参阅 [Integration Services (SSIS) 日志记录](performance/integration-services-ssis-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="7582b-126">For more information, see [Integration Services &#40;SSIS&#41; Logging](performance/integration-services-ssis-logging.md).</span></span>  
  
  
