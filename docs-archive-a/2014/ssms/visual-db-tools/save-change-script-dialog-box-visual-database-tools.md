---
title: “保存更改脚本”对话框 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.generatechangescript
- vdtsql.chm:65544
ms.assetid: fc9d1639-5efa-44fe-a04f-4d4d0def2833
author: stevestein
ms.author: sstein
ms.openlocfilehash: 19a2bb2ce9a219c195421e2efa203fc115e1ae1b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682572"
---
# <a name="save-change-script-dialog-box-visual-database-tools"></a><span data-ttu-id="81cf4-102">“保存更改脚本”对话框 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="81cf4-102">Save Change Script Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="81cf4-103">此对话框可显示您在上次保存表以后所做更改的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本。</span><span class="sxs-lookup"><span data-stu-id="81cf4-103">This dialog box shows the [!INCLUDE[tsql](../../includes/tsql-md.md)] script for the changes you have made since you last saved the table.</span></span> <span data-ttu-id="81cf4-104">使用该对话框还可以将脚本保存到位于所选位置的文本文件中。</span><span class="sxs-lookup"><span data-stu-id="81cf4-104">It also allows you to save the script to a text file at a location you choose.</span></span>  
  
 <span data-ttu-id="81cf4-105">当您在表设计器中对表进行的更改尚未保存时，则可访问此对话框。</span><span class="sxs-lookup"><span data-stu-id="81cf4-105">You can access this dialog box after you have made unsaved changes to a table in Table Designer.</span></span> <span data-ttu-id="81cf4-106">在“表设计器”  菜单上，单击“生成更改脚本”  。</span><span class="sxs-lookup"><span data-stu-id="81cf4-106">On the **Table Designer** menu, click **Generate Change Script**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="81cf4-107">Visual Database Tools 提供的更改脚本没有包含错误处理功能。</span><span class="sxs-lookup"><span data-stu-id="81cf4-107">Change scripts provided by Visual Database Tools contain no error handling.</span></span> <span data-ttu-id="81cf4-108">这些脚本假设在工具打开后数据库对象没有发生更改，因此不会发生与更改相关的问题。</span><span class="sxs-lookup"><span data-stu-id="81cf4-108">They assume that database objects have not changed since the tool was opened, and that change-related problems will therefore not occur.</span></span> <span data-ttu-id="81cf4-109">运行更改脚本之前，您应在脚本中包括适当的错误处理语句。</span><span class="sxs-lookup"><span data-stu-id="81cf4-109">Before running a change script, you should include the appropriate error-handling statements.</span></span>  
  
## <a name="options"></a><span data-ttu-id="81cf4-110">选项</span><span class="sxs-lookup"><span data-stu-id="81cf4-110">Options</span></span>  
 <span data-ttu-id="81cf4-111">**每次保存时自动生成更改脚本**</span><span class="sxs-lookup"><span data-stu-id="81cf4-111">**Automatically generate change script on every save**</span></span>  
 <span data-ttu-id="81cf4-112">如果选择此选项，则在每次保存对表的更改时都会显示“保存更改脚本”  对话框。</span><span class="sxs-lookup"><span data-stu-id="81cf4-112">If checked, the **Save Change Script** dialog box will appear any time you save changes to a table.</span></span>  
  
 <span data-ttu-id="81cf4-113">**是**</span><span class="sxs-lookup"><span data-stu-id="81cf4-113">**Yes**</span></span>  
 <span data-ttu-id="81cf4-114">打开“保存”  对话框，在其中可选择保存文本文件的位置。</span><span class="sxs-lookup"><span data-stu-id="81cf4-114">Bring up the **Save** dialog box where you can choose the location for the text file.</span></span>  
  
 <span data-ttu-id="81cf4-115">**是**</span><span class="sxs-lookup"><span data-stu-id="81cf4-115">**No**</span></span>  
 <span data-ttu-id="81cf4-116">取消创建更改脚本。</span><span class="sxs-lookup"><span data-stu-id="81cf4-116">Cancel the creation of the change script.</span></span>  
  
  
