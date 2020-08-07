---
title: 为事物添加批注 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- annotations [Master Data Services], for transactions
ms.assetid: f5a6b2ca-56de-4e42-9da8-fba0ac3e8d92
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c384f4241d0ddcd78fd8942fe28da8c0b5b1e77c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690691"
---
# <a name="annotate-a-transaction-master-data-services"></a><span data-ttu-id="a64dd-102">为事务添加批注 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="a64dd-102">Annotate a Transaction (Master Data Services)</span></span>
  <span data-ttu-id="a64dd-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，为保留历史记录的目的而希望提供有关事务的支持详细信息时，可以为事务添加批注。</span><span class="sxs-lookup"><span data-stu-id="a64dd-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], annotate a transaction when you want to provide supporting details about the transaction for historical purposes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a64dd-104">您无法删除批注。</span><span class="sxs-lookup"><span data-stu-id="a64dd-104">You cannot delete annotations.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a64dd-105">必备条件</span><span class="sxs-lookup"><span data-stu-id="a64dd-105">Prerequisites</span></span>  
  
-   <span data-ttu-id="a64dd-106">若要为创建的事务添加批注，您必须有权访问 **“资源管理器”** 功能区域，并且必须至少对要添加批注的模型对象具有 **“更新”** 权限。</span><span class="sxs-lookup"><span data-stu-id="a64dd-106">To annotate transactions that you created, you must have permission to access the **Explorer** functional area, and have a minimum of **Update** permission to the model object you want to annotate.</span></span>  
  
-   <span data-ttu-id="a64dd-107">若要为所有用户的事务添加批注，您必须有权访问 **“版本管理”** 功能区域并且必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="a64dd-107">To annotate transactions for all users, you must have permission to access the **Version Management** functional area and be a model administrator.</span></span> <span data-ttu-id="a64dd-108">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="a64dd-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-annotate-a-transaction-in-explorer"></a><span data-ttu-id="a64dd-109">为资源管理器中为事务添加批注</span><span class="sxs-lookup"><span data-stu-id="a64dd-109">To annotate a transaction in Explorer</span></span>  
  
1.  <span data-ttu-id="a64dd-110">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 在 \*\*\*\* 主页上，从“模型”列表中，选择模型。</span><span class="sxs-lookup"><span data-stu-id="a64dd-110">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, from the **Model** list, select a model.</span></span>  
  
2.  <span data-ttu-id="a64dd-111">\*\*\*\* 从“版本”列表中，选择某一版本。</span><span class="sxs-lookup"><span data-stu-id="a64dd-111">From the **Version** list, select a version.</span></span>  
  
3.  <span data-ttu-id="a64dd-112">单击 **“资源管理器”**。</span><span class="sxs-lookup"><span data-stu-id="a64dd-112">Click **Explorer**.</span></span>  
  
4.  <span data-ttu-id="a64dd-113">从菜单栏中指向 **“实体”** ，然后单击包含具有要添加批注的事务的成员的实体。</span><span class="sxs-lookup"><span data-stu-id="a64dd-113">From the menu bar, point to **Entities** and click the entity that contains the member with a transaction you want to annotate.</span></span>  
  
5.  <span data-ttu-id="a64dd-114">在网格中，单击该成员所在的行。</span><span class="sxs-lookup"><span data-stu-id="a64dd-114">In the grid, click the row of the member.</span></span>  
  
6.  <span data-ttu-id="a64dd-115">单击 **“查看事务”**。</span><span class="sxs-lookup"><span data-stu-id="a64dd-115">Click **View Transactions**.</span></span>  
  
7.  <span data-ttu-id="a64dd-116">在 **“查看事务”** 对话框中，单击要添加批注的事务。</span><span class="sxs-lookup"><span data-stu-id="a64dd-116">In the **View Transactions** dialog box, click the transaction you want to annotate.</span></span>  
  
8.  <span data-ttu-id="a64dd-117">在该对话框的底部的框中，键入您的批注。</span><span class="sxs-lookup"><span data-stu-id="a64dd-117">In the box at the bottom of the dialog box, type your annotation.</span></span>  
  
9. <span data-ttu-id="a64dd-118">单击 **“添加批注”**。</span><span class="sxs-lookup"><span data-stu-id="a64dd-118">Click **Add Annotation**.</span></span> <span data-ttu-id="a64dd-119">该批注显示在 **“批注”** 窗格中。</span><span class="sxs-lookup"><span data-stu-id="a64dd-119">The annotation is displayed in the **Annotations** pane.</span></span>  
  
### <a name="to-annotate-a-transaction-in-version-management-administrators-only"></a><span data-ttu-id="a64dd-120">在版本管理中为事务添加批注（仅限管理员）</span><span class="sxs-lookup"><span data-stu-id="a64dd-120">To annotate a transaction in Version Management (administrators only)</span></span>  
  
1.  <span data-ttu-id="a64dd-121">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 主页上，单击 **“版本管理”**。</span><span class="sxs-lookup"><span data-stu-id="a64dd-121">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, click **Version Management**.</span></span>  
  
2.  <span data-ttu-id="a64dd-122">在菜单栏上，单击 **“事务”**。</span><span class="sxs-lookup"><span data-stu-id="a64dd-122">On the menu bar, click **Transactions**.</span></span>  
  
3.  <span data-ttu-id="a64dd-123">在 **“事务”** 窗格中，单击网格中您要添加批注的事务所对应的行。</span><span class="sxs-lookup"><span data-stu-id="a64dd-123">In the **Transactions** pane, click the row in the grid for the transaction you want to annotate.</span></span>  
  
4.  <span data-ttu-id="a64dd-124">在 **“事务批注”** 窗格的 **“批注”** 框中，键入您的批注。</span><span class="sxs-lookup"><span data-stu-id="a64dd-124">In the **Transaction Annotations** pane, in the **Annotation** box, type your annotation.</span></span>  
  
5.  <span data-ttu-id="a64dd-125">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="a64dd-125">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a64dd-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a64dd-126">See Also</span></span>  
 <span data-ttu-id="a64dd-127">[批注 &#40;Master Data Services&#41;](../../2014/master-data-services/annotations-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="a64dd-127">[Annotations &#40;Master Data Services&#41;](../../2014/master-data-services/annotations-master-data-services.md) </span></span>  
 [<span data-ttu-id="a64dd-128">事务 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="a64dd-128">Transactions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/transactions-master-data-services.md)  
  
  
