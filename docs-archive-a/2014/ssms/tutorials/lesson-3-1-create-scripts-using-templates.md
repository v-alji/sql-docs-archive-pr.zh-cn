---
title: 使用模板创建脚本| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: ed48014c-3fc9-48ff-8c0f-8d1822195f14
author: stevestein
ms.author: sstein
ms.openlocfilehash: b404ecc505e93c302e4c737f9c0b0161d9015519
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690278"
---
# <a name="create-scripts-using-templates"></a><span data-ttu-id="f7575-102">使用模板创建脚本</span><span class="sxs-lookup"><span data-stu-id="f7575-102">Create Scripts Using Templates</span></span>
  <span data-ttu-id="f7575-103">Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 提供了大量脚本模板，其中包含了许多常用任务的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="f7575-103">Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] provides a large number of script templates containing the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements for many common tasks.</span></span> <span data-ttu-id="f7575-104">这些模板包含用户提供的值（如表名称）的参数。</span><span class="sxs-lookup"><span data-stu-id="f7575-104">These templates contain parameters for the user-provided values such as a table name.</span></span> <span data-ttu-id="f7575-105">使用该参数，可以只键入一次名称，然后自动将该名称复制到脚本中所有必要的位置。</span><span class="sxs-lookup"><span data-stu-id="f7575-105">Using the parameters, you can type the name once and then automatically copy the name to all the necessary locations within the script.</span></span> <span data-ttu-id="f7575-106">可以编写自己的自定义模板，以支持频繁编写的脚本。</span><span class="sxs-lookup"><span data-stu-id="f7575-106">You can write your own custom templates to support the scripts that you write most often.</span></span> <span data-ttu-id="f7575-107">也可以重新组织模板树，移动模板或创建新文件夹以保存模板。</span><span class="sxs-lookup"><span data-stu-id="f7575-107">You can also reorganize the template tree, moving templates or creating new folders to hold the templates.</span></span> <span data-ttu-id="f7575-108">在以下练习中，将使用模板创建一个数据库，并指定排序规则模板。</span><span class="sxs-lookup"><span data-stu-id="f7575-108">In the following practice, you will use a template to create a database, specifying collation template.</span></span>  
  
## <a name="using-templates"></a><span data-ttu-id="f7575-109">使用模板</span><span class="sxs-lookup"><span data-stu-id="f7575-109">Using Templates</span></span>  
  
#### <a name="to-create-a-script-using-a-template"></a><span data-ttu-id="f7575-110">若要使用模板创建脚本，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="f7575-110">To create a script using a template</span></span>  
  
1.  <span data-ttu-id="f7575-111">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]的“视图”  菜单上，单击“模板资源管理器” 。</span><span class="sxs-lookup"><span data-stu-id="f7575-111">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], on the **View** menu, click **Template Explorer**.</span></span>  
  
2.  <span data-ttu-id="f7575-112">模板资源管理器中的模板是分组列出的。</span><span class="sxs-lookup"><span data-stu-id="f7575-112">The templates in Template Explorer are organized into groups.</span></span> <span data-ttu-id="f7575-113">展开“数据库”\*\*\*\*，再双击“创建数据库”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f7575-113">Expand **Database**, and then double-click **Create Database**.</span></span>  
  
3.  <span data-ttu-id="f7575-114">在“连接到数据库引擎”\*\*\*\* 对话框中，填写连接信息，然后单击“连接”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f7575-114">In the **Connect to Database Engine** dialog box, complete the connection information and then click **Connect**.</span></span> <span data-ttu-id="f7575-115">此时将打开一个新查询编辑器窗口，其中包含“创建数据库”\*\*\*\* 模板的内容。</span><span class="sxs-lookup"><span data-stu-id="f7575-115">A new Query Editor window opens, containing the contents of the **Create Database** template.</span></span>  
  
4.  <span data-ttu-id="f7575-116">在 **“查询”** 菜单上，单击 **“指定模板参数的值”** 。</span><span class="sxs-lookup"><span data-stu-id="f7575-116">On the **Query** menu, click **Specify Values for Template Parameters**.</span></span>  
  
5.  <span data-ttu-id="f7575-117">在“指定模板参数的值”\*\*\*\* 对话框中，“值”\*\*\*\* 列包含一个 **Database_Name** 参数的建议值。</span><span class="sxs-lookup"><span data-stu-id="f7575-117">In the **Specify Values for Template Parameters** dialog box, the **Value** column contains a suggested value for the **Database_Name** parameter.</span></span> <span data-ttu-id="f7575-118">在“数据库名称”\*\*\*\* 参数框中，键入 **Marketing**，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f7575-118">In the **Database Name** parameter box, type **Marketing**, and then click **OK**.</span></span> <span data-ttu-id="f7575-119">请注意“Marketing”插入脚本中的几个位置。</span><span class="sxs-lookup"><span data-stu-id="f7575-119">Note how "Marketing" is inserted into the script in several locations.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="f7575-120">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="f7575-120">Next Task in Lesson</span></span>  
 [<span data-ttu-id="f7575-121">创建自定义模板</span><span class="sxs-lookup"><span data-stu-id="f7575-121">Create Custom Templates</span></span>](lesson-3-2-create-custom-templates.md)  
  
  
