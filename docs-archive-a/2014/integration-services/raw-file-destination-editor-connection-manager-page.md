---
title: 原始文件目标编辑器 (连接管理器页) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rawfiledestinationconnectionmanager.f1
ms.assetid: a0ec9643-3b44-4467-b855-f45ae4794f7f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a693591921a5669eb9bc8160f0be076ab4d6869b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687995"
---
# <a name="raw-file-destination-editor-connection-manager-page"></a><span data-ttu-id="53322-102">原始文件目标编辑器（“连接管理器”页）</span><span class="sxs-lookup"><span data-stu-id="53322-102">Raw File Destination Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="53322-103">使用原始文件目标编辑器配置原始文件目标以将原始数据写入文件。</span><span class="sxs-lookup"><span data-stu-id="53322-103">Use the Raw File Destination Editor to configure the Raw File destination to write raw data to a file.</span></span>  
  
 <span data-ttu-id="53322-104">**您希望做什么？**</span><span class="sxs-lookup"><span data-stu-id="53322-104">**What do you want to do?**</span></span>  
  
-   [<span data-ttu-id="53322-105">打开原始文件目标编辑器</span><span class="sxs-lookup"><span data-stu-id="53322-105">Open the Raw File Destination Editor</span></span>](#open)  
  
-   [<span data-ttu-id="53322-106">设置 "连接管理器" 选项卡上的选项</span><span class="sxs-lookup"><span data-stu-id="53322-106">Set options on the Connection Manager tab</span></span>](#connection)  
  
-   [<span data-ttu-id="53322-107">设置“列”选项卡上的选项</span><span class="sxs-lookup"><span data-stu-id="53322-107">Set options on the Columns tab</span></span>](#mapping)  
  
##  <a name="open-the-raw-file-destination-editor"></a><a name="open"></a><span data-ttu-id="53322-108">打开原始文件目标编辑器</span><span class="sxs-lookup"><span data-stu-id="53322-108">Open the Raw File Destination Editor</span></span>  
  
1.  <span data-ttu-id="53322-109">将原始文件目标添加到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 中的 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]包。</span><span class="sxs-lookup"><span data-stu-id="53322-109">Add the Raw File destination to an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package, in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="53322-110">右键单击该组件，然后单击 **“编辑”**。</span><span class="sxs-lookup"><span data-stu-id="53322-110">Right-click the component and then click **Edit**.</span></span>  
  
##  <a name="set-options-on-the-connection-manager-tab"></a><a name="connection"></a> <span data-ttu-id="53322-111">设置“连接管理器”选项卡上的选项</span><span class="sxs-lookup"><span data-stu-id="53322-111">Set options on the Connection Manager tab</span></span>  
 <span data-ttu-id="53322-112">**访问模式**</span><span class="sxs-lookup"><span data-stu-id="53322-112">**Access mode**</span></span>  
 <span data-ttu-id="53322-113">选择指定文件名的方式。</span><span class="sxs-lookup"><span data-stu-id="53322-113">Select how the file name is specified.</span></span> <span data-ttu-id="53322-114">选择 **“文件名”** 可以直接输入文件名和路径，选择 **“变量中的文件名”** 可以指定包含文件名的变量。</span><span class="sxs-lookup"><span data-stu-id="53322-114">Select **File name** to enter the file name and path directly, of **File name from variable** to specify a variable that contains the file name.</span></span>  
  
 <span data-ttu-id="53322-115">**“文件名”** 或 **“变量名称”**</span><span class="sxs-lookup"><span data-stu-id="53322-115">**File name** or **Variable name**</span></span>  
 <span data-ttu-id="53322-116">输入原始文件的名称和路径，或者选择包含文件名的变量。</span><span class="sxs-lookup"><span data-stu-id="53322-116">Enter the name and path of the raw file, or select the variable that contains the file name.</span></span>  
  
 <span data-ttu-id="53322-117">**写入选项**</span><span class="sxs-lookup"><span data-stu-id="53322-117">**Write option**</span></span>  
 <span data-ttu-id="53322-118">选择用来创建和写入文件的方法。</span><span class="sxs-lookup"><span data-stu-id="53322-118">Select the method used to create and write to the file.</span></span>  
  
 <span data-ttu-id="53322-119">**生成初始原始文件**</span><span class="sxs-lookup"><span data-stu-id="53322-119">**Generate initial raw file**</span></span>  
 <span data-ttu-id="53322-120">单击此按钮可以生成仅包含列的空原始文件（仅元数据文件），而无需运行包。</span><span class="sxs-lookup"><span data-stu-id="53322-120">Click the button to generate an empty raw file that contains only the columns (metadata-only file), without having to run the package.</span></span> <span data-ttu-id="53322-121">该文件包含在 **“原始文件目标编辑器”** 的 **“列”** 页上选择的列。</span><span class="sxs-lookup"><span data-stu-id="53322-121">The file contains the columns that you selected on the **Columns** page of the **Raw File Destination Editor**.</span></span> <span data-ttu-id="53322-122">可以将原始文件源指向此仅元数据文件。</span><span class="sxs-lookup"><span data-stu-id="53322-122">You can point the Raw File source to this metadata-only file.</span></span>  
  
 <span data-ttu-id="53322-123">单击 **“生成初始原始文件”** 时，将显示一个消息框。</span><span class="sxs-lookup"><span data-stu-id="53322-123">When you click **Generate initial raw file**, a message box appears.</span></span> <span data-ttu-id="53322-124">单击 **“确定”** 可继续创建文件。</span><span class="sxs-lookup"><span data-stu-id="53322-124">Click **OK** to proceed with creating the file.</span></span> <span data-ttu-id="53322-125">单击 **“取消”** 可选择 **“列”** 页上的其他列列表。</span><span class="sxs-lookup"><span data-stu-id="53322-125">Click **Cancel** to select a different list of columns on the **Columns** page.</span></span>  
  
##  <a name="set-options-on-the-columns-tab"></a><a name="mapping"></a><span data-ttu-id="53322-126">设置 "列" 选项卡上的选项</span><span class="sxs-lookup"><span data-stu-id="53322-126">Set options on the Columns tab</span></span>  
 <span data-ttu-id="53322-127">**可用输入列**</span><span class="sxs-lookup"><span data-stu-id="53322-127">**Available Input Columns**</span></span>  
 <span data-ttu-id="53322-128">选择要写入原始文件的一个或多个输入列。</span><span class="sxs-lookup"><span data-stu-id="53322-128">Select one or more input columns to write to the raw file.</span></span>  
  
 <span data-ttu-id="53322-129">**输入列**</span><span class="sxs-lookup"><span data-stu-id="53322-129">**Input Column**</span></span>  
 <span data-ttu-id="53322-130">当您在 **“可用输入列”** 下选择某一输入列时，该输入列将自动添加到此表中，或者，您可以直接在此表中选择该输入列。</span><span class="sxs-lookup"><span data-stu-id="53322-130">An input column is automatically added to this table when you select it under **Available Input Columns**, or you can select the input column directly in this table.</span></span>  
  
 <span data-ttu-id="53322-131">**输出别名**</span><span class="sxs-lookup"><span data-stu-id="53322-131">**Output Alias**</span></span>  
 <span data-ttu-id="53322-132">指定要用于输出列的备用名称。</span><span class="sxs-lookup"><span data-stu-id="53322-132">Specify an alternate name to use for the output column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53322-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="53322-133">See Also</span></span>  
 [<span data-ttu-id="53322-134">原始文件目标</span><span class="sxs-lookup"><span data-stu-id="53322-134">Raw File Destination</span></span>](data-flow/raw-file-destination.md)  
  
  
