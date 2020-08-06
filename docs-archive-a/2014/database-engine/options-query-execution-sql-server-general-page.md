---
title: 选项 (查询执行-SQL Server-"常规" 页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.QueryExecution.SqlServer.SqlExecutionGeneral
ms.assetid: 3f8d59bc-3f97-4e5d-8b86-5ac670d20780
author: rothja
ms.author: jroth
ms.openlocfilehash: eaa95293636d02674fb720dcd1b8146279f78e72
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590341"
---
# <a name="options-query-execution-sql-server-general-page"></a><span data-ttu-id="05c11-102">选项 (查询执行-SQL Server-"常规" 页) </span><span class="sxs-lookup"><span data-stu-id="05c11-102">Options (Query Execution-SQL Server-General Page)</span></span>
  <span data-ttu-id="05c11-103">使用此页可指定用于运行 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 查询的选项。</span><span class="sxs-lookup"><span data-stu-id="05c11-103">Use this page to specify the options for running [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] queries.</span></span> <span data-ttu-id="05c11-104">对这些选项所做的更改仅应用于新的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 查询。</span><span class="sxs-lookup"><span data-stu-id="05c11-104">Changes to these options are only applied to new [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] queries.</span></span> <span data-ttu-id="05c11-105">若要更改当前查询的选项，请在“查询”\*\*\*\* 菜单上单击“查询选项”\*\*\*\*，或在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 查询窗口中单击右键，再选择“查询选项”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="05c11-105">To change the options for a current query, click **Query Options** on the **Query** menu, or in a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Query window right-click and select **Query Options**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="05c11-106">选项</span><span class="sxs-lookup"><span data-stu-id="05c11-106">Options</span></span>  
 <span data-ttu-id="05c11-107">**SET ROWCOUNT**</span><span class="sxs-lookup"><span data-stu-id="05c11-107">**SET ROWCOUNT**</span></span>  
 <span data-ttu-id="05c11-108">默认值为 0，指示 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 在收到所有结果之前将一直等待结果。</span><span class="sxs-lookup"><span data-stu-id="05c11-108">The default value of 0 indicates that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] will wait for results until all results are received.</span></span> <span data-ttu-id="05c11-109">如果希望 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 在获取指定数目的行后暂停查询，请提供一个大于 0 的值。</span><span class="sxs-lookup"><span data-stu-id="05c11-109">Provide a value greater than 0 if you want [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to halt the query after obtaining the specified number of rows.</span></span> <span data-ttu-id="05c11-110">若要关闭此选项（以便返回所有的行），请将 SET ROWCOUNT 指定为 0。</span><span class="sxs-lookup"><span data-stu-id="05c11-110">To turn this option off (so that all rows are returned), specify SET ROWCOUNT 0.</span></span>  
  
 <span data-ttu-id="05c11-111">**SET TEXTSIZE**</span><span class="sxs-lookup"><span data-stu-id="05c11-111">**SET TEXTSIZE**</span></span>  
 <span data-ttu-id="05c11-112">默认值为 2,147,483,647 字节，表示 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 将提供长达 `text` 和 `ntext` 数据字段上限的完整数据字段。</span><span class="sxs-lookup"><span data-stu-id="05c11-112">The default value of 2,147,483,647 bytes indicates that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] will provide complete data fields up to the limit of `text` and `ntext` data fields.</span></span> <span data-ttu-id="05c11-113">提供较小的数值，可以在存在大量值时限制结果数量。</span><span class="sxs-lookup"><span data-stu-id="05c11-113">Provide a smaller number to limit results in the case of large values.</span></span> <span data-ttu-id="05c11-114">超出指定数量的列将被截断。</span><span class="sxs-lookup"><span data-stu-id="05c11-114">Columns greater than the number provided will be truncated.</span></span>  
  
 <span data-ttu-id="05c11-115">**执行超时值**</span><span class="sxs-lookup"><span data-stu-id="05c11-115">**Execution time-out**</span></span>  
 <span data-ttu-id="05c11-116">在 **“新建连接”** 对话框中设置默认值。</span><span class="sxs-lookup"><span data-stu-id="05c11-116">Sets the default value in the **New Connection** dialog box.</span></span> <span data-ttu-id="05c11-117">使用此数字调整框可以设置 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 在取消查询之前等待的时间（秒）。</span><span class="sxs-lookup"><span data-stu-id="05c11-117">Use this spin box to tell [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] the number of seconds to wait before canceling the query.</span></span> <span data-ttu-id="05c11-118">值0表示无限期等待或无超时。对于新安装，此值为0。</span><span class="sxs-lookup"><span data-stu-id="05c11-118">A value of 0 indicates an infinite wait, or no time-out. This value is 0 on a new installation.</span></span>  
  
 <span data-ttu-id="05c11-119">**批分隔符**</span><span class="sxs-lookup"><span data-stu-id="05c11-119">**Batch separator**</span></span>  
 <span data-ttu-id="05c11-120">键入用来将 [!INCLUDE[tsql](../includes/tsql-md.md)] 语句分隔为批的词。</span><span class="sxs-lookup"><span data-stu-id="05c11-120">Type a word that you use to separate [!INCLUDE[tsql](../includes/tsql-md.md)] statements into batches.</span></span> <span data-ttu-id="05c11-121">默认值为 GO。</span><span class="sxs-lookup"><span data-stu-id="05c11-121">The default is GO.</span></span>  
  
 <span data-ttu-id="05c11-122">**默认情况下，在 SQLCMD 模式下打开新查询**</span><span class="sxs-lookup"><span data-stu-id="05c11-122">**By default, open new queries in SQLCMD Mode**</span></span>  
 <span data-ttu-id="05c11-123">选中此复选框可在 SQLCMD 模式下打开新查询。</span><span class="sxs-lookup"><span data-stu-id="05c11-123">Select this check box to open new queries in SQLCMD mode.</span></span> <span data-ttu-id="05c11-124">有关 SQLCMD 模式的详细信息，请参阅[使用查询编辑器编辑 SQLCMD 脚本](../relational-databases/scripting/edit-sqlcmd-scripts-with-query-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="05c11-124">For more information about SQLCMD mode, see [Edit SQLCMD Scripts with Query Editor](../relational-databases/scripting/edit-sqlcmd-scripts-with-query-editor.md).</span></span>  
  
 <span data-ttu-id="05c11-125">选择此选项时，请记住下列限制：</span><span class="sxs-lookup"><span data-stu-id="05c11-125">When you select this option, be aware of the following limitations:</span></span>  
  
-   <span data-ttu-id="05c11-126">[!INCLUDE[ssDE](../includes/ssde-md.md)] 查询编辑器中的 IntelliSense 处于关闭状态。</span><span class="sxs-lookup"><span data-stu-id="05c11-126">IntelliSense in the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor is turned off.</span></span>  
  
-   <span data-ttu-id="05c11-127">由于查询编辑器不能从命令行运行，因此您不能传入命令行参数（如变量）。</span><span class="sxs-lookup"><span data-stu-id="05c11-127">Because Query Editor does not run from the command line, you cannot pass in command-line parameters such as variables.</span></span>  
  
-   <span data-ttu-id="05c11-128">由于查询编辑器无法响应操作系统提示，因此您一定要记住不要运行交互式语句。</span><span class="sxs-lookup"><span data-stu-id="05c11-128">Because Query Editor cannot respond to operating-system prompts, you must be careful not to run interactive statements.</span></span>  
  
 <span data-ttu-id="05c11-129">**重置为默认值**</span><span class="sxs-lookup"><span data-stu-id="05c11-129">**Reset to Default**</span></span>  
 <span data-ttu-id="05c11-130">单击此项可将此页上的所有值重置为原始默认值。</span><span class="sxs-lookup"><span data-stu-id="05c11-130">Click to reset all values on this page to the original default values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05c11-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="05c11-131">See Also</span></span>  
 [<span data-ttu-id="05c11-132">sqlcmd 实用工具</span><span class="sxs-lookup"><span data-stu-id="05c11-132">sqlcmd Utility</span></span>](../tools/sqlcmd-utility.md)  
  
  
