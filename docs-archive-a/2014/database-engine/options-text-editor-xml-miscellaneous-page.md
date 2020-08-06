---
title: 选项 (文本编辑器-XML-杂项页面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 1a9509f0-c663-4b31-b396-7f5dc4371651
author: rothja
ms.author: jroth
ms.openlocfilehash: d937368d30122442ccbc40372a6b8e1cabc141e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682374"
---
# <a name="options-text-editor---xml---miscellaneous-page"></a><span data-ttu-id="e7fa0-102">选项（“文本编辑器”-“XML”-“杂项”页）</span><span class="sxs-lookup"><span data-stu-id="e7fa0-102">Options (Text Editor - XML - Miscellaneous Page)</span></span>

<span data-ttu-id="e7fa0-103">使用“选项”\*\*\*\* 对话框，可以更改 XML 编辑器的自动完成设置和架构设置。</span><span class="sxs-lookup"><span data-stu-id="e7fa0-103">The **Options** dialog box lets you change the autocompletion and schema settings for the XML Editor.</span></span> <span data-ttu-id="e7fa0-104">若要使用这些设置，请在“工具”\*\*\*\* 菜单上单击“选项”\*\*\*\*，展开“文本编辑器”文件夹\*\*\*\*，单击“XML”\*\*\*\*，再单击“杂项”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e7fa0-104">These settings are available when, on the **Tools** menu, you click **Options**, expand the **Text Editor** folder, click **XML** and then click **Miscellaneous** .</span></span>  
  
## <a name="auto-insert"></a><span data-ttu-id="e7fa0-105">自动插入</span><span class="sxs-lookup"><span data-stu-id="e7fa0-105">Auto Insert</span></span>  
 <span data-ttu-id="e7fa0-106">**结束标记**</span><span class="sxs-lookup"><span data-stu-id="e7fa0-106">**Close tags**</span></span>  
 <span data-ttu-id="e7fa0-107">文本编辑器在创建 XML 元素时将添加关闭标记。</span><span class="sxs-lookup"><span data-stu-id="e7fa0-107">The Text Editor adds close tags when authoring XML elements.</span></span> <span data-ttu-id="e7fa0-108">如果选择了元素开始标记，该编辑器将插入匹配的关闭标记，包括匹配的命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="e7fa0-108">If an element start tag is selected, the editor inserts the matching close tag, including a matching namespace prefix.</span></span> <span data-ttu-id="e7fa0-109">默认情况下，此复选框为选中状态。</span><span class="sxs-lookup"><span data-stu-id="e7fa0-109">This check box is selected by default.</span></span>  
  
 <span data-ttu-id="e7fa0-110">**特性引号**</span><span class="sxs-lookup"><span data-stu-id="e7fa0-110">**Attribute quotes**</span></span>  
 <span data-ttu-id="e7fa0-111">创建 XML 属性时，编辑器将插入 `="``"` 字符并将插入号 (**^** ) 置于引号内。</span><span class="sxs-lookup"><span data-stu-id="e7fa0-111">When authoring XML attributes, the editor inserts the `="``"` characters and positions the caret (**^)** inside the quotation marks.</span></span> <span data-ttu-id="e7fa0-112">默认情况下，此复选框为选中状态。</span><span class="sxs-lookup"><span data-stu-id="e7fa0-112">This check box is selected by default.</span></span>  
  
 <span data-ttu-id="e7fa0-113">**命名空间声明**</span><span class="sxs-lookup"><span data-stu-id="e7fa0-113">**Namespace declarations**</span></span>  
 <span data-ttu-id="e7fa0-114">文本编辑器将在需要的位置自动插入命名空间声明。</span><span class="sxs-lookup"><span data-stu-id="e7fa0-114">The editor automatically inserts namespace declarations wherever they are needed.</span></span> <span data-ttu-id="e7fa0-115">默认情况下，此复选框为选中状态。</span><span class="sxs-lookup"><span data-stu-id="e7fa0-115">This check box is selected by default.</span></span>  
  
 <span data-ttu-id="e7fa0-116">**其他标记(注释，CDATA)**</span><span class="sxs-lookup"><span data-stu-id="e7fa0-116">**Other markup (Comments, CDATA)**</span></span>  
 <span data-ttu-id="e7fa0-117">注释、CDATA、DOCTYPE、处理指令和其他标记是自动完成的。</span><span class="sxs-lookup"><span data-stu-id="e7fa0-117">Comments, CDATA, DOCTYPE, processing instructions, and other markup is autocompleted.</span></span> <span data-ttu-id="e7fa0-118">默认情况下，此复选框为选中状态。</span><span class="sxs-lookup"><span data-stu-id="e7fa0-118">This check box is selected by default.</span></span>  
  
## <a name="network"></a><span data-ttu-id="e7fa0-119">网络</span><span class="sxs-lookup"><span data-stu-id="e7fa0-119">Network</span></span>  
 <span data-ttu-id="e7fa0-120">**自动下载 DTD 和架构**</span><span class="sxs-lookup"><span data-stu-id="e7fa0-120">**Automatically download DTDs and schemas**</span></span>  
 <span data-ttu-id="e7fa0-121">架构和文档类型定义 (DTD) 是从 HTTP 位置上自动下载的。</span><span class="sxs-lookup"><span data-stu-id="e7fa0-121">Schemas and document type definitions (DTDs) are automatically downloaded from HTTP locations.</span></span> <span data-ttu-id="e7fa0-122">此功能使用了启用自动代理服务器检测功能的 System.Net。</span><span class="sxs-lookup"><span data-stu-id="e7fa0-122">This feature uses System.Net with autoproxy server detection enabled.</span></span> <span data-ttu-id="e7fa0-123">默认情况下，此复选框为选中状态。</span><span class="sxs-lookup"><span data-stu-id="e7fa0-123">This check box is selected by default.</span></span>  
  
## <a name="outlining"></a><span data-ttu-id="e7fa0-124">大纲显示</span><span class="sxs-lookup"><span data-stu-id="e7fa0-124">Outlining</span></span>  
 <span data-ttu-id="e7fa0-125">**打开文件时进入大纲模式**</span><span class="sxs-lookup"><span data-stu-id="e7fa0-125">**Enter outlining mode when files open**</span></span>  
 <span data-ttu-id="e7fa0-126">打开文件时，将启用大纲显示功能。</span><span class="sxs-lookup"><span data-stu-id="e7fa0-126">Turns on the outlining feature when a file is opened.</span></span> <span data-ttu-id="e7fa0-127">默认情况下，此复选框为选中状态。</span><span class="sxs-lookup"><span data-stu-id="e7fa0-127">This check box is selected by default.</span></span>  
  
## <a name="caching"></a><span data-ttu-id="e7fa0-128">Caching</span><span class="sxs-lookup"><span data-stu-id="e7fa0-128">Caching</span></span>  
 <span data-ttu-id="e7fa0-129">**架构**</span><span class="sxs-lookup"><span data-stu-id="e7fa0-129">**Schemas**</span></span>  
 <span data-ttu-id="e7fa0-130">指定架构缓存的位置。</span><span class="sxs-lookup"><span data-stu-id="e7fa0-130">Specifies the location of the schema cache.</span></span> <span data-ttu-id="e7fa0-131">单击“浏览(...)”按钮在新窗口中打开当前的架构缓存。</span><span class="sxs-lookup"><span data-stu-id="e7fa0-131">The Browse button (...) opens the current schema cache location in a new window.</span></span> <span data-ttu-id="e7fa0-132">默认位置为 *\<Management Studio install directory>* \xml\schemas。</span><span class="sxs-lookup"><span data-stu-id="e7fa0-132">The default location is *\<Management Studio install directory>* \Xml\Schemas.</span></span>  
