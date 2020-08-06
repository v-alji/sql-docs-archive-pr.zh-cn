---
title: 导入项目向导 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.importprojectwizard.f1
ms.assetid: 9247ad6c-4bd1-43ab-b347-583181cb9917
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 81a990995d7e98c21b61f484372d31c9a1773102
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586892"
---
# <a name="import-project-wizard"></a><span data-ttu-id="27e8d-102">导入项目向导</span><span class="sxs-lookup"><span data-stu-id="27e8d-102">Import Project Wizard</span></span>
  <span data-ttu-id="27e8d-103">使用 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 导入项目向导可以基于现有的项目创建一个新的 Integration Services 项目。</span><span class="sxs-lookup"><span data-stu-id="27e8d-103">Use the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Import Project Wizard create a new Integration Services project based on an existing one.</span></span> <span data-ttu-id="27e8d-104">导入已部署到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 目录的项目，或从项目部署文件（扩展名为 .ispac）导入项目。</span><span class="sxs-lookup"><span data-stu-id="27e8d-104">Import projects that have already been deployed to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] catalog or import projects from a project deployment file (.ispac extension).</span></span>  
  
### <a name="to-create-a-project-based-on-a-project-in-ispac-file-or-in-catalog"></a><span data-ttu-id="27e8d-105">基于 .ispac 文件或目录中的项目创建项目</span><span class="sxs-lookup"><span data-stu-id="27e8d-105">To create a project based on a project in .ispac file or in catalog</span></span>  
  
1.  <span data-ttu-id="27e8d-106">单击 "**文件**"，指向 "**新建**"，然后单击 "项目"。</span><span class="sxs-lookup"><span data-stu-id="27e8d-106">Click **File**, point to **New**, and click Project.</span></span>  
  
2.  <span data-ttu-id="27e8d-107">展开 **“商业智能”**，然后单击 **Integration Services**。</span><span class="sxs-lookup"><span data-stu-id="27e8d-107">Expand **Business Intelligence**, and click **Integration Services**.</span></span>  
  
3.  <span data-ttu-id="27e8d-108">在中间的窗格中选择 **“Integration Services 导入向导”** ，为解决方案键入 **“名称”** ，为项目指定 **“文件夹”** ，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="27e8d-108">Select **Integration Services Import Wizard** in the middle pane, type a **name** for the solution, project, and specify the **folder** for the project, and then click **OK**.</span></span>  
  
     <span data-ttu-id="27e8d-109">此时应看到 **“Integration Services 导入项目向导”**。</span><span class="sxs-lookup"><span data-stu-id="27e8d-109">You should see the **Integration Services Import Project Wizard**.</span></span> <span data-ttu-id="27e8d-110">该向导将基于现有的项目创建一个新的 Integration Services 项目。</span><span class="sxs-lookup"><span data-stu-id="27e8d-110">This wizard creates a new Integration Services project based on an existing one</span></span>  
  
4.  <span data-ttu-id="27e8d-111">在 **“简介”** 页上单击 **“下一步”** 以便看到 **“选择源”** 页。</span><span class="sxs-lookup"><span data-stu-id="27e8d-111">Click **Next** on the **Introduction** page to see the **Select Source** page.</span></span>  
  
5.  <span data-ttu-id="27e8d-112">指定要从 .ispac 文件还是从目录导入项目。</span><span class="sxs-lookup"><span data-stu-id="27e8d-112">Specify whether you want to import project from an .ispac file or from a catalog.</span></span>  
  
    -   <span data-ttu-id="27e8d-113">如果您选择 **“项目部署文件”** 选项，则指定指向 .ispac 文件的路径。</span><span class="sxs-lookup"><span data-stu-id="27e8d-113">If you select **Project deployment file** option, specify the path to the .ispac file.</span></span>  
  
    -   <span data-ttu-id="27e8d-114">如果您选择 **“Integration Services 目录”** 选项，则指定目录在其上存在的数据库服务器实例的名称，以及指向该目录中的项目的路径。</span><span class="sxs-lookup"><span data-stu-id="27e8d-114">If you select **Integration Services Catalog** option, specify the name of database server instance on which the catalog exists, and the path to the project in the catalog.</span></span>  
  
6.  <span data-ttu-id="27e8d-115">在 **“选择源”** 页上单击 **“下一步”** 以便看到 **“检查”** 页。</span><span class="sxs-lookup"><span data-stu-id="27e8d-115">Click **Next** on the **Select Source** page to see the **Review** page.</span></span> <span data-ttu-id="27e8d-116">查看在该页上显示的与向导将要执行的导入操作有关的信息。</span><span class="sxs-lookup"><span data-stu-id="27e8d-116">Review the information displayed on the page about the import operation the wizard is going to perform.</span></span>  
  
7.  <span data-ttu-id="27e8d-117">单击 **“导入”** 以便基于您选择的项目创建一个新的 Integration Services 项目。</span><span class="sxs-lookup"><span data-stu-id="27e8d-117">Click **Import** to create a new Integration Services project based on the one you selected.</span></span>  
  
8.  <span data-ttu-id="27e8d-118">**“结果”** 页应该显示向导执行的导入操作的结果。</span><span class="sxs-lookup"><span data-stu-id="27e8d-118">The **Results** page should display the results from import operation the wizard performed.</span></span> <span data-ttu-id="27e8d-119">单击 **“保存报表”** 可以将报表保存到某一 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="27e8d-119">Click **Save Report** to save the report to an XML file.</span></span>  
  
9. <span data-ttu-id="27e8d-120">单击“**关闭**”以关闭向导。</span><span class="sxs-lookup"><span data-stu-id="27e8d-120">Click **Close** to close the wizard.</span></span>  
  
  
