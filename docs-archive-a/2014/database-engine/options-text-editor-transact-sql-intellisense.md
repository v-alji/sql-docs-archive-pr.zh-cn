---
title: 选项 (文本编辑器-Transact-sql-IntelliSense) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.SQL.Advanced
- VS.ToolsOptionsPages.Text_Editor.SQL_Server_Tools.Advanced
dev_langs:
- TSQL
ms.assetid: 1855d916-5bf9-4d94-b0fb-9f9bb05ff950
author: rothja
ms.author: jroth
ms.openlocfilehash: 2d8f9c865516dc5e4c0ddadbdc908a9b4c8ec366
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588691"
---
# <a name="options-text-editor-transact-sql-intellisense"></a><span data-ttu-id="f693a-102">选项 (文本编辑器-Transact-sql-IntelliSense) </span><span class="sxs-lookup"><span data-stu-id="f693a-102">Options (Text Editor-Transact-SQL-IntelliSense)</span></span>
  <span data-ttu-id="f693a-103">您可以使用 **“选项”** 对话框更改 [!INCLUDE[ssDE](../includes/ssde-md.md)] 查询编辑器的 IntelliSense 设置。</span><span class="sxs-lookup"><span data-stu-id="f693a-103">The **Options** dialog box lets you change the IntelliSense settings for the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor.</span></span> <span data-ttu-id="f693a-104">若要显示这些设置，请在“工具”\*\*\*\* 菜单上单击“选项”\*\*\*\*，依次展开“文本编辑器”\*\*\*\* 文件夹和“Transact-SQL”\*\*\*\* 文件夹，然后单击“高级”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f693a-104">These settings are available when, on the **Tools** menu, you click **Options**, expand the **Text Editor** folder, expand the **Transact-SQL** folder, and then click **Advanced**.</span></span>  
  
## <a name="transact-sql-intellisense-settings"></a><span data-ttu-id="f693a-105">Transact-SQL IntelliSense 设置</span><span class="sxs-lookup"><span data-stu-id="f693a-105">Transact-SQL IntelliSense Settings</span></span>  
 <span data-ttu-id="f693a-106">指定 [!INCLUDE[ssDE](../includes/ssde-md.md)] 查询编辑器的 IntelliSense 选项。</span><span class="sxs-lookup"><span data-stu-id="f693a-106">Specifies the IntelliSense options for the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor.</span></span>  
  
### <a name="enable-intellisense"></a><span data-ttu-id="f693a-107">启用 IntelliSense</span><span class="sxs-lookup"><span data-stu-id="f693a-107">Enable IntelliSense</span></span>  
 <span data-ttu-id="f693a-108">启用 IntelliSense 功能。</span><span class="sxs-lookup"><span data-stu-id="f693a-108">Enables the IntelliSense features.</span></span> <span data-ttu-id="f693a-109">如果未选中此复选框，具体的 IntelliSense 选项不可用。</span><span class="sxs-lookup"><span data-stu-id="f693a-109">When this box is not selected, the specific IntelliSense options are unavailable.</span></span> <span data-ttu-id="f693a-110">默认情况下，此复选框处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="f693a-110">By default, this check box is selected.</span></span>  
  
 <span data-ttu-id="f693a-111">**用下划线标出错误**</span><span class="sxs-lookup"><span data-stu-id="f693a-111">**Underline errors**</span></span>  
 <span data-ttu-id="f693a-112">在查询窗口中标识 [!INCLUDE[tsql](../includes/tsql-md.md)] 语句中的语法和语义错误。</span><span class="sxs-lookup"><span data-stu-id="f693a-112">Identifies syntax and semantic errors in [!INCLUDE[tsql](../includes/tsql-md.md)] statements in the query window.</span></span> <span data-ttu-id="f693a-113">所有错误和警告将以红色显示。</span><span class="sxs-lookup"><span data-stu-id="f693a-113">All errors and warnings appear in red.</span></span> <span data-ttu-id="f693a-114">只有已为其实现 IntelliSense 的 [!INCLUDE[tsql](../includes/tsql-md.md)] 语句才支持错误和警告。</span><span class="sxs-lookup"><span data-stu-id="f693a-114">Errors and warnings are supported only for the [!INCLUDE[tsql](../includes/tsql-md.md)] statements for which IntelliSense has been implemented.</span></span> <span data-ttu-id="f693a-115">默认情况下，此复选框处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="f693a-115">By default, this check box is selected.</span></span>  
  
 <span data-ttu-id="f693a-116">**大纲语句**</span><span class="sxs-lookup"><span data-stu-id="f693a-116">**Outline statements**</span></span>  
 <span data-ttu-id="f693a-117">打开文件时启用大纲显示功能。</span><span class="sxs-lookup"><span data-stu-id="f693a-117">Enables the outlining feature when a file is opened.</span></span> <span data-ttu-id="f693a-118">这将创建可折叠的 [!INCLUDE[tsql](../includes/tsql-md.md)] 代码块。</span><span class="sxs-lookup"><span data-stu-id="f693a-118">This creates collapsible blocks of [!INCLUDE[tsql](../includes/tsql-md.md)] code.</span></span> <span data-ttu-id="f693a-119">默认情况下，此复选框处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="f693a-119">By default, this check box is selected.</span></span>  
  
 <span data-ttu-id="f693a-120">**最大脚本大小**</span><span class="sxs-lookup"><span data-stu-id="f693a-120">**Maximum script size**</span></span>  
 <span data-ttu-id="f693a-121">指定脚本的大小，达到此大小时将禁用 IntelliSense 功能。</span><span class="sxs-lookup"><span data-stu-id="f693a-121">Specifies the size at which IntelliSense functionality is disabled.</span></span> <span data-ttu-id="f693a-122">如果脚本超过指定大小，则发出一条警告消息。</span><span class="sxs-lookup"><span data-stu-id="f693a-122">If a script exceeds the specified size, a warning message is issued.</span></span> <span data-ttu-id="f693a-123">该编辑器窗口的所有 IntelliSense 功能（颜色编码功能除外）将被禁用。</span><span class="sxs-lookup"><span data-stu-id="f693a-123">All IntelliSense features, except color coding, are disabled for that editor window.</span></span> <span data-ttu-id="f693a-124">在删除了足够多的文本以将脚本大小降低到限制范围内时，IntelliSense 将重新启用。</span><span class="sxs-lookup"><span data-stu-id="f693a-124">IntelliSense is reenabled when enough text is deleted to reduce the script size to under the limit.</span></span> <span data-ttu-id="f693a-125">对大型脚本启用 IntelliSense 会降低速度较慢的计算机的性能。</span><span class="sxs-lookup"><span data-stu-id="f693a-125">Enabling IntelliSense for large script sizes can decrease performance on slow computers.</span></span> <span data-ttu-id="f693a-126">允许的大小为 100 KB、500 KB、1 MB、2 MB 和无限制。</span><span class="sxs-lookup"><span data-stu-id="f693a-126">The allowed sizes are 100 KB, 500 KB, 1 MB, 2 MB, and Unlimited.</span></span> <span data-ttu-id="f693a-127">默认值为 1 MB。</span><span class="sxs-lookup"><span data-stu-id="f693a-127">The default is 1 MB.</span></span>  
  
 <span data-ttu-id="f693a-128">**内置函数名称的大小写**</span><span class="sxs-lookup"><span data-stu-id="f693a-128">**Casing for built-in function names**</span></span>  
 <span data-ttu-id="f693a-129">指定完成列表中内置 [!INCLUDE[tsql](../includes/tsql-md.md)] 函数的名称采用大写形式（例如 DATEADD）还是小写形式（例如 dateadd）。</span><span class="sxs-lookup"><span data-stu-id="f693a-129">Specifies whether the names of built-in [!INCLUDE[tsql](../includes/tsql-md.md)] functions that are included in completion lists use uppercase letters, such as DATEADD; or lowercase letters, such as dateadd.</span></span> <span data-ttu-id="f693a-130">请选择最符合您使用的 [!INCLUDE[tsql](../includes/tsql-md.md)] 编码约定的选项。</span><span class="sxs-lookup"><span data-stu-id="f693a-130">Select the option that best matches the [!INCLUDE[tsql](../includes/tsql-md.md)] coding conventions that you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f693a-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f693a-131">See Also</span></span>  
 [<span data-ttu-id="f693a-132">IntelliSense &#40;SQL Server Management Studio 疑难解答&#41;</span><span class="sxs-lookup"><span data-stu-id="f693a-132">Troubleshooting IntelliSense &#40;SQL Server Management Studio&#41;</span></span>](../relational-databases/scripting/troubleshooting-intellisense.md)  
  
  
