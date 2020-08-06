---
title: 替换模板参数 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.templates.replaceparameters.f1
helpviewer_keywords:
- template parameters [Template Explorer]
- templates [Transact-SQL], replacing parameters
- Replace (Query) Template Parameters dialog box
- replacing template parameters
ms.assetid: 1234aa14-3464-4a3e-922a-5cfb8fb23627
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1d87b17a110efe118f7796487448e4d3bae30375
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588214"
---
# <a name="replace-template-parameters"></a><span data-ttu-id="2abe9-102">替换模板参数</span><span class="sxs-lookup"><span data-stu-id="2abe9-102">Replace Template Parameters</span></span>
  <span data-ttu-id="2abe9-103">模板包含每次使用模板时可由实现特定值替换的参数。</span><span class="sxs-lookup"><span data-stu-id="2abe9-103">Templates contain parameters that can be replaced by implementation-specific values each time the template is used.</span></span> <span data-ttu-id="2abe9-104">在代码编辑器中打开模板之后，可以使用与您的实现相关的值替换这些参数。</span><span class="sxs-lookup"><span data-stu-id="2abe9-104">After opening a template in a code editor, you can replace the parameters with values relevant to your implementation.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="2abe9-105">开始之前</span><span class="sxs-lookup"><span data-stu-id="2abe9-105">Before You Begin</span></span>  
 <span data-ttu-id="2abe9-106">“指定模板参数的值”  对话框是包含三列的网格。</span><span class="sxs-lookup"><span data-stu-id="2abe9-106">The **Specify Values for Template Parameters** dialog is a grid with three columns.</span></span> <span data-ttu-id="2abe9-107">“参数”  和“类型”  列是只读的，不能更改。</span><span class="sxs-lookup"><span data-stu-id="2abe9-107">The **Parameter** and **Type** columns are read-only and cannot be changed.</span></span> <span data-ttu-id="2abe9-108">查看“值”  列的内容，将任意默认值更改为对你的实现合适的值。</span><span class="sxs-lookup"><span data-stu-id="2abe9-108">Review the contents of the **Value** column, and change any of the defaults to values appropriate for your implementation.</span></span>  
  
 <span data-ttu-id="2abe9-109">若要使用此对话框，必须将脚本中的参数按以下格式括在尖括号 (`< >`) 内：`<`parameter_name  `,` data_type  `,` default_value  `>`。</span><span class="sxs-lookup"><span data-stu-id="2abe9-109">To use this dialog box, you must have parameters in your script enclosed in angle brackets (`< >`) in the format `<`*parameter_name*`,` *data_type*`,` *default_value*`>`.</span></span>  
  
## <a name="replace-template-parameters"></a><span data-ttu-id="2abe9-110">替换模板参数</span><span class="sxs-lookup"><span data-stu-id="2abe9-110">Replace Template Parameters</span></span>  
 <span data-ttu-id="2abe9-111">在代码编辑器窗口中打开模板后：</span><span class="sxs-lookup"><span data-stu-id="2abe9-111">After opening the template in a code editor window:</span></span>  
  
1.  <span data-ttu-id="2abe9-112">在 **“查询”** 菜单上，单击 **“指定模板参数的值”** 。</span><span class="sxs-lookup"><span data-stu-id="2abe9-112">On the **Query** menu, click **Specify Values for Template Parameters**.</span></span>  
  
2.  <span data-ttu-id="2abe9-113">在“指定模板参数的值”  对话框中，“值”  列包含每个参数的建议值。</span><span class="sxs-lookup"><span data-stu-id="2abe9-113">In the **Specify Values for Template Parameters** dialog box, the **Values** column contains a suggested value for each parameter.</span></span> <span data-ttu-id="2abe9-114">接受值或将其替换为新值。</span><span class="sxs-lookup"><span data-stu-id="2abe9-114">Accept the value or replace it with a new value.</span></span>  
  
3.  <span data-ttu-id="2abe9-115">单击“确定”  关闭“替换模板参数”  对话框并在查询编辑器中修改脚本。</span><span class="sxs-lookup"><span data-stu-id="2abe9-115">Click **OK** to close the **Replace Template Parameters** dialog box and modify the script in the query editor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2abe9-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2abe9-116">See Also</span></span>  
 <span data-ttu-id="2abe9-117">[模板资源管理器](template-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="2abe9-117">[Template Explorer](template-explorer.md) </span></span>  
 [<span data-ttu-id="2abe9-118">打开模板</span><span class="sxs-lookup"><span data-stu-id="2abe9-118">Open a Template</span></span>](open-a-template.md)  
  
  
