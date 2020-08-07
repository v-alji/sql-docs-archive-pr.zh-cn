---
title: “配置”对话框 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.SSIS.SSMS.ISPROJECTPROP.PARAMETERS.F1
- SQL12.SSIS.SSMS.ISPROJECTPROP.REFERENCES.F1
- sql12.dts.designer.configure.f1
ms.assetid: 10183c8d-b1be-420f-972a-96ea97d4f4d8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 857baf3421f2744144e10b0df0b770538f533192
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587988"
---
# <a name="configure-dialog-box"></a><span data-ttu-id="62133-102">配置对话框</span><span class="sxs-lookup"><span data-stu-id="62133-102">Configure Dialog Box</span></span>
  <span data-ttu-id="62133-103">使用 **“配置”** 对话框可为包和项目配置参数、连接管理器和对环境的引用。</span><span class="sxs-lookup"><span data-stu-id="62133-103">Use the **Configure** dialog box to configure parameters, connection managers, and references to environments, for packages and projects.</span></span>  
  
 <span data-ttu-id="62133-104">**您希望做什么？**</span><span class="sxs-lookup"><span data-stu-id="62133-104">**What do you want to do?**</span></span>  
  
-   [<span data-ttu-id="62133-105">打开“配置”对话框</span><span class="sxs-lookup"><span data-stu-id="62133-105">Open the Configure Dialog Box</span></span>](#open_dialog)  
  
-   [<span data-ttu-id="62133-106">设置“参数”页上的选项</span><span class="sxs-lookup"><span data-stu-id="62133-106">Set the options on the Parameters page</span></span>](#parameter)  
  
-   [<span data-ttu-id="62133-107">设置“引用”页上的选项</span><span class="sxs-lookup"><span data-stu-id="62133-107">Set the options on the References page</span></span>](#references)  
  
##  <a name="open-the-configure-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="62133-108">打开“配置”对话框</span><span class="sxs-lookup"><span data-stu-id="62133-108">Open the Configure Dialog Box</span></span>  
  
1.  <span data-ttu-id="62133-109">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，连接到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务器。</span><span class="sxs-lookup"><span data-stu-id="62133-109">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="62133-110">正在连接到承载 SSISDB 数据库的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的实例。</span><span class="sxs-lookup"><span data-stu-id="62133-110">You're connecting to the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that hosts the SSISDB database.</span></span>  
  
2.  <span data-ttu-id="62133-111">在对象资源管理器中，展开树以便显示 **“Integration Services 目录”** 节点。</span><span class="sxs-lookup"><span data-stu-id="62133-111">In Object Explorer, expand the tree to display the **Integration Services Catalogs** node.</span></span>  
  
3.  <span data-ttu-id="62133-112">展开 **“SSISDB”** 节点。</span><span class="sxs-lookup"><span data-stu-id="62133-112">Expand the **SSISDB** node.</span></span>  
  
4.  <span data-ttu-id="62133-113">展开包含您要配置的包或项目的文件夹。</span><span class="sxs-lookup"><span data-stu-id="62133-113">Expand the folder that contains the package or project that you want to configure.</span></span>  
  
5.  <span data-ttu-id="62133-114">右键单击该包或项目，然后单击“配置”。 </span><span class="sxs-lookup"><span data-stu-id="62133-114">Right-click the package or project, and then click **Configure**.</span></span>  
  
##  <a name="set-the-options-on-the-parameters-page"></a><a name="parameter"></a> <span data-ttu-id="62133-115">设置“参数”页上的选项</span><span class="sxs-lookup"><span data-stu-id="62133-115">Set the options on the Parameters page</span></span>  
 <span data-ttu-id="62133-116">使用 **“参数”** 页查看参数名称和值，然后修改值。</span><span class="sxs-lookup"><span data-stu-id="62133-116">Use the **Parameters** page to view parameter names and values, and to modify the values.</span></span>  
  
 <span data-ttu-id="62133-117">在“范围”下拉列表中，选择“参数”和“连接管理器”选项卡中显示的参数的范围。   </span><span class="sxs-lookup"><span data-stu-id="62133-117">Select the scope of the parameters displayed in the **Parameters** and **Connection Managers** tabs, in the **Scope** drop-down list.</span></span>  
  
 <span data-ttu-id="62133-118">以下是 **“参数”** 选项卡的选项列表。</span><span class="sxs-lookup"><span data-stu-id="62133-118">The following is a list of the options in the **Parameters** tab.</span></span>  
  
 <span data-ttu-id="62133-119">**容器**</span><span class="sxs-lookup"><span data-stu-id="62133-119">**Container**</span></span>  
 <span data-ttu-id="62133-120">列出包含参数的对象。</span><span class="sxs-lookup"><span data-stu-id="62133-120">Lists the object that contains the parameter.</span></span>  
  
 <span data-ttu-id="62133-121">**名称**</span><span class="sxs-lookup"><span data-stu-id="62133-121">**Name**</span></span>  
 <span data-ttu-id="62133-122">列出参数名称。</span><span class="sxs-lookup"><span data-stu-id="62133-122">Lists the parameter name.</span></span>  
  
 <span data-ttu-id="62133-123">**值**</span><span class="sxs-lookup"><span data-stu-id="62133-123">**Value**</span></span>  
 <span data-ttu-id="62133-124">列出参数值。</span><span class="sxs-lookup"><span data-stu-id="62133-124">Lists the parameter value.</span></span> <span data-ttu-id="62133-125">单击省略号按钮可更改 **“设置参数值”** 对话框中的值。</span><span class="sxs-lookup"><span data-stu-id="62133-125">Click the ellipsis button to change the value in the **Set Parameter Value** dialog box.</span></span>  
  
 <span data-ttu-id="62133-126">以下是 **“连接管理器”** 选项卡中的选项列表。使用此选项卡可以更改连接管理器属性的值。</span><span class="sxs-lookup"><span data-stu-id="62133-126">The following is a list of the options in the **Connection Managers** tab. You use this tab to change values for connection manager properties.</span></span> <span data-ttu-id="62133-127">将在 SSIS 服务器上为这些属性自动生成参数。</span><span class="sxs-lookup"><span data-stu-id="62133-127">Parameters are automatically generated on the SSIS server for the properties.</span></span>  
  
 <span data-ttu-id="62133-128">**容器**</span><span class="sxs-lookup"><span data-stu-id="62133-128">**Container**</span></span>  
 <span data-ttu-id="62133-129">列出包含连接管理器的对象。</span><span class="sxs-lookup"><span data-stu-id="62133-129">Lists the object that contains the connection manager.</span></span>  
  
 <span data-ttu-id="62133-130">**名称**</span><span class="sxs-lookup"><span data-stu-id="62133-130">**Name**</span></span>  
 <span data-ttu-id="62133-131">列出连接管理器名称。</span><span class="sxs-lookup"><span data-stu-id="62133-131">Lists the connection manager name.</span></span>  
  
 <span data-ttu-id="62133-132">**属性名称**</span><span class="sxs-lookup"><span data-stu-id="62133-132">**Property name**</span></span>  
 <span data-ttu-id="62133-133">列出连接管理器属性的名称。</span><span class="sxs-lookup"><span data-stu-id="62133-133">Lists the name of the connection manager property.</span></span>  
  
 <span data-ttu-id="62133-134">**值**</span><span class="sxs-lookup"><span data-stu-id="62133-134">**Value**</span></span>  
 <span data-ttu-id="62133-135">列出分配给连接管理器属性的值。</span><span class="sxs-lookup"><span data-stu-id="62133-135">Lists the value assigned to the connection manager property.</span></span> <span data-ttu-id="62133-136">单击省略号按钮可更改 **“设置参数值”** 对话框中的值。</span><span class="sxs-lookup"><span data-stu-id="62133-136">Click the ellipsis button to change the value in the **Set Parameter Value** dialog box.</span></span> <span data-ttu-id="62133-137">您可以输入一个文字值、映射包含您要使用的值的环境变量，或使用包中的默认值。</span><span class="sxs-lookup"><span data-stu-id="62133-137">You can enter a literal value, map an environment variable that contains the value you want to use, or use the default value from the package.</span></span>  
  
##  <a name="set-the-options-on-the-references-page"></a><a name="references"></a> <span data-ttu-id="62133-138">设置“引用”页上的选项</span><span class="sxs-lookup"><span data-stu-id="62133-138">Set the options on the References page</span></span>  
 <span data-ttu-id="62133-139">使用 **“引用”** 页来添加和删除对环境的引用以及访问环境属性。</span><span class="sxs-lookup"><span data-stu-id="62133-139">Use the **References** page to add and remove references to environments, and to access environment properties.</span></span>  
  
 <span data-ttu-id="62133-140">环境可为已部署到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务器的项目中包含的包指定运行时值。</span><span class="sxs-lookup"><span data-stu-id="62133-140">An environment specifies runtime values for packages contained in the projects you've deployed to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
 <span data-ttu-id="62133-141">**环境**</span><span class="sxs-lookup"><span data-stu-id="62133-141">**Environment**</span></span>  
 <span data-ttu-id="62133-142">列出环境。</span><span class="sxs-lookup"><span data-stu-id="62133-142">Lists the environment.</span></span>  
  
 <span data-ttu-id="62133-143">**环境文件夹**</span><span class="sxs-lookup"><span data-stu-id="62133-143">**Environment Folder**</span></span>  
 <span data-ttu-id="62133-144">列出包含环境的文件夹。</span><span class="sxs-lookup"><span data-stu-id="62133-144">Lists the folder that contains the environment.</span></span>  
  
 <span data-ttu-id="62133-145">**打开**</span><span class="sxs-lookup"><span data-stu-id="62133-145">**Open**</span></span>  
 <span data-ttu-id="62133-146">单击可打开“环境属性”对话框。 </span><span class="sxs-lookup"><span data-stu-id="62133-146">Click to open the **Environment Properties** dialog box.</span></span>  
  
 <span data-ttu-id="62133-147">**添加**</span><span class="sxs-lookup"><span data-stu-id="62133-147">**Add**</span></span>  
 <span data-ttu-id="62133-148">单击可添加对环境的引用。</span><span class="sxs-lookup"><span data-stu-id="62133-148">Click to add a reference to an environment.</span></span> <span data-ttu-id="62133-149">在 **“浏览环境”** 对话框中，单击一个环境，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="62133-149">In the **Browse Environments** dialog box click an environment and then click **OK**.</span></span>  
  
 <span data-ttu-id="62133-150">您可以选择 **“SSISDB”** 节点下的任何项目文件夹中包含的环境。</span><span class="sxs-lookup"><span data-stu-id="62133-150">You can select an environment contained in any project folder under the **SSISDB** node.</span></span>  
  
 <span data-ttu-id="62133-151">**删除**</span><span class="sxs-lookup"><span data-stu-id="62133-151">**Remove**</span></span>  
 <span data-ttu-id="62133-152">单击“引用”区域中列出的环境，然后单击“删除”。  </span><span class="sxs-lookup"><span data-stu-id="62133-152">Click an environment listed in the **References** area, and then click **Remove**.</span></span>  
  
  
