---
title: " (SSAS 表格) 中复制和粘贴数据 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.pastepreviewdb.f1
ms.assetid: 2f8d8b3d-810b-4c31-98f2-341015e13da8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 30df733377f3cb6f7583d380fbb8e92a0ea69e88
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579189"
---
# <a name="copy-and-paste-data-ssas-tabular"></a><span data-ttu-id="a93d1-102">复制并粘贴数据（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="a93d1-102">Copy and Paste Data (SSAS Tabular)</span></span>
  <span data-ttu-id="a93d1-103">可以从外部应用程序复制表数据并将它粘贴到模型设计器中的新表或现有表。</span><span class="sxs-lookup"><span data-stu-id="a93d1-103">You can copy table data from external applications and paste it into a new or existing table in the model designer.</span></span> <span data-ttu-id="a93d1-104">从剪贴板粘贴的数据必须是 HTML 格式，例如，从 Excel 或 Word 中复制的数据。</span><span class="sxs-lookup"><span data-stu-id="a93d1-104">The data that you paste from the Clipboard must be in HTML format, for example, data that is copied from Excel or Word.</span></span> <span data-ttu-id="a93d1-105">模型设计器将对粘贴数据自动检测并应用数据类型。</span><span class="sxs-lookup"><span data-stu-id="a93d1-105">The model designer will automatically detect and apply data types to the pasted data.</span></span> <span data-ttu-id="a93d1-106">您也可以手动修改列的数据类型或显示格式。</span><span class="sxs-lookup"><span data-stu-id="a93d1-106">You can also manually modify the data type or display formatting of a column.</span></span>  
  
 <span data-ttu-id="a93d1-107">与具有数据源连接的表不同，粘贴的表没有“连接名称”或“源数据”属性。</span><span class="sxs-lookup"><span data-stu-id="a93d1-107">Unlike tables with a data source connection, pasted tables do not have a Connection Name or Source Data property.</span></span> <span data-ttu-id="a93d1-108">粘贴的数据在 Model.bim 文件中保持不变。</span><span class="sxs-lookup"><span data-stu-id="a93d1-108">Pasted data is persisted in the Model.bim file.</span></span> <span data-ttu-id="a93d1-109">保存项目或 Model.bim 文件时，也保存粘贴的数据。</span><span class="sxs-lookup"><span data-stu-id="a93d1-109">When the project or Model.bim file is saved, the pasted data is also saved.</span></span>  
  
 <span data-ttu-id="a93d1-110">部署模型时，无论在部署时是否处理模型，都还将部署粘贴的数据。</span><span class="sxs-lookup"><span data-stu-id="a93d1-110">When a model is deployed, pasted data will also be deployed with it regardless if the model is processed with the deployment.</span></span>  
  
 <span data-ttu-id="a93d1-111">本主题的内容：</span><span class="sxs-lookup"><span data-stu-id="a93d1-111">Sections in this topic:</span></span>  
  
-   [<span data-ttu-id="a93d1-112">先决条件</span><span class="sxs-lookup"><span data-stu-id="a93d1-112">Prerequisites</span></span>](#bkmk_prerequisites)  
  
-   [<span data-ttu-id="a93d1-113">粘贴数据</span><span class="sxs-lookup"><span data-stu-id="a93d1-113">Paste Data</span></span>](#bkmk_paste_data)  
  
-   [<span data-ttu-id="a93d1-114">“粘贴预览”对话框</span><span class="sxs-lookup"><span data-stu-id="a93d1-114">Paste Preview Dialog Box</span></span>](#bkmk_paste_preview)  
  
##  <a name="prerequisites"></a><a name="bkmk_prerequisites"></a><span data-ttu-id="a93d1-115">先决条件</span><span class="sxs-lookup"><span data-stu-id="a93d1-115">Prerequisites</span></span>  
 <span data-ttu-id="a93d1-116">粘贴数据时存在一些限制：</span><span class="sxs-lookup"><span data-stu-id="a93d1-116">There are some restrictions when pasting data:</span></span>  
  
-   <span data-ttu-id="a93d1-117">粘贴的表的行数不能超过 10,000。</span><span class="sxs-lookup"><span data-stu-id="a93d1-117">Pasted tables cannot have more than 10,000 rows.</span></span>  
  
-   <span data-ttu-id="a93d1-118">粘贴的表不能分区。</span><span class="sxs-lookup"><span data-stu-id="a93d1-118">Pasted tables cannot be partitioned.</span></span>  
  
-   <span data-ttu-id="a93d1-119">在 DirectQuery 模式中不支持粘贴的表。</span><span class="sxs-lookup"><span data-stu-id="a93d1-119">Pasted tables are not supported in DirectQuery mode.</span></span>  
  
-   <span data-ttu-id="a93d1-120">仅当使用通过从剪贴板粘贴数据初始创建的表时， **“追加粘贴”** 和 **“替换粘贴”** 选项才可用。</span><span class="sxs-lookup"><span data-stu-id="a93d1-120">The **Paste Append** and **Paste Replace** options are only available when working with a table that was initially created by pasting data from the Clipboard.</span></span> <span data-ttu-id="a93d1-121">不能使用 **“追加粘贴”** 或 **“替换粘贴”** 向导入的数据来自另一数据源类型的表添加数据。</span><span class="sxs-lookup"><span data-stu-id="a93d1-121">You cannot use **Paste Append** or **Paste Replace** to add data into a table of imported data from another type of data source.</span></span>  
  
-   <span data-ttu-id="a93d1-122">当使用 **“追加粘贴”** 或 **“替换粘贴”** 时，新数据必须与原始数据包含相同列数。</span><span class="sxs-lookup"><span data-stu-id="a93d1-122">When you use **Paste Append** or **Paste Replace**, the new data must contain exactly the same number of columns as the original data.</span></span> <span data-ttu-id="a93d1-123">最好是粘贴或追加的数据列还应与目标表中的那些数据列属于相同的数据类型或兼容的数据类型。</span><span class="sxs-lookup"><span data-stu-id="a93d1-123">Preferably, the columns of data that you paste or append should also be of the same or compatible data type as those in the destination table.</span></span> <span data-ttu-id="a93d1-124">在某些情况下，可以使用不同的数据类型，但可能会显示“类型不匹配” \*\*\*\* 错误。</span><span class="sxs-lookup"><span data-stu-id="a93d1-124">In some cases you can use a different data type, but a **Type mismatch** error may be displayed.</span></span>  
  
##  <a name="paste-data"></a><a name="bkmk_paste_data"></a><span data-ttu-id="a93d1-125">粘贴数据</span><span class="sxs-lookup"><span data-stu-id="a93d1-125">Paste Data</span></span>  
  
#### <a name="to-paste-data-into-the-designer"></a><span data-ttu-id="a93d1-126">向设计器粘贴数据</span><span class="sxs-lookup"><span data-stu-id="a93d1-126">To paste data into the designer</span></span>  
  
-   <span data-ttu-id="a93d1-127">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，单击 **“编辑”** 菜单，然后单击以下项之一：</span><span class="sxs-lookup"><span data-stu-id="a93d1-127">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click the **Edit** menu, and then clicke of the following:</span></span>  
  
    -   <span data-ttu-id="a93d1-128">单击 **“粘贴”** 可以将剪贴板的内容粘贴到新表中。</span><span class="sxs-lookup"><span data-stu-id="a93d1-128">Click **Paste** to paste the contents of the Clipboard into a new table.</span></span>  
  
    -   <span data-ttu-id="a93d1-129">单击 **“追加粘贴”** 可以将剪贴板内容作为附加行粘贴到所选表中。</span><span class="sxs-lookup"><span data-stu-id="a93d1-129">Click **Paste Append** to paste the contents of the Clipboard as additional rows into the selected table.</span></span> <span data-ttu-id="a93d1-130">新行将添加到表的末尾。</span><span class="sxs-lookup"><span data-stu-id="a93d1-130">The new rows will be added to the end of the table.</span></span>  
  
    -   <span data-ttu-id="a93d1-131">单击 **“替换粘贴”** 可以用剪贴板内容取代所选表。</span><span class="sxs-lookup"><span data-stu-id="a93d1-131">Click **Paste Replace** to replace the selected table with the contents of the Clipboard.</span></span> <span data-ttu-id="a93d1-132">所有现有列标题的名称都将保留在表中，并且将保留关系。</span><span class="sxs-lookup"><span data-stu-id="a93d1-132">All existing column header names will remain in the table, and relationships are preserved.</span></span>  
  
##  <a name="paste-preview-dialog-box"></a><a name="bkmk_paste_preview"></a><span data-ttu-id="a93d1-133">"粘贴预览" 对话框</span><span class="sxs-lookup"><span data-stu-id="a93d1-133">Paste Preview Dialog Box</span></span>  
 <span data-ttu-id="a93d1-134">**“粘贴预览”** 对话框可用于查看复制到设计器窗口中的数据的预览以及确保数据正确复制。</span><span class="sxs-lookup"><span data-stu-id="a93d1-134">The **Paste Preview** dialog box enables you to see a preview of data that is copied into the designer window and to ensure that the data is copied correctly.</span></span> <span data-ttu-id="a93d1-135">若要访问此对话框，请将 HTML 格式的基于表的数据复制到剪贴板中，然后在设计器中，单击“编辑”\*\*\*\* 菜单，然后单击“粘贴”\*\*\*\*、“追加粘贴”\*\*\*\* 或“替换粘贴”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a93d1-135">To access this dialog box, copy table-based data in the HTML format to the clipboard, and then in the designer, click on the **Edit** menu, and then click **Paste**, **Paste Append**, or **Paste Replace**.</span></span> <span data-ttu-id="a93d1-136">仅当通过从剪贴板复制和粘贴来添加或替换所创建的表中的数据时， **“粘贴追加”** 和 **“粘贴替换”** 选项才可用。</span><span class="sxs-lookup"><span data-stu-id="a93d1-136">The **Paste Append** and **Paste Replace** options are only available when you add or replace data in a table that was created by copying and pasting from the Clipboard.</span></span> <span data-ttu-id="a93d1-137">不能使用 **“粘贴追加”** 或 **“粘贴替换”** 向包含导入数据的表添加数据。</span><span class="sxs-lookup"><span data-stu-id="a93d1-137">You cannot use **Paste Append** or **Paste Replace** to add data into a table of imported data.</span></span>  
  
 <span data-ttu-id="a93d1-138">根据您是将数据粘贴到全新的表中，将数据粘贴到现有表中并用新数据替换现有数据，还是将数据追加到现有表中，此对话框的选项将有所不同。</span><span class="sxs-lookup"><span data-stu-id="a93d1-138">The options for this dialog box are different depending on whether you paste data into a completely new table, paste data into an existing table and then replace the existing data with the new data, or whether you append data to an existing table.</span></span>  
  
### <a name="paste-to-new-table"></a><span data-ttu-id="a93d1-139">粘贴到新表中</span><span class="sxs-lookup"><span data-stu-id="a93d1-139">Paste to New Table</span></span>  
 <span data-ttu-id="a93d1-140">**表名称**</span><span class="sxs-lookup"><span data-stu-id="a93d1-140">**Table name**</span></span>  
 <span data-ttu-id="a93d1-141">指定将在设计器窗口中创建的表的名称。</span><span class="sxs-lookup"><span data-stu-id="a93d1-141">Specify the name of the table that will be created in the designer.</span></span>  
  
 <span data-ttu-id="a93d1-142">**要粘贴的数据**</span><span class="sxs-lookup"><span data-stu-id="a93d1-142">**Data to be pasted**</span></span>  
 <span data-ttu-id="a93d1-143">显示将添加到目标表中的剪贴板内容的示例。</span><span class="sxs-lookup"><span data-stu-id="a93d1-143">Shows a sample of the Clipboard contents that will be added to the destination table.</span></span>  
  
### <a name="paste-append"></a><span data-ttu-id="a93d1-144">“追加粘贴”</span><span class="sxs-lookup"><span data-stu-id="a93d1-144">Paste Append</span></span>  
 <span data-ttu-id="a93d1-145">**表中的现有数据**</span><span class="sxs-lookup"><span data-stu-id="a93d1-145">**Existing data in the table**</span></span>  
 <span data-ttu-id="a93d1-146">显示表中现有数据的示例，以便您可以验证列、数据类型等等。</span><span class="sxs-lookup"><span data-stu-id="a93d1-146">Shows a sample of the existing data in the table so that you can verify the columns, data types, etc.</span></span>  
  
 <span data-ttu-id="a93d1-147">**要粘贴的数据**</span><span class="sxs-lookup"><span data-stu-id="a93d1-147">**Data to be pasted**</span></span>  
 <span data-ttu-id="a93d1-148">显示剪贴板内容的示例。</span><span class="sxs-lookup"><span data-stu-id="a93d1-148">Shows a sample of the Clipboard contents.</span></span> <span data-ttu-id="a93d1-149">将为现有数据追加此数据。</span><span class="sxs-lookup"><span data-stu-id="a93d1-149">The existing data will be appended by this data.</span></span>  
  
### <a name="paste-replace"></a><span data-ttu-id="a93d1-150">“替换粘贴”</span><span class="sxs-lookup"><span data-stu-id="a93d1-150">Paste Replace</span></span>  
 <span data-ttu-id="a93d1-151">**表中的现有数据**</span><span class="sxs-lookup"><span data-stu-id="a93d1-151">**Existing data in the table**</span></span>  
 <span data-ttu-id="a93d1-152">显示表中现有数据的示例，以便您可以验证列、数据类型等等。</span><span class="sxs-lookup"><span data-stu-id="a93d1-152">Shows a sample of the existing data in the table so that you can verify the columns, data types, etc.</span></span>  
  
 <span data-ttu-id="a93d1-153">**要粘贴的数据**</span><span class="sxs-lookup"><span data-stu-id="a93d1-153">**Data to be pasted**</span></span>  
 <span data-ttu-id="a93d1-154">显示剪贴板内容的示例。</span><span class="sxs-lookup"><span data-stu-id="a93d1-154">Shows a sample of the Clipboard contents.</span></span> <span data-ttu-id="a93d1-155">目标表中的现有数据将被删除，并且将新行插入到表中。</span><span class="sxs-lookup"><span data-stu-id="a93d1-155">The existing data in the destination table will be deleted and the new rows will be inserted into the table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a93d1-156">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a93d1-156">See Also</span></span>  
 <span data-ttu-id="a93d1-157">[&#40;SSAS 表格&#41;导入数据](import-data-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="a93d1-157">[Import Data &#40;SSAS Tabular&#41;](import-data-ssas-tabular.md) </span></span>  
 <span data-ttu-id="a93d1-158">[&#40;SSAS 表格&#41;支持的数据源](tabular-models/data-sources-supported-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="a93d1-158">[Data Sources Supported &#40;SSAS Tabular&#41;](tabular-models/data-sources-supported-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="a93d1-159">设置列的数据类型（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="a93d1-159">Set the Data Type of a Column &#40;SSAS Tabular&#41;</span></span>](tabular-models/set-the-data-type-of-a-column-ssas-tabular.md)  
  
  
