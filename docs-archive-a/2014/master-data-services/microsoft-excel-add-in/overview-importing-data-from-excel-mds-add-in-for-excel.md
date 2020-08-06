---
title: MDS Add-in for Excel) 发布数据 (|Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: ea84a9aa-aeec-411b-ab8d-bc1b14f864a3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ab37a353469d1902394a3e2cd8060d9be82abb40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691300"
---
# <a name="publishing-data-mds-add-in-for-excel"></a><span data-ttu-id="cb8a6-102">发布数据（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="cb8a6-102">Publishing Data (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="cb8a6-103">在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，要想与其他用户共享数据，可将数据发布到 MDS 存储库。</span><span class="sxs-lookup"><span data-stu-id="cb8a6-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], publish data to the MDS repository when you want to share it with other users.</span></span> <span data-ttu-id="cb8a6-104">数据一经发布，即可供该外接程序的其他用户下载。</span><span class="sxs-lookup"><span data-stu-id="cb8a6-104">As soon as data is published, it is available for other users of the Add-in to download.</span></span>  
  
 <span data-ttu-id="cb8a6-105">发布数据时，已添加或更新的所有数据都会发布到 MDS 存储库。</span><span class="sxs-lookup"><span data-stu-id="cb8a6-105">When you publish data, any data you've added or updated is published to the MDS repository.</span></span> <span data-ttu-id="cb8a6-106">已删除的数据不会发布，必须单独删除数据。</span><span class="sxs-lookup"><span data-stu-id="cb8a6-106">Data you've deleted is not published-you must delete data separately.</span></span> <span data-ttu-id="cb8a6-107">有关详细信息，请参阅 [删除行（用于 Excel 的 MDS 外接程序）](delete-a-row-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="cb8a6-107">For more information, see [Delete a Row &#40;MDS Add-in for Excel&#41;](delete-a-row-mds-add-in-for-excel.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cb8a6-108">发布不能用于创建新实体。</span><span class="sxs-lookup"><span data-stu-id="cb8a6-108">Publishing cannot be used to create a new entity.</span></span> <span data-ttu-id="cb8a6-109">有关创建实体的详细信息，请参阅[创建实体（用于 Excel 的 MDS 外接程序）](create-an-entity-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="cb8a6-109">For more information about creating entities, see [Create an Entity &#40;MDS Add-in for Excel&#41;](create-an-entity-mds-add-in-for-excel.md).</span></span>  
  
## <a name="when-multiple-users-publish-at-the-same-time"></a><span data-ttu-id="cb8a6-110">当多个用户同时发布时</span><span class="sxs-lookup"><span data-stu-id="cb8a6-110">When Multiple Users Publish at the Same Time</span></span>  
 <span data-ttu-id="cb8a6-111">多个用户可以对相同的数据发布更新。</span><span class="sxs-lookup"><span data-stu-id="cb8a6-111">Multiple users can publish updates to the same data.</span></span> <span data-ttu-id="cb8a6-112">更新会在每个用户发布时保存到数据库中。</span><span class="sxs-lookup"><span data-stu-id="cb8a6-112">As each user publishes, the update is saved to the database.</span></span> <span data-ttu-id="cb8a6-113">这表示未使用最近更新的数据的用户仍可以在自己发布时更改数据值。</span><span class="sxs-lookup"><span data-stu-id="cb8a6-113">This means that a user who was not working with the most recently-updated data can still change the value when he or she publishes.</span></span>  
  
 <span data-ttu-id="cb8a6-114">只有更新的数据才会发布到数据库中。</span><span class="sxs-lookup"><span data-stu-id="cb8a6-114">Only the updates you make are published to the database.</span></span> <span data-ttu-id="cb8a6-115">不发布工作表中的任何过时数据。</span><span class="sxs-lookup"><span data-stu-id="cb8a6-115">Any out-of-date data in the worksheet is not published.</span></span>  
  
## <a name="transactions-and-annotations"></a><span data-ttu-id="cb8a6-116">事务和批注</span><span class="sxs-lookup"><span data-stu-id="cb8a6-116">Transactions and Annotations</span></span>  
 <span data-ttu-id="cb8a6-117">每个已发布的更改都保存为一个事务。</span><span class="sxs-lookup"><span data-stu-id="cb8a6-117">Each published change is saved as a transaction.</span></span> <span data-ttu-id="cb8a6-118">如果您愿意，则可以向事务添加批注（注释），解释您做出更改的原因。</span><span class="sxs-lookup"><span data-stu-id="cb8a6-118">If you choose, you can add annotations (comments) to a transaction, to explain why you made the change.</span></span>  
  
-   <span data-ttu-id="cb8a6-119">您不能为删除操作添加批注，尽管删除操作可另存为管理员可以撤消的事务。</span><span class="sxs-lookup"><span data-stu-id="cb8a6-119">You cannot annotate deletions, although deletions are saved as transactions that can be reversed by an administrator.</span></span>  
  
-   <span data-ttu-id="cb8a6-120">如果更改成员的**代码**值，则不会将其记录为事务，并且该成员以前的所有事务都将不可用。</span><span class="sxs-lookup"><span data-stu-id="cb8a6-120">If you change the **Code** value for a member, it is not recorded as a transaction, and all previous transactions for the member are unavailable.</span></span>  
  
-   <span data-ttu-id="cb8a6-121">您可以查看其他用户对成员执行的事务。</span><span class="sxs-lookup"><span data-stu-id="cb8a6-121">You can view transactions made to a member by other users.</span></span> <span data-ttu-id="cb8a6-122">还可以查看对成员执行的所有事务，即便不再对特定属性拥有权限。</span><span class="sxs-lookup"><span data-stu-id="cb8a6-122">You can also view all transactions you've made to a member, even if you no longer have permission to specific attributes.</span></span>  
  
 <span data-ttu-id="cb8a6-123">您可以查看对成员执行的所有事务。</span><span class="sxs-lookup"><span data-stu-id="cb8a6-123">You can view all transactions made to a member.</span></span> <span data-ttu-id="cb8a6-124">有关详细信息，请参阅 [查看成员的所有批注或事务（用于 Excel 的 MDS 外接程序）](view-all-annotations-or-transactions-for-a-member-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="cb8a6-124">For more information, see [View All Annotations or Transactions for a Member &#40;MDS Add-in for Excel&#41;](view-all-annotations-or-transactions-for-a-member-mds-add-in-for-excel.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="cb8a6-125">如果您输入的批注超过 500 个字符，该批注将被自动截断。</span><span class="sxs-lookup"><span data-stu-id="cb8a6-125">If you enter an annotation of more than 500 characters, the annotation is automatically truncated.</span></span>  
  
## <a name="business-rule-and-other-validation"></a><span data-ttu-id="cb8a6-126">业务规则和其他验证</span><span class="sxs-lookup"><span data-stu-id="cb8a6-126">Business Rule and Other Validation</span></span>  
 <span data-ttu-id="cb8a6-127">发布数据时，将执行验证，在确保数据准确无误后才将其添加到 MDS 存储库中。</span><span class="sxs-lookup"><span data-stu-id="cb8a6-127">When you publish data, validation is performed to ensure data is accurate before it's added to the MDS repository.</span></span> <span data-ttu-id="cb8a6-128">如果数据不符合指定的条件，则不会将其发布到存储库。</span><span class="sxs-lookup"><span data-stu-id="cb8a6-128">If the data does not meet specified criteria, it will not be published to the repository.</span></span> <span data-ttu-id="cb8a6-129">有关详细信息，请参阅[验证数据（用于 Excel 的 MDS 外接程序）](validating-data-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="cb8a6-129">For more information, see [Validating Data &#40;MDS Add-in for Excel&#41;](validating-data-mds-add-in-for-excel.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="cb8a6-130">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="cb8a6-130">Related Tasks</span></span>  
  
|<span data-ttu-id="cb8a6-131">任务说明</span><span class="sxs-lookup"><span data-stu-id="cb8a6-131">Task Description</span></span>|<span data-ttu-id="cb8a6-132">主题</span><span class="sxs-lookup"><span data-stu-id="cb8a6-132">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="cb8a6-133">将数据从活动工作表发布回 MDS 存储库。</span><span class="sxs-lookup"><span data-stu-id="cb8a6-133">Publish data from the active worksheet back to the MDS repository.</span></span>|[<span data-ttu-id="cb8a6-134">将数据从 Excel 发布到 MDS &#40;MDS Add-in for Excel&#41;</span><span class="sxs-lookup"><span data-stu-id="cb8a6-134">Publish Data from Excel to MDS &#40;MDS Add-in for Excel&#41;</span></span>](import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)|  
|<span data-ttu-id="cb8a6-135">同时从 MDS 存储库和工作表中删除行。</span><span class="sxs-lookup"><span data-stu-id="cb8a6-135">Delete a row from the MDS repository and from the worksheet at the same time.</span></span>|[<span data-ttu-id="cb8a6-136">删除行（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="cb8a6-136">Delete a Row &#40;MDS Add-in for Excel&#41;</span></span>](delete-a-row-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a><span data-ttu-id="cb8a6-137">相关内容</span><span class="sxs-lookup"><span data-stu-id="cb8a6-137">Related Content</span></span>  
  
-   [<span data-ttu-id="cb8a6-138">刷新数据（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="cb8a6-138">Refreshing Data &#40;MDS Add-in for Excel&#41;</span></span>](refreshing-data-mds-add-in-for-excel.md)  
  
-   [<span data-ttu-id="cb8a6-139">用于 Microsoft Excel 的 Master Data Services 外接程序</span><span class="sxs-lookup"><span data-stu-id="cb8a6-139">Master Data Services Add-in for Microsoft Excel</span></span>](master-data-services-add-in-for-microsoft-excel.md)  
  
  
