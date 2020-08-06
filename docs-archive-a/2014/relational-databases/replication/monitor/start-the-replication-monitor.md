---
title: 启动复制监视器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Replication Monitor, starting
ms.assetid: e037bd27-cc87-4ee9-9e5f-83f6d717cfa4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cff23206923825d0e86e47ad6921c19f45e68b35
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693751"
---
# <a name="start-the-replication-monitor"></a><span data-ttu-id="ab85a-102">启动复制监视器</span><span class="sxs-lookup"><span data-stu-id="ab85a-102">Start the Replication Monitor</span></span>
  <span data-ttu-id="ab85a-103">可以从任何 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 实例上的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中启动复制监视器，也可以在命令提示符下启动复制监视器。</span><span class="sxs-lookup"><span data-stu-id="ab85a-103">Replication Monitor can be started from [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] on any instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], or from the command prompt.</span></span> <span data-ttu-id="ab85a-104">启动复制监视器后，将发布服务器添加至监视器。</span><span class="sxs-lookup"><span data-stu-id="ab85a-104">After starting Replication Monitor, add one or more Publishers to monitor.</span></span> <span data-ttu-id="ab85a-105">有关详细信息，请参阅 [从复制监视器中添加和删除发布服务器](add-and-remove-publishers-from-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="ab85a-105">For more information, see [Add and Remove Publishers from Replication Monitor](add-and-remove-publishers-from-replication-monitor.md).</span></span>  
  
### <a name="to-start-replication-monitor-from-sql-server-management-studio"></a><span data-ttu-id="ab85a-106">从 SQL Server Management Studio 启动复制监视器</span><span class="sxs-lookup"><span data-stu-id="ab85a-106">To start Replication Monitor from SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="ab85a-107">连接至 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]实例，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="ab85a-107">Connect to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="ab85a-108">右键单击 **“复制”** 文件夹或它的任一子文件夹，然后单击 **“启动复制监视器”** 。</span><span class="sxs-lookup"><span data-stu-id="ab85a-108">Right-click the **Replication** folder or any of its subfolders, and then click **Launch Replication Monitor**.</span></span>  
  
### <a name="to-start-replication-monitor-from-the-command-prompt"></a><span data-ttu-id="ab85a-109">从命令提示符启动复制监视器</span><span class="sxs-lookup"><span data-stu-id="ab85a-109">To start Replication Monitor from the command prompt</span></span>  
  
1.  <span data-ttu-id="ab85a-110">在命令提示符下，导航到工具安装目录。</span><span class="sxs-lookup"><span data-stu-id="ab85a-110">From the command prompt, navigate to the tools installation directory.</span></span> <span data-ttu-id="ab85a-111">默认路径为 [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]Tools\Binn\。</span><span class="sxs-lookup"><span data-stu-id="ab85a-111">The default path is [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]Tools\Binn\ .</span></span>  
  
2.  <span data-ttu-id="ab85a-112">运行 sqlmonitor.exe。</span><span class="sxs-lookup"><span data-stu-id="ab85a-112">Run sqlmonitor.exe.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab85a-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ab85a-113">See Also</span></span>  
 [<span data-ttu-id="ab85a-114">监视复制</span><span class="sxs-lookup"><span data-stu-id="ab85a-114">Monitoring Replication</span></span>](../monitoring-replication.md)  
  
  
