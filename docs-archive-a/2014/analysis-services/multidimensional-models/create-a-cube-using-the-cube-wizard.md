---
title: 使用多维数据集向导创建多维数据集 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- cubes [Analysis Services], creating
ms.assetid: d46d659c-3a4e-4364-94ac-f5eb6ba0ec25
author: minewiskan
ms.author: owend
ms.openlocfilehash: 441c296c0fd71b2a9c2b8332743da6224839a471
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691978"
---
# <a name="create-a-cube-using-the-cube-wizard"></a><span data-ttu-id="ae19f-102">使用多维数据集向导创建多维数据集</span><span class="sxs-lookup"><span data-stu-id="ae19f-102">Create a Cube Using the Cube Wizard</span></span>
  <span data-ttu-id="ae19f-103">可以使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中的多维数据集向导来创建新的多维数据集。</span><span class="sxs-lookup"><span data-stu-id="ae19f-103">You can create a new cube by using the Cube Wizard in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
### <a name="to-create-a-new-cube"></a><span data-ttu-id="ae19f-104">创建新的多维数据集</span><span class="sxs-lookup"><span data-stu-id="ae19f-104">To create a new cube</span></span>  
  
1.  <span data-ttu-id="ae19f-105">在**解决方案资源管理器**中，右键单击 "**多维数据**集"，然后单击 "**新建多维数据集**"。</span><span class="sxs-lookup"><span data-stu-id="ae19f-105">In **Solution Explorer**, right-click **Cubes**, and then click **New Cube**.</span></span>  
  
2.  <span data-ttu-id="ae19f-106">在多维数据集向导的 **“选择创建方法”** 页上，选择 **“使用现有表”**，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="ae19f-106">On the **Select Creation Method** page of the Cube Wizard, select **Use existing tables**, and then click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ae19f-107">有时可能必须在不使用现有表的情况下创建多维数据集。</span><span class="sxs-lookup"><span data-stu-id="ae19f-107">You might occasionally have to create a cube without using existing tables.</span></span> <span data-ttu-id="ae19f-108">若要创建一个空的多维数据集，请选择 **“创建空的多维数据集”**。</span><span class="sxs-lookup"><span data-stu-id="ae19f-108">To create an empty cube, select **Create an empty cube**.</span></span> <span data-ttu-id="ae19f-109">若要生成表，请选择 **“在数据源中生成表”**。</span><span class="sxs-lookup"><span data-stu-id="ae19f-109">To generate tables, select **Generate tables in the data source**.</span></span>  
  
3.  <span data-ttu-id="ae19f-110">在 **“选择度量值组表”** 页上，执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="ae19f-110">On the **Select Measure Group Tables** page, do the following procedures:</span></span>  
  
    1.  <span data-ttu-id="ae19f-111">在 **“数据源视图”** 列表中，选择数据源视图。</span><span class="sxs-lookup"><span data-stu-id="ae19f-111">In the **Data source view** list, select a data source view.</span></span>  
  
    2.  <span data-ttu-id="ae19f-112">在 **“度量值组表”** 列表中，选择将用于创建度量值组的表。</span><span class="sxs-lookup"><span data-stu-id="ae19f-112">In the **Measure group tables** list, select the tables that will be used to create measure groups.</span></span>  
  
    3.  <span data-ttu-id="ae19f-113">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="ae19f-113">Click **Next**.</span></span>  
  
4.  <span data-ttu-id="ae19f-114">在 **“选择度量值”** 页上，选择要在多维数据集中包含的度量值，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="ae19f-114">On the **Select Measures** page, select the measures that you want to include in the cube, and then click **Next**.</span></span>  
  
     <span data-ttu-id="ae19f-115">另外，您可以更改度量值和度量值组的名称。</span><span class="sxs-lookup"><span data-stu-id="ae19f-115">Optionally, you can change the names of the measures and measure groups.</span></span>  
  
5.  <span data-ttu-id="ae19f-116">在 **“选择现有维度”** 页上，选择要在多维数据集中包含的现有维度，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="ae19f-116">On the **Select Existing Dimensions** page, select the existing dimensions to include in the cube, and then click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ae19f-117"> 对于任何选定的度量值组，如果数据库中已存在维度，则会出现 **“选择现有维度”** 页。</span><span class="sxs-lookup"><span data-stu-id="ae19f-117">The **Select Existing Dimensions** page appears if dimensions already exist in the database for any of the selected measure groups.</span></span>  
  
6.  <span data-ttu-id="ae19f-118">在 **“选择新维度”** 页上，选择要创建的新维度，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="ae19f-118">On the **Select New Dimensions** page, select the new dimensions to create, and then click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ae19f-119"> 如果有任何表适用于维度表，并且这些表尚未被现有维度使用，则会出现 **“选择新维度”** 页。</span><span class="sxs-lookup"><span data-stu-id="ae19f-119">The **Select New Dimensions** page appears if any tables would be good candidates for dimension tables, and the tables have not already been used by existing dimensions.</span></span>  
  
7.  <span data-ttu-id="ae19f-120">在 **“选择缺少的维度键”** 页上，为维度选择一个键，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="ae19f-120">On the **Select Missing Dimension Keys** page, select a key for the dimension, and then click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ae19f-121"> 如果您指定的任何维度表都未定义键，则会出现 **“选择缺少的维度键”** 页。</span><span class="sxs-lookup"><span data-stu-id="ae19f-121">The **Select Missing Dimension Keys** page appears if any of the dimension tables that you specified do not have a key defined.</span></span>  
  
8.  <span data-ttu-id="ae19f-122">在 **“完成向导”** 页中，输入新多维数据集的名称，并查看该多维数据集的结构。</span><span class="sxs-lookup"><span data-stu-id="ae19f-122">On the **Completing the Wizard** page, enter a name for the new cube and review the cube structure.</span></span> <span data-ttu-id="ae19f-123">若要进行更改，请单击 **“上一步”**；否则，单击 **“完成”**。</span><span class="sxs-lookup"><span data-stu-id="ae19f-123">If you want to make changes, click **Back**; otherwise, click **Finish**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ae19f-124">完成多维数据集向导后，可以使用多维数据集设计器来配置多维数据集。</span><span class="sxs-lookup"><span data-stu-id="ae19f-124">You can use Cube Designer after you complete the Cube Wizard to configure the cube.</span></span> <span data-ttu-id="ae19f-125">还可以使用维度设计器来添加、删除和配置所创建维度中的属性和层次结构。</span><span class="sxs-lookup"><span data-stu-id="ae19f-125">You can also use Dimension Designer to add, remove, and configure attributes and hierarchies in the dimensions that you created.</span></span>  
  
  
