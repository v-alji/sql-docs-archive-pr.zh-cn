---
title: 更改用于捕获更改的表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- makChanToTab
ms.assetid: a309f82a-c6ef-464d-a6ef-df555bfb609a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 258eb8e761ac697bebd630cc0e627941b4ffc7d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579707"
---
# <a name="make-changes-to-the-tables-selected-for-capturing-changes"></a><span data-ttu-id="0607e-102">对为捕获更改选择的表进行更改</span><span class="sxs-lookup"><span data-stu-id="0607e-102">Make Changes to the Tables Selected for Capturing Changes</span></span>
  <span data-ttu-id="0607e-103">在此对话框中，您可以从要捕获变更的所选表中选择特定列。</span><span class="sxs-lookup"><span data-stu-id="0607e-103">In this dialog box, you can select specific columns from the selected table to capture changes from.</span></span> <span data-ttu-id="0607e-104">您还可以编辑 **“安全角色”** 和 **“捕获实例”** 信息。</span><span class="sxs-lookup"><span data-stu-id="0607e-104">You can also edit the **Security Role** and **Capture Instance** information.</span></span>  
  
 <span data-ttu-id="0607e-105">您可以在此对话框中对为捕获变更而选择的表进行以下更改。</span><span class="sxs-lookup"><span data-stu-id="0607e-105">You can make the following changes to the tables you selected for capturing changes in this dialog box.</span></span>  
  
 <span data-ttu-id="0607e-106">**对在 CDC 实例中包含的列进行更改：**</span><span class="sxs-lookup"><span data-stu-id="0607e-106">**Make changes to which columns are included in the CDC instance:**</span></span>  
  
 <span data-ttu-id="0607e-107">执行下列一种或两种操作：</span><span class="sxs-lookup"><span data-stu-id="0607e-107">Do one or both of the following:</span></span>  
  
-   <span data-ttu-id="0607e-108">选中要包括的任何其他列旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="0607e-108">Select the check box next to any additional column you want to include.</span></span>  
  
-   <span data-ttu-id="0607e-109">取消选中不想再包括的任何列旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="0607e-109">Clear the check box next to any column that you no longer want to include.</span></span>  
  
 <span data-ttu-id="0607e-110">**更改特定列的数据类型**：</span><span class="sxs-lookup"><span data-stu-id="0607e-110">**Change the data type for a specific column**:</span></span>  
  
 <span data-ttu-id="0607e-111">您可以为特定列选择不同的数据类型。</span><span class="sxs-lookup"><span data-stu-id="0607e-111">You can select a different data type for a specific column.</span></span> <span data-ttu-id="0607e-112">您只能将数据类型更改为与原始数据类型兼容的数据类型。</span><span class="sxs-lookup"><span data-stu-id="0607e-112">You can only change the data type to a data type that is compatible with the original data type.</span></span>  
  
 <span data-ttu-id="0607e-113">若要更改数据类型，请在 **“数据类型”** 列中单击，然后选择不同的数据类型。</span><span class="sxs-lookup"><span data-stu-id="0607e-113">To change the data type, click in the **Data Type** column and select a different data type.</span></span> <span data-ttu-id="0607e-114">只有与原始数据类型兼容的数据类型可用。</span><span class="sxs-lookup"><span data-stu-id="0607e-114">Only data types that are compatible with the original data type are available.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0607e-115">如果没有其他数据类型可供选择，则下拉列表将不可用。</span><span class="sxs-lookup"><span data-stu-id="0607e-115">If no additional data types can be selected, the drop-down list is not available.</span></span>  
  
 <span data-ttu-id="0607e-116">**更改安全角色**</span><span class="sxs-lookup"><span data-stu-id="0607e-116">**Change the Security Role**</span></span>  
  
 <span data-ttu-id="0607e-117">键入一个新名称或在 **“安全角色”** 字段中编辑安全访问控制角色的名称。</span><span class="sxs-lookup"><span data-stu-id="0607e-117">Type a new name or edit the name of the security gating role in the **Security Role** field.</span></span>  
  
 <span data-ttu-id="0607e-118">**更改或添加捕获实例**</span><span class="sxs-lookup"><span data-stu-id="0607e-118">**Change or add a capture instance**</span></span>  
  
 <span data-ttu-id="0607e-119">在 **“捕获实例”** 字段中，输入捕获实例的名称。</span><span class="sxs-lookup"><span data-stu-id="0607e-119">In the **Capture Instance** field enter a name for the capture instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0607e-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0607e-120">See Also</span></span>  
 <span data-ttu-id="0607e-121">[如何创建 SQL Server 更改数据库实例](how-to-create-the-sql-server-change-database-instance.md) </span><span class="sxs-lookup"><span data-stu-id="0607e-121">[How to Create the SQL Server Change Database Instance](how-to-create-the-sql-server-change-database-instance.md) </span></span>  
 [<span data-ttu-id="0607e-122">选择 Oracle 表和列</span><span class="sxs-lookup"><span data-stu-id="0607e-122">Select Oracle Tables and Columns</span></span>](select-oracle-tables-and-columns.md)  
  
  
