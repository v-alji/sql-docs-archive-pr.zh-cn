---
title: 管理 (SQL Server 数据挖掘外接程序) 的模型 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, importing
- mining models, deleting
- mining models, managing
- mining models, training
- mining models, processing
- mining models, exporting
ms.assetid: c11380f0-7c24-4668-9cdf-9c53e4aff665
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5f4b5961ec79bb949bf7fa5f53a980f066e81379
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589331"
---
# <a name="manage-models-sql-server-data-mining-add-ins"></a><span data-ttu-id="5528e-102">管理模型（SQL Server 数据挖掘外接程序）</span><span class="sxs-lookup"><span data-stu-id="5528e-102">Manage Models (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="5528e-103">![“数据挖掘”功能区中的“管理模型”按钮](media/dmc-manage.gif "“数据挖掘”功能区中的“管理模型”按钮")</span><span class="sxs-lookup"><span data-stu-id="5528e-103">![Manage Models button, Data Mining ribbon](media/dmc-manage.gif "Manage Models button, Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="5528e-104">利用 "**管理模型**" 对话框，您可以与 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 当前连接到的服务器中存储的现有挖掘模型和挖掘结构进行交互。</span><span class="sxs-lookup"><span data-stu-id="5528e-104">The **Manage Models** dialog box enables you to interact with existing mining models and mining structures that are stored in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server to which you are currently connected.</span></span> <span data-ttu-id="5528e-105">您还可以查看和管理已在当前会话期间创建的临时结构和模型。</span><span class="sxs-lookup"><span data-stu-id="5528e-105">You can also view and manage temporary structures and models that have been created during the current session.</span></span> <span data-ttu-id="5528e-106">如果您同时使用会话模型和存储在服务器上的模型，则这两种模型在该对话框中都是可见的。</span><span class="sxs-lookup"><span data-stu-id="5528e-106">If you have used both session models and models stored on a server, both are visible in the dialog box.</span></span>  
  
## <a name="using-the-manage-models-wizard"></a><span data-ttu-id="5528e-107">使用管理模型向导</span><span class="sxs-lookup"><span data-stu-id="5528e-107">Using the Manage Models Wizard</span></span>  
 <span data-ttu-id="5528e-108">单击 "**管理模型**" 时，将打开 "**管理挖掘结构和模型**" 对话框，为管理现有数据挖掘模型和结构提供以下功能的访问权限：</span><span class="sxs-lookup"><span data-stu-id="5528e-108">When you click **Manage Models**, the **Manage Mining Structures and Models** dialog box opens, providing access to the following functionality for managing existing data mining models and structures:</span></span>  
  
-   <span data-ttu-id="5528e-109">重命名挖掘模型或结构</span><span class="sxs-lookup"><span data-stu-id="5528e-109">Rename a mining model or structure</span></span>  
  
-   <span data-ttu-id="5528e-110">删除挖掘模型或结构</span><span class="sxs-lookup"><span data-stu-id="5528e-110">Delete a mining model or structure</span></span>  
  
-   <span data-ttu-id="5528e-111">清除挖掘模型或结构</span><span class="sxs-lookup"><span data-stu-id="5528e-111">Clear a mining model or structure</span></span>  
  
-   <span data-ttu-id="5528e-112">使用新数据或现有数据处理挖掘结构</span><span class="sxs-lookup"><span data-stu-id="5528e-112">Process a mining structure, using either new or existing data</span></span>  
  
-   <span data-ttu-id="5528e-113">导出或导入挖掘模型或结构</span><span class="sxs-lookup"><span data-stu-id="5528e-113">Export or import a mining model or structure</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5528e-114">您不能使用此对话框创建查询或模型。</span><span class="sxs-lookup"><span data-stu-id="5528e-114">You cannot create queries or models by using this dialog box.</span></span> <span data-ttu-id="5528e-115">若要创建新的挖掘结构，请使用 Excel 数据挖掘客户端中提供的向导之一，或使用**数据挖掘查询高级编辑器**。</span><span class="sxs-lookup"><span data-stu-id="5528e-115">To create a new mining structure, use one of the wizards provided in the Data Mining Client for Excel, or use the **Data Mining Query Advanced Editor**.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="5528e-116">要求</span><span class="sxs-lookup"><span data-stu-id="5528e-116">Requirements</span></span>  
 <span data-ttu-id="5528e-117">若要管理数据挖掘模型，您必须首先创建到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例的连接。</span><span class="sxs-lookup"><span data-stu-id="5528e-117">To manage data mining models, you must first create a connection to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="5528e-118">连接是必需的，即使处理的是存储在临时文件中的会话模型也需要连接。</span><span class="sxs-lookup"><span data-stu-id="5528e-118">A connection is required even if you are working with session models stored in a temporary file.</span></span> <span data-ttu-id="5528e-119">有关如何创建或更改连接的详细信息，请参阅[连接到源数据 &#40;Excel 数据挖掘客户端&#41;](connect-to-source-data-data-mining-client-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="5528e-119">For more information about how to create or change a connection, see [Connect to Source Data &#40;Data Mining Client for Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).</span></span>  
  
 <span data-ttu-id="5528e-120">如果所连接到的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例不包含任何现有数据挖掘结构或数据挖掘模型，您可以使用此外接程序提供的向导和其他工具来创建它们。</span><span class="sxs-lookup"><span data-stu-id="5528e-120">If the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that you connect to does not contain any existing data mining structures or data mining models, you can create them by using the wizards and other tools provided by this add-in.</span></span> <span data-ttu-id="5528e-121">您还可以通过使用**数据挖掘模型高级编辑器**来创建新模型。</span><span class="sxs-lookup"><span data-stu-id="5528e-121">You can also create new models by using the **Data Mining Model Advanced Editor**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5528e-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5528e-122">See Also</span></span>  
 <span data-ttu-id="5528e-123">[记录挖掘模型 &#40;Excel 数据挖掘外接程序&#41;](documenting-mining-models-data-mining-add-ins-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="5528e-123">[Documenting Mining Models &#40;Data Mining Add-ins for Excel&#41;](documenting-mining-models-data-mining-add-ins-for-excel.md) </span></span>  
 [<span data-ttu-id="5528e-124">&#40;Excel 数据挖掘外接程序部署和缩放挖掘模型&#41;</span><span class="sxs-lookup"><span data-stu-id="5528e-124">Deploying and Scaling Mining Models &#40;Data Mining Add-ins for Excel&#41;</span></span>](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)   

  
