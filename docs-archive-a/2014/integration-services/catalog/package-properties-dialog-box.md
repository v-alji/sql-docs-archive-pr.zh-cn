---
title: “包属性”对话框 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.ispackageprop.general.f1
- sql12.ssis.ssms.packageproperties.f1
ms.assetid: a70acbf4-5f5c-4606-8ce4-8eb3684233de
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b386bf4e75ff784cd8d4a96363515786d242d2a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580835"
---
# <a name="package-properties-dialog-box"></a><span data-ttu-id="d51c4-102">“包属性”对话框</span><span class="sxs-lookup"><span data-stu-id="d51c4-102">Package Properties Dialog Box</span></span>
  <span data-ttu-id="d51c4-103">使用 **“包属性”** 对话框可以查看在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务器上存储的包的属性。</span><span class="sxs-lookup"><span data-stu-id="d51c4-103">Use the **Package Properties** dialog box to view properties for packages that are stored on the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
 <span data-ttu-id="d51c4-104">有关详细信息，请参阅 [Integration Services (SSIS) 服务器](integration-services-ssis-server-and-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="d51c4-104">For more information, see [Integration Services &#40;SSIS&#41; Server](integration-services-ssis-server-and-catalog.md).</span></span>  
  
 <span data-ttu-id="d51c4-105">**您希望做什么？**</span><span class="sxs-lookup"><span data-stu-id="d51c4-105">**What do you want to do?**</span></span>  
  
-   [<span data-ttu-id="d51c4-106">打开“包属性”对话框</span><span class="sxs-lookup"><span data-stu-id="d51c4-106">Open the Package Properties dialog box</span></span>](#open_dialog)  
  
-   [<span data-ttu-id="d51c4-107">配置选项</span><span class="sxs-lookup"><span data-stu-id="d51c4-107">Configure the Options</span></span>](#options)  
  
##  <a name="open-the-package-properties-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="d51c4-108">打开“包属性”对话框</span><span class="sxs-lookup"><span data-stu-id="d51c4-108">Open the Package Properties dialog box</span></span>  
  
1.  <span data-ttu-id="d51c4-109">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，连接到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务器。</span><span class="sxs-lookup"><span data-stu-id="d51c4-109">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="d51c4-110">正在连接到承载 SSISDB 数据库的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的实例。</span><span class="sxs-lookup"><span data-stu-id="d51c4-110">You're connecting to the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that hosts the SSISDB database.</span></span>  
  
2.  <span data-ttu-id="d51c4-111">在对象资源管理器中，展开树以便显示 **“Integration Services 目录”** 节点。</span><span class="sxs-lookup"><span data-stu-id="d51c4-111">In Object Explorer, expand the tree to display the **Integration Services Catalogs** node.</span></span>  
  
3.  <span data-ttu-id="d51c4-112">展开 **“SSISDB”** 节点。</span><span class="sxs-lookup"><span data-stu-id="d51c4-112">Expand the **SSISDB** node.</span></span>  
  
4.  <span data-ttu-id="d51c4-113">展开包含您要查看其属性的包的文件夹。</span><span class="sxs-lookup"><span data-stu-id="d51c4-113">Expand the folder that contains the package you want to view properties for.</span></span>  
  
5.  <span data-ttu-id="d51c4-114">右键单击该包，然后选择“属性”  。</span><span class="sxs-lookup"><span data-stu-id="d51c4-114">Right-click the package, and then select **Properties**.</span></span>  
  
##  <a name="configure-the-options"></a><a name="options"></a> <span data-ttu-id="d51c4-115">配置选项</span><span class="sxs-lookup"><span data-stu-id="d51c4-115">Configure the Options</span></span>  
 <span data-ttu-id="d51c4-116">使用 **“常规”** 页可以查看所选包的属性。</span><span class="sxs-lookup"><span data-stu-id="d51c4-116">Use the **General** page to view the properties of the selected package.</span></span>  
  
 <span data-ttu-id="d51c4-117">“常规”  页上的所有属性都是只读的。</span><span class="sxs-lookup"><span data-stu-id="d51c4-117">All properties on the **General** page are read-only.</span></span>  
  
 <span data-ttu-id="d51c4-118">**名称**</span><span class="sxs-lookup"><span data-stu-id="d51c4-118">**Name**</span></span>  
 <span data-ttu-id="d51c4-119">显示包的名称。</span><span class="sxs-lookup"><span data-stu-id="d51c4-119">Displays the name of the package.</span></span>  
  
 <span data-ttu-id="d51c4-120">**标识符**</span><span class="sxs-lookup"><span data-stu-id="d51c4-120">**Identifier**</span></span>  
 <span data-ttu-id="d51c4-121">列出包 ID。</span><span class="sxs-lookup"><span data-stu-id="d51c4-121">Lists the package ID.</span></span>  
  
 <span data-ttu-id="d51c4-122">**入口点**</span><span class="sxs-lookup"><span data-stu-id="d51c4-122">**Entry Point**</span></span>  
 <span data-ttu-id="d51c4-123">值 `True` 表示直接启动包。</span><span class="sxs-lookup"><span data-stu-id="d51c4-123">The value of `True` indicates that the package is started directly.</span></span> <span data-ttu-id="d51c4-124">值 `False` 表示该包由另一个包通过执行包任务启动。</span><span class="sxs-lookup"><span data-stu-id="d51c4-124">The value of `False` indicates that the package is started by another package using the Execute Package task.</span></span> <span data-ttu-id="d51c4-125">默认值为 `True`。</span><span class="sxs-lookup"><span data-stu-id="d51c4-125">The default value is `True`.</span></span>  
  
 <span data-ttu-id="d51c4-126">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中为父包和子包设置此属性，方法是在解决方案资源管理器中右键单击包，然后单击“入口点包”  。</span><span class="sxs-lookup"><span data-stu-id="d51c4-126">You set this property in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] for both the parent package and the child packages by right-clicking the package in Solution Explorer and then clicking **Entry-point Package**.</span></span>  
  
 <span data-ttu-id="d51c4-127">**说明**</span><span class="sxs-lookup"><span data-stu-id="d51c4-127">**Description**</span></span>  
 <span data-ttu-id="d51c4-128">显示包的可选说明。</span><span class="sxs-lookup"><span data-stu-id="d51c4-128">Displays the optional description of the package.</span></span>  
  
  
