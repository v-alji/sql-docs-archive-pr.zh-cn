---
title: 原始文件目标编辑器 (列 "页) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rawfiledestinationcolumns.f1
ms.assetid: 37f61d0b-1269-42ee-94ab-011cbaac63e9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8a89d8ca46805a23fd03465ed40428081499dccb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687996"
---
# <a name="raw-file-destination-editor-columns-page"></a><span data-ttu-id="2e828-102">原始文件目标编辑器（“列”页）</span><span class="sxs-lookup"><span data-stu-id="2e828-102">Raw File Destination Editor (Columns Page)</span></span>
  <span data-ttu-id="2e828-103">使用原始文件目标编辑器配置原始文件目标以将原始数据写入文件。</span><span class="sxs-lookup"><span data-stu-id="2e828-103">Use the Raw File Destination Editor to configure the Raw File destination to write raw data to a file.</span></span>  
  
 <span data-ttu-id="2e828-104">**您希望做什么？**</span><span class="sxs-lookup"><span data-stu-id="2e828-104">**What do you want to do?**</span></span>  
  
-   [<span data-ttu-id="2e828-105">打开原始文件目标编辑器</span><span class="sxs-lookup"><span data-stu-id="2e828-105">Open the Raw File Destination Editor</span></span>](#open)  
  
-   [<span data-ttu-id="2e828-106">设置 "连接管理器" 选项卡上的选项</span><span class="sxs-lookup"><span data-stu-id="2e828-106">Set options on the Connection Manager tab</span></span>](#connection)  
  
-   [<span data-ttu-id="2e828-107">设置“列”选项卡上的选项</span><span class="sxs-lookup"><span data-stu-id="2e828-107">Set options on the Columns tab</span></span>](#mapping)  
  
##  <a name="open-the-raw-file-destination-editor"></a><a name="open"></a><span data-ttu-id="2e828-108">打开原始文件目标编辑器</span><span class="sxs-lookup"><span data-stu-id="2e828-108">Open the Raw File Destination Editor</span></span>  
  
1.  <span data-ttu-id="2e828-109">将原始文件目标添加到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 中的 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]包。</span><span class="sxs-lookup"><span data-stu-id="2e828-109">Add the Raw File destination to an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package, in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="2e828-110">右键单击该组件，然后单击 **“编辑”**。</span><span class="sxs-lookup"><span data-stu-id="2e828-110">Right-click the component and then click **Edit**.</span></span>  
  
##  <a name="set-options-on-the-connection-manager-tab"></a><a name="connection"></a> <span data-ttu-id="2e828-111">设置“连接管理器”选项卡上的选项</span><span class="sxs-lookup"><span data-stu-id="2e828-111">Set options on the Connection Manager tab</span></span>  
 <span data-ttu-id="2e828-112">**访问模式**</span><span class="sxs-lookup"><span data-stu-id="2e828-112">**Access mode**</span></span>  
 <span data-ttu-id="2e828-113">选择指定文件名的方式。</span><span class="sxs-lookup"><span data-stu-id="2e828-113">Select how the file name is specified.</span></span> <span data-ttu-id="2e828-114">选择 **“文件名”** 可以直接输入文件名和路径，选择 **“变量中的文件名”** 可以指定包含文件名的变量。</span><span class="sxs-lookup"><span data-stu-id="2e828-114">Select **File name** to enter the file name and path directly, of **File name from variable** to specify a variable that contains the file name.</span></span>  
  
 <span data-ttu-id="2e828-115">**“文件名”** 或 **“变量名称”**</span><span class="sxs-lookup"><span data-stu-id="2e828-115">**File name** or **Variable name**</span></span>  
 <span data-ttu-id="2e828-116">输入原始文件的名称和路径，或者选择包含文件名的变量。</span><span class="sxs-lookup"><span data-stu-id="2e828-116">Enter the name and path of the raw file, or select the variable that contains the file name.</span></span>  
  
 <span data-ttu-id="2e828-117">**写入选项**</span><span class="sxs-lookup"><span data-stu-id="2e828-117">**Write option**</span></span>  
 <span data-ttu-id="2e828-118">选择用来创建和写入文件的方法。</span><span class="sxs-lookup"><span data-stu-id="2e828-118">Select the method used to create and write to the file.</span></span>  
  
 <span data-ttu-id="2e828-119">**生成初始原始文件**</span><span class="sxs-lookup"><span data-stu-id="2e828-119">**Generate initial raw file**</span></span>  
 <span data-ttu-id="2e828-120">单击此按钮可以生成仅包含列的空原始文件（仅元数据文件），而无需运行包。</span><span class="sxs-lookup"><span data-stu-id="2e828-120">Click the button to generate an empty raw file that contains only the columns (metadata-only file), without having to run the package.</span></span> <span data-ttu-id="2e828-121">可以将原始文件源指向仅元数据文件。</span><span class="sxs-lookup"><span data-stu-id="2e828-121">You can point the Raw File source to the metadata-only file.</span></span>  
  
 <span data-ttu-id="2e828-122">单击此按钮时，将显示列的列表。</span><span class="sxs-lookup"><span data-stu-id="2e828-122">When you click the button, a list of the columns appears.</span></span> <span data-ttu-id="2e828-123">您可以单击“取消”以修改列或单击“确定”以继续创建该文件。</span><span class="sxs-lookup"><span data-stu-id="2e828-123">You can click cancel and modify the columns or click OK to proceed with creating the file.</span></span>  
  
##  <a name="set-options-on-the-columns-tab"></a><a name="mapping"></a><span data-ttu-id="2e828-124">设置 "列" 选项卡上的选项</span><span class="sxs-lookup"><span data-stu-id="2e828-124">Set options on the Columns tab</span></span>  
 <span data-ttu-id="2e828-125">**可用输入列**</span><span class="sxs-lookup"><span data-stu-id="2e828-125">**Available Input Columns**</span></span>  
 <span data-ttu-id="2e828-126">选择要写入原始文件的一个或多个输入列。</span><span class="sxs-lookup"><span data-stu-id="2e828-126">Select one or more input columns to write to the raw file.</span></span>  
  
 <span data-ttu-id="2e828-127">**输入列**</span><span class="sxs-lookup"><span data-stu-id="2e828-127">**Input Column**</span></span>  
 <span data-ttu-id="2e828-128">当您在 **“可用输入列”** 下选择某一输入列时，该输入列将自动添加到此表中，或者，您可以直接在此表中选择该输入列。</span><span class="sxs-lookup"><span data-stu-id="2e828-128">An input column is automatically added to this table when you select it under **Available Input Columns**, or you can select the input column directly in this table.</span></span>  
  
 <span data-ttu-id="2e828-129">**输出别名**</span><span class="sxs-lookup"><span data-stu-id="2e828-129">**Output Alias**</span></span>  
 <span data-ttu-id="2e828-130">指定要用于输出列的备用名称。</span><span class="sxs-lookup"><span data-stu-id="2e828-130">Specify an alternate name to use for the output column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e828-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2e828-131">See Also</span></span>  
 [<span data-ttu-id="2e828-132">原始文件目标</span><span class="sxs-lookup"><span data-stu-id="2e828-132">Raw File Destination</span></span>](data-flow/raw-file-destination.md)  
  
  
