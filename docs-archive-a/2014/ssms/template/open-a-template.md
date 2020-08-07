---
title: 打开模板 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- templates [Transact-SQL], opening
- opening templates
ms.assetid: 605b0f4c-5ba1-4249-ad1c-6341df77cd7a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 43b75d68fafea759e4d7873c1fb738d7964dcf57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588213"
---
# <a name="open-a-template"></a><span data-ttu-id="5d326-102">打开模板</span><span class="sxs-lookup"><span data-stu-id="5d326-102">Open a Template</span></span>
  <span data-ttu-id="5d326-103">可以从模板资源管理器中打开模板。</span><span class="sxs-lookup"><span data-stu-id="5d326-103">You can open a template from Template Explorer.</span></span>  
  
## <a name="to-open-a-template-from-template-explorer"></a><span data-ttu-id="5d326-104">从模板资源管理器中打开模板</span><span class="sxs-lookup"><span data-stu-id="5d326-104">To open a template from Template Explorer</span></span>  
 <span data-ttu-id="5d326-105">可以从模板资源管理器中打开模板。</span><span class="sxs-lookup"><span data-stu-id="5d326-105">You can open templates from the Template Explorer.</span></span>  
  
1.  <span data-ttu-id="5d326-106">若要打开模板资源管理器，请在“视图”  菜单上单击“模板资源管理器”  。</span><span class="sxs-lookup"><span data-stu-id="5d326-106">To open Template Explorer, on the **View** menu, click **Template Explorer**.</span></span>  
  
2.  <span data-ttu-id="5d326-107">在模板类别列表中，展开包含要打开的模板的类别。</span><span class="sxs-lookup"><span data-stu-id="5d326-107">In the list of template categories, expand the category that contains the template you want to open.</span></span>  
  
3.  <span data-ttu-id="5d326-108">有三种方法可以打开模板：</span><span class="sxs-lookup"><span data-stu-id="5d326-108">There are three ways to open the template:</span></span>  
  
    1.  <span data-ttu-id="5d326-109">双击模板以在代码编辑器窗口中将其打开。</span><span class="sxs-lookup"><span data-stu-id="5d326-109">Double-click the template to open it in a code editor window.</span></span>  
  
    2.  <span data-ttu-id="5d326-110">右键单击模板并选择“打开”  以在代码编辑器窗口中将其打开。</span><span class="sxs-lookup"><span data-stu-id="5d326-110">Right-click the template and select **Open** to open it in a code editor window.</span></span>  
  
    3.  <span data-ttu-id="5d326-111">将模板拖到代码编辑器窗口，以将模板代码添加到编辑器窗口的内容中。</span><span class="sxs-lookup"><span data-stu-id="5d326-111">Drag the template into a code editor window to add the template code to the contents of the editor window.</span></span>  
  
 <span data-ttu-id="5d326-112">打开模板之后，使用“替换模板参数”  对话框将模板参数替换为具体的值。</span><span class="sxs-lookup"><span data-stu-id="5d326-112">After the template is open, use the **Replace Template Parameters** dialog box to replace the template parameters with your values.</span></span>  
  
 <span data-ttu-id="5d326-113">如果打开模板启动了一个新的编辑器窗口，将使用当前活动连接的凭据打开该窗口。</span><span class="sxs-lookup"><span data-stu-id="5d326-113">If opening a template launches a new editor window, the window will open with the credentials of the current active connection.</span></span> <span data-ttu-id="5d326-114">例如，如果在打开 CREATE DATABASE 模板时聚焦对象资源管理器中的某个 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例，将使用到该实例的连接打开新的编辑器窗口。</span><span class="sxs-lookup"><span data-stu-id="5d326-114">For example, if you are focused on an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] in Object Explorer when you open the CREATE DATABASE template, a new editor window will be opened using a connection to that instance.</span></span> <span data-ttu-id="5d326-115">如果没有活动连接， [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 将显示登录对话框。</span><span class="sxs-lookup"><span data-stu-id="5d326-115">If there is no active connection, [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] will present a login dialog.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d326-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5d326-116">See Also</span></span>  
 <span data-ttu-id="5d326-117">[模板资源管理器](template-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="5d326-117">[Template Explorer](template-explorer.md) </span></span>  
 [<span data-ttu-id="5d326-118">替换模板参数</span><span class="sxs-lookup"><span data-stu-id="5d326-118">Replace Template Parameters</span></span>](replace-template-parameters.md)  
  
  
