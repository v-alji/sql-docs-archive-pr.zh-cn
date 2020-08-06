---
title: 复制列转换编辑器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.copymaptransformation.f1
helpviewer_keywords:
- Copy Column Transformation Editor
ms.assetid: d8e70541-d563-4ce4-bf66-bc888a0d3026
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7647d25891b37e5f09356d427072e84b45882e4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587535"
---
# <a name="copy-column-transformation-editor"></a><span data-ttu-id="59391-102">复制列转换编辑器</span><span class="sxs-lookup"><span data-stu-id="59391-102">Copy Column Transformation Editor</span></span>
  <span data-ttu-id="59391-103">可以使用 **“复制列转换编辑器”** 对话框选择要复制的列，以及为新的输出列指定名称。</span><span class="sxs-lookup"><span data-stu-id="59391-103">Use the **Copy Column Transformation Editor** dialog box to select columns to copy and to assign names for the new output columns.</span></span>  
  
 <span data-ttu-id="59391-104">若要了解有关复制列转换的详细信息，请参阅 [Copy Column Transformation](data-flow/transformations/copy-column-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="59391-104">To learn more about the Copy Column transformation, see [Copy Column Transformation](data-flow/transformations/copy-column-transformation.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="59391-105">如果只是将所有源数据复制到目标，可能无需使用复制列转换。</span><span class="sxs-lookup"><span data-stu-id="59391-105">When you are simply copying all of your source data to a destination, it may not be necessary to use the Copy Column transformation.</span></span> <span data-ttu-id="59391-106">某些情况下，如果不需要进行任何数据转换，可以直接将源连接到目标。</span><span class="sxs-lookup"><span data-stu-id="59391-106">In some scenarios, you can connect a source directly to a destination, when no data transformation is required.</span></span> <span data-ttu-id="59391-107">在这些情况下，使用 SQL Server 导入和导出向导创建包通常更可取。</span><span class="sxs-lookup"><span data-stu-id="59391-107">In these circumstances it is often preferable to use the SQL Server Import and Export Wizard to create your package for you.</span></span> <span data-ttu-id="59391-108">以后，您可以根据需要增强并重新配置包。</span><span class="sxs-lookup"><span data-stu-id="59391-108">Later you can enhance and reconfigure the package as needed.</span></span> <span data-ttu-id="59391-109">有关更多信息，请参见 [SQL Server Import and Export Wizard](import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="59391-109">For more information, see [SQL Server Import and Export Wizard](import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="59391-110">选项</span><span class="sxs-lookup"><span data-stu-id="59391-110">Options</span></span>  
 <span data-ttu-id="59391-111">**可用输入列**</span><span class="sxs-lookup"><span data-stu-id="59391-111">**Available Input Columns**</span></span>  
 <span data-ttu-id="59391-112">使用复选框选择要复制的列。</span><span class="sxs-lookup"><span data-stu-id="59391-112">Select columns to copy by using the check boxes.</span></span> <span data-ttu-id="59391-113">选择后，会将输入列添加到下表中。</span><span class="sxs-lookup"><span data-stu-id="59391-113">Your selections add input columns to the table below.</span></span>  
  
 <span data-ttu-id="59391-114">**输入列**</span><span class="sxs-lookup"><span data-stu-id="59391-114">**Input Column**</span></span>  
 <span data-ttu-id="59391-115">从可用的输入列列表中选择要复制的列。</span><span class="sxs-lookup"><span data-stu-id="59391-115">Select columns to copy from the list of available input columns.</span></span> <span data-ttu-id="59391-116">通过选中 **“可用输入列”** 表中的复选框来选择列。</span><span class="sxs-lookup"><span data-stu-id="59391-116">Your selections are reflected in the check box selections in the **Available Input Columns** table.</span></span>  
  
 <span data-ttu-id="59391-117">**输出别名**</span><span class="sxs-lookup"><span data-stu-id="59391-117">**Output Alias**</span></span>  
 <span data-ttu-id="59391-118">为每个新的输出列键入一个别名。</span><span class="sxs-lookup"><span data-stu-id="59391-118">Type an alias for each new output column.</span></span> <span data-ttu-id="59391-119">默认值为输入列名称后面跟着 **“的副本”**；不过，您也可以任选一个唯一的描述性名称。</span><span class="sxs-lookup"><span data-stu-id="59391-119">The default is **Copy of**, followed by the name of the input column; however, you can choose any unique, descriptive name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59391-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="59391-120">See Also</span></span>  
 [<span data-ttu-id="59391-121">Integration Services 错误和消息引用</span><span class="sxs-lookup"><span data-stu-id="59391-121">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
