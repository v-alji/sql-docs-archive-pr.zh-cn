---
title: 如何创建和编辑 CDC 服务 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 1b3d47a5-dc89-482d-bbc7-fff04f194c43
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d90534b475901b08fcd2e09acdc0f7976f0fb6e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87683019"
---
# <a name="how-to-create-and-edit-a-cdc-service"></a><span data-ttu-id="32f58-102">如何创建和编辑 CDC 服务</span><span class="sxs-lookup"><span data-stu-id="32f58-102">How to Create and Edit a CDC Service</span></span>
  <span data-ttu-id="32f58-103">这些过程介绍如何从 CDC 服务配置控制台创建和编辑新的 Oracle CDC Windows 服务。</span><span class="sxs-lookup"><span data-stu-id="32f58-103">These procedures describe how to create and edit a new Oracle CDC Service from the CDC Service Configuration Console.</span></span>  
  
 <span data-ttu-id="32f58-104">此过程要求对配置了 Oracle CDC 服务的计算机具有管理员权限的 Windows 用户。</span><span class="sxs-lookup"><span data-stu-id="32f58-104">This procedure requires a Windows user with administrator privileges on the computer where the Oracle CDC service is configured.</span></span>  
  
### <a name="to-create-a-new-cdc-service"></a><span data-ttu-id="32f58-105">创建新的 CDC 服务</span><span class="sxs-lookup"><span data-stu-id="32f58-105">To create a new CDC service</span></span>  
  
1.  <span data-ttu-id="32f58-106">从 **“开始”** 菜单上，选择 **“Oracle CDC 服务配置”** 。</span><span class="sxs-lookup"><span data-stu-id="32f58-106">From the **Start** menu, select **CDC Service Configuration for Oracle**.</span></span>  
  
2.  <span data-ttu-id="32f58-107">从左侧窗格中，右键单击“本地 CDC 服务”，然后选择“新建服务”。</span><span class="sxs-lookup"><span data-stu-id="32f58-107">From the left pane, right click Local CDC Services and select New Service</span></span>  
  
     <span data-ttu-id="32f58-108">也可以从 **“操作”** 窗格中选择 **“新建服务”** 。</span><span class="sxs-lookup"><span data-stu-id="32f58-108">You can also click **New Service** from the **Actions** pane.</span></span>  
  
3.  <span data-ttu-id="32f58-109">在“新建 Oracle CDC 服务”对话框中键入或输入所需信息。</span><span class="sxs-lookup"><span data-stu-id="32f58-109">Type or enter the required information in the New Oracle CDC Service dialog box.</span></span> <span data-ttu-id="32f58-110">有关如何在“新建 Oracle CDC 服务”对话框中输入信息的信息，请参阅 [Create and Edit an Oracle CDC Service](create-and-edit-an-oracle-cdc-service.md) 。</span><span class="sxs-lookup"><span data-stu-id="32f58-110">See [Create and Edit an Oracle CDC Service](create-and-edit-an-oracle-cdc-service.md) for information on how to enter information in the New Oracle CDC Service dialog box.</span></span>  
  
     <span data-ttu-id="32f58-111">在“新建 Oracle CDC 服务”对话框中提供的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名由 Oracle CDC 服务在该服务运行时使用。</span><span class="sxs-lookup"><span data-stu-id="32f58-111">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login provided in the New Oracle CDC Service dialog box is used by the Oracle CDC Service when the service runs.</span></span> <span data-ttu-id="32f58-112">该登录名仅需是公共固定服务器角色的成员，无需其他权限。</span><span class="sxs-lookup"><span data-stu-id="32f58-112">This login only needs to be a member of the public fixed-server role, no other privileges are needed.</span></span> <span data-ttu-id="32f58-113">在添加了新的 Oracle CDC 实例后，该登录名将接收对关联的 **CDC 数据库的** db_owner [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 访问权限。</span><span class="sxs-lookup"><span data-stu-id="32f58-113">Once new Oracle CDC Instances are added, that login receives **db_owner** access to the associated [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC databases.</span></span>  
  
4.  <span data-ttu-id="32f58-114">在完成输入所需的信息后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="32f58-114">When you finish entering the required information, click **OK**.</span></span>  
  
     <span data-ttu-id="32f58-115">若要创建 Oracle CDC Windows 服务定义，程序需要对关联的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中的 MSXDBCDC 数据库具有更新访问权限。</span><span class="sxs-lookup"><span data-stu-id="32f58-115">To create the Oracle CDC Windows Service definition, the program needs update access to the MSXDBCDC database in the associated [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="32f58-116">在单击 **“确定”** 后，将出现一个对话框，提示用户输入具有对 MSXDBCDC 数据库的更新访问权限的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名。</span><span class="sxs-lookup"><span data-stu-id="32f58-116">When you click **OK**, a dialog box prompts the user to enter a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login with an update access to the MSXDBCDC database.</span></span>  
  
     <span data-ttu-id="32f58-117">有关必须在“连接到 SQL Server”对话框中键入的数据的信息，请参阅 [Connection to SQL Server](connection-to-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="32f58-117">For information about the data you must type into the Connect to SQL Server dialog box, see [Connection to SQL Server](connection-to-sql-server.md).</span></span>  
  
5.  <span data-ttu-id="32f58-118">单击 **“确定”** 关闭“新建 Oracle CDC 服务”对话框。</span><span class="sxs-lookup"><span data-stu-id="32f58-118">Click **OK** to close the New Oracle CDC Service dialog box.</span></span>  
  
### <a name="to-edit-a-cdc-service"></a><span data-ttu-id="32f58-119">编辑 CDC 服务</span><span class="sxs-lookup"><span data-stu-id="32f58-119">To edit a CDC service</span></span>  
  
1.  <span data-ttu-id="32f58-120">从 **“开始”** 菜单上，选择 **“Oracle CDC 服务配置”** 。</span><span class="sxs-lookup"><span data-stu-id="32f58-120">From the **Start** menu, select **CDC Service Configuration for Oracle**.</span></span>  
  
2.  <span data-ttu-id="32f58-121">从左侧窗格中，选择“本地 CDC 服务”  ，然后右键单击要编辑的本地服务并且选择“属性”  。</span><span class="sxs-lookup"><span data-stu-id="32f58-121">From the left pane, select **Local CDC Services** then right-click the local service you want to edit and select **Properties**.</span></span>  
  
     <span data-ttu-id="32f58-122">还可以在中部选择要使用的服务，然后从 **“操作”** 窗格中单击 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="32f58-122">You can also select the service you are working with in the middle and then from the **Actions** pane, click **Properties**.</span></span>  
  
3.  <span data-ttu-id="32f58-123">在“CDC 服务属性”对话框中键入或输入所需信息。</span><span class="sxs-lookup"><span data-stu-id="32f58-123">Type or enter the required information in the CDC Service Properties dialog box.</span></span> <span data-ttu-id="32f58-124">有关如何在“CDC 服务属性”对话框中输入信息的信息，请参阅 [Create and Edit an Oracle CDC Service](create-and-edit-an-oracle-cdc-service.md) 。</span><span class="sxs-lookup"><span data-stu-id="32f58-124">See [Create and Edit an Oracle CDC Service](create-and-edit-an-oracle-cdc-service.md) for information on how to enter information in the CDC Service Properties dialog box.</span></span>  
  
4.  <span data-ttu-id="32f58-125">在您输入完所需信息后，单击 **“确定”** ，“连接到 SQL Server”对话框将打开。</span><span class="sxs-lookup"><span data-stu-id="32f58-125">When you finish entering the required information, Click **OK**, the Connect to SQL Server dialog box opens.</span></span>  
  
     <span data-ttu-id="32f58-126">在对 MSXDBDCDC 数据库没有写入权限的登录名尝试创建新的 Oracle CDC 实例时，将显示错误消息。</span><span class="sxs-lookup"><span data-stu-id="32f58-126">When a login without write permission to the MSXDBDCDC database attempts to create a new Oracle CDC instance an error message is displayed.</span></span> <span data-ttu-id="32f58-127">在该对话框中单击 **“确定”** 将显示“连接到 SQL Server”对话框。</span><span class="sxs-lookup"><span data-stu-id="32f58-127">Click **OK** in that dialog box to display the Connect to SQL Server dialog box.</span></span> <span data-ttu-id="32f58-128">在此对话框中，必须为对 MSXDBCDC 数据库具有写入权限的登录名（例如 **db_owner** 数据库角色）输入凭据。</span><span class="sxs-lookup"><span data-stu-id="32f58-128">In this dialog box you must enter the credentials for a login that has write permission to the MSXDBCDC database, such the **db_owner** database role.</span></span>  
  
     <span data-ttu-id="32f58-129">有关必须在“连接到 SQL Server”对话框中键入的数据的信息，请参阅 [Connection to SQL Server](connection-to-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="32f58-129">For information about the data you must type into the Connect to SQL Server dialog box, see [Connection to SQL Server](connection-to-sql-server.md).</span></span>  
  
5.  <span data-ttu-id="32f58-130">在“连接到 Oracle”对话框中单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="32f58-130">Click **OK** in the Connect to Oracle dialog box.</span></span> <span data-ttu-id="32f58-131">这两个对话框将关闭，并且将更新并注册该服务。</span><span class="sxs-lookup"><span data-stu-id="32f58-131">Both dialog boxes close and the service is updated and registered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32f58-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="32f58-132">See Also</span></span>  
 <span data-ttu-id="32f58-133">[Change Data Capture Designer for Oracle by Attunity](change-data-capture-designer-for-oracle-by-attunity.md) </span><span class="sxs-lookup"><span data-stu-id="32f58-133">[Change Data Capture Designer for Oracle by Attunity](change-data-capture-designer-for-oracle-by-attunity.md) </span></span>  
 [<span data-ttu-id="32f58-134">创建和编辑 Oracle CDC 服务</span><span class="sxs-lookup"><span data-stu-id="32f58-134">Create and Edit an Oracle CDC Service</span></span>](create-and-edit-an-oracle-cdc-service.md)  
  
  
