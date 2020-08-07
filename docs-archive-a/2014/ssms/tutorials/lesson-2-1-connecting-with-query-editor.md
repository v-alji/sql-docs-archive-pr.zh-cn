---
title: 连接查询编辑器 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 48725f54-a7b6-4b79-948e-965c1fe4eef1
author: stevestein
ms.author: sstein
ms.openlocfilehash: b50783450dfb9516c78a465806ee322d7a575377
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588206"
---
# <a name="connecting-with-query-editor"></a><span data-ttu-id="bf562-102">连接查询编辑器</span><span class="sxs-lookup"><span data-stu-id="bf562-102">Connecting with Query Editor</span></span>
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="bf562-103">允许在与服务器断开连接时编写或编辑代码。</span><span class="sxs-lookup"><span data-stu-id="bf562-103">permits you to write or edit code while disconnected from the server.</span></span> <span data-ttu-id="bf562-104">当服务器不可用或要节省短缺的服务器或网络资源时，这一点很有用。</span><span class="sxs-lookup"><span data-stu-id="bf562-104">This can be useful when the server is not available or when you want to conserve scarce server or network resources.</span></span> <span data-ttu-id="bf562-105">您也可以更改查询编辑器与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 新实例的连接，而无需打开新的查询编辑器窗口或重新键入代码。</span><span class="sxs-lookup"><span data-stu-id="bf562-105">You can also change the connection of Query Editor to a new instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] without opening a new Query Editor window or retyping your code.</span></span>  
  
## <a name="coding-offline"></a><span data-ttu-id="bf562-106">脱机编码</span><span class="sxs-lookup"><span data-stu-id="bf562-106">Coding Offline</span></span>  
  
#### <a name="to-write-code-offline-and-then-connect-to-different-servers"></a><span data-ttu-id="bf562-107">脱机编写代码然后连接到其他服务器</span><span class="sxs-lookup"><span data-stu-id="bf562-107">To write code offline and then connect to different servers</span></span>  
  
1.  <span data-ttu-id="bf562-108">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 工具栏上，单击“数据库引擎查询”\*\*\*\* 以打开“查询编辑器”。</span><span class="sxs-lookup"><span data-stu-id="bf562-108">On the [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] toolbar, click **Database Engine Query** to open the Query Editor.</span></span>  
  
2.  <span data-ttu-id="bf562-109">在“连接到数据库引擎”\*\*\*\* 对话框中，单击“取消”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bf562-109">In the **Connect to Database Engine** dialog box, click **Cancel**.</span></span> <span data-ttu-id="bf562-110">系统将打开查询编辑器，同时，查询编辑器的标题栏将指示您没有连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="bf562-110">The Query Editor opens, and the title bar for the Query Editor indicates that you are not connected to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
3.  <span data-ttu-id="bf562-111">在代码窗格中，键入下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句：</span><span class="sxs-lookup"><span data-stu-id="bf562-111">In the code pane, type the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
    ```  
    SELECT * FROM Production.Product;  
    GO  
    ```  
  
     <span data-ttu-id="bf562-112">此时，可以通过依次单击“连接”\*\*\*\*、“执行”\*\*\*\*、“分析”\*\*\*\* 或“显示估计的执行计划”\*\*\*\* 连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，“查询”\*\*\*\* 菜单、“查询编辑器”工具栏或在“查询编辑器”窗口中右键单击时显示的快捷菜单中均提供了这些选项。</span><span class="sxs-lookup"><span data-stu-id="bf562-112">At this point you can connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by clicking **Connect**, **Execute**, **Parse**, or **Display Estimated Execution Plan**, all of which are available from either the **Query** menu, the Query Editor toolbar, or from the shortcut menu when you right-click in the Query Editor window.</span></span> <span data-ttu-id="bf562-113">对于本练习，我们将使用工具栏。</span><span class="sxs-lookup"><span data-stu-id="bf562-113">For this practice, we'll use the toolbar.</span></span>  
  
4.  <span data-ttu-id="bf562-114">在工具栏上，单击“执行”\*\*\*\* 按钮，打开“连接到数据库引擎”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="bf562-114">On the toolbar, click the **Execute** button to open the **Connect to Database Engine** dialog box.</span></span>  
  
5.  <span data-ttu-id="bf562-115">在“服务器名称”\*\*\*\* 文本框中，键入服务器名称，再单击“选项”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bf562-115">In the **Server name** text box, type your server name, and then click **Options**.</span></span>  
  
6.  <span data-ttu-id="bf562-116">在“连接属性”\*\*\*\* 选项卡上的“连接到数据库”\*\*\*\* 列表中，浏览服务器，选择 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]，再单击“连接”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bf562-116">On the **Connection Properties** tab, in the **Connect to database** list, browse the server to select [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] and then click **Connect**.</span></span>  
  
7.  <span data-ttu-id="bf562-117">若要使用同一个连接打开另一个“查询编辑器”窗口，请在工具栏上单击“新建查询”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bf562-117">To open another Query Editor window with the same connection, on the toolbar click **New Query**.</span></span>  
  
8.  <span data-ttu-id="bf562-118">若要更改连接，请在“查询编辑器”窗口中右键单击，指向“连接”\*\*\*\*，再单击“更改连接”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bf562-118">To change connections, right-click in the Query Editor window, point to **Connection**, and then click **Change Connection**.</span></span>  
  
9. <span data-ttu-id="bf562-119">在“连接到 SQL Server”\*\*\*\* 对话框中，选择 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的另一个实例（如果有），再单击“连接”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bf562-119">In the **Connect to SQL Server** dialog box, select another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] if available, and then click **Connect**.</span></span>  
  
 <span data-ttu-id="bf562-120">您可以利用查询编辑器的这项新功能在多台服务器上轻松运行相同的代码。</span><span class="sxs-lookup"><span data-stu-id="bf562-120">This new feature of Query Editor enables you to easily run the same code on several servers.</span></span> <span data-ttu-id="bf562-121">这对于涉及类似服务器的维护操作很有效。</span><span class="sxs-lookup"><span data-stu-id="bf562-121">This may be useful for maintenance actions involving similar servers.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="bf562-122">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="bf562-122">Next Task in Lesson</span></span>  
 [<span data-ttu-id="bf562-123">添加缩进</span><span class="sxs-lookup"><span data-stu-id="bf562-123">Adding Indentation</span></span>](lesson-2-2-adding-indentation.md)  
  
  
