---
title: 从对象资源管理器连接到实例 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 9803a8a0-a8f1-4b65-87b8-989b06850194
author: stevestein
ms.author: sstein
ms.openlocfilehash: 918dd3ed6e8eb765f2cb7077107407c324c51a4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576518"
---
# <a name="connect-to-an-instance-from-object-explorer"></a><span data-ttu-id="25db4-102">从对象资源管理器连接到实例</span><span class="sxs-lookup"><span data-stu-id="25db4-102">Connect to an Instance From Object Explorer</span></span>
  <span data-ttu-id="25db4-103">若要使用对象资源管理器管理对象，必须首先将对象资源管理器连接到包含对象的实例。</span><span class="sxs-lookup"><span data-stu-id="25db4-103">To manage objects by using Object Explorer, you must first connect Object Explorer to the instance that contains the objects.</span></span> <span data-ttu-id="25db4-104">可以同时将对象资源管理器连接到多个实例。</span><span class="sxs-lookup"><span data-stu-id="25db4-104">You can connect Object Explorer to multiple instances at the same time.</span></span>  
  
## <a name="connecting-object-explorer-to-a-server"></a><span data-ttu-id="25db4-105">将对象资源管理器连接到服务器</span><span class="sxs-lookup"><span data-stu-id="25db4-105">Connecting Object Explorer to a Server</span></span>  
 <span data-ttu-id="25db4-106">若要使用对象资源管理器，必须先将其连接到服务器上。</span><span class="sxs-lookup"><span data-stu-id="25db4-106">To use Object Explorer you must first connect to a server.</span></span> <span data-ttu-id="25db4-107">单击对象资源管理器工具栏上的“连接”\*\*\*\*，并从下拉列表中选择服务器的类型。</span><span class="sxs-lookup"><span data-stu-id="25db4-107">Click **Connect** on the Object Explorer toolbar and choose the type of server from the drop-down list.</span></span> <span data-ttu-id="25db4-108">将打开“连接到服务器”对话框。</span><span class="sxs-lookup"><span data-stu-id="25db4-108">The **Connect to Server** dialog box opens.</span></span> <span data-ttu-id="25db4-109">若要连接，您至少要提供服务器名称和正确的身份验证信息。</span><span class="sxs-lookup"><span data-stu-id="25db4-109">To connect, you must provide at least the name of the server and the correct authentication information.</span></span>  
  
## <a name="optional-object-explorer-connection-settings"></a><span data-ttu-id="25db4-110">可选的对象资源管理器连接设置</span><span class="sxs-lookup"><span data-stu-id="25db4-110">Optional Object Explorer Connection Settings</span></span>  
 <span data-ttu-id="25db4-111">连接到服务器时，可以在“连接到服务器”\*\*\*\* 对话框中指定其他连接信息。</span><span class="sxs-lookup"><span data-stu-id="25db4-111">When connecting to a server, you can specify additional connection information in the **Connect to Server** dialog box.</span></span> <span data-ttu-id="25db4-112">“连接到服务器”\*\*\*\* 对话框将保留上次使用的设置，新连接（例如新代码编辑器窗口）将使用这些设置。</span><span class="sxs-lookup"><span data-stu-id="25db4-112">The **Connect to Server** dialog box will retain the last used settings, and new connections, such as new code editor windows, will use those settings.</span></span>  
  
 <span data-ttu-id="25db4-113">若要指定可选的连接设置，请遵循以下步骤：</span><span class="sxs-lookup"><span data-stu-id="25db4-113">To specify optional connection settings, follow these steps:</span></span>  
  
1.  <span data-ttu-id="25db4-114">单击对象资源管理器工具栏上的“连接”\*\*\*\*，并单击要连接到的服务器类型。</span><span class="sxs-lookup"><span data-stu-id="25db4-114">Click **Connect** on the Object Explorer toolbar, and click the type of server to connect to.</span></span> <span data-ttu-id="25db4-115">此时会显示“连接到服务器”对话框。</span><span class="sxs-lookup"><span data-stu-id="25db4-115">The **Connect to Server** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="25db4-116">在“服务器名称”\*\*\*\* 框中，键入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="25db4-116">In the **Server Name** box, type the name of your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
3.  <span data-ttu-id="25db4-117">单击“选项”。</span><span class="sxs-lookup"><span data-stu-id="25db4-117">Click **Options**.</span></span> <span data-ttu-id="25db4-118">“连接到服务器”\*\*\*\* 对话框将显示其他选项。</span><span class="sxs-lookup"><span data-stu-id="25db4-118">The **Connect to Server** dialog box displays additional options.</span></span>  
  
4.  <span data-ttu-id="25db4-119">单击“连接属性”\*\*\*\* 选项卡以配置其他设置。</span><span class="sxs-lookup"><span data-stu-id="25db4-119">Click the **Connection Properties** tab to configure the additional settings.</span></span> <span data-ttu-id="25db4-120">可用的设置因服务器类型而异。</span><span class="sxs-lookup"><span data-stu-id="25db4-120">The settings that are available vary depending upon the server type.</span></span> <span data-ttu-id="25db4-121">下面是可用于 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的设置。</span><span class="sxs-lookup"><span data-stu-id="25db4-121">The following settings are available for the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
    |<span data-ttu-id="25db4-122">设置</span><span class="sxs-lookup"><span data-stu-id="25db4-122">Setting</span></span>|<span data-ttu-id="25db4-123">说明</span><span class="sxs-lookup"><span data-stu-id="25db4-123">Description</span></span>|  
    |-------------|-----------------|  
    |<span data-ttu-id="25db4-124">**连接到数据库**</span><span class="sxs-lookup"><span data-stu-id="25db4-124">**Connect to database**</span></span>|<span data-ttu-id="25db4-125">从服务器上的可用数据库中选择。</span><span class="sxs-lookup"><span data-stu-id="25db4-125">Choose from the available databases on the server.</span></span> <span data-ttu-id="25db4-126">此列表只显示您具有查看权限的数据库。</span><span class="sxs-lookup"><span data-stu-id="25db4-126">This list will only show databases that you have permission to view.</span></span>|  
    |<span data-ttu-id="25db4-127">**网络协议**</span><span class="sxs-lookup"><span data-stu-id="25db4-127">**Network protocol**</span></span>|<span data-ttu-id="25db4-128">从 Shared Memory、TCP/IP 或 Named Pipes 中选择。</span><span class="sxs-lookup"><span data-stu-id="25db4-128">Select from Shared Memory, TCP/IP, or Named Pipes.</span></span>|  
    |<span data-ttu-id="25db4-129">**网络数据包大小**</span><span class="sxs-lookup"><span data-stu-id="25db4-129">**Network packet size**</span></span>|<span data-ttu-id="25db4-130">以字节为单位进行配置。</span><span class="sxs-lookup"><span data-stu-id="25db4-130">Configure in bytes.</span></span> <span data-ttu-id="25db4-131">默认设置是 4096 字节。</span><span class="sxs-lookup"><span data-stu-id="25db4-131">The default setting is 4096 bytes.</span></span>|  
    |<span data-ttu-id="25db4-132">**连接超时**</span><span class="sxs-lookup"><span data-stu-id="25db4-132">**Connection timeout**</span></span>|<span data-ttu-id="25db4-133">以秒为单位进行配置。</span><span class="sxs-lookup"><span data-stu-id="25db4-133">Configure in seconds.</span></span> <span data-ttu-id="25db4-134">默认值是 15 秒。</span><span class="sxs-lookup"><span data-stu-id="25db4-134">The default setting is 15 seconds.</span></span>|  
    |<span data-ttu-id="25db4-135">**执行超时**</span><span class="sxs-lookup"><span data-stu-id="25db4-135">**Execution timeout**</span></span>|<span data-ttu-id="25db4-136">以秒为单位进行配置。</span><span class="sxs-lookup"><span data-stu-id="25db4-136">Configure in seconds.</span></span> <span data-ttu-id="25db4-137">默认设置 (0) 表示执行永远不会超时。</span><span class="sxs-lookup"><span data-stu-id="25db4-137">The default setting (0) indicates that execution will never time out.</span></span>|  
    |<span data-ttu-id="25db4-138">**加密连接**</span><span class="sxs-lookup"><span data-stu-id="25db4-138">**Encrypt connection**</span></span>|<span data-ttu-id="25db4-139">强制加密。</span><span class="sxs-lookup"><span data-stu-id="25db4-139">Forces encryption.</span></span>|  
  
5.  <span data-ttu-id="25db4-140">若要将指定的服务器添加到已注册的服务器列表中，请单击“已注册的服务器”\*\*\*\* 选项卡，并在希望显示新服务器的位置上单击，然后完成连接。</span><span class="sxs-lookup"><span data-stu-id="25db4-140">To add the specified server to your list of registered servers, click the **Registered Server** tab, click on the location where you want the new server to appear, and then complete the connection.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="25db4-141">使用“其他连接参数”\*\*\*\* 页可以将更多连接参数添加到连接字符串。</span><span class="sxs-lookup"><span data-stu-id="25db4-141">Use the **Additional Connection Parameters** page to add more connection parameters to the connection string.</span></span> <span data-ttu-id="25db4-142">有关详细信息，请参阅[连接到服务器（“其他连接参数”页）](../../database-engine/connect-to-server-additional-connection-parameters-page.md)。</span><span class="sxs-lookup"><span data-stu-id="25db4-142">For more information, see [Connect to Server &#40;Additional Connection Parameters Page&#41;](../../database-engine/connect-to-server-additional-connection-parameters-page.md).</span></span>  
  
  
