---
title: 从脚本任务返回结果 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], status information
- ExecutionValue property
- status information [Integration Services]
- TaskResult property
- SSIS Script task, status information
ms.assetid: ac06805b-c2db-44bd-af5c-5a0debe36dd7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bef3e93644377f715b5ad24e0a53df053197a03a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689517"
---
# <a name="returning-results-from-the-script-task"></a><span data-ttu-id="f756a-102">从脚本任务返回结果</span><span class="sxs-lookup"><span data-stu-id="f756a-102">Returning Results from the Script Task</span></span>
  <span data-ttu-id="f756a-103">脚本任务可使用 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> 和可选的 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> 属性将状态信息返回到 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 运行库，这些属性可用于在脚本任务完成后确定工作流的路径。</span><span class="sxs-lookup"><span data-stu-id="f756a-103">The Script task uses the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> and the optional <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> properties to return status information to the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] runtime that can be used to determine the path of the workflow after the Script task has finished.</span></span>  
  
## <a name="taskresult"></a><span data-ttu-id="f756a-104">TaskResult</span><span class="sxs-lookup"><span data-stu-id="f756a-104">TaskResult</span></span>  
 <span data-ttu-id="f756a-105"><xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> 属性可报告任务是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="f756a-105">The <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> property reports whether the task succeeded or failed.</span></span> <span data-ttu-id="f756a-106">例如：</span><span class="sxs-lookup"><span data-stu-id="f756a-106">For example:</span></span>  
  
 `Dts.TaskResult = ScriptResults.Success`  
  
## <a name="executionvalue"></a><span data-ttu-id="f756a-107">ExecutionValue</span><span class="sxs-lookup"><span data-stu-id="f756a-107">ExecutionValue</span></span>  
 <span data-ttu-id="f756a-108"><xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> 属性还可以选择返回一个用户定义的对象，该对象可量化或提供有关脚本任务成功或失败的详细信息。</span><span class="sxs-lookup"><span data-stu-id="f756a-108">The <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> property optionally returns a user-defined object that quantifies or provides more information about the success or failure of the Script task.</span></span> <span data-ttu-id="f756a-109">例如，FTP 任务使用 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> 属性返回所传输的文件数。</span><span class="sxs-lookup"><span data-stu-id="f756a-109">For example, the FTP task uses the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> property to return the number of files transferred.</span></span> <span data-ttu-id="f756a-110">执行 SQL 任务返回受其影响的行数。</span><span class="sxs-lookup"><span data-stu-id="f756a-110">The Execute SQL task returns the number of rows affected by the task.</span></span> <span data-ttu-id="f756a-111"><xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> 还可用于确定工作流的路径。</span><span class="sxs-lookup"><span data-stu-id="f756a-111">The <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> can also be used to determine the path of the workflow.</span></span> <span data-ttu-id="f756a-112">例如：</span><span class="sxs-lookup"><span data-stu-id="f756a-112">For example:</span></span>  
  
 `Dim rowsAffected as Integer`  
  
 `...`  
  
 `rowsAffected = 1000`  
  
 `Dts.ExecutionValue = rowsAffected`  
  
<span data-ttu-id="f756a-113">![Integration Services 图标 (小型) ](../../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="f756a-113">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="f756a-114">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="f756a-114">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="f756a-115">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="f756a-115">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="f756a-116">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="f756a-116">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
