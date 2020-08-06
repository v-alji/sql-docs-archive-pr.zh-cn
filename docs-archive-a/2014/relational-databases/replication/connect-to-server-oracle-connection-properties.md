---
title: 连接到服务器 (Oracle)，连接属性 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.oracleconnection.connectionprops.f1
helpviewer_keywords:
- Connect to Server dialog box, replication
ms.assetid: 1bb7396f-cbb2-4f88-b82b-543287ed4172
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4c76a3058283a098357701a44de48efff917acd7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577569"
---
# <a name="connect-to-server-oracle-connection-properties"></a><span data-ttu-id="55f25-102">连接到服务器 (Oracle)，连接属性</span><span class="sxs-lookup"><span data-stu-id="55f25-102">Connect to Server (Oracle), Connection Properties</span></span>
  <span data-ttu-id="55f25-103">可以使用 **“连接到服务器”** 对话框的 **“连接属性”** 选项卡指定 **“网关”** 或 **“完整”** 发布选项。</span><span class="sxs-lookup"><span data-stu-id="55f25-103">Use the **Connection Properties** tab of the **Connect to Server** dialog box to specify a publishing option of **Gateway** or **Complete**.</span></span> <span data-ttu-id="55f25-104">标识发布服务器后，除非删除并重新配置发布服务器，否则无法更改此选项。</span><span class="sxs-lookup"><span data-stu-id="55f25-104">After a Publisher is identified, this option cannot be changed without dropping and reconfiguring the Publisher.</span></span> <span data-ttu-id="55f25-105">有关详细信息，请参阅[配置 Oracle 发布服务器](non-sql/configure-an-oracle-publisher.md)。</span><span class="sxs-lookup"><span data-stu-id="55f25-105">For more information, see [Configure an Oracle Publisher](non-sql/configure-an-oracle-publisher.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="55f25-106">选项</span><span class="sxs-lookup"><span data-stu-id="55f25-106">Options</span></span>  
 <span data-ttu-id="55f25-107">**发布者类型**</span><span class="sxs-lookup"><span data-stu-id="55f25-107">**Publisher type**</span></span>  
 <span data-ttu-id="55f25-108">选择 **“网关”** 或 **“完整”** 。</span><span class="sxs-lookup"><span data-stu-id="55f25-108">Select **Gateway** or **Complete**.</span></span> <span data-ttu-id="55f25-109">**“完整”** 选项用于为快照和事务发布提供所支持的完整的 Oracle 发布功能集。</span><span class="sxs-lookup"><span data-stu-id="55f25-109">The **Complete** option is designed to provide snapshot and transactional publications with the complete set of supported features for Oracle publishing.</span></span> <span data-ttu-id="55f25-110">**“网关”** 选项提供特定的设计优化，以提高复制作为系统间的网关时的性能。</span><span class="sxs-lookup"><span data-stu-id="55f25-110">The **Gateway** option provides specific design optimizations to improve performance for cases where replication serves as a gateway between systems.</span></span> <span data-ttu-id="55f25-111">如果计划在多个事务发布中发布同一个表，则无法使用 **“网关”** 选项。</span><span class="sxs-lookup"><span data-stu-id="55f25-111">The **Gateway** option cannot be used if you plan to publish the same table in multiple transactional publications.</span></span> <span data-ttu-id="55f25-112">如果选择 **“网关”** ，则一个表可以最多出现在一个事务发布中或出现在任意数量的快照发布中。</span><span class="sxs-lookup"><span data-stu-id="55f25-112">A table can appear in at most one transactional publication and any number of snapshot publications if you select **Gateway**.</span></span>  
  
 <span data-ttu-id="55f25-113">**超时值**</span><span class="sxs-lookup"><span data-stu-id="55f25-113">**Timeouts**</span></span>  
 <span data-ttu-id="55f25-114">指定在发生超时错误之前，[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 分发服务器尝试连接到 Oracle 发布服务器的时间。</span><span class="sxs-lookup"><span data-stu-id="55f25-114">Specify how long the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributor should attempt to connect to the Oracle Publisher before a timeout error occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55f25-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="55f25-115">See Also</span></span>  
 <span data-ttu-id="55f25-116">[有关 Oracle 发布的术语词汇表](non-sql/glossary-of-terms-for-oracle-publishing.md) </span><span class="sxs-lookup"><span data-stu-id="55f25-116">[Glossary of Terms for Oracle Publishing](non-sql/glossary-of-terms-for-oracle-publishing.md) </span></span>  
 [<span data-ttu-id="55f25-117">Oracle 发布服务器性能优化</span><span class="sxs-lookup"><span data-stu-id="55f25-117">Performance Tuning for Oracle Publishers</span></span>](non-sql/performance-tuning-for-oracle-publishers.md)  
  
  
