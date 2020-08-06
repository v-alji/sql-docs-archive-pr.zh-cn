---
title: 比较所复制表的差异（复制编程）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- tablediff utility
- comparing replicated tables
ms.assetid: cd253a17-0c85-42b4-912c-690169ebe799
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0d804c7d4ac9cc54fa144b7054c6032663b76c0a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693789"
---
# <a name="compare-replicated-tables-for-differences-replication-programming"></a><span data-ttu-id="c6dfb-102">比较所复制表的差异（复制编程）</span><span class="sxs-lookup"><span data-stu-id="c6dfb-102">Compare Replicated Tables for Differences (Replication Programming)</span></span>
  <span data-ttu-id="c6dfb-103">项目验证用于确定发布服务器和订阅服务器上的表项目的已发布数据是否不同，这可能表明无法收敛。</span><span class="sxs-lookup"><span data-stu-id="c6dfb-103">Article validation is used to determine if published data for table articles at the Publisher and Subscriber are not identical, which can indicate non-convergence.</span></span> <span data-ttu-id="c6dfb-104">有关详细信息，请参阅[验证已复制的数据](../validate-data-at-the-subscriber.md)。</span><span class="sxs-lookup"><span data-stu-id="c6dfb-104">For more information, see [Validate Replicated Data](../validate-data-at-the-subscriber.md).</span></span> <span data-ttu-id="c6dfb-105">但是，验证仅返回通过或失败信息，而不会提供任何有关源表和目标表之间存在哪些差异的信息。</span><span class="sxs-lookup"><span data-stu-id="c6dfb-105">However, validation only returns pass or fail information and does not provide any information about what is different between the source and destination tables.</span></span> <span data-ttu-id="c6dfb-106">**tablediff** 命令提示实用工具返回两个表之间存在的详细差异信息，甚至可生成 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 脚本，以使订阅与发布服务器上的数据实现收敛。</span><span class="sxs-lookup"><span data-stu-id="c6dfb-106">The **tablediff** command prompt utility returns detailed difference information between two tables and can even generate a [!INCLUDE[tsql](../../../includes/tsql-md.md)] script to bring a subscription into convergence with data at the Publisher.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c6dfb-107">**tablediff** 实用工具仅受 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服务器的支持。</span><span class="sxs-lookup"><span data-stu-id="c6dfb-107">The **tablediff** utility is only supported for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] servers.</span></span>  
  
### <a name="to-compare-replicated-tables-for-differences-using-tablediff"></a><span data-ttu-id="c6dfb-108">使用 tablediff 比较复制的表之间的不同</span><span class="sxs-lookup"><span data-stu-id="c6dfb-108">To compare replicated tables for differences using tablediff</span></span>  
  
1.  <span data-ttu-id="c6dfb-109">从复制拓扑中任何服务器的命令提示符处，运行 [tablediff Utility](../../../tools/tablediff-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="c6dfb-109">From the command prompt at any server in a replication topology, run the [tablediff Utility](../../../tools/tablediff-utility.md).</span></span> <span data-ttu-id="c6dfb-110">指定下列参数：</span><span class="sxs-lookup"><span data-stu-id="c6dfb-110">Specify the following parameters:</span></span>  
  
    -   <span data-ttu-id="c6dfb-111">**-sourceserver** - 已知其上数据正确的服务器的名称，通常为发布服务器。</span><span class="sxs-lookup"><span data-stu-id="c6dfb-111">**-sourceserver** - name of the server on which the data is known to be correct, usually the Publisher.</span></span>  
  
    -   <span data-ttu-id="c6dfb-112">**-sourcedatabase** - 包含正确数据的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="c6dfb-112">**-sourcedatabase** - name of the database containing the correct data.</span></span>  
  
    -   <span data-ttu-id="c6dfb-113">**-sourcetable** - 要比较的项目的源表的名称。</span><span class="sxs-lookup"><span data-stu-id="c6dfb-113">**-sourcetable** - name of the source table for the article being compared.</span></span>  
  
    -   <span data-ttu-id="c6dfb-114">（可选） **-sourceschema** - 源表的架构所有者（如果不为默认架构）。</span><span class="sxs-lookup"><span data-stu-id="c6dfb-114">(Optional) **-sourceschema** - schema owner of the source table, if not the default schema.</span></span>  
  
    -   <span data-ttu-id="c6dfb-115">（可选） **-sourceuser** 和 **-sourcepassword** （当使用 SQL Server 身份验证连接到发布服务器时。）</span><span class="sxs-lookup"><span data-stu-id="c6dfb-115">(Optional) **-sourceuser** and **-sourcepassword** when using SQL Server Authentication to connect to the Publisher.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="c6dfb-116">请尽可能使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="c6dfb-116">When possible, use Windows Authentication.</span></span> <span data-ttu-id="c6dfb-117">如果必须使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 身份验证，则在运行时提示用户输入安全凭据。</span><span class="sxs-lookup"><span data-stu-id="c6dfb-117">If you must use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="c6dfb-118">如果必须在脚本文件中存储凭据，则必须保护文件以防止未经授权的访问。</span><span class="sxs-lookup"><span data-stu-id="c6dfb-118">If you must store credentials in a script file, you must secure the file to prevent unauthorized access.</span></span>  
  
    -   <span data-ttu-id="c6dfb-119">**-destinationserver** - 要比较其上数据的服务器的名称，通常为订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="c6dfb-119">**-destinationserver** - name of the server on which the data is being compared, usually a Subscriber.</span></span>  
  
    -   <span data-ttu-id="c6dfb-120">**-destinationdatabase** - 要比较的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="c6dfb-120">**-destinationdatabase** - name of a the database being compared.</span></span>  
  
    -   <span data-ttu-id="c6dfb-121">**-destinationtable** - 要比较的表的名称。</span><span class="sxs-lookup"><span data-stu-id="c6dfb-121">**-destinationtable** - name of the table being compared.</span></span>  
  
    -   <span data-ttu-id="c6dfb-122">（可选） **-destinationschema** - 目标表的架构所有者（如果不为默认架构）。</span><span class="sxs-lookup"><span data-stu-id="c6dfb-122">(Optional) **-destinationschema** - schema owner of the destination table, if not the default schema.</span></span>  
  
    -   <span data-ttu-id="c6dfb-123">（可选） **-destinationuser** 和 **-destinationpassword** （当使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 身份验证连接到订阅服务器时。）</span><span class="sxs-lookup"><span data-stu-id="c6dfb-123">(Optional) **-destinationuser** and **-destinationpassword** when using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication to connect to the Subscriber.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="c6dfb-124">请尽可能使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="c6dfb-124">When possible, use Windows Authentication.</span></span> <span data-ttu-id="c6dfb-125">如果必须使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 身份验证，则在运行时提示用户输入安全凭据。</span><span class="sxs-lookup"><span data-stu-id="c6dfb-125">If you must use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="c6dfb-126">如果必须在脚本文件中存储凭据，则必须保护文件以防止未经授权的访问。</span><span class="sxs-lookup"><span data-stu-id="c6dfb-126">If you must store credentials in a script file, you must secure the file to prevent unauthorized access.</span></span>  
  
    -   <span data-ttu-id="c6dfb-127">（可选）使用 **-c** 来执行列级比较。</span><span class="sxs-lookup"><span data-stu-id="c6dfb-127">(Optional) Use **-c** to do a column-level comparison.</span></span>  
  
    -   <span data-ttu-id="c6dfb-128">（可选）使用 **-q** 来执行快速的行计数和仅限架构的比较。</span><span class="sxs-lookup"><span data-stu-id="c6dfb-128">(Optional) Use **-q** to do a fast, row count- and schema-only comparison.</span></span>  
  
    -   <span data-ttu-id="c6dfb-129">（可选）为 **-o** 指定文件名和路径以将结果输出到某个文件。</span><span class="sxs-lookup"><span data-stu-id="c6dfb-129">(Optional) Specify a file name and path for **-o** to output the results to a file.</span></span>  
  
    -   <span data-ttu-id="c6dfb-130">（可选）为 **-et**指定要将结果插入其中的订阅数据库中的表。</span><span class="sxs-lookup"><span data-stu-id="c6dfb-130">(Optional) Specify a table in the subscription database into which to insert results for **-et**.</span></span> <span data-ttu-id="c6dfb-131">如果该表已经存在，则指定 **-dt** 以首先删除该表。</span><span class="sxs-lookup"><span data-stu-id="c6dfb-131">If the table already exists, specify **-dt** to first drop the table.</span></span>  
  
    -   <span data-ttu-id="c6dfb-132">（可选）使用 **-f** 生成 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 文件以修复订阅服务器上的数据，以便与发布服务器上的数据匹配。</span><span class="sxs-lookup"><span data-stu-id="c6dfb-132">(Optional) Use **-f** to generate a [!INCLUDE[tsql](../../../includes/tsql-md.md)] file to fix data at the Subscriber so that it matches data at the Publisher.</span></span> <span data-ttu-id="c6dfb-133">使用 **-df** 指定每个文件中的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句数量。</span><span class="sxs-lookup"><span data-stu-id="c6dfb-133">Use **-df** to specify the number of [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements in each file.</span></span>  
  
    -   <span data-ttu-id="c6dfb-134">（可选）使用 **-rc** 和 **-ri** 指定重试某项操作的次数和重试时间间隔。</span><span class="sxs-lookup"><span data-stu-id="c6dfb-134">(Optional) Use **-rc** and **-ri** to specify the number of times to retry an operation and the retry interval.</span></span>  
  
    -   <span data-ttu-id="c6dfb-135">（可选）使用 **-strict** 以强制在源表和目标表之间执行严格的架构比较。</span><span class="sxs-lookup"><span data-stu-id="c6dfb-135">(Optional) Use **-strict** to enforce strict schema comparison between source and destination tables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6dfb-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c6dfb-136">See Also</span></span>  
 [<span data-ttu-id="c6dfb-137">在订阅服务器上验证数据</span><span class="sxs-lookup"><span data-stu-id="c6dfb-137">Validate Data at the Subscriber</span></span>](../validate-data-at-the-subscriber.md)  
  
  
