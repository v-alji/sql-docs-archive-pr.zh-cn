---
title: “验证”对话框 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.ispackagevalidate.f1
- sql12.ssis.ssms.isprojectvalidate.f1
ms.assetid: 134e14ce-4f8d-4a20-889a-918014c841d8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 69e29d106dc9f4f100bf191911c5c34e0250be8f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578367"
---
# <a name="validate-dialog-box"></a><span data-ttu-id="49668-102">“验证”对话框</span><span class="sxs-lookup"><span data-stu-id="49668-102">Validate Dialog Box</span></span>
  <span data-ttu-id="49668-103">使用 **“验证”** 对话框检查 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目或包中的常见问题。</span><span class="sxs-lookup"><span data-stu-id="49668-103">Use the **Validate** dialog box to check for common problems in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] a project or package.</span></span>  
  
 <span data-ttu-id="49668-104">如果有问题，将在该对话框的顶部显示一条消息。</span><span class="sxs-lookup"><span data-stu-id="49668-104">If there is a problem, a message is displayed at the top of the dialog box.</span></span> <span data-ttu-id="49668-105">否则，在顶部显示“就绪”一词。</span><span class="sxs-lookup"><span data-stu-id="49668-105">Otherwise, the term Ready displays at the top.</span></span>  
  
 <span data-ttu-id="49668-106">**您希望做什么？**</span><span class="sxs-lookup"><span data-stu-id="49668-106">**What do you want to do?**</span></span>  
  
-   [<span data-ttu-id="49668-107">打开“验证”对话框</span><span class="sxs-lookup"><span data-stu-id="49668-107">Open the Validate dialog box</span></span>](#open_dialog)  
  
-   [<span data-ttu-id="49668-108">设置“常规”页上的选项</span><span class="sxs-lookup"><span data-stu-id="49668-108">Set the options on the General page</span></span>](#general)  
  
##  <a name="open-the-validate-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="49668-109">打开“验证”对话框</span><span class="sxs-lookup"><span data-stu-id="49668-109">Open the Validate dialog box</span></span>  
  
1.  <span data-ttu-id="49668-110">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，连接到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务器。</span><span class="sxs-lookup"><span data-stu-id="49668-110">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="49668-111">正在连接到承载 SSISDB 数据库的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的实例。</span><span class="sxs-lookup"><span data-stu-id="49668-111">You're connecting to the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that hosts the SSISDB database.</span></span>  
  
2.  <span data-ttu-id="49668-112">在对象资源管理器中，展开树以便显示 **“Integration Services 目录”** 节点。</span><span class="sxs-lookup"><span data-stu-id="49668-112">In Object Explorer, expand the tree to display the **Integration Services Catalogs** node.</span></span>  
  
3.  <span data-ttu-id="49668-113">展开 **“SSISDB”** 节点。</span><span class="sxs-lookup"><span data-stu-id="49668-113">Expand the **SSISDB** node.</span></span>  
  
4.  <span data-ttu-id="49668-114">展开包含您要验证的项目或包的文件夹。</span><span class="sxs-lookup"><span data-stu-id="49668-114">Expand the folder that contains the project or package you want to validate.</span></span>  
  
5.  <span data-ttu-id="49668-115">右键单击该包，然后单击“验证”  。</span><span class="sxs-lookup"><span data-stu-id="49668-115">Right-click the package or package, and then click **Validate**.</span></span>  
  
##  <a name="set-the-options-on-the-general-page"></a><a name="general"></a> <span data-ttu-id="49668-116">设置“常规”页上的选项</span><span class="sxs-lookup"><span data-stu-id="49668-116">Set the options on the General page</span></span>  
 <span data-ttu-id="49668-117">**环境**</span><span class="sxs-lookup"><span data-stu-id="49668-117">**Environment**</span></span>  
 <span data-ttu-id="49668-118">选择要用于验证项目或包的环境。</span><span class="sxs-lookup"><span data-stu-id="49668-118">Select the environment that you want to use to validate the project or package.</span></span>  
  
 <span data-ttu-id="49668-119">**32 位运行时**</span><span class="sxs-lookup"><span data-stu-id="49668-119">**32-bit runtime**</span></span>  
 <span data-ttu-id="49668-120">选择使用 32 位运行时来执行包。</span><span class="sxs-lookup"><span data-stu-id="49668-120">Select to use a 32-bit runtime to execute a package.</span></span>  
  
 <span data-ttu-id="49668-121">**“参数”** 选项卡列出了用于验证项目或包的参数值。</span><span class="sxs-lookup"><span data-stu-id="49668-121">The **Parameters** tab lists the parameter values that you use to validate the project or package.</span></span> <span data-ttu-id="49668-122">以下是“参数”选项卡上的选项。</span><span class="sxs-lookup"><span data-stu-id="49668-122">The following are the options on the Parameters tab.</span></span>  
  
 <span data-ttu-id="49668-123">**容器**</span><span class="sxs-lookup"><span data-stu-id="49668-123">**Container**</span></span>  
 <span data-ttu-id="49668-124">列出包含参数的对象。</span><span class="sxs-lookup"><span data-stu-id="49668-124">Lists the object that contains the parameter.</span></span>  
  
 <span data-ttu-id="49668-125">**Parameter**</span><span class="sxs-lookup"><span data-stu-id="49668-125">**Parameter**</span></span>  
 <span data-ttu-id="49668-126">列出参数的名称</span><span class="sxs-lookup"><span data-stu-id="49668-126">Lists the name of the parameters</span></span>  
  
 <span data-ttu-id="49668-127">**值**</span><span class="sxs-lookup"><span data-stu-id="49668-127">**Value**</span></span>  
 <span data-ttu-id="49668-128">列出参数值。</span><span class="sxs-lookup"><span data-stu-id="49668-128">Lists the parameter value.</span></span>  
  
 <span data-ttu-id="49668-129">**“连接管理器”** 选项卡列出了用于验证项目或包的连接管理器属性值。</span><span class="sxs-lookup"><span data-stu-id="49668-129">The **Connection Managers** tab lists the connection manager property values that you use to validate the project or package.</span></span>  
  
 <span data-ttu-id="49668-130">以下是 **“连接管理器”** 选项卡中的选项。</span><span class="sxs-lookup"><span data-stu-id="49668-130">The following are the options on the **Connection Managers** tab.</span></span>  
  
 <span data-ttu-id="49668-131">**容器**</span><span class="sxs-lookup"><span data-stu-id="49668-131">**Container**</span></span>  
 <span data-ttu-id="49668-132">列出包含连接管理器的对象。</span><span class="sxs-lookup"><span data-stu-id="49668-132">Lists the object that contains the connection manager.</span></span>  
  
 <span data-ttu-id="49668-133">**名称**</span><span class="sxs-lookup"><span data-stu-id="49668-133">**Name**</span></span>  
 <span data-ttu-id="49668-134">列出连接管理器名称。</span><span class="sxs-lookup"><span data-stu-id="49668-134">Lists the connection manager name.</span></span>  
  
 <span data-ttu-id="49668-135">**属性名称**</span><span class="sxs-lookup"><span data-stu-id="49668-135">**Property name**</span></span>  
 <span data-ttu-id="49668-136">列出连接管理器属性的名称。</span><span class="sxs-lookup"><span data-stu-id="49668-136">Lists the name of the connection manager property.</span></span>  
  
 <span data-ttu-id="49668-137">**值**</span><span class="sxs-lookup"><span data-stu-id="49668-137">**Value**</span></span>  
 <span data-ttu-id="49668-138">列出分配给连接管理器属性的值。</span><span class="sxs-lookup"><span data-stu-id="49668-138">Lists the value assigned to the connection manager property.</span></span>  
  
  
