---
title: 添加非 SQL Server 订阅服务器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.addnonsqlsubscriber.f1
ms.assetid: 21beeaa0-4b9e-48da-be63-1b9ff14e03d2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e36d048b11fcc71b27ab0ab2ee815b0284187c4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587364"
---
# <a name="add-non-sql-server-subscriber"></a><span data-ttu-id="0680a-102">添加非 SQL Server 订阅服务器</span><span class="sxs-lookup"><span data-stu-id="0680a-102">Add Non-SQL Server Subscriber</span></span>
  <span data-ttu-id="0680a-103">复制支持创建对 Oracle 和 IBM DB2 订阅服务器的快照和事务发布的推送订阅。</span><span class="sxs-lookup"><span data-stu-id="0680a-103">Replication supports creating push subscriptions to snapshot and transactional publications for Oracle and IBM DB2 Subscribers.</span></span>  
  
## <a name="options"></a><span data-ttu-id="0680a-104">选项</span><span class="sxs-lookup"><span data-stu-id="0680a-104">Options</span></span>  
 <span data-ttu-id="0680a-105">**要添加的订阅服务器类型**</span><span class="sxs-lookup"><span data-stu-id="0680a-105">**Type of Subscriber to add**</span></span>  
 <span data-ttu-id="0680a-106">选择 Oracle 订阅服务器或 IBM DB2 订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="0680a-106">Select an Oracle Subscriber or IBM DB2 Subscriber.</span></span> <span data-ttu-id="0680a-107">有关对这些订阅服务器的支持的详细信息，请参阅[非 SQL Server 订阅服务器](non-sql/non-sql-server-subscribers.md)。</span><span class="sxs-lookup"><span data-stu-id="0680a-107">For more information about support for these Subscribers, see [Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md).</span></span>  
  
 <span data-ttu-id="0680a-108">**数据源名称**</span><span class="sxs-lookup"><span data-stu-id="0680a-108">**Data source name**</span></span>  
 <span data-ttu-id="0680a-109">用于在网络上定位数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="0680a-109">The name used to locate the database on a network.</span></span> <span data-ttu-id="0680a-110">复制使用数据源名称以及在此向导的 **“分发代理安全性”** 页中指定的登录名、密码和所有连接选项，来为数据库生成连接字符串。</span><span class="sxs-lookup"><span data-stu-id="0680a-110">Replication produces a connection string for the database using the data source name, combined with the login, password, and any connection options you specify in the **Distribution Agent Security** page in this wizard.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0680a-111">在分发代理尝试初始化订阅之前， [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不能验证数据源名称和连接字符串。</span><span class="sxs-lookup"><span data-stu-id="0680a-111">The data source name and connection string are not validated by [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] until the Distribution Agent attempts to initialize the subscription.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0680a-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0680a-112">See Also</span></span>  
 <span data-ttu-id="0680a-113">[为非 SQL Server 订阅服务器创建订阅](create-a-subscription-for-a-non-sql-server-subscriber.md) </span><span class="sxs-lookup"><span data-stu-id="0680a-113">[Create a Subscription for a Non-SQL Server Subscriber](create-a-subscription-for-a-non-sql-server-subscriber.md) </span></span>  
 <span data-ttu-id="0680a-114">[Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md) </span><span class="sxs-lookup"><span data-stu-id="0680a-114">[Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md) </span></span>  
 [<span data-ttu-id="0680a-115">订阅发布</span><span class="sxs-lookup"><span data-stu-id="0680a-115">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
