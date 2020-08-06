---
title: 快照文件夹 | Microsoft Docs
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.replicationutilities.specifysnapshotfolder.f1
ms.assetid: 3eb1b73f-ddb3-4d09-be6e-811c414698e9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 48b490c65662edf65018e98dd1bc3339f6aae6b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591235"
---
# <a name="snapshot-folder"></a><span data-ttu-id="b13e8-102">快照文件夹</span><span class="sxs-lookup"><span data-stu-id="b13e8-102">Snapshot Folder</span></span>
  <span data-ttu-id="b13e8-103">**“快照文件夹”** 页出现在配置分发向导和新建发布向导中。</span><span class="sxs-lookup"><span data-stu-id="b13e8-103">The **Snapshot Folder** page appears in the Configure Distribution Wizard and in the New Publication Wizard.</span></span> <span data-ttu-id="b13e8-104">为快照文件夹指定的位置将用作此向导中启用的所有发布服务器的默认位置（默认快照文件夹无法应用到以后使用 **“分发服务器属性”** 对话框启用的发布服务器）。</span><span class="sxs-lookup"><span data-stu-id="b13e8-104">The location you specify for the snapshot folder will be used as the default for all Publishers enabled in this wizard (the default snapshot folder does not apply to Publishers that are later enabled using the **Distributor Properties** dialog box).</span></span> <span data-ttu-id="b13e8-105">对于配置分发向导的 **“发布服务器”** 页上或 **“分发服务器属性”** 对话框上的任何发布服务器，您均可以覆盖此默认值。</span><span class="sxs-lookup"><span data-stu-id="b13e8-105">You can override this default for any Publisher on the **Publishers** page of the Configure Distribution Wizard or the **Distributor Properties** dialog box.</span></span>  
  
 <span data-ttu-id="b13e8-106">快照文件夹只是指定共享的目录。向此文件夹中执行读写操作的代理必须对其具有足够的访问权限。</span><span class="sxs-lookup"><span data-stu-id="b13e8-106">The snapshot folder is simply a directory that you have designated as a share; agents that read from and write to this folder must have sufficient permissions to access it.</span></span> <span data-ttu-id="b13e8-107">有关正确保护文件夹的详细信息，请参阅[保护快照文件夹](security/secure-the-snapshot-folder.md)。</span><span class="sxs-lookup"><span data-stu-id="b13e8-107">For more information about securing the folder appropriately, see [Secure the Snapshot Folder](security/secure-the-snapshot-folder.md).</span></span> <span data-ttu-id="b13e8-108">在实现复制之前，请测试复制代理是否能够连接到快照文件夹。</span><span class="sxs-lookup"><span data-stu-id="b13e8-108">Prior to implementing replication, test that the replication agents will be able to connect to the snapshot folder.</span></span> <span data-ttu-id="b13e8-109">以每个代理所使用的帐户登录，再尝试访问快照文件夹。</span><span class="sxs-lookup"><span data-stu-id="b13e8-109">Log on under the account that will be used by each agent and then attempt to access the snapshot folder.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b13e8-110">选项</span><span class="sxs-lookup"><span data-stu-id="b13e8-110">Options</span></span>  
 <span data-ttu-id="b13e8-111">**快照文件夹**</span><span class="sxs-lookup"><span data-stu-id="b13e8-111">**Snapshot folder**</span></span>  
 <span data-ttu-id="b13e8-112">输入用来存储快照文件的文件夹的路径。</span><span class="sxs-lookup"><span data-stu-id="b13e8-112">Enter the path for the folder where you want snapshot files stored.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="b13e8-113">建议您将网络共享作为快照文件夹的位置。</span><span class="sxs-lookup"><span data-stu-id="b13e8-113">recommends that you use a network share as a snapshot folder location.</span></span> <span data-ttu-id="b13e8-114">其他计算机上的代理无法访问本地路径（以驱动器号开头的路径，如 C:\\）。</span><span class="sxs-lookup"><span data-stu-id="b13e8-114">Local paths (those starting with a drive letter, such as C:\\) are not accessible to agents on other computers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b13e8-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b13e8-115">See Also</span></span>  
 <span data-ttu-id="b13e8-116">[备用快照文件夹位置](alternate-snapshot-folder-locations.md) </span><span class="sxs-lookup"><span data-stu-id="b13e8-116">[Alternate Snapshot Folder Locations](alternate-snapshot-folder-locations.md) </span></span>  
 <span data-ttu-id="b13e8-117">[“配置分发”](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="b13e8-117">[Configure Distribution](configure-distribution.md) </span></span>  
 <span data-ttu-id="b13e8-118">[配置发布和分发](configure-publishing-and-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="b13e8-118">[Configure Publishing and Distribution](configure-publishing-and-distribution.md) </span></span>  
 <span data-ttu-id="b13e8-119">[查看和修改分发服务器和发布服务器属性](view-and-modify-distributor-and-publisher-properties.md) </span><span class="sxs-lookup"><span data-stu-id="b13e8-119">[View and Modify Distributor and Publisher Properties](view-and-modify-distributor-and-publisher-properties.md) </span></span>  
 [<span data-ttu-id="b13e8-120">使用快照初始化订阅</span><span class="sxs-lookup"><span data-stu-id="b13e8-120">Initialize a Subscription with a Snapshot</span></span>](initialize-a-subscription-with-a-snapshot.md)  
  
  
