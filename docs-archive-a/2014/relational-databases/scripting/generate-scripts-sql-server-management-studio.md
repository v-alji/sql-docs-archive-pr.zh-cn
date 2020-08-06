---
title: 生成脚本
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 9711c617-3c68-4e5a-aea3-befc64d51524
author: rothja
ms.author: jroth
ms.openlocfilehash: 199d5e0c98d220861ee0dfb48a44a71675d8ba87
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590717"
---
# <a name="generate-scripts-sql-server-management-studio"></a><span data-ttu-id="af9cf-102">生成脚本 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="af9cf-102">Generate Scripts (SQL Server Management Studio)</span></span>
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="af9cf-103">提供了两种机制，用于生成 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本。</span><span class="sxs-lookup"><span data-stu-id="af9cf-103">provides two mechanisms for generating [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts.</span></span> <span data-ttu-id="af9cf-104">您可以使用 "**生成和发布脚本向导**" 为多个对象创建脚本。</span><span class="sxs-lookup"><span data-stu-id="af9cf-104">You can create scripts for multiple objects by using the **Generate and Publish Scripts Wizard.**.</span></span> <span data-ttu-id="af9cf-105">还可以通过使用 **“对象资源管理器”** 中的 **“编写脚本为”** 菜单为单个对象或多个对象生成脚本。</span><span class="sxs-lookup"><span data-stu-id="af9cf-105">You can also generate a script for individual objects or multiple objects by using the **Script as** menu in **Object Explorer**.</span></span>  
  
1.  <span data-ttu-id="af9cf-106">**选择一种方法：**  [生成和发布脚本向导](#GenPubScriptWiz)、 [对象资源管理器“编写脚本为”菜单](#OEScriptAsMenu)</span><span class="sxs-lookup"><span data-stu-id="af9cf-106">**Choose a method:**  [Generate and Publish Scripts Wizard](#GenPubScriptWiz), [Object Explorer Script As Menu](#OEScriptAsMenu)</span></span>  
  
2.  <span data-ttu-id="af9cf-107">**若要使用“编写脚本为”菜单：**  [编写单个对象的脚本](#ScriptSingleObject)、 [使用对象资源管理器为两个对象编写脚本](#ScriptTwoObjectsOE)、 [使用对象资源管理器详细信息为两个对象编写脚本](#ScriptTwoObjectsOED)</span><span class="sxs-lookup"><span data-stu-id="af9cf-107">**To use the Script As menu:**  [Script a Single Object](#ScriptSingleObject), [Script Two Objects Using Object Explorer](#ScriptTwoObjectsOE), [Script Two Objects Using Object Explorer Details](#ScriptTwoObjectsOED)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="af9cf-108">开始之前</span><span class="sxs-lookup"><span data-stu-id="af9cf-108">Before You Begin</span></span>  
 <span data-ttu-id="af9cf-109">选择最能满足您的需求的机制。</span><span class="sxs-lookup"><span data-stu-id="af9cf-109">Choose the mechanism that best meets your requirements.</span></span>  
  
###  <a name="generate-and-publish-scripts-wizard"></a><a name="GenPubScriptWiz"></a> <span data-ttu-id="af9cf-110">生成和发布脚本向导</span><span class="sxs-lookup"><span data-stu-id="af9cf-110">Generate and Publish Scripts Wizard</span></span>  
 <span data-ttu-id="af9cf-111">使用 **“生成和发布脚本向导”** 可为多个对象创建 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本。</span><span class="sxs-lookup"><span data-stu-id="af9cf-111">Use the **Generate and Publish Scripts Wizard** to create a [!INCLUDE[tsql](../../includes/tsql-md.md)] script for many objects.</span></span> <span data-ttu-id="af9cf-112">此向导为数据库中的所有对象或所选对象子集生成脚本。</span><span class="sxs-lookup"><span data-stu-id="af9cf-112">The wizard generates a script of all the objects in a database, or a subset of the objects that you select.</span></span> <span data-ttu-id="af9cf-113">该向导具有许多用于您的脚本的选项，例如是否包括权限、排序规则和约束等。</span><span class="sxs-lookup"><span data-stu-id="af9cf-113">The wizard has many options for your scripts, such as whether to include permissions, collation, constraints, and so on.</span></span> <span data-ttu-id="af9cf-114">有关使用向导的说明，请参阅 [Generate and Publish Scripts Wizard](generate-and-publish-scripts-wizard.md).</span><span class="sxs-lookup"><span data-stu-id="af9cf-114">For instructions on using the wizard, see [Generate and Publish Scripts Wizard](generate-and-publish-scripts-wizard.md).</span></span>  
  
###  <a name="object-explorer-script-as-menu"></a><a name="OEScriptAsMenu"></a> <span data-ttu-id="af9cf-115">对象资源管理器“编写脚本为”菜单</span><span class="sxs-lookup"><span data-stu-id="af9cf-115">Object Explorer Script As Menu</span></span>  
 <span data-ttu-id="af9cf-116">可以使用对象资源管理器 **“编写脚本为”** 菜单编写单个对象的脚本、编写多个对象的脚本或为单个对象编写多条脚本语句。</span><span class="sxs-lookup"><span data-stu-id="af9cf-116">You can use the **Object Explorer Script as** menu to script a single object, script multiple objects, or script multible statements for a single objects.</span></span> <span data-ttu-id="af9cf-117">您可以选择多种脚本类型之一；例如，创建、更改或删除对象。</span><span class="sxs-lookup"><span data-stu-id="af9cf-117">You can choose one of several types of scripts; for example to create, alter, or drop the object.</span></span> <span data-ttu-id="af9cf-118">您可以将脚本保存到查询编辑器窗口、文件或剪贴板。</span><span class="sxs-lookup"><span data-stu-id="af9cf-118">You can save the script in a Query Editor window, to a file, or to the Clipboard.</span></span> <span data-ttu-id="af9cf-119">脚本以 Unicode 格式创建。</span><span class="sxs-lookup"><span data-stu-id="af9cf-119">The script is created in Unicode format.</span></span>  
  
##  <a name="to-generate-a-script-of-a-single-object"></a><a name="ScriptSingleObject"></a> <span data-ttu-id="af9cf-120">生成单个对象的脚本</span><span class="sxs-lookup"><span data-stu-id="af9cf-120">To generate a script of a single object</span></span>  
 <span data-ttu-id="af9cf-121">**编写单个对象的脚本**</span><span class="sxs-lookup"><span data-stu-id="af9cf-121">**To script a single object**</span></span>  
  
1.  <span data-ttu-id="af9cf-122">在对象资源管理器中，连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="af9cf-122">In Object Explorer, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="af9cf-123">展开 **“数据库”** ，然后展开包含要对其编写脚本的对象的数据库。</span><span class="sxs-lookup"><span data-stu-id="af9cf-123">Expand **Databases**, and then expand the database containing the object to be scripted.</span></span>  
  
3.  <span data-ttu-id="af9cf-124">展开该对象的类别。</span><span class="sxs-lookup"><span data-stu-id="af9cf-124">Expand the category of the object.</span></span> <span data-ttu-id="af9cf-125">例如，展开 **“表”** 或 **“视图”** 节点。</span><span class="sxs-lookup"><span data-stu-id="af9cf-125">For example, expand the **Tables** or **Views** node.</span></span>  
  
4.  <span data-ttu-id="af9cf-126">右键单击该对象，指向 "**脚本 \<object type> 为**"，例如，指向 "**编写表脚本为**"。</span><span class="sxs-lookup"><span data-stu-id="af9cf-126">Right-click the object, point to **Script \<object type> as**, For example, point to **Script Table as**.</span></span>  
  
5.  <span data-ttu-id="af9cf-127">指向脚本类型，如 **“创建到”** 或 **“更改到”** 。</span><span class="sxs-lookup"><span data-stu-id="af9cf-127">Point to the script type, such as **Create to** or **Alter to**.</span></span>  
  
6.  <span data-ttu-id="af9cf-128">选择要保存该脚本的位置，如 **“新查询编辑器窗口”** 或 **“剪贴板”** 。</span><span class="sxs-lookup"><span data-stu-id="af9cf-128">Select the location to save the script, such as **New Query Editor Window** or **Clipboard**.</span></span>  
  
##  <a name="to-generate-a-script-of-two-objects-using-object-explorer"></a><a name="ScriptTwoObjectsOE"></a><span data-ttu-id="af9cf-129">使用对象资源管理器生成两个对象的脚本</span><span class="sxs-lookup"><span data-stu-id="af9cf-129">To generate a script of two objects using Object Explorer</span></span>  
 <span data-ttu-id="af9cf-130">**使用对象资源管理器为两个对象编写脚本**</span><span class="sxs-lookup"><span data-stu-id="af9cf-130">**To script two objects using Object Explorer**</span></span>  
  
 <span data-ttu-id="af9cf-131">有时您可能需要使用具有多个选项的脚本，如删除一个过程后再创建一个过程，或者创建一个表后再更改一个表。</span><span class="sxs-lookup"><span data-stu-id="af9cf-131">Sometimes you may want a script with multiple options, such as drop a procedure and then create a procedure, or create a table and then alter a table.</span></span> <span data-ttu-id="af9cf-132">如果您需要创建引用不同类型的对象（如表、视图和存储过程）的脚本，下面的用于为多个对象生成脚本的过程也适用。</span><span class="sxs-lookup"><span data-stu-id="af9cf-132">The processes below for generating scripts of multiple objects also work if you need to create a script that references different types of objects, such as tables, views, and stored procedures.</span></span>  
  
1.  <span data-ttu-id="af9cf-133">在对象资源管理器中，连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="af9cf-133">In Object Explorer, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="af9cf-134">展开 **“数据库”** ，然后展开包含要对其编写脚本的对象的数据库。</span><span class="sxs-lookup"><span data-stu-id="af9cf-134">Expand **Databases**, and then expand the database containing the objects to be scripted.</span></span>  
  
3.  <span data-ttu-id="af9cf-135">右键单击要编写脚本的第一个对象，指向 "**脚本 \<object type> 为**"，然后在 "**另存为**" 选择中选择 "**新建查询编辑器窗口**" 作为输出目标。</span><span class="sxs-lookup"><span data-stu-id="af9cf-135">Right-click the first object to be scripted, point to **Script \<object type> as**, and in the **Save as** selections chooses **New Query Editor Window** as the output destination.</span></span>  
  
4.  <span data-ttu-id="af9cf-136">导航到第二个要编写脚本的对象。</span><span class="sxs-lookup"><span data-stu-id="af9cf-136">Navigate to the second object you want to script.</span></span>  
  
5.  <span data-ttu-id="af9cf-137">右键单击该对象，指向 "**脚本 \<object type> 为**"，然后在 "**另存为**" 选项中选择 "**剪贴板**" 作为输出目标。</span><span class="sxs-lookup"><span data-stu-id="af9cf-137">Right-click the object, point to **Script \<object type> as**, and in the **Save as** selections chooses **Clipboard** as the output destination.</span></span>  
  
6.  <span data-ttu-id="af9cf-138">在“查询编辑器”窗口中打开第一个对象，然后从剪贴板中粘贴第二个对象的脚本。</span><span class="sxs-lookup"><span data-stu-id="af9cf-138">In the Query Editor window opened for the first object, paste the script for the second object from the clipboard.</span></span>  
  
##  <a name="to-generate-a-script-of-two-objects-using-object-explorer-details"></a><a name="ScriptTwoObjectsOED"></a><span data-ttu-id="af9cf-139">使用对象资源管理器详细信息为两个对象生成脚本</span><span class="sxs-lookup"><span data-stu-id="af9cf-139">To generate a script of two objects using Object Explorer Details</span></span>  
 <span data-ttu-id="af9cf-140">**使用“对象资源管理器详细信息”为两个对象编写脚本**</span><span class="sxs-lookup"><span data-stu-id="af9cf-140">**To script two objects using Object Explorer Details**</span></span>  
  
 <span data-ttu-id="af9cf-141">可以使用 **“对象资源管理器详细信息”** 窗格为相同类别的多个对象生成一个脚本。</span><span class="sxs-lookup"><span data-stu-id="af9cf-141">You can use the **Object Explorer Details** pane to generate a script for mutliple objects of the same category.</span></span>  
  
1.  <span data-ttu-id="af9cf-142">在对象资源管理器中，连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="af9cf-142">In Object Explorer, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="af9cf-143">展开 **“数据库”** ，然后展开包含要对其编写脚本的对象的数据库。</span><span class="sxs-lookup"><span data-stu-id="af9cf-143">Expand **Databases**, and then expand the database containing the objects to be scripted.</span></span>  
  
3.  <span data-ttu-id="af9cf-144">展开要编写脚本的对象类型的类别节点，如 **“表”** 节点。</span><span class="sxs-lookup"><span data-stu-id="af9cf-144">Expand the category node of the types of object you want to script, such as the **Tables** node.</span></span>  
  
4.  <span data-ttu-id="af9cf-145">可通过选中 **F7** 或打开 **“视图”** 菜单并选择 **“对象资源管理器详细信息”** 来打开 **“对象资源管理器详细信息”** 窗格。</span><span class="sxs-lookup"><span data-stu-id="af9cf-145">Open the **Object Explorer Details** pane by either selecting **F7**, or opening the **View** menu and selecting **Object Explorer Details**.</span></span>  
  
5.  <span data-ttu-id="af9cf-146">左键单击要编写脚本的对象之一。</span><span class="sxs-lookup"><span data-stu-id="af9cf-146">Left-click one of the objects you want to script.</span></span>  
  
6.  <span data-ttu-id="af9cf-147">然后，按住 Ctrl 并左键单击第二个要编写脚本的对象。</span><span class="sxs-lookup"><span data-stu-id="af9cf-147">Crtl + left-click the second object you want to script.</span></span>  
  
7.  <span data-ttu-id="af9cf-148">右键单击所选对象之一，然后选择 "**脚本 \<object type> 为**"。</span><span class="sxs-lookup"><span data-stu-id="af9cf-148">Right-click one of the selected objects, and select **Script \<object type> as**.</span></span>  
  
  
