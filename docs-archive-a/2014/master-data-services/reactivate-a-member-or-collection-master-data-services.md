---
title: 重新激活成员或集合 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- collections [Master Data Services], reactivating
- consolidated members [Master Data Services], reactivating
- reactivating members [Master Data Services]
- members [Master Data Services], reactivating
- reactivating collections [Master Data Services]
- leaf members [Master Data Services], reactivating
ms.assetid: bb4884c0-3658-4763-92d1-636804278b1c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c449a5a277128bbca6ae24e848bcf12cb0881968
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589192"
---
# <a name="reactivate-a-member-or-collection-master-data-services"></a><span data-ttu-id="baaaa-102">重新激活成员或集合 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="baaaa-102">Reactivate a Member or Collection (Master Data Services)</span></span>
  <span data-ttu-id="baaaa-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，可以重新激活以下成员：</span><span class="sxs-lookup"><span data-stu-id="baaaa-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you can reactivate a member that was either:</span></span>  
  
-   <span data-ttu-id="baaaa-104">这些成员已通过临时过程停用。</span><span class="sxs-lookup"><span data-stu-id="baaaa-104">Deactivated by the staging process.</span></span>  
  
-   <span data-ttu-id="baaaa-105">已在 MDS [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]中删除这些成员。</span><span class="sxs-lookup"><span data-stu-id="baaaa-105">Deleted in the MDS [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)].</span></span>  
  
-   <span data-ttu-id="baaaa-106">已在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 应用程序中删除这些成员。</span><span class="sxs-lookup"><span data-stu-id="baaaa-106">Deleted in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application.</span></span>  
  
 <span data-ttu-id="baaaa-107">重新激活成员时，将还原成员的属性以及成员在层次结构和集合中的成员身份。</span><span class="sxs-lookup"><span data-stu-id="baaaa-107">When you reactivate a member, its attributes and its membership in hierarchies and collections are restored.</span></span>  
  
 <span data-ttu-id="baaaa-108">您还可以重新激活集合。</span><span class="sxs-lookup"><span data-stu-id="baaaa-108">You can also reactivate collections.</span></span> <span data-ttu-id="baaaa-109">重新激活集合时，将还原集合的属性和集合中的成员。</span><span class="sxs-lookup"><span data-stu-id="baaaa-109">When you do, the collection's attributes and the members that belong to the collection are restored.</span></span>  
  
 <span data-ttu-id="baaaa-110">重新激活集合或成员时，将还原以前的所有事务。</span><span class="sxs-lookup"><span data-stu-id="baaaa-110">When either a collection or member is reactivated, all previous transactions are restored.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="baaaa-111">必备条件</span><span class="sxs-lookup"><span data-stu-id="baaaa-111">Prerequisites</span></span>  
 <span data-ttu-id="baaaa-112">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="baaaa-112">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="baaaa-113">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，您必须具有对 **“版本管理”** 功能区域的权限。</span><span class="sxs-lookup"><span data-stu-id="baaaa-113">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], you must have permission to the **Version Management** functional area.</span></span>  
  
-   <span data-ttu-id="baaaa-114">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="baaaa-114">You must be a model administrator.</span></span> <span data-ttu-id="baaaa-115">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="baaaa-115">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-reactivate-a-member-or-collection"></a><span data-ttu-id="baaaa-116">重新激活成员或集合</span><span class="sxs-lookup"><span data-stu-id="baaaa-116">To reactivate a member or collection</span></span>  
  
1.  <span data-ttu-id="baaaa-117">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 主页上，单击 **“版本管理”**。</span><span class="sxs-lookup"><span data-stu-id="baaaa-117">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, click **Version Management**.</span></span>  
  
2.  <span data-ttu-id="baaaa-118">在菜单栏上，单击 **“事务”**。</span><span class="sxs-lookup"><span data-stu-id="baaaa-118">On the menu bar, click **Transactions**.</span></span>  
  
3.  <span data-ttu-id="baaaa-119">在 **“事务”** 页上，从 **“模型”** 列表中选择某个模型。</span><span class="sxs-lookup"><span data-stu-id="baaaa-119">On the **Transactions** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="baaaa-120">\*\*\*\* 从“版本”列表中，选择某一版本。</span><span class="sxs-lookup"><span data-stu-id="baaaa-120">From the **Version** list, select a version.</span></span>  
  
5.  <span data-ttu-id="baaaa-121">在 **“事务”** 窗格中，单击要重新激活的成员或集合所对应的行。</span><span class="sxs-lookup"><span data-stu-id="baaaa-121">In the **Transactions** pane, click the row for the member or collection you want to reactivate.</span></span> <span data-ttu-id="baaaa-122">此行应在“旧值”\*\*\*\* 列中显示“活动”\*\*\*\* 并在“新值”\*\*\*\* 列中显示“已停用”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="baaaa-122">This row should have **Active** displayed in the **Prior Value** column and **De-Activated** in the **New Value** column.</span></span>  
  
6.  <span data-ttu-id="baaaa-123">单击 **“撤消事务”**。</span><span class="sxs-lookup"><span data-stu-id="baaaa-123">Click **Reverse Transaction**.</span></span>  
  
7.  <span data-ttu-id="baaaa-124">在确认对话框中，单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="baaaa-124">On the confirmation dialog box, click **OK**.</span></span> <span data-ttu-id="baaaa-125">添加新事务，在 **“新值”** 列中显示 **“活动”** 。</span><span class="sxs-lookup"><span data-stu-id="baaaa-125">A new transaction is added, showing **Active** in the **New Value** column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baaaa-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="baaaa-126">See Also</span></span>  
 <span data-ttu-id="baaaa-127">[使用 &#40;Master Data Services 的临时过程来停用或删除成员&#41;](add-update-and-delete-data-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="baaaa-127">[Deactivate or Delete Members by Using the Staging Process &#40;Master Data Services&#41;](add-update-and-delete-data-master-data-services.md) </span></span>  
 <span data-ttu-id="baaaa-128">[&#40;Master Data Services 中删除成员或集合&#41;](../../2014/master-data-services/delete-a-member-or-collection-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="baaaa-128">[Delete a Member or Collection &#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-member-or-collection-master-data-services.md) </span></span>  
 <span data-ttu-id="baaaa-129">[成员 &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="baaaa-129">[Members &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md) </span></span>  
 [<span data-ttu-id="baaaa-130">集合 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="baaaa-130">Collections &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/collections-master-data-services.md)  
  
  
