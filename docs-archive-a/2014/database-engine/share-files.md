---
title: 共享文件 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- sharing files
- file sharing [SQL Server]
- version control services [SQL Server], file sharing
ms.assetid: 645f5c0a-e949-4e87-8988-85e4d6128464
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 79909fcdb09e349798edfe285475f8a898c3bf04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693448"
---
# <a name="share-files"></a><span data-ttu-id="c3731-102">共享文件</span><span class="sxs-lookup"><span data-stu-id="c3731-102">Share Files</span></span>
  <span data-ttu-id="c3731-103">可以使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 在各个源代码管理项目间共享一些项。</span><span class="sxs-lookup"><span data-stu-id="c3731-103">You can use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to share items across source control projects.</span></span> <span data-ttu-id="c3731-104">如果共享了某个项，则对该项的任何更改都会反映在共享该项的每个项目中。</span><span class="sxs-lookup"><span data-stu-id="c3731-104">When you share an item, any changes to the item are reflected in every project to which the item is shared.</span></span>  
  
 <span data-ttu-id="c3731-105">项共享可为源代码管理用户带来下列好处：</span><span class="sxs-lookup"><span data-stu-id="c3731-105">Item sharing provides the following advantages to source control users:</span></span>  
  
-   <span data-ttu-id="c3731-106">对于使用共享项的每个项目，不必单独存储一个该项的副本，从而可节省源代码管理客户端和服务器上的磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="c3731-106">Makes it unnecessary for each project that uses the shared item to store a separate copy of the item, conserving disk space on both the source control client and server.</span></span> <span data-ttu-id="c3731-107">源代码管理提供程序将共享项存储在一个中央位置，共享该项的每个项目存储一个指向该位置的指针。</span><span class="sxs-lookup"><span data-stu-id="c3731-107">The source control provider stores the shared item in one central location, and every project to which it is shared stores a pointer to that location.</span></span>  
  
-   <span data-ttu-id="c3731-108">避免了版本的不兼容性。</span><span class="sxs-lookup"><span data-stu-id="c3731-108">Avoids version incompatibilities.</span></span> <span data-ttu-id="c3731-109">由于共享项的每个项目都使用相同版本的项，因此避免了在多个项目中独立更改项的每个副本时导致的冲突。</span><span class="sxs-lookup"><span data-stu-id="c3731-109">Because every project to which the item is shared uses the same version of the item, you avoid the conflicts that arise when each copy of an item is changing independently within multiple projects.</span></span>  
  
### <a name="to-share-an-item"></a><span data-ttu-id="c3731-110">共享一个项</span><span class="sxs-lookup"><span data-stu-id="c3731-110">To share an item</span></span>  
  
1.  <span data-ttu-id="c3731-111">在解决方案资源管理器中，选择要存放共享文件的文件夹或项目。</span><span class="sxs-lookup"><span data-stu-id="c3731-111">In Solution Explorer, select either the folder or project in which you want to place the shared files.</span></span>  
  
2.  <span data-ttu-id="c3731-112">在 "**文件**" 菜单上，指向 "**源代码管理**"，然后单击 "**共享**"。</span><span class="sxs-lookup"><span data-stu-id="c3731-112">On the **File** menu, point to **Source Control**, and then click **Share**.</span></span>  
  
3.  <span data-ttu-id="c3731-113">在 "**共享方式**" 对话框中，浏览要共享的项的目录列表，并单击该项。</span><span class="sxs-lookup"><span data-stu-id="c3731-113">In the **Share with** dialog box, browse the directory list for the item you want to share, and click that item.</span></span>  
  
4.  <span data-ttu-id="c3731-114">单击“共享”。</span><span class="sxs-lookup"><span data-stu-id="c3731-114">Click **Share**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3731-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c3731-115">See Also</span></span>  
 [<span data-ttu-id="c3731-116">源代码管理基础</span><span class="sxs-lookup"><span data-stu-id="c3731-116">Source Control Basics</span></span>](../../2014/database-engine/source-control-basics.md)  
  
  
