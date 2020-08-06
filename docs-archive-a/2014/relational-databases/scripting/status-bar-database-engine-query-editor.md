---
title: 状态栏（数据库引擎查询编辑器）
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: e7f2d6f4-bb94-4cf5-a096-c34397e679af
author: rothja
ms.author: jroth
ms.openlocfilehash: 743ae0a4152daee19aa67f85337ae4077a3ed7f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589503"
---
# <a name="status-bar-database-engine-query-editor"></a><span data-ttu-id="7f7c4-102">状态栏（数据库引擎查询编辑器）</span><span class="sxs-lookup"><span data-stu-id="7f7c4-102">Status Bar (Database Engine Query Editor)</span></span>
  <span data-ttu-id="7f7c4-103">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器窗口的状态栏可进行颜色编码，以便指示每个窗口连接到的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="7f7c4-103">The status bar of [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor windows can be color coded to indicate which instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] each window is connected to.</span></span>  
  
1.  <span data-ttu-id="7f7c4-104">**开始之前：** [状态栏颜色](#StatusBarColors)</span><span class="sxs-lookup"><span data-stu-id="7f7c4-104">**Before you begin:**  [Status Bar Colors](#StatusBarColors)</span></span>  
  
2.  <span data-ttu-id="7f7c4-105">**在以下位置设置服务器状态颜色的具体步骤：** [对象资源管理器](#SetOEServerColor)、[注册服务器](#SetRegServerColor)</span><span class="sxs-lookup"><span data-stu-id="7f7c4-105">**To set a server status color in:**  [Object Explorer](#SetOEServerColor), [Registered Server](#SetRegServerColor)</span></span>  
  
3.  <span data-ttu-id="7f7c4-106">**使用状态颜色的具体步骤：** [使用服务器颜色打开查询编辑器](#OpenServerColor)、[打开指定状态颜色的查询编辑器](#OpenSpecColor)</span><span class="sxs-lookup"><span data-stu-id="7f7c4-106">**To use a status color:**  [Open Query Editor Using a Server Color](#OpenServerColor), [Open a Query Editor Specifying a Status Color](#OpenSpecColor)</span></span>  
  
##  <a name="status-bar-colors"></a><a name="StatusBarColors"></a> <span data-ttu-id="7f7c4-107">状态栏颜色</span><span class="sxs-lookup"><span data-stu-id="7f7c4-107">Status Bar Colors</span></span>  
 <span data-ttu-id="7f7c4-108">您可以在 **“对象资源管理器”** 或 **“已注册服务器”** 中将状态栏颜色与特定的服务器节点相关联。</span><span class="sxs-lookup"><span data-stu-id="7f7c4-108">You can associate a status bar color with a specific server node in either **Object Explorer** or **Registered Servers**.</span></span> <span data-ttu-id="7f7c4-109">只能为连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]实例的服务器节点指定颜色，不能为针对其他 SQL Server 技术的服务器节点指定颜色。</span><span class="sxs-lookup"><span data-stu-id="7f7c4-109">The colors can only be specified for server nodes connected to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], not server nodes for other SQL Server technologies.</span></span> <span data-ttu-id="7f7c4-110">您还可以在每次将新的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器窗口连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]实例时，指定自定义状态栏颜色。</span><span class="sxs-lookup"><span data-stu-id="7f7c4-110">You can also specify a custom status bar color each time you connect a new [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="7f7c4-111">然后，您可以使用为服务器节点定义的状态颜色打开查询编辑器窗口，或者为该编辑器窗口指定唯一颜色。</span><span class="sxs-lookup"><span data-stu-id="7f7c4-111">You can then open a query editor window using either the status color defined for the server node, or specify a unique color for that editor window.</span></span>  
  
 <span data-ttu-id="7f7c4-112">在对象资源管理器中为服务器节点设置自定义的状态栏颜色必须在进行连接时完成。</span><span class="sxs-lookup"><span data-stu-id="7f7c4-112">Setting a custom status bar color for a server node in Object Explorer must be done when making the connection.</span></span> <span data-ttu-id="7f7c4-113">若要更改与某一现有服务器节点相关联的颜色，您必须首先断开连接，然后重新连接并且指定新颜色。</span><span class="sxs-lookup"><span data-stu-id="7f7c4-113">To change the color associated with an existing server node, you must disconnect and then reconnect specifying the new color.</span></span>  
  
##  <a name="set-the-status-color-for-a-server-in-object-explorer"></a><a name="SetOEServerColor"></a> <span data-ttu-id="7f7c4-114">在对象资源管理器中为服务器设置状态颜色</span><span class="sxs-lookup"><span data-stu-id="7f7c4-114">Set the Status Color for a Server in Object Explorer</span></span>  
 <span data-ttu-id="7f7c4-115">**在对象资源管理器中设置服务器状态颜色**</span><span class="sxs-lookup"><span data-stu-id="7f7c4-115">**To set a server status color in Object Explorer**</span></span>  
  
1.  <span data-ttu-id="7f7c4-116">在“对象资源管理器”中，选择“连接”按钮，然后选择“数据库引擎…”    。</span><span class="sxs-lookup"><span data-stu-id="7f7c4-116">In **Object Explorer**, select the **Connect** button and then select **Database Engine...**.</span></span>  
  
2.  <span data-ttu-id="7f7c4-117">在“连接到服务器”对话框上，选择“选项 >>”   。</span><span class="sxs-lookup"><span data-stu-id="7f7c4-117">On the **Connect to Server** dialog, select **Options >>**.</span></span>  
  
3.  <span data-ttu-id="7f7c4-118">选中 **“使用自定义颜色”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="7f7c4-118">Select the **Use custom color** check box.</span></span>  
  
4.  <span data-ttu-id="7f7c4-119">若要选择颜色，请选择“选择...”按钮  。</span><span class="sxs-lookup"><span data-stu-id="7f7c4-119">To select the color, select the **Select...** button.</span></span>  
  
5.  <span data-ttu-id="7f7c4-120">选择基础颜色或自定义颜色，然后选择“确定”。</span><span class="sxs-lookup"><span data-stu-id="7f7c4-120">Select either a basic or custom color, then select OK.</span></span>  
  
6.  <span data-ttu-id="7f7c4-121">填写其余连接信息，然后选择 **“连接”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="7f7c4-121">Fill in the rest of the connection information, and then select the **Connect** button.</span></span>  
  
##  <a name="set-the-status-color-for-a-registered-server"></a><a name="SetRegServerColor"></a> <span data-ttu-id="7f7c4-122">为已注册服务器设置状态颜色</span><span class="sxs-lookup"><span data-stu-id="7f7c4-122">Set the Status Color For a Registered Server</span></span>  
 <span data-ttu-id="7f7c4-123">**为已注册服务器设置服务器颜色**</span><span class="sxs-lookup"><span data-stu-id="7f7c4-123">**To set a server color For a Registered Server**</span></span>  
  
1.  <span data-ttu-id="7f7c4-124">在“已注册服务器”中，右键单击服务器节点，然后选择“属性…”   。</span><span class="sxs-lookup"><span data-stu-id="7f7c4-124">In **Registered Servers**, right click the server node and then select **Properties...**.</span></span>  
  
2.  <span data-ttu-id="7f7c4-125">在 **“编辑服务器注册属性”** 对话框中，选择 **“连接属性”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="7f7c4-125">On the **Edit Server Registration Properties** dialog, select the **Connection Properties** tab.</span></span>  
  
3.  <span data-ttu-id="7f7c4-126">选中 **“使用自定义颜色”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="7f7c4-126">Select the **Use custom color** check box.</span></span>  
  
4.  <span data-ttu-id="7f7c4-127">若要选择颜色，请选择“选择...”按钮  。</span><span class="sxs-lookup"><span data-stu-id="7f7c4-127">To select the color, select the **Select...** button.</span></span>  
  
5.  <span data-ttu-id="7f7c4-128">选择基础颜色或自定义颜色，然后选择“确定”。</span><span class="sxs-lookup"><span data-stu-id="7f7c4-128">Select either a basic or custom color, then select OK.</span></span>  
  
6.  <span data-ttu-id="7f7c4-129">在 **“编辑服务器注册属性”** 对话框中，选择 **“保存”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="7f7c4-129">Select the **Save** button on the **Edit Server Registration Properties** dialog.</span></span>  
  
##  <a name="open-an-editor-using-a-server-color"></a><a name="OpenServerColor"></a> <span data-ttu-id="7f7c4-130">使用服务器颜色打开编辑器</span><span class="sxs-lookup"><span data-stu-id="7f7c4-130">Open An Editor Using a Server Color</span></span>  
 <span data-ttu-id="7f7c4-131">**使用服务器颜色打开编辑器窗口**</span><span class="sxs-lookup"><span data-stu-id="7f7c4-131">**To open an editor window using a server color**</span></span>  
  
-   <span data-ttu-id="7f7c4-132">右键单击“对象资源管理器”或“已注册服务器”中的服务器节点，然后选择“新建查询”    。</span><span class="sxs-lookup"><span data-stu-id="7f7c4-132">Right-click a server node in either **Object Explorer** or **Registered Servers**, and select **New Query**.</span></span>  
  
-   <span data-ttu-id="7f7c4-133">或者，突出显示服务器节点，然后选择 **“新建查询”** 工具栏按钮。</span><span class="sxs-lookup"><span data-stu-id="7f7c4-133">Alternatively, highlight a server node, and then select the **New Query** toolbar button.</span></span>  
  
-   <span data-ttu-id="7f7c4-134">编辑器窗口中的状态栏将使用为关联服务器定义的颜色。</span><span class="sxs-lookup"><span data-stu-id="7f7c4-134">The status bar in the editor window will use the color defined for the associated server.</span></span>  
  
##  <a name="open-an-editor-specifying-a-status-color"></a><a name="OpenSpecColor"></a> <span data-ttu-id="7f7c4-135">打开编辑器并且指定状态颜色</span><span class="sxs-lookup"><span data-stu-id="7f7c4-135">Open an Editor Specifying a Status Color</span></span>  
 <span data-ttu-id="7f7c4-136">**打开编辑器窗口并且指定状态颜色**</span><span class="sxs-lookup"><span data-stu-id="7f7c4-136">**To open an editor window specifying a status color**</span></span>  
  
-   <span data-ttu-id="7f7c4-137">打开 **“文件”** 菜单，选择 **“新建”** ，然后选择 **“数据库引擎查询”** 。</span><span class="sxs-lookup"><span data-stu-id="7f7c4-137">Open the **File** menu, select **New**, and then select **Database Engine Query**.</span></span>  
  
-   <span data-ttu-id="7f7c4-138">在“连接到服务器”对话框上，选择“选项 >>”   。</span><span class="sxs-lookup"><span data-stu-id="7f7c4-138">On the **Connect to Server** dialog, select **Options >>**.</span></span>  
  
-   <span data-ttu-id="7f7c4-139">选中 **“使用自定义颜色”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="7f7c4-139">Select the **Use custom color** check box.</span></span>  
  
-   <span data-ttu-id="7f7c4-140">若要选择颜色，请选择“选择...”按钮  。</span><span class="sxs-lookup"><span data-stu-id="7f7c4-140">To select the color, select the **Select...** button.</span></span>  
  
-   <span data-ttu-id="7f7c4-141">选择基础颜色或自定义颜色，然后选择“确定”。</span><span class="sxs-lookup"><span data-stu-id="7f7c4-141">Select either a basic or custom color, then select OK.</span></span>  
  
-   <span data-ttu-id="7f7c4-142">填写其余连接信息，然后选择 **“连接”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="7f7c4-142">Fill in the rest of the connection information, and then select the **Connect** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f7c4-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7f7c4-143">See Also</span></span>  
 [<span data-ttu-id="7f7c4-144">查询和文本编辑器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="7f7c4-144">Query and Text Editors &#40;SQL Server Management Studio&#41;</span></span>](../scripting/query-and-text-editors-sql-server-management-studio.md)  
  
  
