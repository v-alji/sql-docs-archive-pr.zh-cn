---
title: 将数据从 Excel 发布到 MDS (MDS Add-in for Excel) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 89fce454-a816-4b33-a26a-d1b9741d269b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 597a954760816d8938628974998fe8f6daad1af5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589733"
---
# <a name="publish-data-from-excel-to-mds-mds-add-in-for-excel"></a><span data-ttu-id="364ba-102">将数据从 Excel 发布到 MDS（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="364ba-102">Publish Data from Excel to MDS (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="364ba-103">在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，如果你在 Excel 中完成处理后想要保存更改以便于其他用户访问，可以将数据发布到 MDS 存储库。</span><span class="sxs-lookup"><span data-stu-id="364ba-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], publish data to the MDS repository when you are finished working in Excel and want to save your changes so other users have access to them.</span></span>  
  
> [!NOTE]
>  -   <span data-ttu-id="364ba-104">发布更改时，将删除 MDS 管理的单元上的注释。</span><span class="sxs-lookup"><span data-stu-id="364ba-104">When you publish changes, comments on MDS-managed cells are deleted.</span></span>  
> -   <span data-ttu-id="364ba-105">在 MDS 托管单元中不支持公式。</span><span class="sxs-lookup"><span data-stu-id="364ba-105">A formula is not supported in an MDS-managed cell.</span></span> <span data-ttu-id="364ba-106">MDS 托管单元中的公式作为文本值处理。</span><span class="sxs-lookup"><span data-stu-id="364ba-106">A formula in an MDS-managed cell is handled as a text value.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="364ba-107">先决条件</span><span class="sxs-lookup"><span data-stu-id="364ba-107">Prerequisites</span></span>  
 <span data-ttu-id="364ba-108">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="364ba-108">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="364ba-109">\*\*\*\* 您必须有权访问“资源管理器”功能区域。</span><span class="sxs-lookup"><span data-stu-id="364ba-109">You must have permission to access the **Explorer** functional area.</span></span>  
  
-   <span data-ttu-id="364ba-110">活动工作表必须包含 MDS 管理的数据，并且您必须对 MDS 管理的数据做出更改或向其添加数据。</span><span class="sxs-lookup"><span data-stu-id="364ba-110">The active worksheet must contain MDS-managed data and you must have made changes or additions to the MDS-managed data.</span></span>  
  
-   <span data-ttu-id="364ba-111">如果添加的是成员，在自动为该实体生成代码时不必指定 **Code** 值。</span><span class="sxs-lookup"><span data-stu-id="364ba-111">If you are adding members, you do not have to specify a **Code** value if codes for the entity are being automatically generated.</span></span> <span data-ttu-id="364ba-112">有关详细信息，请参阅[&#41;&#40;Master Data Services 自动创建代码](../automatic-code-creation-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="364ba-112">For more information, see [Automatic Code Creation &#40;Master Data Services&#41;](../automatic-code-creation-master-data-services.md).</span></span>  
  
### <a name="to-publish-data-to-the-mds-repository"></a><span data-ttu-id="364ba-113">将数据发布到 MDS 存储库</span><span class="sxs-lookup"><span data-stu-id="364ba-113">To publish data to the MDS repository</span></span>  
  
1.  <span data-ttu-id="364ba-114">在 **“发布并验证”** 组中，单击 **“发布”**。</span><span class="sxs-lookup"><span data-stu-id="364ba-114">In the **Publish and Validate** group, click **Publish**.</span></span>  
  
2.  <span data-ttu-id="364ba-115">可选。</span><span class="sxs-lookup"><span data-stu-id="364ba-115">Optional.</span></span> <span data-ttu-id="364ba-116">如果显示“发布并添加批注”\*\*\*\* 对话框，请选择为所有更新共享相同的批注（注释），或者为每个更改逐个添加批注。</span><span class="sxs-lookup"><span data-stu-id="364ba-116">If the **Publish and Annotate** dialog box is displayed, choose to share the same annotation (comment) for all updates, or to annotate each change individually.</span></span>  
  
3.  <span data-ttu-id="364ba-117">可选。</span><span class="sxs-lookup"><span data-stu-id="364ba-117">Optional.</span></span> <span data-ttu-id="364ba-118">选中 **“不再显示此对话框”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="364ba-118">Select the **Do not show this dialog box again** check box.</span></span> <span data-ttu-id="364ba-119">通过选择 **“设置”** 并选中 **“在发布时显示‘发布并添加批注’对话框”** 复选框，将来可始终显示该对话框。</span><span class="sxs-lookup"><span data-stu-id="364ba-119">You can always show the dialog box in the future by choosing **Settings** and selecting the **Show Publish and Annotate dialog box when publishing** check box.</span></span>  
  
4.  <span data-ttu-id="364ba-120">单击“发布”。</span><span class="sxs-lookup"><span data-stu-id="364ba-120">Click **Publish**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="364ba-121">如果要向工作表添加新成员（行）但无法将其成功添加至 MDS 存储库，则你可能并非对工作表中的所有属性都具有“更新”\*\*\*\* 权限。</span><span class="sxs-lookup"><span data-stu-id="364ba-121">If you are adding new members (rows) to your worksheet and you cannot successfully publish them to the MDS repository, you may not have **Update** permission to all of the attributes in the worksheet.</span></span> <span data-ttu-id="364ba-122">在 **“检查”** 选项卡上的 **“更改”** 组中，单击 **“取消工作表保护”** ，然后再次尝试发布。</span><span class="sxs-lookup"><span data-stu-id="364ba-122">On the **Review** tab, in the **Changes** group, click **Unprotect Sheet** and try to publish again.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="364ba-123">后续步骤</span><span class="sxs-lookup"><span data-stu-id="364ba-123">Next Steps</span></span>  
 [<span data-ttu-id="364ba-124">应用业务规则（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="364ba-124">Apply Business Rules &#40;MDS Add-in for Excel&#41;</span></span>](apply-business-rules-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a><span data-ttu-id="364ba-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="364ba-125">See Also</span></span>  
 <span data-ttu-id="364ba-126">[MDS Add-in for Excel&#41;发布数据 &#40;](overview-importing-data-from-excel-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="364ba-126">[Publishing Data &#40;MDS Add-in for Excel&#41;](overview-importing-data-from-excel-mds-add-in-for-excel.md) </span></span>  
 [<span data-ttu-id="364ba-127">验证数据（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="364ba-127">Validating Data &#40;MDS Add-in for Excel&#41;</span></span>](validating-data-mds-add-in-for-excel.md)  
  
  
