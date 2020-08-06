---
title: 选项 (文本编辑器-XML 格式页面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 97373178-d288-4127-af37-d9f5fe1b8607
author: rothja
ms.author: jroth
ms.openlocfilehash: dce36142fe9974c0167fca700c509642e05d89b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690024"
---
# <a name="options-text-editor---xml---formatting-page"></a><span data-ttu-id="c4562-102">选项（“文本编辑器”-“XML”-“格式”页）</span><span class="sxs-lookup"><span data-stu-id="c4562-102">Options (Text Editor - XML - Formatting Page)</span></span>

<span data-ttu-id="c4562-103">使用此对话框，可以为 XML 编辑器指定格式设置。</span><span class="sxs-lookup"><span data-stu-id="c4562-103">This dialog box allows you to specify the formatting settings for the XML Editor.</span></span> <span data-ttu-id="c4562-104">可从“工具”\*\*\*\* 菜单访问“选项”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="c4562-104">You can access the **Options** dialog box from the **Tools** menu.</span></span>  
  
> [!NOTE]  
> <span data-ttu-id="c4562-105">从“选项”\*\*\*\* 对话框依次选择“文本编辑器”\*\*\*\* 文件夹、“XML”\*\*\*\* 文件夹和“格式”\*\*\*\* 选项后，这些设置将可用。</span><span class="sxs-lookup"><span data-stu-id="c4562-105">These settings are available when you select the **Text Editor** folder, the **XML** folder, and then the **Formatting** option from the **Options** dialog box.</span></span>  
  
## <a name="attributes"></a><span data-ttu-id="c4562-106">属性</span><span class="sxs-lookup"><span data-stu-id="c4562-106">Attributes</span></span>  
 <span data-ttu-id="c4562-107">**保留手动属性格式化**</span><span class="sxs-lookup"><span data-stu-id="c4562-107">**Preserve manual attribute formatting**</span></span>  
 <span data-ttu-id="c4562-108">请不要重新设置属性的格式。</span><span class="sxs-lookup"><span data-stu-id="c4562-108">Do not reformat attributes.</span></span> <span data-ttu-id="c4562-109">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="c4562-109">This is the default.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c4562-110">如果这些属性位于多行上，则编辑器会缩进属性的每一行，以与父元素的缩进大小相匹配。</span><span class="sxs-lookup"><span data-stu-id="c4562-110">If the attributes are on multiple lines, the editor indents each line of attributes to match the indentation of the parent element.</span></span>  
  
 <span data-ttu-id="c4562-111">**对齐属性，每个属性都位于一个单独的行上**</span><span class="sxs-lookup"><span data-stu-id="c4562-111">**Align attributes each on a separate line**</span></span>  
 <span data-ttu-id="c4562-112">垂直对齐第二个属性和后续属性，以便与第一个属性的缩进大小相匹配。</span><span class="sxs-lookup"><span data-stu-id="c4562-112">Align the second and subsequent attributes vertically to match the indentation of the first attribute.</span></span> <span data-ttu-id="c4562-113">下面的 XML 文本就是如何对齐属性的示例：</span><span class="sxs-lookup"><span data-stu-id="c4562-113">The following XML text is an example of how the attributes would be aligned.</span></span>  
  
```  
<item id = "123-A"  
      name = "hammer"  
      price = "9.95"  
</item>  
```  
  
## <a name="auto-reformat"></a><span data-ttu-id="c4562-114">自动重新设置格式</span><span class="sxs-lookup"><span data-stu-id="c4562-114">Auto Reformat</span></span>  
 <span data-ttu-id="c4562-115">**在从剪贴板粘贴时。**</span><span class="sxs-lookup"><span data-stu-id="c4562-115">**On paste from clipboard.**</span></span>  
 <span data-ttu-id="c4562-116">重新设置从剪贴板粘贴的 XML 文本的格式。</span><span class="sxs-lookup"><span data-stu-id="c4562-116">Reformat XML text pasted from the clipboard.</span></span>  
  
 <span data-ttu-id="c4562-117">**在完成结束标记时**</span><span class="sxs-lookup"><span data-stu-id="c4562-117">**On completion of end tag**</span></span>  
 <span data-ttu-id="c4562-118">在完成结束标记时重新设置元素的格式。</span><span class="sxs-lookup"><span data-stu-id="c4562-118">Reformat the element when the end tag is completed.</span></span>  
  
## <a name="mixed-content"></a><span data-ttu-id="c4562-119">混合内容</span><span class="sxs-lookup"><span data-stu-id="c4562-119">Mixed Content</span></span>  
 <span data-ttu-id="c4562-120">**默认情况下设置混合内容的格式。**</span><span class="sxs-lookup"><span data-stu-id="c4562-120">**Format mixed content by default.**</span></span>  
 <span data-ttu-id="c4562-121">尝试重新设置混合内容的格式，在 `xml:space="preserve"` 作用域中找到该内容时除外。</span><span class="sxs-lookup"><span data-stu-id="c4562-121">Attempt to reformat mixed content, except when the content is found in an `xml:space="preserve"` scope.</span></span> <span data-ttu-id="c4562-122">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="c4562-122">This is the default.</span></span>  
  
 <span data-ttu-id="c4562-123">如果某个元素同时包含文本和标记，则这些内容会被视为混合内容。</span><span class="sxs-lookup"><span data-stu-id="c4562-123">If an element contains a mix of text and markup, the contents are considered to be mixed content.</span></span> <span data-ttu-id="c4562-124">下面是包含混合内容的元素的示例：</span><span class="sxs-lookup"><span data-stu-id="c4562-124">Following is an example of an element with mixed content.</span></span>  
  
```  
<dir>c:\data\AlphaProject\  
  <file readOnly="false">test1.txt</file>  
  <file readOnly="false">test2.txt</file>  
```  
  
 \</dir>  
  
## <a name="see-also"></a><span data-ttu-id="c4562-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c4562-125">See Also</span></span>  
 [<span data-ttu-id="c4562-126">XML 编辑器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="c4562-126">XML Editor &#40;SQL Server Management Studio&#41;</span></span>](../ssms/sql-server-management-studio-ssms.md)  
