---
title: 通过 Internet 复制 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Web publishing [SQL Server replication], about Web publishing
- Web publishing [SQL Server replication]
- Internet [SQL Server replication]
- Internet [SQL Server replication], publishing
ms.assetid: 04e7f4ed-e244-4bbe-ba12-09c33abea09e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 46c61f8a5383c87d46fa0dbda18876b43ffb7739
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577519"
---
# <a name="replication-over-the-internet"></a><span data-ttu-id="47f12-102">通过 Internet 复制</span><span class="sxs-lookup"><span data-stu-id="47f12-102">Replication over the Internet</span></span>
  <span data-ttu-id="47f12-103">通过 Internet 复制数据，可以使断开连接的远程用户在需要时使用到 Internet 的连接访问数据。</span><span class="sxs-lookup"><span data-stu-id="47f12-103">Replicating data over the Internet allows remote, disconnected users to access data when they need it using a connection to the Internet.</span></span> <span data-ttu-id="47f12-104">使用以下方式在 Internet 上复制数据：</span><span class="sxs-lookup"><span data-stu-id="47f12-104">Replicate data over the Internet using:</span></span>  
  
-   <span data-ttu-id="47f12-105">虚拟专用网络 (VPN)。</span><span class="sxs-lookup"><span data-stu-id="47f12-105">A Virtual Private Network (VPN).</span></span> <span data-ttu-id="47f12-106">有关详细信息，请参阅[使用 VPN 通过 Internet 发布数据](publish-data-over-the-internet-using-vpn.md)。</span><span class="sxs-lookup"><span data-stu-id="47f12-106">For more information, see [Publish Data over the Internet Using VPN](publish-data-over-the-internet-using-vpn.md).</span></span>  
  
-   <span data-ttu-id="47f12-107">对于合并复制，使用 Web 同步选项。</span><span class="sxs-lookup"><span data-stu-id="47f12-107">The Web synchronization option for merge replication.</span></span> <span data-ttu-id="47f12-108">有关详细信息，请参阅 [Web Synchronization for Merge Replication](web-synchronization-for-merge-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="47f12-108">For more information, see [Web Synchronization for Merge Replication](web-synchronization-for-merge-replication.md).</span></span>  
  
 <span data-ttu-id="47f12-109">所有类型的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 复制都可以通过 VPN 来复制数据。但如果使用的是合并复制，应考虑使用 Web 同步。</span><span class="sxs-lookup"><span data-stu-id="47f12-109">All types of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication can replicate data over a VPN, but you should consider Web synchronization if you are using merge replication.</span></span>  
  
  
