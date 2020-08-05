---
title: Web 服务器信息 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.webserverinformation.f1
ms.assetid: 86d72275-45c7-459f-98cf-f5a366ed279c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f7b461ed26b3e234f083add3312e256e164efc9b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580665"
---
# <a name="web-server-information"></a><span data-ttu-id="1c515-102">Web 服务器信息</span><span class="sxs-lookup"><span data-stu-id="1c515-102">Web Server Information</span></span>
  <span data-ttu-id="1c515-103">若要使用合并复制的 Web 同步选项，必须提供 Web 服务器信息。</span><span class="sxs-lookup"><span data-stu-id="1c515-103">Web server information is required to use the Web synchronization option for merge replication.</span></span> <span data-ttu-id="1c515-104">有关配置 Web 同步的信息，请参阅[配置 Web 同步](configure-web-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="1c515-104">For information about configuring Web synchronization, see [Configure Web Synchronization](configure-web-synchronization.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="1c515-105">选项</span><span class="sxs-lookup"><span data-stu-id="1c515-105">Options</span></span>  
 <span data-ttu-id="1c515-106">**Web 服务器地址**</span><span class="sxs-lookup"><span data-stu-id="1c515-106">**Web server address**</span></span>  
 <span data-ttu-id="1c515-107">如果在“发布属性”对话框的“FTP 快照和 Internet”页中指定了 Web 服务器地址，该地址将作为默认值显示在此文本框中   。</span><span class="sxs-lookup"><span data-stu-id="1c515-107">If you specified a Web server address in the **FTP Snapshot andInternet** page of the **Publication Properties** dialog box, it appears in this text box as a default.</span></span> <span data-ttu-id="1c515-108">您可以接受此默认值，也可以为同步此订阅的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet 信息服务 (IIS) 服务器输入完全限定的 Web 服务器地址。</span><span class="sxs-lookup"><span data-stu-id="1c515-108">Either accept the default or enter a fully qualified Web server address for the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS) server that synchronizes this subscription.</span></span>  
  
 <span data-ttu-id="1c515-109">**各个订阅服务器将如何连接到 Web 服务器?**</span><span class="sxs-lookup"><span data-stu-id="1c515-109">**How will each Subscriber connect to the Web server?**</span></span>  
 <span data-ttu-id="1c515-110">指定用于连接到 Web 服务器的身份验证的类型。</span><span class="sxs-lookup"><span data-stu-id="1c515-110">Specify the type of authentication used to connect to the Web server.</span></span> <span data-ttu-id="1c515-111">建议您将基本身份验证与安全套接字层 (SSL) 一起使用，以连接到 IIS 服务器。</span><span class="sxs-lookup"><span data-stu-id="1c515-111">It is recommended to use Basic Authentication for connections to the IIS server in conjunction with Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="1c515-112">如果选择了基本身份验证，请输入用于从订阅服务器连接到 IIS 服务器的登录名和密码。</span><span class="sxs-lookup"><span data-stu-id="1c515-112">If you select Basic Authentication, enter the login and password that will be used to connect from the Subscriber to the IIS server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c515-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1c515-113">See Also</span></span>  
 <span data-ttu-id="1c515-114">[Create a Pull Subscription](create-a-pull-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="1c515-114">[Create a Pull Subscription](create-a-pull-subscription.md) </span></span>  
 <span data-ttu-id="1c515-115">[查看和修改请求订阅属性](view-and-modify-pull-subscription-properties.md) </span><span class="sxs-lookup"><span data-stu-id="1c515-115">[View and Modify Pull Subscription Properties](view-and-modify-pull-subscription-properties.md) </span></span>  
 <span data-ttu-id="1c515-116">[Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md) </span><span class="sxs-lookup"><span data-stu-id="1c515-116">[Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md) </span></span>  
 <span data-ttu-id="1c515-117">[Subscribe to Publications](subscribe-to-publications.md) </span><span class="sxs-lookup"><span data-stu-id="1c515-117">[Subscribe to Publications](subscribe-to-publications.md) </span></span>  
 [<span data-ttu-id="1c515-118">合并复制的 Web 同步</span><span class="sxs-lookup"><span data-stu-id="1c515-118">Web Synchronization for Merge Replication</span></span>](web-synchronization-for-merge-replication.md)  
  
  