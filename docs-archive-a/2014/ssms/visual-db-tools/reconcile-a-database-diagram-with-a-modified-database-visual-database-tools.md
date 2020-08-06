---
title: 将数据库关系图与已修改的数据库进行协调 (Visual Database Tools) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- updating diagram to match database
- reconciling database diagrams
- diagrams [SQL Server], reconciling changes
- updating database to match diagram
- database diagrams [SQL Server], reconciling changes
ms.assetid: eda8dea2-eedd-43a7-85aa-92bd97783b5f
author: stevestein
ms.author: sstein
ms.openlocfilehash: e5e5127ab613a6f791919a98899e40caa2ddac20
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688379"
---
# <a name="reconcile-a-database-diagram-with-a-modified-database-visual-database-tools"></a><span data-ttu-id="dc929-102">协调数据库关系图与已修改的数据库 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="dc929-102">Reconcile a Database Diagram with a Modified Database (Visual Database Tools)</span></span>
  <span data-ttu-id="dc929-103">当您准备好对数据库进行更新以与您的关系图匹配时，即可保存数据库关系图。</span><span class="sxs-lookup"><span data-stu-id="dc929-103">You save your database diagram when you are ready to update the database to match your diagram.</span></span> <span data-ttu-id="dc929-104">但是，如果其他用户在您打开关系图后更新了相应的数据库，他们的更改可能会影响您的关系图，同样如果您在其他用户打开关系图后更新数据库，那么您的更改也会影响他们的关系图。</span><span class="sxs-lookup"><span data-stu-id="dc929-104">However, if other users have updated the database since you opened your diagram, their changes might affect your diagram and vice versa.</span></span>  
  
 <span data-ttu-id="dc929-105">保存关系图将通过改写其他用户的更改来使数据库与您的关系图一致，以便数据库与关系图匹配。</span><span class="sxs-lookup"><span data-stu-id="dc929-105">Saving your diagram will reconcile the database with your diagram by overwriting other users' changes so that the database will match your diagram.</span></span>  
  
### <a name="to-update-a-database-to-match-your-diagram"></a><span data-ttu-id="dc929-106">更新数据库以匹配关系图</span><span class="sxs-lookup"><span data-stu-id="dc929-106">To update a database to match your diagram</span></span>  
  
1.  <span data-ttu-id="dc929-107">保存数据库关系图。</span><span class="sxs-lookup"><span data-stu-id="dc929-107">Save your database diagram.</span></span>  
  
     <span data-ttu-id="dc929-108">如果以前未保存过关系图，请在“保存新的数据库关系图”  对话框中为该关系图键入名称，再选择“确定”  。</span><span class="sxs-lookup"><span data-stu-id="dc929-108">If you have not previously saved your diagram, type a name for the diagram in the **Save New Database Diagram** dialog box and choose **OK**.</span></span>  
  
2.  <span data-ttu-id="dc929-109">“保存”  对话框会列出在保存关系图时将受到影响的表。</span><span class="sxs-lookup"><span data-stu-id="dc929-109">The **Save** dialog box lists the tables that will be affected when you save your diagram.</span></span> <span data-ttu-id="dc929-110">选择“是”  继续执行操作。</span><span class="sxs-lookup"><span data-stu-id="dc929-110">Choose **Yes** to continue.</span></span>  
  
3.  <span data-ttu-id="dc929-111">“检测到数据库更改”  对话框将列出已修改并将进行更改以与关系图匹配的对象。</span><span class="sxs-lookup"><span data-stu-id="dc929-111">The **Database Changes Detected** dialog box lists the objects that were modified and will be changed to match your diagram.</span></span> <span data-ttu-id="dc929-112">选择“是”  以保存该关系图并接受更改列表。</span><span class="sxs-lookup"><span data-stu-id="dc929-112">Choose **Yes** to save the diagram and accept the list of changes.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="dc929-113">如果您的关系图中包含已在数据库中删除的表和列，那么当您保存关系图时，数据库中只会重新创建其定义。</span><span class="sxs-lookup"><span data-stu-id="dc929-113">If your diagram contains tables and columns that were deleted in the database, only their definitions are recreated in the database when you save your diagram.</span></span> <span data-ttu-id="dc929-114">此过程无法还原删除这些对象之前存在于这些对象中的任何数据。</span><span class="sxs-lookup"><span data-stu-id="dc929-114">This process does not restore any data that existed in these objects before their deletion.</span></span>  
  
### <a name="to-update-your-diagram-to-match-a-modified-database"></a><span data-ttu-id="dc929-115">更新关系图以与已修改的数据库匹配</span><span class="sxs-lookup"><span data-stu-id="dc929-115">To update your diagram to match a modified database</span></span>  
  
1.  <span data-ttu-id="dc929-116">关闭关系图而不保存更改。</span><span class="sxs-lookup"><span data-stu-id="dc929-116">Close your diagram without saving changes.</span></span>  
  
2.  <span data-ttu-id="dc929-117">在对象资源管理器中右键单击该关系图。</span><span class="sxs-lookup"><span data-stu-id="dc929-117">Right-click the diagram in Object Explorer.</span></span>  
  
3.  <span data-ttu-id="dc929-118">在快捷菜单中单击“刷新”  。</span><span class="sxs-lookup"><span data-stu-id="dc929-118">From the shortcut menu click **Refresh**.</span></span>  
  
4.  <span data-ttu-id="dc929-119">重新打开该关系图。</span><span class="sxs-lookup"><span data-stu-id="dc929-119">Reopen the diagram.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc929-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dc929-120">See Also</span></span>  
 [<span data-ttu-id="dc929-121">使用数据库关系图 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="dc929-121">Work with Database Diagrams &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
