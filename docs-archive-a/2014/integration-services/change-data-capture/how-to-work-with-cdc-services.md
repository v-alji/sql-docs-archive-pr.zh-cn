---
title: 如何使用 CDC 服务 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: db5c718a-6e7f-48ec-82a3-9d5b131716e5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7cfb5a0ed0e9ded8e0be118deb3c819626448896
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580831"
---
# <a name="how-to-work-with-cdc-services"></a><span data-ttu-id="6427d-102">如何使用 CDC 服务</span><span class="sxs-lookup"><span data-stu-id="6427d-102">How to Work with CDC Services</span></span>
  <span data-ttu-id="6427d-103">本过程介绍如何使用 CDC 服务配置控制台准备 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，以便使用 Oracle CDC 服务和创建新的 CDC 服务。</span><span class="sxs-lookup"><span data-stu-id="6427d-103">This procedure describes how to use the CDC Service Configuration Console to prepare a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance to work with Oracle CDC Services and to create a new CDC service.</span></span>  
  
### <a name="to-work-with-cdc-services"></a><span data-ttu-id="6427d-104">使用 CDC 服务</span><span class="sxs-lookup"><span data-stu-id="6427d-104">To work with CDC services</span></span>  
  
1.  <span data-ttu-id="6427d-105">从 **“开始”** 菜单上，选择 **“Oracle CDC 服务配置”** 。</span><span class="sxs-lookup"><span data-stu-id="6427d-105">From the **Start** menu, select the **CDC Service Configuration for Oracle**.</span></span>  
  
2.  <span data-ttu-id="6427d-106">从左侧窗格中，选择“本地 CDC 服务”（根级别）。 </span><span class="sxs-lookup"><span data-stu-id="6427d-106">From the left pane, select **Local CDC Services** (the root level).</span></span>  
  
3.  <span data-ttu-id="6427d-107">您可以执行一项或两项下列任务：</span><span class="sxs-lookup"><span data-stu-id="6427d-107">You carry out the one or both of the following tasks:</span></span>  
  
    -   <span data-ttu-id="6427d-108">**准备 SQL Server**</span><span class="sxs-lookup"><span data-stu-id="6427d-108">**Prepare SQL Server**</span></span>  
  
         <span data-ttu-id="6427d-109">从 CDC 服务配置控制台右侧的 **“操作”** 窗格中选择此选项。</span><span class="sxs-lookup"><span data-stu-id="6427d-109">Select this option from the **Actions** pane on the right side of the CDC Service Configuration Console.</span></span>  
  
         <span data-ttu-id="6427d-110">还可以右键单击“本地 CDC 服务”  ，然后选择“准备 SQL Server”  。</span><span class="sxs-lookup"><span data-stu-id="6427d-110">You can also right-click **Local CDC Services** and select **Prepare SQL Server**.</span></span>  
  
         <span data-ttu-id="6427d-111">“为 Oracle CDC 准备 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例”对话框随即将会打开。</span><span class="sxs-lookup"><span data-stu-id="6427d-111">The Preparing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instance for Oracle CDC dialog box opens.</span></span>  
  
         <span data-ttu-id="6427d-112">若要为 Oracle CDC 服务准备 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，登录名必须具有含 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 固定服务器角色的 `dbcreator` 登录名。</span><span class="sxs-lookup"><span data-stu-id="6427d-112">To prepare the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance for Oracle CDC services, the login must have a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login with the `dbcreator` fixed server role.</span></span> <span data-ttu-id="6427d-113">此登录名用于创建 MSXDBCDC 数据库，该数据库是添加 Oracle CDC 服务以及以后添加 Oracle CDC 实例所必需的。</span><span class="sxs-lookup"><span data-stu-id="6427d-113">This login is used to create the MSXDBCDC database that is required for adding Oracle CDC Services and, later on, Oracle CDC Instances.</span></span>  
  
         <span data-ttu-id="6427d-114">有关如何使用此对话框的信息，请参阅 [Prepare SQL Server for CDC](prepare-sql-server-for-cdc.md)。</span><span class="sxs-lookup"><span data-stu-id="6427d-114">For information on how to use this dialog box, see [Prepare SQL Server for CDC](prepare-sql-server-for-cdc.md).</span></span> <span data-ttu-id="6427d-115">有关如何为 CDC 启用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的信息，请参阅 [如何为 CDC 准备 SQL Server](how-to-prepare-sql-server-for-cdc.md)。</span><span class="sxs-lookup"><span data-stu-id="6427d-115">For information on how to enable a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance for CDC, see [How to Prepare SQL Server for CDC](how-to-prepare-sql-server-for-cdc.md).</span></span>  
  
    -   <span data-ttu-id="6427d-116">**创建新的 CDC 服务**</span><span class="sxs-lookup"><span data-stu-id="6427d-116">**Create a new CDC service**</span></span>  
  
         <span data-ttu-id="6427d-117">从 CDC 服务配置控制台右侧的 **“操作”** 窗格中，单击 **“新建服务”** 。</span><span class="sxs-lookup"><span data-stu-id="6427d-117">Click **New Service** from the **Actions** pane on the right side of the CDC Service Configuration Console.</span></span>  
  
         <span data-ttu-id="6427d-118">还可以右键单击“本地 CDC 服务”，然后选择“新建服务”。  </span><span class="sxs-lookup"><span data-stu-id="6427d-118">You can also right-Click **Local CDC Services** and select **New Service**.</span></span>  
  
         <span data-ttu-id="6427d-119">“新建 Oracle CDC 服务”对话框将打开。</span><span class="sxs-lookup"><span data-stu-id="6427d-119">The New Oracle CDC Service dialog box opens.</span></span>  
  
         <span data-ttu-id="6427d-120">有关如何使用此对话框的信息，请参阅 [创建和编辑 Oracle CDC 服务](create-and-edit-an-oracle-cdc-service.md)。</span><span class="sxs-lookup"><span data-stu-id="6427d-120">For information on how to use this dialog box, see [Create and Edit an Oracle CDC Service](create-and-edit-an-oracle-cdc-service.md).</span></span> <span data-ttu-id="6427d-121">有关如何创建或编辑 CDC 服务的信息，请参阅 [如何创建和编辑 CDC 服务](how-to-create-and-edit-a-cdc-service.md)。</span><span class="sxs-lookup"><span data-stu-id="6427d-121">For information on how to create or edit a CDC service, see [How to Create and Edit a CDC Service](how-to-create-and-edit-a-cdc-service.md).</span></span>  
  
         <span data-ttu-id="6427d-122">Oracle CDC 服务使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名仅需是 `public` 固定服务器角色的成员，无需其他权限。</span><span class="sxs-lookup"><span data-stu-id="6427d-122">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login used by the Oracle CDC Service only needs to be a member of the `public` fixed-server role, no other privileges are needed.</span></span> <span data-ttu-id="6427d-123">但是，若要创建 Oracle CDC 服务，该登录名必须对 MSXDBCDC 数据库具有写入权限，例如，必须向该登录名分配 **db_owner** 数据库角色。</span><span class="sxs-lookup"><span data-stu-id="6427d-123">However, to create the Oracle CDC Service, the login must have write permission to the MSXDBCDC database, for example the **db_owner** database role must be assigned to the login.</span></span> <span data-ttu-id="6427d-124">在对 MSXDBDCDC 数据库没有写入权限的登录名尝试创建新的 Oracle CDC 实例时，将显示错误消息。</span><span class="sxs-lookup"><span data-stu-id="6427d-124">When a login without write permission to the MSXDBDCDC database attempts to create a new Oracle CDC instance an error message is displayed.</span></span> <span data-ttu-id="6427d-125">在该对话框中单击 **“确定”** 将显示“连接到 SQL Server”对话框。</span><span class="sxs-lookup"><span data-stu-id="6427d-125">Click **OK** in that dialog box to display the Connect to SQL Server dialog box.</span></span>  
  
         <span data-ttu-id="6427d-126">有关如何为对 MSXDBCDC 数据库具有写入权限的登录名（例如 **db_owner** 数据库角色）输入凭据的信息，请参阅 [创建和编辑 Oracle CDC 服务](create-and-edit-an-oracle-cdc-service.md) 和 [连接到 SQL Server](connection-to-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="6427d-126">For information on how to enter the credentials for a login that has write permission to the MSXDBCDC database, such the **db_owner** database role, see [Create and Edit an Oracle CDC Service](create-and-edit-an-oracle-cdc-service.md) and [Connection to SQL Server](connection-to-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6427d-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6427d-127">See Also</span></span>  
 [<span data-ttu-id="6427d-128">使用 CDC 服务</span><span class="sxs-lookup"><span data-stu-id="6427d-128">Work with CDC Services</span></span>](work-with-cdc-services.md)  
  
  
