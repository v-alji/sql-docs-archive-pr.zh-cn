---
title: "\"启用-禁用写回\" 对话框 (Analysis Services 多维数据) |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitiondesigner.writebackenabledisable.f1
ms.assetid: 2d254393-3f0d-4b70-8b98-87159f9f3639
author: minewiskan
ms.author: owend
ms.openlocfilehash: 54ee4597ee78f45682730bd0e8d7119d204eaf2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591626"
---
# <a name="enable-disable-writeback-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="b6abf-102">"启用-禁用写回" 对话框 (Analysis Services 多维数据) </span><span class="sxs-lookup"><span data-stu-id="b6abf-102">Enable-Disable Writeback Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="b6abf-103">可以使用“启用/禁用写回”\*\*\*\* 对话框，为多维数据集中的度量值组启用或禁用写回。</span><span class="sxs-lookup"><span data-stu-id="b6abf-103">The **Enable/Disable Writeback** dialog box enables or disables writeback for a measure group in a cube.</span></span> <span data-ttu-id="b6abf-104">对度量值组启用写回将定义一个写回分区，并为该度量值组创建一个写回表。</span><span class="sxs-lookup"><span data-stu-id="b6abf-104">Enabling writeback on a measure group defines a writeback partition and creates a writeback table for that measure group.</span></span> <span data-ttu-id="b6abf-105">对度量值组禁用写回将删除写回分区（但不会删除写回表），以免发生意外数据丢失。</span><span class="sxs-lookup"><span data-stu-id="b6abf-105">Disabling writeback on a measure group removes the writeback partition but does not delete the writeback table, to avoid unanticipated data loss.</span></span> <span data-ttu-id="b6abf-106">通过执行以下操作可以显示“启用/禁用写回”\*\*\*\* 对话框：</span><span class="sxs-lookup"><span data-stu-id="b6abf-106">The **Enable/Disable Writeback** dialog box is displayed by:</span></span>  
  
-   <span data-ttu-id="b6abf-107">在多维数据集设计器中的“分区”\*\*\*\* 选项卡上，单击“度量值组”\*\*\*\* 窗格中的“写回设置”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b6abf-107">Clicking **Writeback Settings** in the **Measure Groups** pane on the **Partitions** tab in Cube Designer.</span></span>  
  
-   <span data-ttu-id="b6abf-108">在多维数据集设计器中的“分区”\*\*\*\* 选项卡上，在“度量值组”\*\*\*\* 窗格的“分区”\*\*\*\* 网格中右键单击某个分区，然后从上下文菜单中选择“写回设置”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b6abf-108">Right-clicking a partition in the **Partitions** grid in the **Measure Groups** pane on the **Partitions** tab in Cube Designer and selecting **Writeback Settings** from the context menu.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b6abf-109">选项</span><span class="sxs-lookup"><span data-stu-id="b6abf-109">Options</span></span>  
 <span data-ttu-id="b6abf-110">**表名称**</span><span class="sxs-lookup"><span data-stu-id="b6abf-110">**Table name**</span></span>  
 <span data-ttu-id="b6abf-111">键入要为所选分区创建的写回表的名称。</span><span class="sxs-lookup"><span data-stu-id="b6abf-111">Type the name of the writeback table to create for the selected partition.</span></span> <span data-ttu-id="b6abf-112">写回表存储对来自客户端应用程序的度量值组所做的更改。</span><span class="sxs-lookup"><span data-stu-id="b6abf-112">The writeback table stores the changes made to the measure group from a client application.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b6abf-113">如果未启用写回，将禁用此选项。</span><span class="sxs-lookup"><span data-stu-id="b6abf-113">This option is disabled if writeback is not enabled.</span></span>  
  
 <span data-ttu-id="b6abf-114">**数据源**</span><span class="sxs-lookup"><span data-stu-id="b6abf-114">**Data source**</span></span>  
 <span data-ttu-id="b6abf-115">选择包含写回表的数据源。</span><span class="sxs-lookup"><span data-stu-id="b6abf-115">Select the data source to contain the writeback table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b6abf-116">如果未启用写回，将禁用此选项。</span><span class="sxs-lookup"><span data-stu-id="b6abf-116">This option is disabled if writeback is not enabled.</span></span>  
  
 <span data-ttu-id="b6abf-117">**新建**</span><span class="sxs-lookup"><span data-stu-id="b6abf-117">**New**</span></span>  
 <span data-ttu-id="b6abf-118">单击显示“连接管理器”\*\*\*\* 对话框，并定义新数据源以包含写回表。</span><span class="sxs-lookup"><span data-stu-id="b6abf-118">Click to display the **Connection Manager** dialog box and define a new data source to contain the writeback table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b6abf-119">如果未启用写回，将禁用此选项。</span><span class="sxs-lookup"><span data-stu-id="b6abf-119">This option is disabled if writeback is not enabled.</span></span>  
  
  
