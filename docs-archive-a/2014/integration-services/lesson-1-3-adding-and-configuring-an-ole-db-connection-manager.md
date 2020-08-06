---
title: 步骤 3：添加和配置 OLE DB 连接管理器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: e7b74cba-a0e5-4478-af12-3f81b9484e9e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3bc4c885ce6c39c72031dd3b528a769cd47ac8f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586841"
---
# <a name="step-3-adding-and-configuring-an-ole-db-connection-manager"></a><span data-ttu-id="6f55f-102">步骤 3：添加并配置 OLE DB 连接管理器</span><span class="sxs-lookup"><span data-stu-id="6f55f-102">Step 3: Adding and Configuring an OLE DB Connection Manager</span></span>
  <span data-ttu-id="6f55f-103">添加了用于连接到数据源的平面文件连接管理器以后，下一个任务是添加用于连接到目标的 OLE DB 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="6f55f-103">After you have added a Flat File connection manager to connect to the data source, the next task is to add an OLE DB connection manager to connect to the destination.</span></span> <span data-ttu-id="6f55f-104">通过 OLE DB 连接管理器，包可以在任何 OLE DB 兼容的数据源中提取数据或加载数据。</span><span class="sxs-lookup"><span data-stu-id="6f55f-104">An OLE DB connection manager enables a package to extract data from or load data into any OLE DB-compliant data source.</span></span> <span data-ttu-id="6f55f-105">使用 OLE DB 连接管理器，可以为连接指定服务器、身份验证方法和默认数据库。</span><span class="sxs-lookup"><span data-stu-id="6f55f-105">Using the OLE DB Connection manager, you can specify the server, the authentication method, and the default database for the connection.</span></span>  
  
 <span data-ttu-id="6f55f-106">在本课中，将创建使用 Windows 身份验证的 OLE DB 连接管理器，以连接到 **AdventureWorksDB2012**的本地实例。</span><span class="sxs-lookup"><span data-stu-id="6f55f-106">In this lesson, you will create an OLE DB connection manager that uses Windows Authentication to connect to the local instance of **AdventureWorksDB2012**.</span></span> <span data-ttu-id="6f55f-107">本教程以后要创建的其他组件（如查找转换和 OLE DB 目标）也将引用此处创建的 OLE DB 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="6f55f-107">The OLE DB connection manager that you create will also be referenced by other components that you will create later in this tutorial, such as the Lookup transformation and the OLE DB destination.</span></span>  
  
### <a name="to-add-and-configure-an-ole-db-connection-manager-to-the-ssis-package"></a><span data-ttu-id="6f55f-108">向 SSIS 包中添加 OLE DB 连接管理器并对其进行配置</span><span class="sxs-lookup"><span data-stu-id="6f55f-108">To add and configure an OLE DB Connection Manager to the SSIS package</span></span>  
  
1.  <span data-ttu-id="6f55f-109">右键单击“连接管理器”\*\*\*\* 区域中的任意位置，再单击“新建 OLE DB 连接”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6f55f-109">Right-click anywhere in the **Connection Managers** area, and then click **New OLE DB Connection**.</span></span>  
  
2.  <span data-ttu-id="6f55f-110">在 **“配置 OLE DB 连接管理器”** 对话框中，单击 **“新建”**。</span><span class="sxs-lookup"><span data-stu-id="6f55f-110">In the **Configure OLE DB Connection Manager** dialog box, click **New**.</span></span>  
  
3.  <span data-ttu-id="6f55f-111">在“服务器名称”\*\*\*\* 中，输入 **localhost**。</span><span class="sxs-lookup"><span data-stu-id="6f55f-111">For **Server name**, enter **localhost**.</span></span>  
  
     <span data-ttu-id="6f55f-112">将 localhost 指定为服务器名称时，连接管理器将连接到本地计算机上的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的默认实例。</span><span class="sxs-lookup"><span data-stu-id="6f55f-112">When you specify localhost as the server name, the connection manager connects to the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on the local computer.</span></span> <span data-ttu-id="6f55f-113">若要使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的远程实例，请将 localhost 替换为要连接到的服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="6f55f-113">To use a remote instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], replace localhost with the name of the server to which you want to connect.</span></span>  
  
4.  <span data-ttu-id="6f55f-114">在“登录到服务器”\*\*\*\* 组中，确认选择了“使用 Windows 身份验证”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6f55f-114">In the **Log on to the server** group, verify that **Use Windows Authentication** is selected.</span></span>  
  
5.  <span data-ttu-id="6f55f-115">在 "**连接到数据库**" 组的 "**选择或输入数据库名称**" 框中，键入或选择 `AdventureWorksDW2012` 。</span><span class="sxs-lookup"><span data-stu-id="6f55f-115">In the **Connect to a database** group, in the **Select or enter a database name** box, type or select `AdventureWorksDW2012`.</span></span>  
  
6.  <span data-ttu-id="6f55f-116">单击“测试连接”\*\*\*\*，验证指定的连接设置是否有效。</span><span class="sxs-lookup"><span data-stu-id="6f55f-116">Click **Test Connection** to verify that the connection settings you have specified are valid.</span></span>  
  
7.  <span data-ttu-id="6f55f-117">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="6f55f-117">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="6f55f-118">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="6f55f-118">Click **OK**.</span></span>  
  
9. <span data-ttu-id="6f55f-119">在“配置 OLE DB 连接管理器”\*\*\*\* 对话框的“数据连接”\*\*\*\* 窗格中，确认选择了“localhost.AdventureWorksDW2012”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6f55f-119">In the **Data Connections** pane of the **Configure OLE DB Connection Manager** dialog box, verify that **localhost.AdventureWorksDW2012** is selected.</span></span>  
  
10. <span data-ttu-id="6f55f-120">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="6f55f-120">Click **OK**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="6f55f-121">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="6f55f-121">Next Task in Lesson</span></span>  
 [<span data-ttu-id="6f55f-122">步骤 4：将数据流任务添加到包</span><span class="sxs-lookup"><span data-stu-id="6f55f-122">Step 4: Adding a Data Flow Task to the Package</span></span>](lesson-1-4-adding-a-data-flow-task-to-the-package.md)  
  
## <a name="see-also"></a><span data-ttu-id="6f55f-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6f55f-123">See Also</span></span>  
 [<span data-ttu-id="6f55f-124">OLE DB 连接管理器</span><span class="sxs-lookup"><span data-stu-id="6f55f-124">OLE DB Connection Manager</span></span>](connection-manager/ole-db-connection-manager.md)  
  
  
