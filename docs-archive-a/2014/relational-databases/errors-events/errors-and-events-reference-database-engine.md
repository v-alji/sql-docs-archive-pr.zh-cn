---
title: 错误和事件参考（数据库引擎）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- errors [SQL Server Database Engine]
- Database Engine [SQL Server], errors
- events [SQL Server Database Engine]
ms.assetid: ea928535-6fd1-4738-a8ed-ffb602f3825e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e991accfd0e6fdd4fa25746499308455eff85ce3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691220"
---
# <a name="errors-and-events-reference-database-engine"></a><span data-ttu-id="3c78f-102">错误和事件参考（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="3c78f-102">Errors and Events Reference (Database Engine)</span></span>

<span data-ttu-id="3c78f-103">本部分包含需要进一步说明的选定数据库引擎错误消息。</span><span class="sxs-lookup"><span data-stu-id="3c78f-103">This section contains selected Database Engine error messages that need further explanation.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="3c78f-104">本节内容</span><span class="sxs-lookup"><span data-stu-id="3c78f-104">In This Section</span></span>  
 <span data-ttu-id="3c78f-105">[数据库引擎事件和错误](database-engine-events-and-errors.md)介绍 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 错误消息的格式，并说明如何查看错误消息并将错误消息返回给应用程序。</span><span class="sxs-lookup"><span data-stu-id="3c78f-105">[Database Engine Events and Errors](database-engine-events-and-errors.md) Describes the format of [!INCLUDE[ssDE](../../includes/ssde-md.md)] error messages and explains how to view error messages and return error messages to applications.</span></span>  
  
 <span data-ttu-id="3c78f-106">介绍 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 错误消息、可能原因以及为更正问题可以采取的所有操作。</span><span class="sxs-lookup"><span data-stu-id="3c78f-106">Provides an explanation of [!INCLUDE[ssDE](../../includes/ssde-md.md)] error messages, possible causes, and any actions you can take to correct the problem.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="3c78f-107">外部资源</span><span class="sxs-lookup"><span data-stu-id="3c78f-107">External Resources</span></span>  
 <span data-ttu-id="3c78f-108">如果您没有在产品文档或网页中找到所需信息，则可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 社区中提问或者向 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 支持人员寻求帮助。</span><span class="sxs-lookup"><span data-stu-id="3c78f-108">If you have not found the information you are looking for in the product documentation or on the Web, you can either ask a question in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] community or request help from [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="3c78f-109">下表提供了指向这些资源的链接并说明了这些资源。</span><span class="sxs-lookup"><span data-stu-id="3c78f-109">The following table links to and describes these resources.</span></span>  
  
|<span data-ttu-id="3c78f-110">资源</span><span class="sxs-lookup"><span data-stu-id="3c78f-110">Resource</span></span>|<span data-ttu-id="3c78f-111">说明</span><span class="sxs-lookup"><span data-stu-id="3c78f-111">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="3c78f-112">SQL Server 社区</span><span class="sxs-lookup"><span data-stu-id="3c78f-112">SQL Server Community</span></span>](https://go.microsoft.com/fwlink/?LinkId=42455)|<span data-ttu-id="3c78f-113">此网站提供指向由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 社区监视的新闻组和论坛的链接。</span><span class="sxs-lookup"><span data-stu-id="3c78f-113">This site has links to newsgroups and forums monitored by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] community.</span></span> <span data-ttu-id="3c78f-114">还列出了诸如博客和网站之类的社区信息资源。</span><span class="sxs-lookup"><span data-stu-id="3c78f-114">It also lists community information sources, such as blogs and Web sites.</span></span> <span data-ttu-id="3c78f-115">尽管不能保证得到答案，但 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 社区对于解决问题还是非常有帮助。</span><span class="sxs-lookup"><span data-stu-id="3c78f-115">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] community is very helpful in answering questions, although an answer cannot be guaranteed.</span></span>|  
|[<span data-ttu-id="3c78f-116">SQL Server 开发人员中心社区</span><span class="sxs-lookup"><span data-stu-id="3c78f-116">SQL Server Developer Center Community</span></span>](https://go.microsoft.com/fwlink/?LinkId=42456)|<span data-ttu-id="3c78f-117">此站点专门提供对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 开发人员有用的新闻组、论坛和其他社区资源。</span><span class="sxs-lookup"><span data-stu-id="3c78f-117">This site focuses on the newsgroups, forums, and other community resources that are useful to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] developers.</span></span>|  
|[<span data-ttu-id="3c78f-118">Microsoft 帮助和支持</span><span class="sxs-lookup"><span data-stu-id="3c78f-118">Microsoft Help and Support</span></span>](https://go.microsoft.com/fwlink/?linkid=16419)|<span data-ttu-id="3c78f-119">您可以使用此网站来获得 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 支持人员的帮助，以便解决具体的问题。</span><span class="sxs-lookup"><span data-stu-id="3c78f-119">You can use this Web site to open a case with a [!INCLUDE[msCoName](../../includes/msconame-md.md)] support professional.</span></span>|  
  
  
