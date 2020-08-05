---
title: 设置文本框方向（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 64bd53f4-2f31-4732-8c2e-64c7b54b6972
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d509f1df29203fa5def79b61b74ae9db8f40d204
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577274"
---
# <a name="set-text-box-orientation-report-builder-and-ssrs"></a><span data-ttu-id="85302-102">设置文本框方向（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="85302-102">Set Text Box Orientation (Report Builder and SSRS)</span></span>
  <span data-ttu-id="85302-103">文本框可以有不同的方向：水平、垂直（从上到下读取文本）或旋转 270 度（从下到上读取文本）。</span><span class="sxs-lookup"><span data-stu-id="85302-103">A text box can be oriented in different directions: horizontally, vertically (text reading from top to bottom), or rotated by 270 degrees (text reading from bottom to top).</span></span> <span data-ttu-id="85302-104">由于是对文本框而非文本设置方向，因此方向适用于文本框中的所有文本。</span><span class="sxs-lookup"><span data-stu-id="85302-104">Because orientation is set on the text box not the text, the orientation applies to all the text in the text box.</span></span> <span data-ttu-id="85302-105">不能为文本的各个部分指定不同的方向。</span><span class="sxs-lookup"><span data-stu-id="85302-105">You cannot specify different orientations for parts of the text.</span></span> <span data-ttu-id="85302-106">需手动调整列宽和行高的大小以容纳旋转的文本。</span><span class="sxs-lookup"><span data-stu-id="85302-106">Size the column width and the row height manually to accommodate the rotated text.</span></span>  
  
 <span data-ttu-id="85302-107">用于指定文本方向的 WritingMode 属性在 "**文本框属性**" 对话框中不可用。</span><span class="sxs-lookup"><span data-stu-id="85302-107">The WritingMode property, which you use to specify text orientation, is not available in the **Text Box Properties** dialog box.</span></span> <span data-ttu-id="85302-108">您需要打开“属性”窗格并且在该窗格中设置属性。</span><span class="sxs-lookup"><span data-stu-id="85302-108">You need to open the Properties pane and set the property there.</span></span> <span data-ttu-id="85302-109">WritingMode 属性的可用值为**水平** (从左到右) ，**垂直** (文本读取到底部) ， **Rotate270** (文本从下到上) 的文本读取。</span><span class="sxs-lookup"><span data-stu-id="85302-109">The available values for the WritingMode property are **Horizontal** (text reading left to right), **Vertical** (text reading top to bottom), **Rotate270** (text reading bottom to top).</span></span> <span data-ttu-id="85302-110">必须手动调整列宽和行高的大小以容纳文本。</span><span class="sxs-lookup"><span data-stu-id="85302-110">You must manually size the column width and the row height to accommodate the text.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-text-orientation"></a><span data-ttu-id="85302-111">设置文本方向</span><span class="sxs-lookup"><span data-stu-id="85302-111">To set text orientation</span></span>  
  
1.  <span data-ttu-id="85302-112">创建一个新报表或打开现有报表。</span><span class="sxs-lookup"><span data-stu-id="85302-112">Create a new report or open an existing report.</span></span>  
  
2.  <span data-ttu-id="85302-113">如果“属性”窗格未打开，请单击 **“视图”** 选项卡并选中 **“属性”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="85302-113">If the Properties pane is not open, click the **View** tab and select the **Properties** check box.</span></span>  
  
3.  <span data-ttu-id="85302-114">单击要更改文本方向的文本框。</span><span class="sxs-lookup"><span data-stu-id="85302-114">Click the text box for which you want to change text orientation.</span></span>  
  
4.  <span data-ttu-id="85302-115">在 "属性" 窗格中找到 "WritingMode" 属性，然后在下拉列表中选择要应用到文本框的文本方向。</span><span class="sxs-lookup"><span data-stu-id="85302-115">Locate the WritingMode property in the Properties pane and in the drop-down list select the text orientation to apply to the text box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="85302-116">对“属性”窗格中的属性进行分类时，WritingMode 位于“本地化”类别中\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="85302-116">When the properties in the Properties pane are organized into categories, WritingMode is in the **Localization** category.</span></span>  
  
5.  <span data-ttu-id="85302-117">在列表框中，选择 **Horizontal**、 **Vertical**或 **Rotate270**。</span><span class="sxs-lookup"><span data-stu-id="85302-117">In the list box, select **Horizontal**, **Vertical**, or **Rotate270**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85302-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="85302-118">See Also</span></span>  
 <span data-ttu-id="85302-119">[文本框 &#40;报表生成器和 SSRS&#41;](text-boxes-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="85302-119">[Text Boxes &#40;Report Builder and SSRS&#41;](text-boxes-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="85302-120">教程：设置文本格式（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="85302-120">Tutorial: Format Text &#40;Report Builder&#41;</span></span>](../tutorial-format-text-report-builder.md)  
  
  
