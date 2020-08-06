---
title: 查询选项执行 (常规页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.query.general.f1
ms.assetid: 858a0263-2f04-4692-b8bf-63e93c998ead
author: rothja
ms.author: jroth
ms.openlocfilehash: ce3848b51b81f111333ba0e9ac12c96432dd9863
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589867"
---
# <a name="query-options-execution-general-page"></a><span data-ttu-id="dfa55-102">“查询选项”中的“执行”（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="dfa55-102">Query Options Execution (General Page)</span></span>
  <span data-ttu-id="dfa55-103">使用此页可指定用于运行查询的选项 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="dfa55-103">Use this page to specify the options for running [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] queries.</span></span> <span data-ttu-id="dfa55-104">若要访问此对话框，请右键单击“查询编辑器”窗口的主体，再单击“查询选项”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="dfa55-104">To access this dialog box, right-click the body of a Query Editor window, and then click **Query Options**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="dfa55-105">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="dfa55-105">UI element list</span></span>  
 <span data-ttu-id="dfa55-106">**SET ROWCOUNT**</span><span class="sxs-lookup"><span data-stu-id="dfa55-106">**SET ROWCOUNT**</span></span>  
 <span data-ttu-id="dfa55-107">默认值为 0，指示 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 在收到所有结果之前将一直等待结果。</span><span class="sxs-lookup"><span data-stu-id="dfa55-107">The default value of 0 indicates that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] will wait for results until all results are received.</span></span> <span data-ttu-id="dfa55-108">如果希望 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 在获取指定数目的行后暂停查询，请提供一个大于 0 的值。</span><span class="sxs-lookup"><span data-stu-id="dfa55-108">Provide a value greater than 0 if you want [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to halt the query after obtaining the specified number of rows.</span></span> <span data-ttu-id="dfa55-109">若要关闭此选项（以便返回所有的行），请将 SET ROWCOUNT 指定为 0。</span><span class="sxs-lookup"><span data-stu-id="dfa55-109">To turn this option off (so that all rows are returned), specify SET ROWCOUNT 0.</span></span>  
  
 <span data-ttu-id="dfa55-110">**SET TEXTSIZE**</span><span class="sxs-lookup"><span data-stu-id="dfa55-110">**SET TEXTSIZE**</span></span>  
 <span data-ttu-id="dfa55-111">默认值为 2,147,483,647 个字节，表示 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 将针对 `text`、`ntext`、`nvarchar(max)` 和 `varchar(max)` 数据字段提供最高上限的数据。</span><span class="sxs-lookup"><span data-stu-id="dfa55-111">The default value of 2,147,483,647 bytes indicates that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] will provide a complete data field up to the limit of `text`, `ntext`, `nvarchar(max)`, and `varchar(max)` data fields.</span></span> <span data-ttu-id="dfa55-112">它将不影响 XML 数据类型。</span><span class="sxs-lookup"><span data-stu-id="dfa55-112">It does not affect the XML data type.</span></span> <span data-ttu-id="dfa55-113">提供较小的数值，可以在存在大量值时限制结果数量。</span><span class="sxs-lookup"><span data-stu-id="dfa55-113">Provide a smaller number to limit results in the case of large values.</span></span> <span data-ttu-id="dfa55-114">超出指定数量的列将被截断。</span><span class="sxs-lookup"><span data-stu-id="dfa55-114">Columns greater than the number provided will be truncated.</span></span>  
  
 <span data-ttu-id="dfa55-115">**执行超时值**</span><span class="sxs-lookup"><span data-stu-id="dfa55-115">**Execution time-out**</span></span>  
 <span data-ttu-id="dfa55-116">指示在取消查询之前等待的秒数。</span><span class="sxs-lookup"><span data-stu-id="dfa55-116">Indicates the number of seconds to wait before canceling the query.</span></span> <span data-ttu-id="dfa55-117">值 0 指示无限期的等待或无超时。</span><span class="sxs-lookup"><span data-stu-id="dfa55-117">A value of 0 indicates an infinite wait, or no time-out.</span></span>  
  
 <span data-ttu-id="dfa55-118">**批分隔符**</span><span class="sxs-lookup"><span data-stu-id="dfa55-118">**Batch separator**</span></span>  
 <span data-ttu-id="dfa55-119">键入用来将 Transact-SQL 语句分隔为批的词。</span><span class="sxs-lookup"><span data-stu-id="dfa55-119">Type a word that you use to separate Transact-SQL statements into batches.</span></span> <span data-ttu-id="dfa55-120">默认值为 GO。</span><span class="sxs-lookup"><span data-stu-id="dfa55-120">The default is GO.</span></span>  
  
 <span data-ttu-id="dfa55-121">**默认情况下，在 SQLCMD 模式下打开新查询**</span><span class="sxs-lookup"><span data-stu-id="dfa55-121">**By default, open new queries in SQLCMD Mode**</span></span>  
 <span data-ttu-id="dfa55-122">选中此复选框可在 SQLCMD 模式下打开新查询。</span><span class="sxs-lookup"><span data-stu-id="dfa55-122">Select this check box to open new queries in SQLCMD mode.</span></span> <span data-ttu-id="dfa55-123">仅当通过 "**工具**" 菜单打开该对话框时，此复选框才可见。</span><span class="sxs-lookup"><span data-stu-id="dfa55-123">This check box is visible only when the dialog box is opened through the **Tools** menu.</span></span>  
  
 <span data-ttu-id="dfa55-124">选择此选项时，请记住下列限制：</span><span class="sxs-lookup"><span data-stu-id="dfa55-124">When you select this option, be aware of the following limitations:</span></span>  
  
-   <span data-ttu-id="dfa55-125">[!INCLUDE[ssDE](../includes/ssde-md.md)] 查询编辑器中的 IntelliSense 处于关闭状态。</span><span class="sxs-lookup"><span data-stu-id="dfa55-125">IntelliSense in the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor is turned off.</span></span>  
  
-   <span data-ttu-id="dfa55-126">由于查询编辑器不能从命令行运行，因此您不能传入命令行参数（如变量）。</span><span class="sxs-lookup"><span data-stu-id="dfa55-126">Because Query Editor does not run from the command line, you cannot pass in command-line parameters such as variables.</span></span>  
  
-   <span data-ttu-id="dfa55-127">由于查询编辑器无法响应操作系统提示，因此您一定要记住不要运行交互式语句。</span><span class="sxs-lookup"><span data-stu-id="dfa55-127">Because Query Editor cannot respond to operating-system prompts, you must be careful not to run interactive statements.</span></span>  
  
 <span data-ttu-id="dfa55-128">**重置为默认值**</span><span class="sxs-lookup"><span data-stu-id="dfa55-128">**Reset to Default**</span></span>  
 <span data-ttu-id="dfa55-129">将此页上的所有值重置为原始默认值。</span><span class="sxs-lookup"><span data-stu-id="dfa55-129">Resets all values on this page to the original default values.</span></span>  
  
  
