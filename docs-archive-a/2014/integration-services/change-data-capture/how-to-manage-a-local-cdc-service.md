---
title: 如何管理本地 CDC 服务 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 7f9be649-cd93-40c1-bc48-0480106f207c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 437590d4b91f2fc80d5bb8a90251bf0dc7c8e18a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682366"
---
# <a name="how-to-manage-a-local-cdc-service"></a><span data-ttu-id="556df-102">如何管理本地 CDC 服务</span><span class="sxs-lookup"><span data-stu-id="556df-102">How to Manage a Local CDC Service</span></span>
  <span data-ttu-id="556df-103">本过程介绍如何使用 CDC 服务配置控制台来管理特定的 CDC 服务。</span><span class="sxs-lookup"><span data-stu-id="556df-103">This procedure describes how to use the CDC Service Configuration Console to manage specific CDC services.</span></span>  
  
### <a name="to-manage-a-specific-cdc-service"></a><span data-ttu-id="556df-104">管理特定的 CDC 服务</span><span class="sxs-lookup"><span data-stu-id="556df-104">To manage a specific CDC Service</span></span>  
  
1.  <span data-ttu-id="556df-105">从 **“开始”** 菜单上，选择 **“Oracle CDC 服务配置”** 。</span><span class="sxs-lookup"><span data-stu-id="556df-105">From the **Start** menu, select the **CDC Service Configuration for Oracle**.</span></span>  
  
2.  <span data-ttu-id="556df-106">从 CDC 服务配置控制台的左侧窗格中，展开 **“本地 CDC 服务”** 。</span><span class="sxs-lookup"><span data-stu-id="556df-106">From the left pane in the CDC Service Configuration Console, expand **Local CDC Services**.</span></span>  
  
3.  <span data-ttu-id="556df-107">选择要使用的 CDC 服务。</span><span class="sxs-lookup"><span data-stu-id="556df-107">Select the CDC service you want to work with.</span></span>  
  
     <span data-ttu-id="556df-108">也可以右键单击要使用的 CDC 服务，然后选择所需操作。</span><span class="sxs-lookup"><span data-stu-id="556df-108">You can also right-click the CDC service you want to work with and select the desired action.</span></span>  
  
     <span data-ttu-id="556df-109">**OR**</span><span class="sxs-lookup"><span data-stu-id="556df-109">**OR**</span></span>  
  
     <span data-ttu-id="556df-110">从 CDC 服务配置控制台的左侧窗格中选择 **“本地 CDC 服务”** ，然后从 CDC 服务配置控制台的中部选择要使用的服务。</span><span class="sxs-lookup"><span data-stu-id="556df-110">Select **Local CDC Services** from the left pane in the CDC Service Configuration Console then select the service you want to work with from the middle section of the CDC Service Configuration Console.</span></span>  
  
     <span data-ttu-id="556df-111">也可以右键单击要使用的 CDC 服务，然后选择所需操作。</span><span class="sxs-lookup"><span data-stu-id="556df-111">You can also right-click the CDC service you want to work with and select the desired action.</span></span>  
  
4.  <span data-ttu-id="556df-112">您可在使用 CDC 服务时执行以下任务。</span><span class="sxs-lookup"><span data-stu-id="556df-112">You can carry out the following tasks when working with a CDC service.</span></span>  
  
    -   <span data-ttu-id="556df-113">**删除服务**</span><span class="sxs-lookup"><span data-stu-id="556df-113">**Delete the service**</span></span>  
  
         <span data-ttu-id="556df-114">从 CDC 服务配置控制台右侧的 **“操作”** 窗格，单击 **“删除”** 以便删除服务。</span><span class="sxs-lookup"><span data-stu-id="556df-114">From the **Actions** pane on the right side of the CDC Service Configuration Console, click **Delete** to delete the service.</span></span>  
  
         <span data-ttu-id="556df-115">也可以右键单击要删除的 CDC 服务，然后选择“删除”  。</span><span class="sxs-lookup"><span data-stu-id="556df-115">You can also right-click the CDC service you want to delete and select **Delete**.</span></span>  
  
         <span data-ttu-id="556df-116">**注意**：如果在删除服务时该服务正在运行，则该服务将在被删除前停止。</span><span class="sxs-lookup"><span data-stu-id="556df-116">**Note**: If the service is running when deleting the service, the service is stopped before being deleted.</span></span>  
  
         <span data-ttu-id="556df-117">若要删除 Oracle CDC Windows 服务定义，程序需要对关联的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中的 MSXDBCDC 数据库具有更新访问权限。</span><span class="sxs-lookup"><span data-stu-id="556df-117">To delete an Oracle CDC Windows Service definition, the program needs update access to the MSXDBCDC database in the associated [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="556df-118">在您单击 **“确定”** 删除该服务后，程序将尝试在 MSXDBCDC 数据库中删除 Oracle CDC 服务注册。</span><span class="sxs-lookup"><span data-stu-id="556df-118">When you click **OK** to delete the service, the program attempts to delete the Oracle CDC Service registration in the MSXDBCDC database.</span></span> <span data-ttu-id="556df-119">如果由于权限不足而失败，将显示一个对话框，提示用户输入具有对 MSXDBCDC 数据库的更新访问权限的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名。</span><span class="sxs-lookup"><span data-stu-id="556df-119">If it fails due to lack of permissions, a dialog box is displayed to prompt the user to enter a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login with an update access to the MSXDBCDC database.</span></span>  
  
         <span data-ttu-id="556df-120">有关必须在“连接到 SQL Server”对话框中输入的数据的信息，请参阅 [Manage an Oracle CDC Service](manage-an-oracle-cdc-service.md) 和 [Connection to SQL Server for Delete](connection-to-sql-server-for-delete.md)。</span><span class="sxs-lookup"><span data-stu-id="556df-120">For information about the data you must enter in the Connect to SQL Server dialog box, see [Manage an Oracle CDC Service](manage-an-oracle-cdc-service.md) and [Connection to SQL Server for Delete](connection-to-sql-server-for-delete.md).</span></span>  
  
    -   <span data-ttu-id="556df-121">**编辑 CDC 服务属性**</span><span class="sxs-lookup"><span data-stu-id="556df-121">**Edit the CDC Service Properties**</span></span>  
  
         <span data-ttu-id="556df-122">从 CDC 服务配置控制台右侧的 **“操作”** 窗格中，单击 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="556df-122">From the **Actions** pane on the right side of the CDC Service Configuration Console, click **Properties**.</span></span>  
  
         <span data-ttu-id="556df-123">也可以右键单击要编辑其属性的 CDC 服务，然后选择“属性”  。</span><span class="sxs-lookup"><span data-stu-id="556df-123">You can also right-click the CDC service where you want to edit the properties and select **Properties**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="556df-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="556df-124">See Also</span></span>  
 [<span data-ttu-id="556df-125">管理 Oracle CDC 服务</span><span class="sxs-lookup"><span data-stu-id="556df-125">Manage an Oracle CDC Service</span></span>](manage-an-oracle-cdc-service.md)  
  
  
