---
title: 新模型页 (报表管理器) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 27d5bf66-b0e7-489e-a830-ffe2ec8e5350
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ed591108585b494ebb4498c1a0ab3e782693a45b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588936"
---
# <a name="new-model-page-report-manager"></a><span data-ttu-id="9d099-102">“新建模型”页（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="9d099-102">New Model Page (Report Manager)</span></span>
  <span data-ttu-id="9d099-103">使用此页可以从共享数据源生成默认的报表模型。</span><span class="sxs-lookup"><span data-stu-id="9d099-103">Use this page to generate a default report model from a shared data source.</span></span> <span data-ttu-id="9d099-104">只能从 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 多维数据源、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 关系数据源和 Oracle 关系数据源生成报表模型。</span><span class="sxs-lookup"><span data-stu-id="9d099-104">You can only generate report models from [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] multidimensional data sources, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] relational data sources, and Oracle relational data sources.</span></span>  
  
 <span data-ttu-id="9d099-105">在报表管理器中生成的模型基于共享数据源的架构。</span><span class="sxs-lookup"><span data-stu-id="9d099-105">Models that you generate in Report Manager are based on the schema of the shared data source.</span></span> <span data-ttu-id="9d099-106">将为数据源中的所有表和列创建实体、文件夹和字段。</span><span class="sxs-lookup"><span data-stu-id="9d099-106">Entities, folders, and fields are created for all tables and columns in the data source.</span></span> <span data-ttu-id="9d099-107">您既不能排除项，也不能设置用于决定如何生成模型的选项。</span><span class="sxs-lookup"><span data-stu-id="9d099-107">You cannot exclude items, nor can you set options that determine how the model is generated.</span></span> <span data-ttu-id="9d099-108">如果要自定义或完善模型，则必须改用模型设计器。</span><span class="sxs-lookup"><span data-stu-id="9d099-108">If you want to customize or refine a model, you must use Model Designer instead.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="9d099-109">导航</span><span class="sxs-lookup"><span data-stu-id="9d099-109">Navigation</span></span>  
 <span data-ttu-id="9d099-110">使用以下过程导航到用户界面 (UI) 中的这一位置。</span><span class="sxs-lookup"><span data-stu-id="9d099-110">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-new-model-page"></a><span data-ttu-id="9d099-111">打开“新建模型”页</span><span class="sxs-lookup"><span data-stu-id="9d099-111">To open the New Model page</span></span>  
  
1.  <span data-ttu-id="9d099-112">打开报表管理器，找到您要从中生成模型的共享数据源。</span><span class="sxs-lookup"><span data-stu-id="9d099-112">Open Report Manager, and locate the shared data source from which you want to generate a model.</span></span>  
  
2.  <span data-ttu-id="9d099-113">悬停在该数据源之上，然后单击下拉箭头。</span><span class="sxs-lookup"><span data-stu-id="9d099-113">Hover over the data source, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="9d099-114">在下拉菜单中，执行以下步骤之一：</span><span class="sxs-lookup"><span data-stu-id="9d099-114">In the drop-down menu, perform one of the following steps:</span></span>  
  
    -   <span data-ttu-id="9d099-115">单击 **“生成报表模型”** 以打开“新建模型”页。</span><span class="sxs-lookup"><span data-stu-id="9d099-115">Click **Generate Report Model** to open the New Model page.</span></span>  
  
    -   <span data-ttu-id="9d099-116">单击 **“管理”** 以打开报表的“常规属性”页。</span><span class="sxs-lookup"><span data-stu-id="9d099-116">Click **Manage** to open the General properties page for the report.</span></span> <span data-ttu-id="9d099-117">然后，单击 **“生成模型”** 以打开“新建模型”页。</span><span class="sxs-lookup"><span data-stu-id="9d099-117">Then click **Generate Model** to open the New Model page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="9d099-118">选项</span><span class="sxs-lookup"><span data-stu-id="9d099-118">Options</span></span>  
 <span data-ttu-id="9d099-119">**名称**</span><span class="sxs-lookup"><span data-stu-id="9d099-119">**Name**</span></span>  
 <span data-ttu-id="9d099-120">指定模型的名称。</span><span class="sxs-lookup"><span data-stu-id="9d099-120">Specifies the name of the model.</span></span> <span data-ttu-id="9d099-121">名称必须至少包含一个字母数字字符。</span><span class="sxs-lookup"><span data-stu-id="9d099-121">A name must contain at least one alphanumeric character.</span></span> <span data-ttu-id="9d099-122">还可以包含空格和某些符号。</span><span class="sxs-lookup"><span data-stu-id="9d099-122">It can also include spaces and some symbols.</span></span> <span data-ttu-id="9d099-123">在指定名称时请不要使用以下字符：</span><span class="sxs-lookup"><span data-stu-id="9d099-123">Do not use the following characters when specifying a name:</span></span>  
  
 <span data-ttu-id="9d099-124">; ?</span><span class="sxs-lookup"><span data-stu-id="9d099-124">; ?</span></span> <span data-ttu-id="9d099-125">： \@ & = +，$/\* \< > |" /</span><span class="sxs-lookup"><span data-stu-id="9d099-125">: \@ & = + , $ / \* \< > | " /</span></span>  
  
 <span data-ttu-id="9d099-126">**描述**</span><span class="sxs-lookup"><span data-stu-id="9d099-126">**Description**</span></span>  
 <span data-ttu-id="9d099-127">显示模型的说明。</span><span class="sxs-lookup"><span data-stu-id="9d099-127">Shows a description of the model.</span></span> <span data-ttu-id="9d099-128">通过报表管理器查看此项的用户在浏览文件夹层次结构时会看到此说明。</span><span class="sxs-lookup"><span data-stu-id="9d099-128">Users who view this item through Report Manager see this description when browsing the folder hierarchy.</span></span>  
  
 <span data-ttu-id="9d099-129">**更改位置**</span><span class="sxs-lookup"><span data-stu-id="9d099-129">**Change Location**</span></span>  
 <span data-ttu-id="9d099-130">显示新模型的文件夹位置。</span><span class="sxs-lookup"><span data-stu-id="9d099-130">Shows the folder location for the new model.</span></span> <span data-ttu-id="9d099-131">可以单击 **“更改位置”** 按钮来选择其他位置。</span><span class="sxs-lookup"><span data-stu-id="9d099-131">You can click the **Change Location** button to select a different location.</span></span>  
  
  
