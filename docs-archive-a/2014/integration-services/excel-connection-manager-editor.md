---
title: Excel 连接管理器编辑器 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.excelconnection.f1
helpviewer_keywords:
- Excel Connection Manager Editor
ms.assetid: 7ff097e4-cafb-4885-a898-05b2a46628c1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7f66de13b710e5ccb577e6f2d67c215572e34767
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587500"
---
# <a name="excel-connection-manager-editor"></a><span data-ttu-id="44993-102">Excel 连接管理器编辑器</span><span class="sxs-lookup"><span data-stu-id="44993-102">Excel Connection Manager Editor</span></span>
  <span data-ttu-id="44993-103">使用 **“Excel 连接管理器编辑器”** 对话框可以将连接添加到现有或新的 [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 工作簿文件。</span><span class="sxs-lookup"><span data-stu-id="44993-103">Use the **Excel Connection Manager Editor** dialog box to add a connection to an existing or a new [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] workbook file.</span></span>  
  
 <span data-ttu-id="44993-104">若要了解有关 Excel 连接管理器的详细信息，请参阅 [Excel Connection Manager](connection-manager/excel-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="44993-104">To learn more about the Excel connection manager, see [Excel Connection Manager](connection-manager/excel-connection-manager.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="44993-105">无法连接到受密码保护的 Excel 文件。</span><span class="sxs-lookup"><span data-stu-id="44993-105">You cannot connect to a password-protected Excel file.</span></span>  
  
## <a name="options"></a><span data-ttu-id="44993-106">选项</span><span class="sxs-lookup"><span data-stu-id="44993-106">Options</span></span>  
 <span data-ttu-id="44993-107">**Excel 文件路径**</span><span class="sxs-lookup"><span data-stu-id="44993-107">**Excel file path**</span></span>  
 <span data-ttu-id="44993-108">键入一个现有或新的 Excel 工作簿文件 (.xls) 的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="44993-108">Type the path and file name of an existing or a new Excel workbook file (.xls).</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="44993-109">当您选择一个指向新的/不存在的文件的**Excel 连接**，然后单击**Excel 工作表名称**的 "**新建**" 时， **excel 目标编辑器**会自动创建该 excel 文件。</span><span class="sxs-lookup"><span data-stu-id="44993-109">The **Excel Destination Editor** automatically creates the Excel file when you select an **Excel Connection** that points to a new/non-existent file and then click **New** for **Name of the Excel Sheet**.</span></span>  
  
 <span data-ttu-id="44993-110">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="44993-110">**Browse**</span></span>  
 <span data-ttu-id="44993-111">使用 "**打开**" 对话框可以导航到 excel 文件所在的文件夹或要在其中创建新文件的文件夹。</span><span class="sxs-lookup"><span data-stu-id="44993-111">Use the **Open** dialog box to navigate to the folder in which the excel file exists or where you want to create the new file.</span></span>  
  
 <span data-ttu-id="44993-112">**Excel 版本**</span><span class="sxs-lookup"><span data-stu-id="44993-112">**Excel version**</span></span>  
 <span data-ttu-id="44993-113">指定用于创建文件的 Microsoft Excel 的版本。</span><span class="sxs-lookup"><span data-stu-id="44993-113">Specify the version of Microsoft Excel that was used to create the file.</span></span>  
  
|<span data-ttu-id="44993-114">选项</span><span class="sxs-lookup"><span data-stu-id="44993-114">Option</span></span>|<span data-ttu-id="44993-115">说明</span><span class="sxs-lookup"><span data-stu-id="44993-115">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="44993-116">Excel 97-2003</span><span class="sxs-lookup"><span data-stu-id="44993-116">Excel 97-2003</span></span>|<span data-ttu-id="44993-117">文件是使用 Excel 97 或更高版本创建的。</span><span class="sxs-lookup"><span data-stu-id="44993-117">File was created using Excel 97 or later.</span></span>|  
|<span data-ttu-id="44993-118">Excel 3。0</span><span class="sxs-lookup"><span data-stu-id="44993-118">Excel 3.0</span></span>|<span data-ttu-id="44993-119">文件是使用 Excel 3.0 创建的。</span><span class="sxs-lookup"><span data-stu-id="44993-119">File was created using Excel 3.0.</span></span>|  
|<span data-ttu-id="44993-120">Excel 4。0</span><span class="sxs-lookup"><span data-stu-id="44993-120">Excel 4.0</span></span>|<span data-ttu-id="44993-121">文件是使用 Excel 4.0 创建的。</span><span class="sxs-lookup"><span data-stu-id="44993-121">File was created using Excel 4.0.</span></span>|  
|<span data-ttu-id="44993-122">Excel 5。0</span><span class="sxs-lookup"><span data-stu-id="44993-122">Excel 5.0</span></span>|<span data-ttu-id="44993-123">文件是使用 Excel 95 (7.0) 创建的。</span><span class="sxs-lookup"><span data-stu-id="44993-123">File was created using Excel 95 (7.0).</span></span>|  
  
 <span data-ttu-id="44993-124">**第一行包含列名称**</span><span class="sxs-lookup"><span data-stu-id="44993-124">**First row has column names**</span></span>  
 <span data-ttu-id="44993-125">指定所选工作表中的第一行数据是否包含列名称。</span><span class="sxs-lookup"><span data-stu-id="44993-125">Specify whether the first row of data in the selected worksheet contains column names.</span></span> <span data-ttu-id="44993-126">此选项的默认值为 **True**。</span><span class="sxs-lookup"><span data-stu-id="44993-126">The default value of this option is **True**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44993-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="44993-127">See Also</span></span>  
 <span data-ttu-id="44993-128">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="44993-128">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="44993-129">使用 Foreach 循环容器循环遍历 Excel 文件和表</span><span class="sxs-lookup"><span data-stu-id="44993-129">Loop through Excel Files and Tables by Using a Foreach Loop Container</span></span>](control-flow/foreach-loop-container.md)  
  
  
