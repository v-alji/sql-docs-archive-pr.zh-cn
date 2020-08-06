---
title: 基于 COM 的自定义冲突解决程序 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- COM-based resolvers [SQL Server replication]
- custom resolvers [SQL Server replication]
ms.assetid: 94195797-ad7a-4962-a8e3-b259cd13aa38
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2b28795c1a7d43bcd4e8cb3f18723e05f9e76966
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690568"
---
# <a name="com-based-custom-resolvers"></a><span data-ttu-id="9e577-102">COM-Based Custom Resolvers</span><span class="sxs-lookup"><span data-stu-id="9e577-102">COM-Based Custom Resolvers</span></span>
  <span data-ttu-id="9e577-103">与默认解决机制相比，自定义冲突解决程序提供了更大的灵活性，可以实现使用复制数据的应用程序所需的业务逻辑。</span><span class="sxs-lookup"><span data-stu-id="9e577-103">Custom resolvers provide more flexibility than the default resolution mechanism, and they can implement business logic required by applications using the replicated data.</span></span> <span data-ttu-id="9e577-104">基于 COM 的自定义冲突解决程序是一个动态链接库 (DLL)，它实现了 **ICustomResolver** COM 接口、方法、属性以及其他专为解决冲突设计的支持接口和类型定义。</span><span class="sxs-lookup"><span data-stu-id="9e577-104">A COM-based custom resolver is a dynamic-link library (DLL) that implements the **ICustomResolver** COM interface, its methods and properties, and other supporting interfaces and type definitions designed specifically for conflict resolution.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9e577-105">如果可能，建议使用业务逻辑处理程序而非基于 COM 的自定义冲突解决程序。</span><span class="sxs-lookup"><span data-stu-id="9e577-105">It is recommended to use a business logic handler rather than a COM-based custom resolver if possible.</span></span> <span data-ttu-id="9e577-106">有关业务逻辑处理程序的详细信息，请参阅[合并同步期间执行业务逻辑](execute-business-logic-during-merge-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="9e577-106">For more information on business logic handlers, see [Execute Business Logic During Merge Synchronization](execute-business-logic-during-merge-synchronization.md).</span></span>  
  
 <span data-ttu-id="9e577-107">若要创建自定义的 COM 冲突解决程序，可以使用 replrec.dll 中提供的类型库；默认情况下，此类型库安装在 [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM 下。</span><span class="sxs-lookup"><span data-stu-id="9e577-107">To build a custom COM resolver, you can use the type library that is provided in the replrec.dll; by default, this library is installed at [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM.</span></span>  
  
 <span data-ttu-id="9e577-108">编写自定义的 COM 冲突解决程序之前，需要决定以下事项：</span><span class="sxs-lookup"><span data-stu-id="9e577-108">Before writing a custom COM resolver, you need to decide:</span></span>  
  
-   <span data-ttu-id="9e577-109">要解决的行更改类型（例如更新、插入和删除）以及是否在上载和/或下载合并更改过程中调用冲突解决程序。</span><span class="sxs-lookup"><span data-stu-id="9e577-109">The types of row changes you want to resolve, such as updates, inserts, and deletes, and whether the resolver should be invoked during the upload of merge changes, the download of merge changes, or both.</span></span> <span data-ttu-id="9e577-110">可以指定一种类型的更改、所有更改或任何组合。</span><span class="sxs-lookup"><span data-stu-id="9e577-110">You can specify one type of change, all changes, or any combination.</span></span> <span data-ttu-id="9e577-111">默认的合并冲突解决程序处理自定义冲突解决程序未处理的所有冲突。</span><span class="sxs-lookup"><span data-stu-id="9e577-111">The default merge conflict resolver handles any conflicts not covered by a custom resolver.</span></span>  
  
-   <span data-ttu-id="9e577-112">是否在解决冲突时使用列跟踪。</span><span class="sxs-lookup"><span data-stu-id="9e577-112">Whether to use column tracking when resolving the conflict.</span></span> <span data-ttu-id="9e577-113">当列级跟踪处于开启状态时，只有那些存在冲突的行中的数据才标志为冲突，否则合并这些数据。</span><span class="sxs-lookup"><span data-stu-id="9e577-113">When column-level tracking is on, only data in those columns where a conflict exists are flagged as a conflict, otherwise the data is merged.</span></span> <span data-ttu-id="9e577-114">但是，解决冲突的方式与行级跟踪相同：优先级入选方覆盖整行数据（但数据可以是来自发布服务器、订阅服务器的混合值，也可以是既不来自发布服务器也不来自订阅服务器的某些更改值）。</span><span class="sxs-lookup"><span data-stu-id="9e577-114">However, conflicts are resolved in the same way as row-level tracking: the priority winner overwrites the entire row of data (but the data can be a mix of values from the Publisher, Subscribers, or some altered values that were from neither Publisher nor Subscribers).</span></span> <span data-ttu-id="9e577-115">有关详细信息，请参阅 [检测并解决合并复制冲突](advanced-merge-replication-conflict-detection-and-resolution.md)。</span><span class="sxs-lookup"><span data-stu-id="9e577-115">For more information, see [Detect and Resolve Merge Replication Conflicts](advanced-merge-replication-conflict-detection-and-resolution.md).</span></span>  
  
 <span data-ttu-id="9e577-116">若要实现基于 COM 的自定义冲突解决程序，请参阅 [为合并项目实现自定义冲突解决程序](../implement-a-custom-conflict-resolver-for-a-merge-article.md)。</span><span class="sxs-lookup"><span data-stu-id="9e577-116">To implement a COM-based custom conflict resolver, see [Implement a Custom Conflict Resolver for a Merge Article](../implement-a-custom-conflict-resolver-for-a-merge-article.md).</span></span>  
  
 <span data-ttu-id="9e577-117">自定义冲突解决程序是针对项目而不是整个发布指定的。</span><span class="sxs-lookup"><span data-stu-id="9e577-117">A custom resolver is specified for an article, not an entire publication.</span></span> <span data-ttu-id="9e577-118">同一个冲突解决程序可用于多个项目，但自定义冲突解决程序中的逻辑通常针对特定的表。</span><span class="sxs-lookup"><span data-stu-id="9e577-118">The same resolver can be used with more than one article, but the logic in custom resolvers is often specific to a particular table.</span></span> <span data-ttu-id="9e577-119">如果在创建冲突解决程序后修改了项目中使用的表（例如，为冲突解决中所用列名重命名），那么自定义冲突解决程序就可能需要修改并重新编译。</span><span class="sxs-lookup"><span data-stu-id="9e577-119">If the table used in the article is modified after the resolver is created (for example, renaming the column name that is used in conflict resolution), the custom resolver might need to be modified and recompiled.</span></span>  
  
 <span data-ttu-id="9e577-120">若要指定自定义冲突解决程序，请参阅 [指定合并项目冲突解决程序](../publish/specify-a-merge-article-resolver.md)。</span><span class="sxs-lookup"><span data-stu-id="9e577-120">To specify a custom resolver, see [Specify a Merge Article Resolver](../publish/specify-a-merge-article-resolver.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e577-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9e577-121">See Also</span></span>  
 <span data-ttu-id="9e577-122">[Advanced Merge Replication Conflict Detection and Resolution](advanced-merge-replication-conflict-detection-and-resolution.md) </span><span class="sxs-lookup"><span data-stu-id="9e577-122">[Advanced Merge Replication Conflict Detection and Resolution](advanced-merge-replication-conflict-detection-and-resolution.md) </span></span>  
 [<span data-ttu-id="9e577-123">Microsoft COM-Based Resolvers</span><span class="sxs-lookup"><span data-stu-id="9e577-123">Microsoft COM-Based Resolvers</span></span>](advanced-merge-replication-conflict-com-based-resolvers.md)  
  
  
