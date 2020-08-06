---
title: 提交版本 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- committing versions [Master Data Services]
- versions [Master Data Services], committing
ms.assetid: 6b967a39-b333-4b84-9e5f-4fb07e156826
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: cec3244d4ddaa78d9168e3ede503fa16756633a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689503"
---
# <a name="commit-a-version-master-data-services"></a><span data-ttu-id="e7077-102">提交版本 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="e7077-102">Commit a Version (Master Data Services)</span></span>
  <span data-ttu-id="e7077-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，提交某一模型的版本以便防止对该模型的成员及其属性的更改。</span><span class="sxs-lookup"><span data-stu-id="e7077-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], commit a version of a model to prevent changes to the model's members and their attributes.</span></span> <span data-ttu-id="e7077-104">已提交的版本无法取消锁定。</span><span class="sxs-lookup"><span data-stu-id="e7077-104">Committed versions cannot be unlocked.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e7077-105">先决条件</span><span class="sxs-lookup"><span data-stu-id="e7077-105">Prerequisites</span></span>  
 <span data-ttu-id="e7077-106">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="e7077-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="e7077-107">您必须有权访问 **“版本管理”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="e7077-107">You must have permission to access the **Version Management** functional area.</span></span>  
  
-   <span data-ttu-id="e7077-108">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="e7077-108">You must be a model administrator.</span></span> <span data-ttu-id="e7077-109">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="e7077-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="e7077-110">版本的状态必须是 **“已锁定”**。</span><span class="sxs-lookup"><span data-stu-id="e7077-110">The version's status must be **Locked**.</span></span> <span data-ttu-id="e7077-111">有关详细信息，请参阅 [锁定版本 (Master Data Services)](../../2014/master-data-services/lock-a-version-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="e7077-111">For more information, see [Lock a Version &#40;Master Data Services&#41;](../../2014/master-data-services/lock-a-version-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="e7077-112">所有成员必须已经成功验证。</span><span class="sxs-lookup"><span data-stu-id="e7077-112">All members must have validated successfully.</span></span>  
  
### <a name="to-commit-a-version"></a><span data-ttu-id="e7077-113">提交版本</span><span class="sxs-lookup"><span data-stu-id="e7077-113">To commit a version</span></span>  
  
1.  <span data-ttu-id="e7077-114">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“版本管理”**。</span><span class="sxs-lookup"><span data-stu-id="e7077-114">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **Version Management**.</span></span>  
  
2.  <span data-ttu-id="e7077-115">在 **“管理版本”** 页上，从菜单栏中，单击 **“验证版本”**。</span><span class="sxs-lookup"><span data-stu-id="e7077-115">On the **Manage Versions** page, on the menu bar, click **Validate Version**.</span></span>  
  
3.  <span data-ttu-id="e7077-116">在 **“验证版本”** 页上，选择要提交的模型和版本。</span><span class="sxs-lookup"><span data-stu-id="e7077-116">On the **Validate Version** page, select the model and version you want to commit.</span></span>  
  
4.  <span data-ttu-id="e7077-117">单击“提交”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="e7077-117">Click **Commit**.</span></span>  
  
5.  <span data-ttu-id="e7077-118">在确认对话框中，单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="e7077-118">In the confirmation dialog box, click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="e7077-119">后续步骤</span><span class="sxs-lookup"><span data-stu-id="e7077-119">Next Steps</span></span>  
  
-   [<span data-ttu-id="e7077-120">创建版本标志 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="e7077-120">Create a Version Flag &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-version-flag-master-data-services.md)  
  
-   [<span data-ttu-id="e7077-121">向版本分配标志 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="e7077-121">Assign a Flag to a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/assign-a-flag-to-a-version-master-data-services.md)  
  
-   [<span data-ttu-id="e7077-122">复制版本 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="e7077-122">Copy a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/copy-a-version-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="e7077-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e7077-123">See Also</span></span>  
 [<span data-ttu-id="e7077-124">版本 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="e7077-124">Versions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/versions-master-data-services.md)  
  
  
