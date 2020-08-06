---
title: 更改扩展事件会话 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
ms.assetid: 114ec05b-7eca-4c87-b276-25e37b84be39
author: rothja
ms.author: jroth
ms.openlocfilehash: 14be41e48262bc7ebc8aeeaf55185f5e35d0c72e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576767"
---
# <a name="alter-an-extended-events-session"></a><span data-ttu-id="c8f58-102">更改扩展事件会话</span><span class="sxs-lookup"><span data-stu-id="c8f58-102">Alter an Extended Events Session</span></span>
  <span data-ttu-id="c8f58-103">在创建扩展事件会话后，可以使用 **“SQL Server 扩展事件向导”** 根据需要更改它。</span><span class="sxs-lookup"><span data-stu-id="c8f58-103">After you create an Extended Events session, you can alter it according to your needs using the **SQL Server Extended Events Wizard**.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="c8f58-104">开始之前</span><span class="sxs-lookup"><span data-stu-id="c8f58-104">Before you Begin</span></span>  
 <span data-ttu-id="c8f58-105">不能更改活动和不活动会话的目标，不能更改活动会话的高级属性配置。</span><span class="sxs-lookup"><span data-stu-id="c8f58-105">You cannot alter a target for active and inactive sessions, and you cannot change the advanced properties configurations for an active session.</span></span>  
  
 <span data-ttu-id="c8f58-106">可以对活动和不活动事件会话进行以下更改：</span><span class="sxs-lookup"><span data-stu-id="c8f58-106">You can make the following alterations to both active and inactive event sessions:</span></span>  
  
-   <span data-ttu-id="c8f58-107">在会话中添加或删除事件，更改事件配置（如事件字段、筛选器和操作）。</span><span class="sxs-lookup"><span data-stu-id="c8f58-107">Add or remove events from the session, and alter the event configurations such as event fields, filters and actions.</span></span>  
  
-   <span data-ttu-id="c8f58-108">添加或删除事件会话的目标。</span><span class="sxs-lookup"><span data-stu-id="c8f58-108">Add or remove a target from the event session.</span></span>  
  
-   <span data-ttu-id="c8f58-109">启用 **“在服务器启动时启动事件会话”** 选项。</span><span class="sxs-lookup"><span data-stu-id="c8f58-109">Enable the **Start the event session on server startup** option.</span></span>  
  
 <span data-ttu-id="c8f58-110">可以对不活动的事件会话进行以下其他更改：</span><span class="sxs-lookup"><span data-stu-id="c8f58-110">You can make the following additional alterations to an inactive event session:</span></span>  
  
-   <span data-ttu-id="c8f58-111">启用 **“跟踪事件之间的关系”** 选项。</span><span class="sxs-lookup"><span data-stu-id="c8f58-111">Enable the **Track the relationship between events** option.</span></span>  
  
-   <span data-ttu-id="c8f58-112">更改高级属性配置。</span><span class="sxs-lookup"><span data-stu-id="c8f58-112">Change the advanced properties configuration.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c8f58-113">“SQL Server 扩展事件向导”\*\*\*\* 不支持事件会话修改。</span><span class="sxs-lookup"><span data-stu-id="c8f58-113">The **SQL Server Extended Events Wizard** does not support event session modification.</span></span>  
  
## <a name="how-to-alter-an-extended-events-session-using-the-sql-server-extended-events-wizard"></a><span data-ttu-id="c8f58-114">如何使用 SQL Server 扩展事件向导更改扩展事件会话</span><span class="sxs-lookup"><span data-stu-id="c8f58-114">How to alter an Extended Events session using the SQL Server Extended Events Wizard</span></span>  
  
-   <span data-ttu-id="c8f58-115">在对象资源管理器中，依次展开 **“管理”**、 **“扩展事件”** 和 **“会话”**。</span><span class="sxs-lookup"><span data-stu-id="c8f58-115">In Object Explorer, expand **Management**, expand **Extended Events**, and then expand **Sessions**.</span></span>  
  
-   <span data-ttu-id="c8f58-116">右键单击要更改的会话，然后单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c8f58-116">Right-click the session you want to alter, and then click **Properties**.</span></span>  
  
-   <span data-ttu-id="c8f58-117">在 **“属性”** 对话框中进行相应的更改，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="c8f58-117">In the **Properties** dialog box, make the appropriate changes, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8f58-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c8f58-118">See Also</span></span>  
 <span data-ttu-id="c8f58-119">[ALTER EVENT SESSION &#40;Transact-sql&#41;](/sql/t-sql/statements/alter-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c8f58-119">[ALTER EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql) </span></span>  
 [<span data-ttu-id="c8f58-120">使用查询编辑器创建扩展事件会话</span><span class="sxs-lookup"><span data-stu-id="c8f58-120">Create an Extended Events Session Using Query Editor</span></span>](../../database-engine/create-an-extended-events-session-using-query-editor.md)  
  
  
