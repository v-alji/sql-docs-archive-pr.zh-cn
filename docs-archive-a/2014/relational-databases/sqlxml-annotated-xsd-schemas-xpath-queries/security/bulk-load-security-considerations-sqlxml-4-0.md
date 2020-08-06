---
title: " (SQLXML 4.0) 时的大容量加载安全注意事项 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, XML Bulk Load
- bulk load [SQLXML], security
- security [SQLXML], XML Bulk Load
- XML Bulk Load [SQLXML], security
ms.assetid: 192fc6d4-ecbc-4a4d-a5cb-55e1f64af318
author: rothja
ms.author: jroth
ms.openlocfilehash: 21c1cbe7f94ef42327aa7b81f75fa521d9f7c0e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591868"
---
# <a name="bulk-load-security-considerations-sqlxml-40"></a><span data-ttu-id="4cb61-102">大容量加载安全性注意事项 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="4cb61-102">Bulk Load Security Considerations (SQLXML 4.0)</span></span>
  <span data-ttu-id="4cb61-103">下面是使用 XML 大容量加载的安全准则：</span><span class="sxs-lookup"><span data-stu-id="4cb61-103">The following are security guidelines for using XML Bulk Load:</span></span>  
  
-   <span data-ttu-id="4cb61-104">指定将大容量加载操作作为事务执行时，需要使用 `TempFilePath` 属性指定用于创建临时文件的文件夹。</span><span class="sxs-lookup"><span data-stu-id="4cb61-104">When you specify that the Bulk Load operation is to be performed as a transaction, you use the `TempFilePath` property to specify a folder in which to create the temporary files.</span></span>  
  
     <span data-ttu-id="4cb61-105">大容量加载进程用以下权限创建这些临时文件：</span><span class="sxs-lookup"><span data-stu-id="4cb61-105">The Bulk Load process creates these temporary files with the following permissions:</span></span>  
  
    -   <span data-ttu-id="4cb61-106">将读取/写入/删除访问权授予大容量加载进程。</span><span class="sxs-lookup"><span data-stu-id="4cb61-106">Read/Write/Delete access is granted to the Bulk Load process.</span></span>  
  
    -   <span data-ttu-id="4cb61-107">读取权限将授予所有用户，因为 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 用来访问这些文件的帐户是未知的。</span><span class="sxs-lookup"><span data-stu-id="4cb61-107">Read permission is granted to all users, because the account under which Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] will access these files is unknown.</span></span> <span data-ttu-id="4cb61-108">通过对包含这些临时文件的文件夹设置适当的权限，可以限制对它们的访问。</span><span class="sxs-lookup"><span data-stu-id="4cb61-108">You can restrict the access to these temporary files by setting the appropriate permissions on the folder that contains them.</span></span>  
  
-   <span data-ttu-id="4cb61-109">XML 大容量加载自身没有任何权限设置。</span><span class="sxs-lookup"><span data-stu-id="4cb61-109">XML Bulk Load does not itself have any permissions settings.</span></span> <span data-ttu-id="4cb61-110">它假定数据库已正确设置，并且用户上下文（即大容量加载使用的登录信息）有合适的权限集。</span><span class="sxs-lookup"><span data-stu-id="4cb61-110">It is assumed that the database is set up correctly and that the user context (that is, the login that Bulk Load is set use) has appropriate permissions set.</span></span>  
  
-   <span data-ttu-id="4cb61-111">在非事务模式中，如果在大容量加载进程期间发生错误，则数据最后可能处于部分加载状态中。</span><span class="sxs-lookup"><span data-stu-id="4cb61-111">In non-transactional mode, if an error occurs during the Bulk Load process, data may be left in a partially loaded state.</span></span> <span data-ttu-id="4cb61-112">大容量加载只是停止于发生这种情况时它所在的点上。</span><span class="sxs-lookup"><span data-stu-id="4cb61-112">Bulk Load will simply stop at the point where it is when this happens.</span></span> <span data-ttu-id="4cb61-113">可以用事务模式缓解此问题。</span><span class="sxs-lookup"><span data-stu-id="4cb61-113">Transactional mode can be used to alleviate this issue.</span></span>  
  
-   <span data-ttu-id="4cb61-114">发生大容量加载错误时，这些错误可能包括有关数据库的信息。</span><span class="sxs-lookup"><span data-stu-id="4cb61-114">When Bulk Load errors occur, they may include information about the database.</span></span> <span data-ttu-id="4cb61-115">例如，它们可能包括表或列的名称，或列类型信息。</span><span class="sxs-lookup"><span data-stu-id="4cb61-115">For example, they may include the name of a table or column, or column type information.</span></span> <span data-ttu-id="4cb61-116">使用大容量加载时，应当小心地从大容量加载进程捕获错误，并返回一般性错误消息，而不要将错误直接显示给用户。</span><span class="sxs-lookup"><span data-stu-id="4cb61-116">When you use Bulk Load, you should take care to catch errors from the Bulk Load process and return a generic error message, rather than exposing errors directly to users.</span></span>  
  
-   <span data-ttu-id="4cb61-117">大容量加载不对它处理的数据的数量设置任何限制。</span><span class="sxs-lookup"><span data-stu-id="4cb61-117">Bulk Load sets no limit on the amount of data it works over.</span></span> <span data-ttu-id="4cb61-118">大容量加载不对要加载的数据的大小做任何检查。</span><span class="sxs-lookup"><span data-stu-id="4cb61-118">Bulk Load does not do any checking on the size of the data to be loaded.</span></span> <span data-ttu-id="4cb61-119">确保有足够内存来处理指定的文件，并确保数据库有足够空间以存储所加载的数据，这二者是执行大容量加载的用户的责任。</span><span class="sxs-lookup"><span data-stu-id="4cb61-119">It is the responsibility of the user executing Bulk Load to ensure that there is enough memory to process the specified file, and that there is enough room in the database to store the data being loaded.</span></span>  
  
-   <span data-ttu-id="4cb61-120">大容量加载不会尝试将提供给它的数据作为代码使用。</span><span class="sxs-lookup"><span data-stu-id="4cb61-120">Bulk Load does not make an attempt to use the data it is given as code.</span></span> <span data-ttu-id="4cb61-121">输入的数据永远不会以任何方式执行。</span><span class="sxs-lookup"><span data-stu-id="4cb61-121">The data input is never executed in any fashion.</span></span> <span data-ttu-id="4cb61-122">输入数据中的任何代码或命令均被视为正常数据，并且不会执行。</span><span class="sxs-lookup"><span data-stu-id="4cb61-122">Any code or commands in the input data are treated as normal data and will not be executed.</span></span>  
  
-   <span data-ttu-id="4cb61-123">大容量加载可能基于 XML 和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据模型之间的差异对给定的数据进行格式更改。</span><span class="sxs-lookup"><span data-stu-id="4cb61-123">Bulk Load may make formatting changes to the given data based on differences between the XML and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data models.</span></span> <span data-ttu-id="4cb61-124">例如，二者指定时间所采用的格式各不相同。</span><span class="sxs-lookup"><span data-stu-id="4cb61-124">For example, the format for specifying a time is different.</span></span> <span data-ttu-id="4cb61-125">大容量加载将尝试解决这些差异。</span><span class="sxs-lookup"><span data-stu-id="4cb61-125">Bulk Load will attempt to resolve these differences.</span></span> <span data-ttu-id="4cb61-126">因此，可能会丢失某些精度信息。</span><span class="sxs-lookup"><span data-stu-id="4cb61-126">As a result, some precision information may be lost.</span></span>  
  
-   <span data-ttu-id="4cb61-127">大容量加载对于它处理数据所用的时间长度没有设置任何限制。</span><span class="sxs-lookup"><span data-stu-id="4cb61-127">Bulk Load sets no limit on the amount of time it takes to process the data.</span></span> <span data-ttu-id="4cb61-128">处理将始终继续，直到处理完成，或发生错误。</span><span class="sxs-lookup"><span data-stu-id="4cb61-128">Processing will continue until processing is complete or an error occurs.</span></span>  
  
-   <span data-ttu-id="4cb61-129">大容量加载可以在数据库中创建和删除临时表，但需要相应权限才能执行该操作。</span><span class="sxs-lookup"><span data-stu-id="4cb61-129">Bulk Load can create and delete temporary tables within the database, and needs permissions to do so.</span></span> <span data-ttu-id="4cb61-130">对这些表的权限将授予正连接到数据库执行大容量加载进程的相同用户。</span><span class="sxs-lookup"><span data-stu-id="4cb61-130">Permissions to these tables will be given to the same user who is connecting to the database for the Bulk Load process.</span></span>  
  
-   <span data-ttu-id="4cb61-131">大容量加载可以创建和删除在事务模式处理期间所使用的临时文件，但需要权限才能执行该操作。</span><span class="sxs-lookup"><span data-stu-id="4cb61-131">Bulk Load can create and delete temporary files used during transactional mode processing, and needs permissions to do so.</span></span> <span data-ttu-id="4cb61-132">创建这些文件时所用的权限将与正在运行大容量加载的线程的当前用户所拥有的权限相同。</span><span class="sxs-lookup"><span data-stu-id="4cb61-132">These files are created with the same permissions as the current user of the thread within which Bulk Load is running.</span></span>  
  
-   <span data-ttu-id="4cb61-133">如果用户设置错误日志文件以便让 SQLXML 将错误写入其中，则在每次执行大容量加载时将以来自最后一个大容量加载进程的数据覆盖该文件。</span><span class="sxs-lookup"><span data-stu-id="4cb61-133">If the user sets an error Log file for SQLXML to write errors into, then each time Bulk Load is executed the file will be overwritten with data from the last Bulk Load process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cb61-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4cb61-134">See Also</span></span>  
 [<span data-ttu-id="4cb61-135">对 XML 数据执行大容量加载 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="4cb61-135">Performing Bulk Load of XML Data &#40;SQLXML 4.0&#41;</span></span>](../bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md)  
  
  
