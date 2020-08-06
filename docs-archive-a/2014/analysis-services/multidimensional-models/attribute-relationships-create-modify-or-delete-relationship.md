---
title: 创建、修改或删除属性关系 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Analysis Services], member properties
- member properties [Analysis Services], creating
ms.assetid: 137b2f40-5dfb-4141-9110-70f961f259cb
author: minewiskan
ms.author: owend
ms.openlocfilehash: b0e25140a75feda708850a2328498fb13df28a0c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577904"
---
# <a name="create-modify-or-delete-an-attribute-relationship"></a><span data-ttu-id="1603a-102">创建、修改或删除属性关系</span><span class="sxs-lookup"><span data-stu-id="1603a-102">Create, Modify, or Delete an Attribute Relationship</span></span>
  <span data-ttu-id="1603a-103">可以使用 **中的维度设计器的** “属性关系” [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]选项卡，创建、修改或删除一个维度中的属性之间的属性关系。</span><span class="sxs-lookup"><span data-stu-id="1603a-103">You can create, modify, or delete an attribute relationship between attributes in a dimension by using the **Attribute Relationships** tab of Dimension Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
### <a name="to-create-an-attribute-relationship"></a><span data-ttu-id="1603a-104">创建属性关系</span><span class="sxs-lookup"><span data-stu-id="1603a-104">To create an Attribute Relationship</span></span>  
  
1.  <span data-ttu-id="1603a-105">在维度设计器中，打开要在其间创建属性关系的属性所属的维度。</span><span class="sxs-lookup"><span data-stu-id="1603a-105">In Dimension Designer, open the dimension that contains the attributes that you want to create an attribute relationship between.</span></span>  
  
2.  <span data-ttu-id="1603a-106">在“属性关系”\*\*\*\* 选项卡的关系图或“属性”\*\*\*\* 窗格中，右键单击某个属性，然后选择“新建属性关系”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1603a-106">On the **Attribute Relationships** tab, right-click an attribute in the diagram or in the **Attributes** pane, and then select **New Attribute Relationship**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1603a-107">若要显示“属性”\*\*\*\* 窗格，请单击工具栏上的“显示列表视图”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1603a-107">To display the **Attributes** pane, click **Show List Views** on the toolbar.</span></span>  
  
3.  <span data-ttu-id="1603a-108">在 **“创建属性关系”** 对话框中，选择源属性及其相关属性。</span><span class="sxs-lookup"><span data-stu-id="1603a-108">In the **Create Attribute Relationship** dialog box, select a source attribute and a related attribute.</span></span>  
  
4.  <span data-ttu-id="1603a-109">在 **“关系类型”** 列表中，选择一个关系类型，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="1603a-109">In the **Relationship type** list, select a relationship type, and then click **OK**.</span></span>  
  
### <a name="to-modify-an-attribute-relationship"></a><span data-ttu-id="1603a-110">修改属性关系</span><span class="sxs-lookup"><span data-stu-id="1603a-110">To modify an Attribute Relationship</span></span>  
  
1.  <span data-ttu-id="1603a-111">在维度设计器中，打开包含要修改的属性关系的维度。</span><span class="sxs-lookup"><span data-stu-id="1603a-111">In Dimension Designer, open the dimension that contains the attribute relationship that you want to modify.</span></span>  
  
2.  <span data-ttu-id="1603a-112">单击 **“属性关系”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="1603a-112">Click the **Attribute Relationships** tab.</span></span>  
  
3.  <span data-ttu-id="1603a-113">在关系图或“属性关系”\*\*\*\* 窗格中，右键单击该属性关系，然后选择“编辑属性关系”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1603a-113">Right-click the attribute relationship in the diagram or in the **Attribute Relationships** pane, and select **Edit Attribute Relationship**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1603a-114">若要显示“属性关系”\*\*\*\* 窗格，请单击工具栏上的“显示列表视图”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1603a-114">To display the **Attribute Relationships** pane, click **Show List Views** on the toolbar.</span></span>  
  
4.  <span data-ttu-id="1603a-115">在 **“编辑属性关系”** 对话框中，选择源属性及其相关属性。</span><span class="sxs-lookup"><span data-stu-id="1603a-115">In the **Edit Attribute Relationship** dialog box, select a source attribute and a related attribute.</span></span>  
  
5.  <span data-ttu-id="1603a-116">在 **“关系类型”** 列表中，选择一个关系类型，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="1603a-116">In the **Relationship type** list, select a relationship type, and then click **OK**.</span></span>  
  
### <a name="to-delete-an-attribute-relationship"></a><span data-ttu-id="1603a-117">删除属性关系</span><span class="sxs-lookup"><span data-stu-id="1603a-117">To delete an Attribute Relationship</span></span>  
  
1.  <span data-ttu-id="1603a-118">在维度设计器中，打开包含要删除的属性关系的维度。</span><span class="sxs-lookup"><span data-stu-id="1603a-118">In Dimension Designer, open the dimension that contains the attribute relationship that you want to delete.</span></span>  
  
2.  <span data-ttu-id="1603a-119">在“属性关系”\*\*\*\* 选项卡的关系图或“属性关系”\*\*\*\* 窗格中，右键单击该属性，然后选择“删除”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1603a-119">On the **Attribute Relationships** tab, right-click the attribute relationship in the diagram or in the **Attribute Relationships** pane, and then select **Delete**.</span></span>  
  
3.  <span data-ttu-id="1603a-120">在 **“删除对象”** 对话框中，单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="1603a-120">In the **Delete Objects** dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1603a-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1603a-121">See Also</span></span>  
 [<span data-ttu-id="1603a-122">的维度设计器中，可以在“维度结构”视图的</span><span class="sxs-lookup"><span data-stu-id="1603a-122">Attribute Relationships</span></span>](../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)  
  
  
