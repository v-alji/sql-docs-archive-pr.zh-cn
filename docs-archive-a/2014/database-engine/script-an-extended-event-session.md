---
title: 编写扩展事件会话的脚本 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 80f9fdde-1f13-4292-a4fc-55da826be3b4
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 11adc60ae7c7e0f8b8012d06f56c83874d3708ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580864"
---
# <a name="script-an-extended-event-session"></a><span data-ttu-id="51564-102">编写扩展事件会话的脚本</span><span class="sxs-lookup"><span data-stu-id="51564-102">Script an Extended Event Session</span></span>
  <span data-ttu-id="51564-103">本主题介绍如何编写事件会话的脚本。</span><span class="sxs-lookup"><span data-stu-id="51564-103">This topic describes how to script an event session.</span></span> <span data-ttu-id="51564-104">您可以导出、更改或删除事件会话，或者将事件会话删除并创建到以下位置：</span><span class="sxs-lookup"><span data-stu-id="51564-104">You can export, alter, or drop the event session, or drop and create the event session to the following:</span></span>  
  
-   <span data-ttu-id="51564-105">**新建查询编辑器窗口**</span><span class="sxs-lookup"><span data-stu-id="51564-105">**New Query Editor Window**</span></span>  
  
-   <span data-ttu-id="51564-106">**文件**</span><span class="sxs-lookup"><span data-stu-id="51564-106">**File**</span></span>  
  
-   <span data-ttu-id="51564-107">**剪贴板**</span><span class="sxs-lookup"><span data-stu-id="51564-107">**Clipboard**</span></span>  
  
-   <span data-ttu-id="51564-108">**代理作业**</span><span class="sxs-lookup"><span data-stu-id="51564-108">**Agent Job**</span></span>  
  
### <a name="to-script-an-existing-event-session"></a><span data-ttu-id="51564-109">编写现有事件会话的脚本</span><span class="sxs-lookup"><span data-stu-id="51564-109">To script an existing event session</span></span>  
  
1.  <span data-ttu-id="51564-110">在对象资源管理器中，依次展开 **“管理”** 节点和 **“扩展事件”**。</span><span class="sxs-lookup"><span data-stu-id="51564-110">In Object Explorer, expand the **Management** node, and then expand **Extended Events**.</span></span>  
  
2.  <span data-ttu-id="51564-111">右键单击您要编写脚本的会话，指向 **“编写会话脚本为”**，指向 **“CREATE 到”**，然后选择要在哪里编写会话的脚本。</span><span class="sxs-lookup"><span data-stu-id="51564-111">Right-click the session you want to script, point to **Script Session as**, point to **CREATE to**, and then select where you want to script the session.</span></span>  
  
### <a name="to-script-a-new-event-session"></a><span data-ttu-id="51564-112">编写新事件会话的脚本</span><span class="sxs-lookup"><span data-stu-id="51564-112">To script a new event session</span></span>  
  
1.  <span data-ttu-id="51564-113">在对象资源管理器中，依次展开 **“管理”** 节点和 **“扩展事件”**。</span><span class="sxs-lookup"><span data-stu-id="51564-113">In Object Explorer, expand the **Management** node, and then expand **Extended Events**.</span></span>  
  
2.  <span data-ttu-id="51564-114">右键单击 **“会话”**，然后单击 **“新建会话”**。</span><span class="sxs-lookup"><span data-stu-id="51564-114">Right-click **Sessions**, and then click **New Session**.</span></span>  
  
3.  <span data-ttu-id="51564-115">在 **“新建会话”** UI 中，创建事件会话，然后从 **“脚本”** 下拉列表中选择要在哪里编写事件会话的脚本。</span><span class="sxs-lookup"><span data-stu-id="51564-115">In the **New Session** UI, create the event session, and then select where you want to script the event session from the **Script** drop-down list.</span></span>  
  
### <a name="to-script-a-modified-event-session"></a><span data-ttu-id="51564-116">编写修改的事件会话的脚本</span><span class="sxs-lookup"><span data-stu-id="51564-116">To script a modified event session</span></span>  
  
1.  <span data-ttu-id="51564-117">在对象资源管理器中，依次展开 **“管理”** 节点和 **“扩展事件”**。</span><span class="sxs-lookup"><span data-stu-id="51564-117">In Object Explorer, expand the **Management** node, and then expand **Extended Events**.</span></span>  
  
2.  <span data-ttu-id="51564-118">右键单击要修改的会话，然后单击 **“属性”**。</span><span class="sxs-lookup"><span data-stu-id="51564-118">Right-click the session you want to modify, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="51564-119">在 **“会话属性”** 对话框中，修改事件会话，然后从 **“脚本”** 下拉列表中选择要在哪里编写修改的会话的脚本。</span><span class="sxs-lookup"><span data-stu-id="51564-119">In the **Session Properties** dialog box, modify the event session, and then select where you want to script the modified session from the **Script** drop-down list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51564-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="51564-120">See Also</span></span>  
 [<span data-ttu-id="51564-121">扩展事件</span><span class="sxs-lookup"><span data-stu-id="51564-121">Extended Events</span></span>](../relational-databases/extended-events/extended-events.md)  
  
  
