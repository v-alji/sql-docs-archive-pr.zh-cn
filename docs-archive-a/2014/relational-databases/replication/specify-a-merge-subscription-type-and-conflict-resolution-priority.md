---
title: 指定合并订阅类型和冲突解决优先级 (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], merge subscription resolvers
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 2b828d83-2341-4924-b92a-4f81a22246c0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a19ae6246fe59308283fbaf2f35e2c49f96b140c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694442"
---
# <a name="specify-a-merge-subscription-type-and-conflict-resolution-priority-sql-server-management-studio"></a><span data-ttu-id="3c459-102">指定合并订阅类型和冲突解决优先级 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="3c459-102">Specify a Merge Subscription Type and Conflict Resolution Priority (SQL Server Management Studio)</span></span>
  <span data-ttu-id="3c459-103">可以在新建订阅向导的 **“订阅类型”** 页上指定合并订阅类型和冲突解决优先级。</span><span class="sxs-lookup"><span data-stu-id="3c459-103">Specify a merge subscription type and conflict resolution priority on the **Subscription Type** page of the New Subscription Wizard.</span></span> <span data-ttu-id="3c459-104">有关使用此向导的详细信息，请参阅 [Create a Pull Subscription](create-a-pull-subscription.md) 和 [Create a Push Subscription](create-a-push-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="3c459-104">For more information about using this wizard, see [Create a Pull Subscription](create-a-pull-subscription.md) and [Create a Push Subscription](create-a-push-subscription.md).</span></span>  
  
 <span data-ttu-id="3c459-105">创建订阅后订阅类型无法修改，但对于“订阅属性 - \<Publisher>: \<PublicationDatabase>”对话框中的服务器订阅类型来说，优先级可以修改。</span><span class="sxs-lookup"><span data-stu-id="3c459-105">Subscription type cannot be modified after a subscription is created, but priority can be modified for the server subscription type in the **Subscription Properties - \<Publisher>: \<PublicationDatabase>** dialog box.</span></span> <span data-ttu-id="3c459-106">有关访问此对话框的详细信息，请参阅 [View and Modify Push Subscription Properties](view-and-modify-push-subscription-properties.md) 和 [View and Modify Pull Subscription Properties](view-and-modify-pull-subscription-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="3c459-106">For more information about accessing this dialog box, see [View and Modify Push Subscription Properties](view-and-modify-push-subscription-properties.md) and [View and Modify Pull Subscription Properties](view-and-modify-pull-subscription-properties.md).</span></span>  
  
### <a name="to-specify-a-merge-subscription-type-and-conflict-resolution-priority"></a><span data-ttu-id="3c459-107">指定合并订阅类型和冲突解决优先级</span><span class="sxs-lookup"><span data-stu-id="3c459-107">To specify a merge subscription type and conflict resolution priority</span></span>  
  
1.  <span data-ttu-id="3c459-108">在新建订阅向导的 **“订阅类型”** 页上，为 **“订阅类型”** 选项选择 **“客户端”** 或 **“服务器”** 。</span><span class="sxs-lookup"><span data-stu-id="3c459-108">On the **Subscription Type** page of the New Subscription Wizard, select **Client** or **Server** for the **Subscription Type** option.</span></span>  
  
2.  <span data-ttu-id="3c459-109">如果选择 **“服务器”** 订阅类型，还要输入 **“冲突解决的优先级”** 选项的值（0.00 到 99.99）。</span><span class="sxs-lookup"><span data-stu-id="3c459-109">If you select a subscription type of **Server**, also enter a value (0.00 to 99.99) for the **Priority for Conflict Resolution** option.</span></span>  
  
### <a name="to-modify-the-conflict-resolution-priority"></a><span data-ttu-id="3c459-110">修改冲突解决优先级</span><span class="sxs-lookup"><span data-stu-id="3c459-110">To modify the conflict resolution priority</span></span>  
  
1.  <span data-ttu-id="3c459-111">在发布服务器的“订阅属性 - \<Publisher>: \<PublicationDatabase>”中，输入“优先级”选项的值（0.00 到 99.99）。</span><span class="sxs-lookup"><span data-stu-id="3c459-111">In the **Subscription Properties - \<Publisher>: \<PublicationDatabase>** at the Publisher, enter a value (0.00 to 99.99) for the **Priority** option.</span></span>  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3c459-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3c459-112">See Also</span></span>  
 <span data-ttu-id="3c459-113">[Advanced Merge Replication Conflict Detection and Resolution](merge/advanced-merge-replication-conflict-detection-and-resolution.md) </span><span class="sxs-lookup"><span data-stu-id="3c459-113">[Advanced Merge Replication Conflict Detection and Resolution](merge/advanced-merge-replication-conflict-detection-and-resolution.md) </span></span>  
 [<span data-ttu-id="3c459-114">订阅发布</span><span class="sxs-lookup"><span data-stu-id="3c459-114">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
