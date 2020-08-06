---
title: “设置参数值”对话框 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ce9c2201-4e9a-4495-948f-b68deeaa7955
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 637267603c66921a566ca0d2a3f49f6142cfd203
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691835"
---
# <a name="set-parameter-value-dialog-box"></a><span data-ttu-id="ec4a0-102">设置参数值对话框</span><span class="sxs-lookup"><span data-stu-id="ec4a0-102">Set Parameter Value Dialog Box</span></span>
  <span data-ttu-id="ec4a0-103">使用 **“设置参数值”** 对话框可为项目和包设置参数和连接管理器属性的值。</span><span class="sxs-lookup"><span data-stu-id="ec4a0-103">Use the **Set Parameter Value** dialog box to set values for parameters and connection manager properties, for projects and packages.</span></span>  
  
 <span data-ttu-id="ec4a0-104">**您希望做什么？**</span><span class="sxs-lookup"><span data-stu-id="ec4a0-104">**What do you want to do?**</span></span>  
  
-   [<span data-ttu-id="ec4a0-105">打开“设置参数值”对话框</span><span class="sxs-lookup"><span data-stu-id="ec4a0-105">Open the Set Parameter Value dialog box</span></span>](#open_dialog)  
  
-   [<span data-ttu-id="ec4a0-106">配置选项</span><span class="sxs-lookup"><span data-stu-id="ec4a0-106">Configure the options</span></span>](#option)  
  
##  <a name="open-the-set-parameter-value-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="ec4a0-107">打开“设置参数值”对话框</span><span class="sxs-lookup"><span data-stu-id="ec4a0-107">Open the Set Parameter Value dialog box</span></span>  
  
1.  <span data-ttu-id="ec4a0-108">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，连接到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务器。</span><span class="sxs-lookup"><span data-stu-id="ec4a0-108">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="ec4a0-109">正在连接到承载 SSISDB 数据库的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的实例。</span><span class="sxs-lookup"><span data-stu-id="ec4a0-109">You're connecting to the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that hosts the SSISDB database.</span></span>  
  
2.  <span data-ttu-id="ec4a0-110">在对象资源管理器中，展开树以便显示 **“Integration Services 目录”** 节点。</span><span class="sxs-lookup"><span data-stu-id="ec4a0-110">In Object Explorer, expand the tree to display the **Integration Services Catalogs** node.</span></span>  
  
3.  <span data-ttu-id="ec4a0-111">展开 **“SSISDB”** 节点。</span><span class="sxs-lookup"><span data-stu-id="ec4a0-111">Expand the **SSISDB** node.</span></span>  
  
4.  <span data-ttu-id="ec4a0-112">右键单击包或项目，单击“配置”  ，然后单击“参数”  选项卡或“连接管理器”  选项卡中的省略号按钮。</span><span class="sxs-lookup"><span data-stu-id="ec4a0-112">Right-click a package or project, click **Configure**, and then click the ellipsis button in the **Parameters** tab or in the **Connection Managers** tab.</span></span>  
  
##  <a name="configure-the-options"></a><a name="option"></a> <span data-ttu-id="ec4a0-113">配置选项</span><span class="sxs-lookup"><span data-stu-id="ec4a0-113">Configure the options</span></span>  
 <span data-ttu-id="ec4a0-114">**Parameter**</span><span class="sxs-lookup"><span data-stu-id="ec4a0-114">**Parameter**</span></span>  
 <span data-ttu-id="ec4a0-115">列出参数名称。</span><span class="sxs-lookup"><span data-stu-id="ec4a0-115">Lists the parameter name.</span></span>  
  
 <span data-ttu-id="ec4a0-116">类型 </span><span class="sxs-lookup"><span data-stu-id="ec4a0-116">**Type**</span></span>  
 <span data-ttu-id="ec4a0-117">列出参数值的数据类型。</span><span class="sxs-lookup"><span data-stu-id="ec4a0-117">Lists the data type of the parameter value.</span></span>  
  
 <span data-ttu-id="ec4a0-118">**说明**</span><span class="sxs-lookup"><span data-stu-id="ec4a0-118">**Description**</span></span>  
 <span data-ttu-id="ec4a0-119">显示参数的可选说明。</span><span class="sxs-lookup"><span data-stu-id="ec4a0-119">Shows an optional description for the parameter.</span></span>  
  
 <span data-ttu-id="ec4a0-120">**编辑值**</span><span class="sxs-lookup"><span data-stu-id="ec4a0-120">**Edit value**</span></span>  
 <span data-ttu-id="ec4a0-121">选择此选项可编辑参数值。</span><span class="sxs-lookup"><span data-stu-id="ec4a0-121">Select this option to edit the parameter value.</span></span>  
  
 <span data-ttu-id="ec4a0-122">**使用包中的默认值**</span><span class="sxs-lookup"><span data-stu-id="ec4a0-122">**Use default value from package**</span></span>  
 <span data-ttu-id="ec4a0-123">选择此选项可以使用存储在包中的默认参数值。</span><span class="sxs-lookup"><span data-stu-id="ec4a0-123">Select this option to use the default parameter value stored in the package.</span></span>  
  
 <span data-ttu-id="ec4a0-124">**使用环境变量**</span><span class="sxs-lookup"><span data-stu-id="ec4a0-124">**Use environment variable**</span></span>  
 <span data-ttu-id="ec4a0-125">选择此选项可使用存储在环境中的由项目或包引用的变量值。</span><span class="sxs-lookup"><span data-stu-id="ec4a0-125">Select this option to use a variable value stored in the environment, which is referenced by the project or package.</span></span> <span data-ttu-id="ec4a0-126">若要向项目或包添加环境引用，请使用 **“配置”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="ec4a0-126">To add an environment reference to a project or package, use the **Configure** dialog box.</span></span> <span data-ttu-id="ec4a0-127">有关详细信息，请参阅 [Configure Dialog Box](configure-dialog-box.md)。</span><span class="sxs-lookup"><span data-stu-id="ec4a0-127">For more information, see [Configure Dialog Box](configure-dialog-box.md).</span></span>  
  
  
