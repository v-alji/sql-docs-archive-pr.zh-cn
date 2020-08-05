---
title: 编辑表属性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- editTabProps
ms.assetid: 95ea72ba-8e40-4177-a963-0fb4d10c56e3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1ba0809b99474704ec0e93e417a04d776bb26d9a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579712"
---
# <a name="edit-the-table-properties"></a><span data-ttu-id="eef71-102">编辑表属性</span><span class="sxs-lookup"><span data-stu-id="eef71-102">Edit the Table Properties</span></span>
  <span data-ttu-id="eef71-103">使用此对话框可编辑所选表中要捕获更改的特定列。</span><span class="sxs-lookup"><span data-stu-id="eef71-103">Use this dialog box to edit the specific columns from the selected table where changes are being captured.</span></span> <span data-ttu-id="eef71-104">您还可以编辑 **“安全角色”** 和 **“捕获实例”** 信息。</span><span class="sxs-lookup"><span data-stu-id="eef71-104">You can also edit the **Security Role** and **Capture Instance** information.</span></span>  
  
### <a name="to-edit-the-columns-to-include-in-the-cdc-instance"></a><span data-ttu-id="eef71-105">编辑要在 CDC 实例中包含的列</span><span class="sxs-lookup"><span data-stu-id="eef71-105">To edit the columns to include in the CDC instance</span></span>  
  
1.  <span data-ttu-id="eef71-106">执行下列一种或两种操作：</span><span class="sxs-lookup"><span data-stu-id="eef71-106">Do one or both of the following:</span></span>  
  
    -   <span data-ttu-id="eef71-107">选中要包括的任何其他列旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="eef71-107">Select the check box next to any additional column you want to include.</span></span>  
  
    -   <span data-ttu-id="eef71-108">取消选中不想再包括的任何列旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="eef71-108">Clear the check box next to any column that you no longer want to include.</span></span>  
  
### <a name="to-edit-the-security-role"></a><span data-ttu-id="eef71-109">编辑安全角色</span><span class="sxs-lookup"><span data-stu-id="eef71-109">To edit the Security Role</span></span>  
  
1.  <span data-ttu-id="eef71-110">键入一个新名称或在 **“安全角色”** 字段中编辑安全角色的名称。</span><span class="sxs-lookup"><span data-stu-id="eef71-110">Type a new name or edit the name of the security role in the **Security Role** field.</span></span>  
  
### <a name="to-create-a-new-capture-instance"></a><span data-ttu-id="eef71-111">创建新的捕获实例</span><span class="sxs-lookup"><span data-stu-id="eef71-111">To create a new capture instance</span></span>  
  
1.  <span data-ttu-id="eef71-112">在 **“安全角色”** 部分的 **“名称”** 字段中，输入捕获实例的名称。</span><span class="sxs-lookup"><span data-stu-id="eef71-112">In the **Security Role** section, **Name** field enter a name for the capture instance.</span></span> <span data-ttu-id="eef71-113">默认情况下，在该字段中输入的名称是当前捕获实例的名称加上在该名称末尾添加的 **_NEW** （例如 **old_instance_NEW**）。</span><span class="sxs-lookup"><span data-stu-id="eef71-113">By default, the name entered in the field is the name of the current capture instance with **_NEW** added to the end of the name (for example, **old_instance_NEW**).</span></span>  
  
2.  <span data-ttu-id="eef71-114">将捕获实例保存为以下项之一：</span><span class="sxs-lookup"><span data-stu-id="eef71-114">Save the capture instance as one of the following:</span></span>  
  
    -   <span data-ttu-id="eef71-115">**新建捕获实例**：在此情况下，将保存新的捕获实例并且不删除旧的捕获实例。</span><span class="sxs-lookup"><span data-stu-id="eef71-115">**New Capture Instance**: In this case a new capture instance is saved and the old capture instance is not deleted.</span></span>  
  
         <span data-ttu-id="eef71-116">**注意**：每个表不能具有超过两个捕获实例。</span><span class="sxs-lookup"><span data-stu-id="eef71-116">**Note**: You can have no more than two capture instances per table.</span></span> <span data-ttu-id="eef71-117">如果已有两个捕获实例，则此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="eef71-117">If there are already two capture instances, this option is not available.</span></span>  
  
    -   <span data-ttu-id="eef71-118">**替换现有的**：在此情况下，将删除当前捕获实例并且用您创建的捕获实例替换。</span><span class="sxs-lookup"><span data-stu-id="eef71-118">**Replace Existing**: In this case the current capture instance is deleted and replaced by the capture instance you created.</span></span> <span data-ttu-id="eef71-119">如果为此表定义了两个捕获实例，则您必须选择要替换的一个实例。</span><span class="sxs-lookup"><span data-stu-id="eef71-119">If there are two capture instances defined for this table, you must select one to replace.</span></span>  
  
 <span data-ttu-id="eef71-120">**注意**：您可以从 **“表”** 选项卡的表列表中删除某一捕获实例。</span><span class="sxs-lookup"><span data-stu-id="eef71-120">**Note**: You can remove a capture instance from the list of tables in the **Table** tab.</span></span>  
  
 <span data-ttu-id="eef71-121">在此对话框中输入完信息后，单击 **“确定”** 以接受更改。</span><span class="sxs-lookup"><span data-stu-id="eef71-121">After you finish entering the information in this dialog box, click **OK** to accept the changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eef71-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="eef71-122">See Also</span></span>  
 <span data-ttu-id="eef71-123">[如何编辑 CDC 实例属性](how-to-edit-the-cdc-instance-properties.md) </span><span class="sxs-lookup"><span data-stu-id="eef71-123">[How to Edit the CDC Instance Properties](how-to-edit-the-cdc-instance-properties.md) </span></span>  
 [<span data-ttu-id="eef71-124">对为捕获更改选择的表进行更改</span><span class="sxs-lookup"><span data-stu-id="eef71-124">Make Changes to the Tables Selected for Capturing Changes</span></span>](make-changes-to-the-tables-selected-for-capturing-changes.md)  
  
  
