---
title: 设置历史记录保持期 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- history retention periods [SQL Server replication]
- retention periods [SQL Server replication]
ms.assetid: c288daab-5181-4d4b-ba2a-8a147098e758
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 13dcf2ad9a9d619a7fdef9c1ed3f7b970e420cdd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591246"
---
# <a name="set-the-history-retention-period-sql-server-management-studio"></a><span data-ttu-id="1a78a-102">设置历史记录保持期 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="1a78a-102">Set the History Retention Period (SQL Server Management Studio)</span></span>
  <span data-ttu-id="1a78a-103">在“分发数据库属性 - \<DistributionDatabase>”对话框的“常规”页上指定历史记录保持期 。</span><span class="sxs-lookup"><span data-stu-id="1a78a-103">Specify the history retention period on the **General** page of the **Distribution Database Properties - \<DistributionDatabase>** dialog box.</span></span> <span data-ttu-id="1a78a-104">此设置控制复制代理历史记录可存储的时间。</span><span class="sxs-lookup"><span data-stu-id="1a78a-104">This setting controls how long replication agent history is stored.</span></span> <span data-ttu-id="1a78a-105">可以从“分发服务器属性 - \<Distributor>”对话框的“常规”页中访问该页 。</span><span class="sxs-lookup"><span data-stu-id="1a78a-105">This page is available from the **General** page of the **Distributor Properties - \<Distributor>** dialog box.</span></span> <span data-ttu-id="1a78a-106">有关访问此对话框的详细信息，请参阅[查看和修改分发服务器和发布服务器属性](view-and-modify-distributor-and-publisher-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="1a78a-106">For more information about accessing this dialog box, see [View and Modify Distributor and Publisher Properties](view-and-modify-distributor-and-publisher-properties.md).</span></span>  
  
### <a name="to-specify-the-history-retention-period"></a><span data-ttu-id="1a78a-107">指定历史记录保持期</span><span class="sxs-lookup"><span data-stu-id="1a78a-107">To specify the history retention period</span></span>  
  
1.  <span data-ttu-id="1a78a-108">在“分发服务器属性 - \<Distributor>”对话框的“常规”页上，单击分发数据库的属性按钮 (…)  。</span><span class="sxs-lookup"><span data-stu-id="1a78a-108">On the **General** page of the **Distributor Properties - \<Distributor>** dialog box, click the properties button (**...**) for the distribution database.</span></span>  
  
2.  <span data-ttu-id="1a78a-109">在 **“至少存储复制性能的历史记录”** 框中输入一个值。</span><span class="sxs-lookup"><span data-stu-id="1a78a-109">Enter a value in the **Store replication performance history at least** box.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1a78a-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1a78a-110">See Also</span></span>  
 [<span data-ttu-id="1a78a-111">配置分发</span><span class="sxs-lookup"><span data-stu-id="1a78a-111">Configure Distribution</span></span>](configure-distribution.md)  
  
  
