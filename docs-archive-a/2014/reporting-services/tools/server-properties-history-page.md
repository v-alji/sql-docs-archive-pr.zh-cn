---
title: 服务器属性（“历史记录”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.history.f1
ms.assetid: be9d8018-a46f-4625-9ae1-138ebe6b38ba
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: df5ff9dc7a94431f8feec112d460938aa1631ef2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587709"
---
# <a name="server-properties-history-page"></a><span data-ttu-id="ab648-102">服务器属性（“历史记录”页）</span><span class="sxs-lookup"><span data-stu-id="ab648-102">Server Properties (History Page)</span></span>
  <span data-ttu-id="ab648-103">使用此页可设置要保留的报表历史记录副本数的默认值。</span><span class="sxs-lookup"><span data-stu-id="ab648-103">Use this page to set a default value for the number of copies of report history to retain.</span></span> <span data-ttu-id="ab648-104">该默认值为所有报表提供建立报表历史记录限制的初始设置。</span><span class="sxs-lookup"><span data-stu-id="ab648-104">The default value provides an initial setting that establishes report history limits for all reports.</span></span> <span data-ttu-id="ab648-105">可以针对不同的报表采用不同的设置。</span><span class="sxs-lookup"><span data-stu-id="ab648-105">You can vary these settings for individual reports.</span></span>  
  
 <span data-ttu-id="ab648-106">报表历史记录是一系列报表快照，这些快照中包括创建快照时报表的数据和布局。</span><span class="sxs-lookup"><span data-stu-id="ab648-106">Report history is a collection of report snapshots that include report data and layout that is current for the report at the time the snapshot is created.</span></span> <span data-ttu-id="ab648-107">可以使用报表历史记录来保留报表在特定日期或时间的副本。</span><span class="sxs-lookup"><span data-stu-id="ab648-107">You can use report history to keep a copy of a report as it was on a specific date or time.</span></span> <span data-ttu-id="ab648-108">可以为在处于本机模式的报表服务器上或配置了 SharePoint 集成模式的报表服务器上运行的单个报表创建和管理报表历史记录。</span><span class="sxs-lookup"><span data-stu-id="ab648-108">You can create and manage report history for individual reports that run on a native mode report server or a report server that is configured for SharePoint integrated mode.</span></span>  
  
 <span data-ttu-id="ab648-109">报表历史记录快照存储在报表服务器数据库中。</span><span class="sxs-lookup"><span data-stu-id="ab648-109">Report history snapshots are stored in the report server database.</span></span> <span data-ttu-id="ab648-110">如果要保留无限多个快照，请确保定期检查数据库大小，确保它的增长速度不会过快或占用太多的磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="ab648-110">If you keep an unlimited number of snapshots, be sure to periodically check the database size to ensure it is not growing too fast or consuming too much disk space.</span></span>  
  
 <span data-ttu-id="ab648-111">若要打开此页，请启动 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]，连接到报表服务器实例，右键单击报表服务器名称，然后选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ab648-111">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server instance, right-click the report server name, and select **Properties**.</span></span> <span data-ttu-id="ab648-112">单击 **“历史记录”** 将此页打开。</span><span class="sxs-lookup"><span data-stu-id="ab648-112">Click **History** to open this page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ab648-113">选项</span><span class="sxs-lookup"><span data-stu-id="ab648-113">Options</span></span>  
 <span data-ttu-id="ab648-114">**不限制报表历史记录中保留的快照数**</span><span class="sxs-lookup"><span data-stu-id="ab648-114">**Keep an unlimited number of snapshots in report history**</span></span>  
 <span data-ttu-id="ab648-115">保留所有的报表历史记录快照。</span><span class="sxs-lookup"><span data-stu-id="ab648-115">Retain all report history snapshots.</span></span> <span data-ttu-id="ab648-116">要减少报表历史记录的大小，必须手动删除快照。</span><span class="sxs-lookup"><span data-stu-id="ab648-116">You must manually delete snapshots to reduce the size of report history.</span></span>  
  
 <span data-ttu-id="ab648-117">**限制报表历史记录的副本数**</span><span class="sxs-lookup"><span data-stu-id="ab648-117">**Limit the copies of report history**</span></span>  
 <span data-ttu-id="ab648-118">保留设定数量的报表历史记录快照。</span><span class="sxs-lookup"><span data-stu-id="ab648-118">Retain a set number of report history snapshots.</span></span> <span data-ttu-id="ab648-119">到达限制后，将从报表历史记录中删除较旧的副本以便为新副本腾出空间。</span><span class="sxs-lookup"><span data-stu-id="ab648-119">When the limit is reached, older copies are removed from report history to make room for newer copies.</span></span>  
  
 <span data-ttu-id="ab648-120">如果以后限制报表历史记录，则在现有的报表历史记录超出您指定的限制时，报表服务器将减少现有的报表历史记录以符合新限制。</span><span class="sxs-lookup"><span data-stu-id="ab648-120">If you limit report history later, when the existing report history exceeds the limit you specify, the report server reduces the existing report history to the new limit.</span></span> <span data-ttu-id="ab648-121">首先删除最旧的报表快照。</span><span class="sxs-lookup"><span data-stu-id="ab648-121">The oldest report snapshots are deleted first.</span></span> <span data-ttu-id="ab648-122">如果报表历史为空或者低于限制，则添加新的报表快照。</span><span class="sxs-lookup"><span data-stu-id="ab648-122">If report history is empty or below the limit, new report snapshots are added.</span></span> <span data-ttu-id="ab648-123">到达限制后，将在添加新的报表快照时删除时间最早的快照。</span><span class="sxs-lookup"><span data-stu-id="ab648-123">When the limit is reached, the oldest snapshot is deleted when a new report snapshot is added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab648-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ab648-124">See Also</span></span>  
 <span data-ttu-id="ab648-125">[设置报表服务器属性 &#40;Management Studio&#41;](set-report-server-properties-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="ab648-125">[Set Report Server Properties &#40;Management Studio&#41;](set-report-server-properties-management-studio.md) </span></span>  
 <span data-ttu-id="ab648-126">[在 Management Studio 中连接到报表服务器](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="ab648-126">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 [<span data-ttu-id="ab648-127">Management Studio 中报表服务器的 F1 帮助</span><span class="sxs-lookup"><span data-stu-id="ab648-127">Report Server in Management Studio F1 Help</span></span>](report-server-in-management-studio-f1-help.md)  
  
  
