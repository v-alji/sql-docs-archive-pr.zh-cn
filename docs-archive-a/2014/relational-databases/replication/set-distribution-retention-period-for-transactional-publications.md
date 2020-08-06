---
title: 设置事务发布的分发保持期 (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- transaction retention periods [SQL Server replication]
- retention periods [SQL Server replication]
ms.assetid: 9a98c53a-fea5-4235-b23d-6c69587c5676
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a68f092c63e75196ab82a81d2a8ca36d13142813
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591247"
---
# <a name="set-the-distribution-retention-period-for-transactional-publications-sql-server-management-studio"></a><span data-ttu-id="6d4d1-102">设置事务发布的分发保持期 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="6d4d1-102">Set the Distribution Retention Period for Transactional Publications (SQL Server Management Studio)</span></span>
  <span data-ttu-id="6d4d1-103">在“分发数据库属性 - \<DistributionDatabase>”对话框中指定最小分发保持期和最大分发保持期。</span><span class="sxs-lookup"><span data-stu-id="6d4d1-103">Specify the minimum distribution retention period and maximum distribution retention period on the **Distribution Database Properties - \<DistributionDatabase>** dialog box.</span></span> <span data-ttu-id="6d4d1-104">可以从“分发服务器属性 - \<Distributor>”对话框的“常规”页中访问该对话框。</span><span class="sxs-lookup"><span data-stu-id="6d4d1-104">This is available from the **General** page of the **Distributor Properties - \<Distributor>** dialog box.</span></span> <span data-ttu-id="6d4d1-105">有关访问此对话框的详细信息，请参阅[查看和修改分发服务器和发布服务器属性](view-and-modify-distributor-and-publisher-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="6d4d1-105">For more information about accessing this dialog box, see [View and Modify Distributor and Publisher Properties](view-and-modify-distributor-and-publisher-properties.md).</span></span>  
  
### <a name="to-specify-the-distribution-retention-period"></a><span data-ttu-id="6d4d1-106">指定分发保持期</span><span class="sxs-lookup"><span data-stu-id="6d4d1-106">To specify the distribution retention period</span></span>  
  
1.  <span data-ttu-id="6d4d1-107">在“分发服务器属性 - \<Distributor>”对话框的“常规”页上，单击分发数据库的属性按钮 (…)  。</span><span class="sxs-lookup"><span data-stu-id="6d4d1-107">On the **General** page of the **Distributor Properties - \<Distributor>** dialog box, click the properties button (**...**) for the distribution database.</span></span>  
  
2.  <span data-ttu-id="6d4d1-108">若要指定最小分发保持期，请在 **“至少”** 框中输入一个值；若要指定最大分发保持期，请在 **“但不超过”** 框中输入一个值。</span><span class="sxs-lookup"><span data-stu-id="6d4d1-108">To specify the minimum distribution retention period, enter a value in the **At least** box; to specify the maximum distribution retention period, enter a value in the **But not more than** box.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6d4d1-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6d4d1-109">See Also</span></span>  
 <span data-ttu-id="6d4d1-110">[“配置分发”](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="6d4d1-110">[Configure Distribution](configure-distribution.md) </span></span>  
 [<span data-ttu-id="6d4d1-111">订阅过期和停用</span><span class="sxs-lookup"><span data-stu-id="6d4d1-111">Subscription Expiration and Deactivation</span></span>](subscription-expiration-and-deactivation.md)  
  
  
