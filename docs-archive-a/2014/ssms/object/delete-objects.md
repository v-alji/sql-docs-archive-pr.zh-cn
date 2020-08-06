---
title: 删除对象 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.deleteobjects.f1
helpviewer_keywords:
- Delete Objects dialog box
ms.assetid: 49541441-179c-40d3-ba0c-01bcae545984
author: stevestein
ms.author: sstein
ms.openlocfilehash: e7b20d1eee3e48c5531b6b788e125b943f7606d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576512"
---
# <a name="delete-objects"></a><span data-ttu-id="9efc0-102">删除对象</span><span class="sxs-lookup"><span data-stu-id="9efc0-102">Delete Objects</span></span>
  <span data-ttu-id="9efc0-103">使用此对话框可以删除数据库或数据库对象。</span><span class="sxs-lookup"><span data-stu-id="9efc0-103">Use this dialog box to delete a database or database object.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="9efc0-104">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="9efc0-104">UI element list</span></span>  
 <span data-ttu-id="9efc0-105">**要删除的对象**</span><span class="sxs-lookup"><span data-stu-id="9efc0-105">**Object to be deleted**</span></span>  
 <span data-ttu-id="9efc0-106">显示要删除的对象的名称、类型、所有者和状态，以及在执行过程中的所有错误消息。</span><span class="sxs-lookup"><span data-stu-id="9efc0-106">Displays the names, types, owners, and status of the objects that are about to be deleted, as well as any messages about errors during execution.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9efc0-107">对数据库运行“删除”  与在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中发出 DROP DATABASE 等效。</span><span class="sxs-lookup"><span data-stu-id="9efc0-107">Running **Delete** on a database is equivalent to issuing DROP DATABASE in [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="9efc0-108">**显示依赖关系**</span><span class="sxs-lookup"><span data-stu-id="9efc0-108">**Show Dependencies**</span></span>  
 <span data-ttu-id="9efc0-109">单击此项可显示依赖于当前所选对象的对象，以及当前对象所依赖的对象（向上和向下依赖关系）。</span><span class="sxs-lookup"><span data-stu-id="9efc0-109">Click to display both the objects that are dependent on the currently selected object and objects that the current object is dependent on (upward and downward dependency).</span></span> <span data-ttu-id="9efc0-110">“显示依赖关系”  对话框中显示的信息是只读的。</span><span class="sxs-lookup"><span data-stu-id="9efc0-110">The information displayed in the **Show Dependencies** dialog box is read-only.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9efc0-111">并不是所有类型的数据库对象都会出现“显示依赖关系”  按钮。</span><span class="sxs-lookup"><span data-stu-id="9efc0-111">The **Show Dependencies** button does not appear for all types of database objects.</span></span> <span data-ttu-id="9efc0-112">若要在“显示依赖关系”  按钮不可用时查看依赖关系，请在对象资源管理器中右键单击该对象，再单击“查看依赖关系”  。</span><span class="sxs-lookup"><span data-stu-id="9efc0-112">To view dependencies when the **Show Dependencies** button is not available, right-click the object in Object Explorer, and then click **View Dependencies**.</span></span>  
  
 <span data-ttu-id="9efc0-113">**删除数据库备份和还原历史记录信息**</span><span class="sxs-lookup"><span data-stu-id="9efc0-113">**Delete backup and restore history information for databases**</span></span>  
 <span data-ttu-id="9efc0-114">只在删除数据库时出现，此复选框会导致从 **msdb** 数据库中删除主题数据库的备份和还原历史记录。</span><span class="sxs-lookup"><span data-stu-id="9efc0-114">Only appears when a database is deleted, this check box causes the backup and restore history for the subject database to be deleted from the **msdb** database.</span></span>  
  
 <span data-ttu-id="9efc0-115">**关闭现有连接**</span><span class="sxs-lookup"><span data-stu-id="9efc0-115">**Close existing connections**</span></span>  
 <span data-ttu-id="9efc0-116">只在删除数据库时出现，此复选框可以终止与主题数据库的连接。</span><span class="sxs-lookup"><span data-stu-id="9efc0-116">Only appears when a database is deleted, this check box terminates connections to the subject database.</span></span>  
  
  
