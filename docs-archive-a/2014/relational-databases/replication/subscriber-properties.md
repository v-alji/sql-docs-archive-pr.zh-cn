---
title: 订阅服务器属性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.configdistwizard.subscribers.f1
helpviewer_keywords:
- Subscriber Properties dialog box
ms.assetid: 32aa0347-64e4-4aa4-ac57-6bd3e5d52070
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 81ab9cf5f277ccfe1044e5a7083f019db9d843ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693240"
---
# <a name="subscriber-properties"></a><span data-ttu-id="b5f26-102">订阅服务器属性</span><span class="sxs-lookup"><span data-stu-id="b5f26-102">Subscriber Properties</span></span>
  <span data-ttu-id="b5f26-103">“订阅服务器属性”对话框包含与运行 **之前的** [!INCLUDE[msCoName](../../includes/msconame-md.md)] 版本的订阅服务器有关的信息[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b5f26-103">The **Subscriber Properties** dialog box contains information relevant to Subscribers running versions of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="b5f26-104">选项</span><span class="sxs-lookup"><span data-stu-id="b5f26-104">Options</span></span>  
 <span data-ttu-id="b5f26-105">**到订阅服务器的代理连接**</span><span class="sxs-lookup"><span data-stu-id="b5f26-105">**Agent Connection to the Subscriber**</span></span>  
 <span data-ttu-id="b5f26-106">分发代理和合并代理从分发服务器连接到订阅服务器时所处的上下文。此选项只适用于 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]以前的版本。</span><span class="sxs-lookup"><span data-stu-id="b5f26-106">The context under which the Distribution Agent and Merge Agent connect from the Distributor to the Subscriber This applies only to versions before [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
 <span data-ttu-id="b5f26-107">选择 **“模拟代理进程帐户”** ，可以使用分发服务器上 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理帐户的上下文连接到订阅服务器；也可以指定 **“SQL Server 身份验证”** ，再输入 **“登录名”** 和 **“密码”** 的值。</span><span class="sxs-lookup"><span data-stu-id="b5f26-107">Select **Impersonate agent process account** to make connections to the Subscriber using the context of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent account at the Distributor, or specify **SQL Server Authentication**, and then enter a value for **Login** and **Password**.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="b5f26-108">建议您选择 **“模拟代理进程帐户”** 。</span><span class="sxs-lookup"><span data-stu-id="b5f26-108">recommends that you select **Impersonate agent process account**.</span></span>  
  
 <span data-ttu-id="b5f26-109">对于 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 及更高版本，可以在新建订阅向导中为每个订阅指定连接信息，并可以在 **“订阅属性”** 对话框中更改连接信息。</span><span class="sxs-lookup"><span data-stu-id="b5f26-109">For [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions, connection information is specified for each subscription in the New Subscription Wizard and can be changed in the **Subscription Properties** dialog box.</span></span>  
  
 <span data-ttu-id="b5f26-110">**默认代理计划**</span><span class="sxs-lookup"><span data-stu-id="b5f26-110">**Default Agent Schedules**</span></span>  
 <span data-ttu-id="b5f26-111">对于运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之前的 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]版本的订阅服务器，为新建订阅向导中所使用的默认计划。</span><span class="sxs-lookup"><span data-stu-id="b5f26-111">The default schedule used in the New Subscription Wizard for Subscribers running versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].</span></span>  
  
 <span data-ttu-id="b5f26-112">**其他**</span><span class="sxs-lookup"><span data-stu-id="b5f26-112">**Miscellaneous**</span></span>  
 <span data-ttu-id="b5f26-113">包含有关订阅服务器和订阅服务器类型的信息。</span><span class="sxs-lookup"><span data-stu-id="b5f26-113">Includes information on the Subscriber and Subscriber type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5f26-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b5f26-114">See Also</span></span>  
 [<span data-ttu-id="b5f26-115">查看和修改分发服务器和发布服务器属性</span><span class="sxs-lookup"><span data-stu-id="b5f26-115">View and Modify Distributor and Publisher Properties</span></span>](view-and-modify-distributor-and-publisher-properties.md)   

 [<span data-ttu-id="b5f26-116">订阅发布</span><span class="sxs-lookup"><span data-stu-id="b5f26-116">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
