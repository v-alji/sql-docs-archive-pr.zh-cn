---
title: 用于 Excel 的数据挖掘外接程序) 的服务器配置实用工具 (|Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 28435f86-5cec-4a1e-9b7d-b2069c1ddddb
author: minewiskan
ms.author: owend
ms.openlocfilehash: f985338e44bf0f4b591fcb70a4e093901626149f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694593"
---
# <a name="server-configuration-utility-data-mining-add-ins-for-excel"></a><span data-ttu-id="c60fe-102">服务器配置实用工具（Excel 数据挖掘外接程序）</span><span class="sxs-lookup"><span data-stu-id="c60fe-102">Server Configuration Utility (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="c60fe-103">在安装 Excel 数据挖掘外接程序时，还会安装服务器配置实用工具，并将在首次打开外接程序时运行。本主题介绍如何使用实用程序连接到实例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，并设置用于处理数据挖掘模型的数据库。</span><span class="sxs-lookup"><span data-stu-id="c60fe-103">When you install the Data Mining Add-ins for Excel, a Server Configuration Utility is also installed, and will run the first time you open the add-ins. This topic describes how to use the utility to connect to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] and set up a database for working with data mining models.</span></span>  
  

  
##  <a name="step-1-connect-to-analysis-services"></a><a name="bkmk_step1"></a><span data-ttu-id="c60fe-104">步骤1：连接到 Analysis Services</span><span class="sxs-lookup"><span data-stu-id="c60fe-104">Step 1: Connect to Analysis Services</span></span>  
 <span data-ttu-id="c60fe-105">选择提供数据挖掘算法并存储您的数据挖掘模型的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 服务器。</span><span class="sxs-lookup"><span data-stu-id="c60fe-105">Choose the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server that provides the data mining algorithms and stores your data mining models.</span></span>  
  
 <span data-ttu-id="c60fe-106">在创建连接以启用数据挖掘时，应选择可使用数据挖掘模型进行试验的服务器。</span><span class="sxs-lookup"><span data-stu-id="c60fe-106">When you create a connection to enable data mining, you should choose a server where you can experiment with data mining models.</span></span> <span data-ttu-id="c60fe-107">我们建议您在服务器上创建新数据库并将该数据库专用于数据挖掘，或请求管理员为您准备数据挖掘服务器。</span><span class="sxs-lookup"><span data-stu-id="c60fe-107">We recommend that you create a new database on the server and dedicate the new database to data mining, or ask your administrator to prepare a data mining server for you.</span></span> <span data-ttu-id="c60fe-108">这样您可以构建模型而不会影响其他服务的性能。</span><span class="sxs-lookup"><span data-stu-id="c60fe-108">That way you can build models without affecting the performance of other services.</span></span>  
  
 <span data-ttu-id="c60fe-109">请注意用于数据挖掘的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 服务器不需要位于您的源数据所在的同一服务器上。</span><span class="sxs-lookup"><span data-stu-id="c60fe-109">Note that the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server that you use for data mining does not need to be on the same server as your source data.</span></span>  
  
 <span data-ttu-id="c60fe-110">**服务器名称**</span><span class="sxs-lookup"><span data-stu-id="c60fe-110">**Server name**</span></span>  
 <span data-ttu-id="c60fe-111">键入包含将用于数据挖掘的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例的服务器名称。</span><span class="sxs-lookup"><span data-stu-id="c60fe-111">Type the name of the server that contains the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that you will use for data mining.</span></span>  
  
 <span data-ttu-id="c60fe-112">**身份验证**</span><span class="sxs-lookup"><span data-stu-id="c60fe-112">**Authentication**</span></span>  
 <span data-ttu-id="c60fe-113">指定身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="c60fe-113">Specify the authentication methods.</span></span> <span data-ttu-id="c60fe-114">Windows 身份验证对于连接到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 是必需的，除非您的管理员配置了通过 HTTPPump 访问服务器。</span><span class="sxs-lookup"><span data-stu-id="c60fe-114">Windows Authentication is required for connections to [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], unless your administrator has configured access to the server via the HTTPPump.</span></span>  
  
##  <a name="step-2-allow-temporary-models"></a><a name="bkmk_step2"></a><span data-ttu-id="c60fe-115">步骤2：允许临时模型</span><span class="sxs-lookup"><span data-stu-id="c60fe-115">Step 2: Allow Temporary Models</span></span>  
 <span data-ttu-id="c60fe-116">在您可以使用外接程序前，必须更改 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 服务器属性以允许创建临时挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="c60fe-116">Before you can use the add-ins, an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server property must be changed to permit the creation of temporary mining models.</span></span>  
  
 <span data-ttu-id="c60fe-117">临时挖掘模型也称为 "*会话模型*"。</span><span class="sxs-lookup"><span data-stu-id="c60fe-117">Temporary mining models are also called *session models*.</span></span> <span data-ttu-id="c60fe-118">这是因为只能在当前会话处于打开状态时存储模型。</span><span class="sxs-lookup"><span data-stu-id="c60fe-118">This is because the models are stored only as long as your current session is open.</span></span> <span data-ttu-id="c60fe-119">关闭到服务器的连接后，将结束会话，会话期间所使用的所有模型都会被删除。</span><span class="sxs-lookup"><span data-stu-id="c60fe-119">When you close your connection to the server, the session is ended and any models used during the session are deleted.</span></span>  
  
 <span data-ttu-id="c60fe-120">使用会话挖掘模型不会影响服务器上的存储空间，不过创建数据挖掘模型所需的开销可能会影响服务器的性能。</span><span class="sxs-lookup"><span data-stu-id="c60fe-120">The use of session mining models does not affect storage space on the server, but the overhead involved in creating data mining models may affect the performance of the server.</span></span>  
  
 <span data-ttu-id="c60fe-121">该向导首先检测您指定的服务器上的设置。</span><span class="sxs-lookup"><span data-stu-id="c60fe-121">The wizard first detects the settings on the server that you specified.</span></span> <span data-ttu-id="c60fe-122">如果服务器已经允许临时挖掘模型，则可以单击 "**下一步**" 继续。</span><span class="sxs-lookup"><span data-stu-id="c60fe-122">If the server already allows temporary mining models, you can click **Next** to continue.</span></span> <span data-ttu-id="c60fe-123">该向导还提供有关如何在指定的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 服务器上启用临时挖掘模型的说明，或如何向 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 管理员发送请求的说明。</span><span class="sxs-lookup"><span data-stu-id="c60fe-123">The wizard also provides instructions for how to enable temporary mining models on the specified [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server, or how to make a request to your [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] administrator.</span></span>  
  
##  <a name="step-3-create-database-for-add-in-users"></a><a name="bkmk_step3"></a><span data-ttu-id="c60fe-124">步骤3：为外接程序用户创建数据库</span><span class="sxs-lookup"><span data-stu-id="c60fe-124">Step 3: Create Database for Add-in Users</span></span>  
 <span data-ttu-id="c60fe-125">在设置和配置向导的此页上，您可以创建专用于数据挖掘的新数据库，或选择现有 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="c60fe-125">On this page of the setup and configuration wizard, you can create a new database that is dedicated to data mining, or select an existing [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="c60fe-126">数据挖掘需要在多维模式下运行的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="c60fe-126">Data mining requires an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that is running in multidimensional mode.</span></span> <span data-ttu-id="c60fe-127">表格模式不支持数据挖掘。</span><span class="sxs-lookup"><span data-stu-id="c60fe-127">Tabular mode does not support data mining.</span></span>  
  
 <span data-ttu-id="c60fe-128">我们建议您创建专用于数据挖掘的单独数据库。</span><span class="sxs-lookup"><span data-stu-id="c60fe-128">We recommend that you create a separate database dedicated to data mining.</span></span> <span data-ttu-id="c60fe-129">这允许您使用数据挖掘模型进行实验，而不影响其他解决方案对象。</span><span class="sxs-lookup"><span data-stu-id="c60fe-129">This lets you experiment with data mining models without affecting other solution objects.</span></span>  
  
 <span data-ttu-id="c60fe-130">如果您选择 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例上的现有数据库，请注意如果使用外接程序创建模型且该名称的模型已存在，则可能覆盖现有模型。</span><span class="sxs-lookup"><span data-stu-id="c60fe-130">If you choose an existing database on an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], note that it is possible to overwrite existing models if you use the add-ins to create a model and a model of that name already exists.</span></span>  
  
 <span data-ttu-id="c60fe-131">**创建新数据库**</span><span class="sxs-lookup"><span data-stu-id="c60fe-131">**Create new database**</span></span>  
 <span data-ttu-id="c60fe-132">选择此选项可以在所选服务器上创建新数据库。</span><span class="sxs-lookup"><span data-stu-id="c60fe-132">Select this option to create a new database on the selected server.</span></span> <span data-ttu-id="c60fe-133">数据挖掘数据库将存储您的数据源、挖掘结构和挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="c60fe-133">A data mining database will store your data sources, mining structures, and mining models.</span></span>  
  
 <span data-ttu-id="c60fe-134">**数据库名称**</span><span class="sxs-lookup"><span data-stu-id="c60fe-134">**Database name**</span></span>  
 <span data-ttu-id="c60fe-135">键入新数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="c60fe-135">Type the name of the new database.</span></span> <span data-ttu-id="c60fe-136">如果该名称未被使用，将为您创建它。</span><span class="sxs-lookup"><span data-stu-id="c60fe-136">If the name is not already in use, it will be created for you.</span></span>  
  
 <span data-ttu-id="c60fe-137">**使用现有数据库**</span><span class="sxs-lookup"><span data-stu-id="c60fe-137">**Use existing database**</span></span>  
 <span data-ttu-id="c60fe-138">选择此选项可以使用现有 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="c60fe-138">Select this option to use an existing [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="c60fe-139">**Database**</span><span class="sxs-lookup"><span data-stu-id="c60fe-139">**Database**</span></span>  
 <span data-ttu-id="c60fe-140">如果您选择了使用现有数据库的选项，必须从列表中选择该数据库名称。</span><span class="sxs-lookup"><span data-stu-id="c60fe-140">If you chose the option to use an existing database, you must select the database name from the list.</span></span>  
  
##  <a name="step-4-give-add-in-users-appropriate-permissions"></a><a name="bkmk_step4"></a><span data-ttu-id="c60fe-141">步骤4：向外接程序用户授予适当的权限</span><span class="sxs-lookup"><span data-stu-id="c60fe-141">Step 4: Give Add-in Users Appropriate Permissions</span></span>  
 <span data-ttu-id="c60fe-142">您必须确保您（和其他任何将使用外接程序的用户）拥有浏览、编辑、处理或创建数据挖掘结构和模型所必需的权限。</span><span class="sxs-lookup"><span data-stu-id="c60fe-142">You must ensure that you (and any other users of the add-ins) have the necessary permissions to browse, edit, process, or create data mining structures and models.</span></span>  
  
 <span data-ttu-id="c60fe-143">默认情况下，使用外接程序时需要进行集成的 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="c60fe-143">By default, integrated Windows Authentication is required to use the add-ins.</span></span>  
  
 <span data-ttu-id="c60fe-144">**将数据库管理权限授予外接程序用户**</span><span class="sxs-lookup"><span data-stu-id="c60fe-144">**Give add-in users database administration permissions**</span></span>  
 <span data-ttu-id="c60fe-145">选择此选项将授予所列用户对数据库的管理访问权限。</span><span class="sxs-lookup"><span data-stu-id="c60fe-145">Select this option to give the listed users administrative access to the database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c60fe-146">这些权限仅应用于 "**数据库名称**" 框中列出的数据库。</span><span class="sxs-lookup"><span data-stu-id="c60fe-146">These permissions apply only to the database listed in the **Database name** box.</span></span>  
  
 <span data-ttu-id="c60fe-147">**数据库名称**</span><span class="sxs-lookup"><span data-stu-id="c60fe-147">**Database name**</span></span>  
 <span data-ttu-id="c60fe-148">显示所选数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="c60fe-148">Displays the name of the selected database.</span></span>  
  
 <span data-ttu-id="c60fe-149">**指定要添加的用户或组**</span><span class="sxs-lookup"><span data-stu-id="c60fe-149">**Specify users or groups to add**</span></span>  
 <span data-ttu-id="c60fe-150">选择将对要用于数据挖掘的数据库有访问权限的登录名。</span><span class="sxs-lookup"><span data-stu-id="c60fe-150">Select the logins that will have access to the database used for data mining.</span></span>  
  
 <span data-ttu-id="c60fe-151">**添加**</span><span class="sxs-lookup"><span data-stu-id="c60fe-151">**Add**</span></span>  
 <span data-ttu-id="c60fe-152">单击此项可打开一个对话框，在其中可添加用户或组。</span><span class="sxs-lookup"><span data-stu-id="c60fe-152">Click to open a dialog box and add users or groups.</span></span>  
  
 <span data-ttu-id="c60fe-153">**移除**</span><span class="sxs-lookup"><span data-stu-id="c60fe-153">**Remove**</span></span>  
 <span data-ttu-id="c60fe-154">单击此项可从具有管理权限的用户列表中删除所选用户或组。</span><span class="sxs-lookup"><span data-stu-id="c60fe-154">Click to remove the selected user or group from the list of users with administration permissions.</span></span>  
  
  
