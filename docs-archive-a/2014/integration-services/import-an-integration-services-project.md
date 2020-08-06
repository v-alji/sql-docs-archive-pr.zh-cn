---
title: 导入 Integration Services 项目 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3301c328-b0f5-4517-915c-93713413e453
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6a98219f3a04d11e086957d64a62e7c64cd51418
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578325"
---
# <a name="import-an-integration-services-project"></a><span data-ttu-id="555dc-102">导入 Integration Services 项目</span><span class="sxs-lookup"><span data-stu-id="555dc-102">Import an Integration Services Project</span></span>
  <span data-ttu-id="555dc-103">使用 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 的“导入项目向导”\*\*\*\* 可以根据现有的部署文件 (.ispac) 或部署到 Integration Services 目录的项目创建一个项目。</span><span class="sxs-lookup"><span data-stu-id="555dc-103">Use the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]**Import Project Wizard** to create a project from an existing deployment file (.ispac) or from a project deployed to Integration services catalog.</span></span> <span data-ttu-id="555dc-104">如果您没有项目的原始副本，但又想根据 .ispac 文件或 SSISDB 目录创建一个项目，此时该功能特别有用。</span><span class="sxs-lookup"><span data-stu-id="555dc-104">This feature is especially useful when you do not have the original copy of the project but you want to create one from an .ispac file or SSISDB catalog.</span></span>  
  
### <a name="to-import-a-project"></a><span data-ttu-id="555dc-105">导入项目</span><span class="sxs-lookup"><span data-stu-id="555dc-105">To Import a Project</span></span>  
  
1.  <span data-ttu-id="555dc-106">在中 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ， **New**单击  >  "**文件**" 菜单上的 "新建**项目**"。</span><span class="sxs-lookup"><span data-stu-id="555dc-106">In [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], click **New** > **Project** on the **File** menu.</span></span>  
  
2.  <span data-ttu-id="555dc-107">在 **“新建项目”** 窗口的 **“已安装的模板”** 区域中，展开 **“商业智能”**，然后单击 **“Integration Services”**。</span><span class="sxs-lookup"><span data-stu-id="555dc-107">In the **Installed Templates** area of the **New Project** window, expand **Business Intelligence**, and click **Integration Services**.</span></span>  
  
3.  <span data-ttu-id="555dc-108">从项目类型列表中选择 **“Integration Services 导入项目向导”** 。</span><span class="sxs-lookup"><span data-stu-id="555dc-108">Select **Integration Services Import Project Wizard** from the project types list.</span></span>  
  
4.  <span data-ttu-id="555dc-109">在 **“名称”** 文本框中为即将创建的新项目键入名称。</span><span class="sxs-lookup"><span data-stu-id="555dc-109">Type a name for the new project to be created in the **Name** text box.</span></span>  
  
5.  <span data-ttu-id="555dc-110">在 **“位置”** 文本框中键入项目的路径或位置，或者单击 **“浏览”** 选择一个位置。</span><span class="sxs-lookup"><span data-stu-id="555dc-110">Type the path or location for the project in the **Location** text box, or click **Browse** to select one.</span></span>  
  
6.  <span data-ttu-id="555dc-111">在 **“解决方案名称”** 文本框中键入解决方案的名称。</span><span class="sxs-lookup"><span data-stu-id="555dc-111">Type a name for the solution in the **Solution name** text box.</span></span>  
  
7.  <span data-ttu-id="555dc-112">单击 **“确定”** 启动 **“Integration Services 导入项目向导”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="555dc-112">Click **OK** to launch the **Integration Services Import Project Wizard** dialog box.</span></span>  
  
8.  <span data-ttu-id="555dc-113">单击 **“下一步”** 切换到 **“选择源”** 页。</span><span class="sxs-lookup"><span data-stu-id="555dc-113">Click **Next** to switch to the **Select Source** page.</span></span>  
  
9. <span data-ttu-id="555dc-114">如果要从 **.ispac** 文件导入，请在 **“路径”** 文本框中键入包含文件名的路径。</span><span class="sxs-lookup"><span data-stu-id="555dc-114">If you are importing from an **.ispac** file, type the path including file name in the **Path** text box.</span></span> <span data-ttu-id="555dc-115">单击 **“浏览”** 导航到要存储解决方案的文件夹，在 **“文件名”** 文本框中键入文件名，然后单击 **“打开”**。</span><span class="sxs-lookup"><span data-stu-id="555dc-115">Click **Browse** to navigate to the folder where you want the solution to be stored and type file name in the **File name** text box, and click **Open**.</span></span>  
  
     <span data-ttu-id="555dc-116">如果要从 **“Integration Services 目录”** 导入，请在 **“服务器名称”** 文本框中键入数据库实例名称，或者单击 **“浏览”** 选择包含该目录的数据库实例。</span><span class="sxs-lookup"><span data-stu-id="555dc-116">If you are importing from an **Integration Services Catalog**, type the database instance name in the **Server name** text box or click **Browse** and select the database instance that contains the catalog.</span></span>  
  
     <span data-ttu-id="555dc-117">单击 **“路径”** 文本框旁边的 **“浏览”** ，展开目录中的文件夹，选择要导入的项目，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="555dc-117">Click **Browse** next to **Path** text box, expand folder in the catalog, select the project you want to import, and click **OK**.</span></span>  
  
     <span data-ttu-id="555dc-118">单击 **“下一步”** 切换到 **“查看”** 页。</span><span class="sxs-lookup"><span data-stu-id="555dc-118">Click **Next** to switch to the **Review** page.</span></span>  
  
10. <span data-ttu-id="555dc-119">查看信息，然后单击 **“导入”** 以基于您所选的现有项目创建一个项目。</span><span class="sxs-lookup"><span data-stu-id="555dc-119">Review the information and click **Import** to create a project based on the existing project you selected.</span></span>  
  
11. <span data-ttu-id="555dc-120">可选：单击 **“保存报表”** 将结果保存到文件中。</span><span class="sxs-lookup"><span data-stu-id="555dc-120">Optional: click **Save Report** to save the results to a file</span></span>  
  
12. <span data-ttu-id="555dc-121">单击 **“关闭”** 以关闭 **“Integration Services 导入项目向导”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="555dc-121">Click **Close** to close the **Integration Services Import Project Wizard** dialog box.</span></span>  
  
  
