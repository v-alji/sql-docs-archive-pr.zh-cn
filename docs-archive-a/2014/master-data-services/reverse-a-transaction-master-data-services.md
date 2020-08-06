---
title: 撤消事物 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- transactions [Master Data Services], reversing
ms.assetid: 6f7c3f07-0f64-4283-8c9c-93facd00a046
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: fb5b1b0932b65b1d6f8fe7b1bc842836e21aaca6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688959"
---
# <a name="reverse-a-transaction-master-data-services"></a><span data-ttu-id="e82b6-102">撤消事务 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="e82b6-102">Reverse a Transaction (Master Data Services)</span></span>
  <span data-ttu-id="e82b6-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，管理员可以在需要撤消操作时撤消事务。</span><span class="sxs-lookup"><span data-stu-id="e82b6-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], administrators can reverse a transaction when an action needs to be undone.</span></span> <span data-ttu-id="e82b6-104">事务的示例包括属性值更改、层次结构移动或成员删除。</span><span class="sxs-lookup"><span data-stu-id="e82b6-104">Examples of transactions are attribute value changes, hierarchy moves, or member deletions.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e82b6-105">先决条件</span><span class="sxs-lookup"><span data-stu-id="e82b6-105">Prerequisites</span></span>  
  
-   <span data-ttu-id="e82b6-106">您必须有权访问 **“版本管理”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="e82b6-106">You must have permission to access the **Version Management** functional area.</span></span>  
  
-   <span data-ttu-id="e82b6-107">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="e82b6-107">You must be a model administrator.</span></span> <span data-ttu-id="e82b6-108">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="e82b6-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-reverse-a-transaction"></a><span data-ttu-id="e82b6-109">撤消事务</span><span class="sxs-lookup"><span data-stu-id="e82b6-109">To reverse a transaction</span></span>  
  
1.  <span data-ttu-id="e82b6-110">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 主页上，单击 **“版本管理”**。</span><span class="sxs-lookup"><span data-stu-id="e82b6-110">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, click **Version Management**.</span></span>  
  
2.  <span data-ttu-id="e82b6-111">在菜单栏上，单击 **“事务”**。</span><span class="sxs-lookup"><span data-stu-id="e82b6-111">On the menu bar, click **Transactions**.</span></span>  
  
3.  <span data-ttu-id="e82b6-112">在 **“事务”** 页上，从 **“模型”** 列表中选择某个模型。</span><span class="sxs-lookup"><span data-stu-id="e82b6-112">On the **Transactions** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="e82b6-113">\*\*\*\* 从“版本”列表中，选择某一版本。</span><span class="sxs-lookup"><span data-stu-id="e82b6-113">From the **Version** list, select a version.</span></span>  
  
5.  <span data-ttu-id="e82b6-114">单击网格中您要撤消的事务所对应的行。</span><span class="sxs-lookup"><span data-stu-id="e82b6-114">Click the row in the grid for the transaction you want to reverse.</span></span>  
  
6.  <span data-ttu-id="e82b6-115">单击 **“撤消事务”**。</span><span class="sxs-lookup"><span data-stu-id="e82b6-115">Click **Reverse Transaction**.</span></span>  
  
7.  <span data-ttu-id="e82b6-116">在确认对话框中，单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="e82b6-116">In the confirmation dialog box, click **OK**.</span></span> <span data-ttu-id="e82b6-117">将向网格添加另一事务以记录撤消的事务。</span><span class="sxs-lookup"><span data-stu-id="e82b6-117">Another transaction is added to the grid to record the reversed transaction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e82b6-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e82b6-118">See Also</span></span>  
 <span data-ttu-id="e82b6-119">[Master Data Services 的事务 &#40;&#41;](../../2014/master-data-services/transactions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="e82b6-119">[Transactions &#40;Master Data Services&#41;](../../2014/master-data-services/transactions-master-data-services.md) </span></span>  
 [<span data-ttu-id="e82b6-120">重新激活成员或集合 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="e82b6-120">Reactivate a Member or Collection &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/reactivate-a-member-or-collection-master-data-services.md)  
  
  
