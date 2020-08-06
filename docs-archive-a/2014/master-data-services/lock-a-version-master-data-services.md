---
title: 锁定版本 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- versions [Master Data Services], locking
- locking versions [Master Data Services]
ms.assetid: 7bb62a84-12d8-4b29-9b6e-6aa25410618e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 68ef979b14d9bd228c7ca89a260b31b2fc6efccd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692432"
---
# <a name="lock-a-version-master-data-services"></a><span data-ttu-id="cb318-102">锁定版本 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="cb318-102">Lock a Version (Master Data Services)</span></span>
  <span data-ttu-id="cb318-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，锁定某一模型的版本以便防止对该模型的成员及其属性的更改。</span><span class="sxs-lookup"><span data-stu-id="cb318-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], lock a version of a model to prevent changes to the model's members and their attributes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cb318-104">在锁定某一版本后，模型管理员可以继续添加、编辑和删除成员。</span><span class="sxs-lookup"><span data-stu-id="cb318-104">When a version is locked, model administrators can continue to add, edit, and remove members.</span></span> <span data-ttu-id="cb318-105">对模型具有权限的其他用户只能查看成员。</span><span class="sxs-lookup"><span data-stu-id="cb318-105">Other users with permission to the model can view members only.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="cb318-106">先决条件</span><span class="sxs-lookup"><span data-stu-id="cb318-106">Prerequisites</span></span>  
 <span data-ttu-id="cb318-107">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="cb318-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="cb318-108">您必须有权访问 **“版本管理”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="cb318-108">You must have permission to access the **Version Management** functional area.</span></span>  
  
-   <span data-ttu-id="cb318-109">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="cb318-109">You must be a model administrator.</span></span> <span data-ttu-id="cb318-110">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="cb318-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="cb318-111">版本的状态必须是 **“打开”**。</span><span class="sxs-lookup"><span data-stu-id="cb318-111">The version's status must be **Open**.</span></span>  
  
### <a name="to-lock-a-version"></a><span data-ttu-id="cb318-112">锁定版本</span><span class="sxs-lookup"><span data-stu-id="cb318-112">To lock a version</span></span>  
  
1.  <span data-ttu-id="cb318-113">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“版本管理”**。</span><span class="sxs-lookup"><span data-stu-id="cb318-113">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **Version Management**.</span></span>  
  
2.  <span data-ttu-id="cb318-114">在 **“管理版本”** 页上，选择要锁定的版本对应的行。</span><span class="sxs-lookup"><span data-stu-id="cb318-114">On the **Manage Versions** page, select the row for the version that you want to lock.</span></span>  
  
3.  <span data-ttu-id="cb318-115">单击“锁定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="cb318-115">Click **Lock**.</span></span>  
  
4.  <span data-ttu-id="cb318-116">在确认对话框中，单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="cb318-116">In the confirmation dialog box, click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="cb318-117">后续步骤</span><span class="sxs-lookup"><span data-stu-id="cb318-117">Next Steps</span></span>  
  
-   [<span data-ttu-id="cb318-118">针对业务规则验证版本 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="cb318-118">Validate a Version against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
-   [<span data-ttu-id="cb318-119">提交版本 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="cb318-119">Commit a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/commit-a-version-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="cb318-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cb318-120">See Also</span></span>  
 <span data-ttu-id="cb318-121">[版本 &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="cb318-121">[Versions &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md) </span></span>  
 [<span data-ttu-id="cb318-122">取消锁定版本 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="cb318-122">Unlock a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/unlock-a-version-master-data-services.md)  
  
  
