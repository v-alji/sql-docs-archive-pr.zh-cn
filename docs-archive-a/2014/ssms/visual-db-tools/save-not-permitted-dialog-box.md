---
title: “保存(不允许)”对话框 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.table.tablerecreatenosave.f1
ms.assetid: 7efda8e3-739f-4c97-a497-b8808a0acbea
author: stevestein
ms.author: sstein
ms.openlocfilehash: 19e5f848f20cf74feb3e802e931cbde3aa8d3dc9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691005"
---
# <a name="save-not-permitted-dialog-box"></a><span data-ttu-id="14ce7-102">“保存”（不允许）对话框</span><span class="sxs-lookup"><span data-stu-id="14ce7-102">Save (Not Permitted) Dialog Box</span></span>
  <span data-ttu-id="14ce7-103">“保存”  （不允许）对话框警告不允许保存更改，因为所做的更改要求删除并重新创建列出的表。</span><span class="sxs-lookup"><span data-stu-id="14ce7-103">The **Save** (Not Permitted) dialog box warns you that saving changes is not permitted because the changes you have made require the listed tables to be dropped and re-created.</span></span>  
  
 <span data-ttu-id="14ce7-104">以下操作可能要求重新创建表：</span><span class="sxs-lookup"><span data-stu-id="14ce7-104">The following actions might require a table to be re-created:</span></span>  
  
-   <span data-ttu-id="14ce7-105">在表中间添加一个新列</span><span class="sxs-lookup"><span data-stu-id="14ce7-105">Adding a new column to the middle of the table</span></span>  
  
-   <span data-ttu-id="14ce7-106">删除列</span><span class="sxs-lookup"><span data-stu-id="14ce7-106">Dropping a column</span></span>  
  
-   <span data-ttu-id="14ce7-107">更改列为 Null 性</span><span class="sxs-lookup"><span data-stu-id="14ce7-107">Changing column nullability</span></span>  
  
-   <span data-ttu-id="14ce7-108">更改列的顺序</span><span class="sxs-lookup"><span data-stu-id="14ce7-108">Changing the order of the columns</span></span>  
  
-   <span data-ttu-id="14ce7-109">更改列的数据类型</span><span class="sxs-lookup"><span data-stu-id="14ce7-109">Changing the data type of a column</span></span>  
  
 <span data-ttu-id="14ce7-110">若要更改此选项，请在“工具”  菜单中单击“选项”  ，展开“设计器”  ，然后单击“表设计器和数据库设计器”  。</span><span class="sxs-lookup"><span data-stu-id="14ce7-110">To change this option, on the **Tools** menu, click **Options**, expand **Designers**, and then click **Table and Database Designers**.</span></span> <span data-ttu-id="14ce7-111">选中或清除“阻止保存要求重新创建表的更改”  复选框。</span><span class="sxs-lookup"><span data-stu-id="14ce7-111">Select or clear the **Prevent saving changes that require the table to be re-created** check box.</span></span>  
  
  
