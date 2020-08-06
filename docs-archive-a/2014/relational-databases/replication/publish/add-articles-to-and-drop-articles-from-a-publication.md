---
title: 向发布 (SQL Server Management Studio) 中添加项目和从中删除项目 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- articles [SQL Server replication], dropping
- deleting articles
- dropping articles
- adding articles
- articles [SQL Server replication], adding
ms.assetid: d5a3e536-62d2-4473-a178-877ba52f7d7f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f7af1cac1f3ee8ecc9cb79632f8a4ef1e66ec82f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591266"
---
# <a name="add-articles-to-and-drop-articles-from-a-publication-sql-server-management-studio"></a><span data-ttu-id="380bf-102">将项目添加到发布中以及从发布中删除项目 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="380bf-102">Add Articles to and Drop Articles from a Publication (SQL Server Management Studio)</span></span>
  <span data-ttu-id="380bf-103">在新建发布向导中创建项目时，首次将其添加到发布中。</span><span class="sxs-lookup"><span data-stu-id="380bf-103">Initially add articles to a publication when you create it in the New Publication Wizard.</span></span> <span data-ttu-id="380bf-104">有关使用此向导的详细信息，请参阅[创建发布](create-a-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="380bf-104">For more information about using this wizard, see [Create a Publication](create-a-publication.md).</span></span>  
  
 <span data-ttu-id="380bf-105">创建发布后，在“发布属性 - \<Publication>”对话框的“项目”页面上添加和删除项目 。</span><span class="sxs-lookup"><span data-stu-id="380bf-105">After a publication is created, add and delete articles on the **Articles** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="380bf-106">有关访问此对话框的详细信息，请参阅 [View and Modify Publication Properties](view-and-modify-publication-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="380bf-106">For more information about accessing this dialog box, see [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span> <span data-ttu-id="380bf-107">有关添加和删除项目的注意事项的信息，请参阅[向现有发布添加项目和从中删除项目](add-articles-to-and-drop-articles-from-existing-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="380bf-107">For information about the considerations for adding and dropping articles, see [Add Articles to and Drop Articles from Existing Publications](add-articles-to-and-drop-articles-from-existing-publications.md).</span></span>  
  
### <a name="to-add-an-article-after-a-publication-is-created"></a><span data-ttu-id="380bf-108">创建发布后添加项目</span><span class="sxs-lookup"><span data-stu-id="380bf-108">To add an article after a publication is created</span></span>  
  
1.  <span data-ttu-id="380bf-109">在“发布属性 - \<Publication>”对话框的“项目”页面上，取消选中“仅在列表中显示已选中的对象”复选框  。</span><span class="sxs-lookup"><span data-stu-id="380bf-109">On the **Articles** page of the **Publication Properties - \<Publication>** dialog box, clear the **Show only checked objects in the list** check box.</span></span> <span data-ttu-id="380bf-110">这样可以查看发布数据库中未发布的对象。</span><span class="sxs-lookup"><span data-stu-id="380bf-110">This allows you to see the unpublished objects in the publication database.</span></span>  
  
2.  <span data-ttu-id="380bf-111">选中要添加的每个项目旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="380bf-111">Select the check box next to each article you want to add.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-delete-an-article"></a><span data-ttu-id="380bf-112">删除项目</span><span class="sxs-lookup"><span data-stu-id="380bf-112">To delete an article</span></span>  
  
1.  <span data-ttu-id="380bf-113">在“发布属性 - \<Publication>”对话框的“项目”页面上，取消选中要删除的每个项目旁边的复选框 。</span><span class="sxs-lookup"><span data-stu-id="380bf-113">On the **Articles** page of the **Publication Properties - \<Publication>** dialog box, clear the check box next to each article you want to delete.</span></span>  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="380bf-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="380bf-114">See Also</span></span>  
 <span data-ttu-id="380bf-115">[Define an Article](define-an-article.md) </span><span class="sxs-lookup"><span data-stu-id="380bf-115">[Define an Article](define-an-article.md) </span></span>  
 [<span data-ttu-id="380bf-116">发布数据和数据库对象</span><span class="sxs-lookup"><span data-stu-id="380bf-116">Publish Data and Database Objects</span></span>](publish-data-and-database-objects.md)  
  
  
