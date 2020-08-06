---
title: 定义和浏览翻译 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0e60be99-3768-499c-a22c-a4ec37e61887
author: minewiskan
ms.author: owend
ms.openlocfilehash: 351960375ce60825dfceccaa83856545c6b9208f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690838"
---
# <a name="defining-and-browsing-translations"></a><span data-ttu-id="dbb65-102">定义和浏览翻译</span><span class="sxs-lookup"><span data-stu-id="dbb65-102">Defining and Browsing Translations</span></span>
  <span data-ttu-id="dbb65-103">翻译是 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 对象的名称在特定语言中的表示形式。</span><span class="sxs-lookup"><span data-stu-id="dbb65-103">A translation is a representation of the names of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] objects in a specific language.</span></span> <span data-ttu-id="dbb65-104">对象包括度量值组、度量值、维度、属性、层次结构、KPI、操作和计算成员。</span><span class="sxs-lookup"><span data-stu-id="dbb65-104">Objects include measure groups, measures, dimensions, attributes, hierarchies, KPIs, actions, and calculated members.</span></span> <span data-ttu-id="dbb65-105">翻译为可支持多种语言的客户端应用程序提供了服务器支持。</span><span class="sxs-lookup"><span data-stu-id="dbb65-105">Translations provide server support for client applications that can support multiple languages.</span></span> <span data-ttu-id="dbb65-106">通过使用这样的客户端，客户端就可以将区域设置标识符 (LCID) 传递给 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]实例，该实例则使用 LCID 来确定在为 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 对象提供元数据时要使用哪一组翻译。</span><span class="sxs-lookup"><span data-stu-id="dbb65-106">By using such a client, the client passes the locale identifier (LCID) to the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], which uses the LCID to determine which set of translations to use when it provides metadata for [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] objects.</span></span> <span data-ttu-id="dbb65-107">如果 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 对象不包含该语言的翻译或不包含指定对象的翻译，则在将该对象元数据返回给客户端时使用默认语言。</span><span class="sxs-lookup"><span data-stu-id="dbb65-107">If an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object does not contain a translation for that language, or does not contain a translation for a specified object, the default language is used in returning the object metadata back to the client.</span></span> <span data-ttu-id="dbb65-108">例如，如果一个法国的业务用户从使用法语区域设置的工作站访问多维数据集，则存在法语翻译时，此业务用户将看到法语的成员标题和成员属性值。</span><span class="sxs-lookup"><span data-stu-id="dbb65-108">For example, if a business user in France accesses a cube from a workstation that has a French locale setting, the business user will see the member captions and member property values in French if a French translation exists.</span></span> <span data-ttu-id="dbb65-109">但是，如果一个德国的业务用户从使用德语区域设置的工作站上访问同一个多维数据集，则此业务用户将看到德语的成员标题和成员属性值。</span><span class="sxs-lookup"><span data-stu-id="dbb65-109">However, if a business user in Germany accesses the same cube from a workstation that has a German locale setting, the business user will see the captions names and member property values in German.</span></span> <span data-ttu-id="dbb65-110">有关详细信息，请参阅[维度翻译](multidimensional-models-olap-logical-dimension-objects/dimension-translations.md)、[多维数据集翻译](multidimensional-models-olap-logical-cube-objects/cube-translations.md)、[翻译 &#40;Analysis Services&#41;](translations-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="dbb65-110">For more information, see [Dimension Translations](multidimensional-models-olap-logical-dimension-objects/dimension-translations.md), [Cube Translations](multidimensional-models-olap-logical-cube-objects/cube-translations.md), [Translations &#40;Analysis Services&#41;](translations-analysis-services.md).</span></span>  
  
 <span data-ttu-id="dbb65-111">在本主题的任务中，您将为“日期”维度中的一组有限的维度对象和 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教程多维数据集中的多维数据集对象定义元数据翻译。</span><span class="sxs-lookup"><span data-stu-id="dbb65-111">In the tasks in this topic, you define metadata translations for a limited set of dimension objects in the Date dimension and cube objects in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span> <span data-ttu-id="dbb65-112">然后浏览这些维度和多维数据集对象，以检查元数据翻译。</span><span class="sxs-lookup"><span data-stu-id="dbb65-112">You will then browse these dimension and cube objects to examine the metadata translations.</span></span>  
  
## <a name="specifying-translations-for-the-date-dimension-metadata"></a><span data-ttu-id="dbb65-113">为“日期”维度元数据指定翻译</span><span class="sxs-lookup"><span data-stu-id="dbb65-113">Specifying Translations for the Date Dimension Metadata</span></span>  
  
1.  <span data-ttu-id="dbb65-114">打开“日期”\*\*\*\* 维度的维度设计器，然后单击“翻译”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="dbb65-114">Open Dimension Designer for the **Date** dimension, and then click the **Translations** tab.</span></span>  
  
     <span data-ttu-id="dbb65-115">每个维度对象的元数据将以默认语言显示。</span><span class="sxs-lookup"><span data-stu-id="dbb65-115">The metadata in the default language for each dimension object appears.</span></span> <span data-ttu-id="dbb65-116">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教程多维数据集中的默认语言为英语。</span><span class="sxs-lookup"><span data-stu-id="dbb65-116">The default language in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube is English.</span></span>  
  
2.  <span data-ttu-id="dbb65-117">在“翻译”\*\*\*\* 选项卡的工具栏上，单击“新建翻译”\*\*\*\* 按钮。</span><span class="sxs-lookup"><span data-stu-id="dbb65-117">On the toolbar of the **Translations** tab, click the **New Translation** button.</span></span>  
  
     <span data-ttu-id="dbb65-118">语言列表将出现在“选择语言”\*\*\*\* 对话框中。</span><span class="sxs-lookup"><span data-stu-id="dbb65-118">A list of languages appears in the **Select Language** dialog box.</span></span>  
  
3.  <span data-ttu-id="dbb65-119">单击“西班牙语(西班牙)”\*\*\*\*，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="dbb65-119">Click **Spanish (Spain)**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="dbb65-120">将显示一个新列，在其中您可以将要翻译的元数据对象定义为用西班牙语翻译。</span><span class="sxs-lookup"><span data-stu-id="dbb65-120">A new column appears in which you will define the Spanish translations for the metadata objects you want to translate.</span></span> <span data-ttu-id="dbb65-121">在本教程中，仅翻译了少数对象来举例说明此过程。</span><span class="sxs-lookup"><span data-stu-id="dbb65-121">In this tutorial, we will only translate a few objects just to illustrate the process.</span></span>  
  
4.  <span data-ttu-id="dbb65-122">在“翻译”\*\*\*\* 选项卡的工具栏上，单击“新建翻译”\*\*\*\* 按钮，在“选择语言”\*\*\*\* 对话框中单击“法语(法国)”\*\*\*\*，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="dbb65-122">On the toolbar of the **Translations** tab, click the **New Translation** button, click **French (France)** in the **Select Language** dialog box, and then click **OK**.</span></span>  
  
     <span data-ttu-id="dbb65-123">将出现另一个语言列，您将在其中定义法语翻译。</span><span class="sxs-lookup"><span data-stu-id="dbb65-123">Another language column appears in which you will define French translations.</span></span>  
  
5.  <span data-ttu-id="dbb65-124">在 "**日期**" 维度的 "**标题**" 对象行中，在 " `Fecha` \*\*西班牙语 (西班牙") \*\*平移列和 `Temps` \*\*法语 (法国) \*\*翻译 "列中键入。</span><span class="sxs-lookup"><span data-stu-id="dbb65-124">In the row for the **Caption** object for the **Date** dimension, type `Fecha` in the **Spanish (Spain)** translation column and `Temps` in the **French (France)** translation column.</span></span>  
  
6.  <span data-ttu-id="dbb65-125">在 "**月份名称**" 属性的 "**标题**" 对象行中，在 " `Mes del Año` \*\*西班牙语 (西班牙") \*\*平移列和 `Mois d'Année` \*\*法语 (法国) \*\*翻译 "列中键入。</span><span class="sxs-lookup"><span data-stu-id="dbb65-125">In the row for the **Caption** object for the **Month Name** attribute, type `Mes del Año` in the **Spanish (Spain)** translation column and `Mois d'Année` in the **French (France)** translation column.</span></span>  
  
     <span data-ttu-id="dbb65-126">请注意，输入这些翻译时，将出现省略号 (**...**) 。</span><span class="sxs-lookup"><span data-stu-id="dbb65-126">Notice that when you enter these translations, an ellipsis (**...**) appears.</span></span> <span data-ttu-id="dbb65-127">单击此省略号可以指定为属性层次结构的每个成员提供翻译的基础表中的列。</span><span class="sxs-lookup"><span data-stu-id="dbb65-127">Clicking this ellipsis will enable you to specify a column in the underlying table that provides translations for each member of the attribute hierarchy.</span></span>  
  
7.  <span data-ttu-id="dbb65-128">对于 "**月份名称**" 属性，单击 "**西班牙语 (西班牙) **翻译" (**...** ") 。</span><span class="sxs-lookup"><span data-stu-id="dbb65-128">Click the ellipsis (**...**) for the **Spanish (Spain)** translation for the **Month Name** attribute.</span></span>  
  
     <span data-ttu-id="dbb65-129">“翻译属性数据”\*\*\*\* 对话框将出现。</span><span class="sxs-lookup"><span data-stu-id="dbb65-129">The **Attribute Data Translation** dialog box appears.</span></span>  
  
8.  <span data-ttu-id="dbb65-130">在“翻译列”\*\*\*\* 列表中，选择“SpanishMonthName”\*\*\*\*，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="dbb65-130">In the **Translation columns** list, select **SpanishMonthName**, as shown in the following image.</span></span>  
  
     <span data-ttu-id="dbb65-131">!["属性数据转换" 对话框](../../2014/tutorials/media/l9-translations-4.gif "“翻译属性数据”对话框")</span><span class="sxs-lookup"><span data-stu-id="dbb65-131">![Attribute Data Translation dialog box](../../2014/tutorials/media/l9-translations-4.gif "Attribute Data Translation dialog box")</span></span>  
  
9. <span data-ttu-id="dbb65-132">单击 **"确定**"，然后在 "**月份名称**" 属性的**法语 (法国) **翻译中单击省略号 (**...** ") 。</span><span class="sxs-lookup"><span data-stu-id="dbb65-132">Click **OK**, and then click the ellipsis (**...**) for the **French (France)** translation for the **Month Name** attribute.</span></span>  
  
10. <span data-ttu-id="dbb65-133">在“翻译列”\*\*\*\* 列表中，选择“FrenchMonthName”\*\*\*\*，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="dbb65-133">In the **Translation columns** list, select **FrenchMonthName**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="dbb65-134">此过程中的步骤阐释了为维度对象和成员定义元数据翻译的过程。</span><span class="sxs-lookup"><span data-stu-id="dbb65-134">The steps in this procedure illustrate the process of defining metadata translations for dimension objects and members.</span></span>  
  
## <a name="specifying-translations-for-the-analysis-services-tutorial-cube-metadata"></a><span data-ttu-id="dbb65-135">为 Analysis Services 教程多维数据集元数据指定翻译</span><span class="sxs-lookup"><span data-stu-id="dbb65-135">Specifying Translations for the Analysis Services Tutorial Cube Metadata</span></span>  
  
1.  <span data-ttu-id="dbb65-136">请切换到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教程多维数据集的多维数据集设计器，然后切换到“翻译”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="dbb65-136">Switch to Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then switch to the **Translations** tab.</span></span>  
  
     <span data-ttu-id="dbb65-137">每个多维数据集对象的元数据将以默认语言显示，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="dbb65-137">The metadata in the default language for each cube object appears, as shown in the following image.</span></span> <span data-ttu-id="dbb65-138">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教程多维数据集中的默认语言为英语。</span><span class="sxs-lookup"><span data-stu-id="dbb65-138">The default language in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube is English.</span></span>  
  
     <span data-ttu-id="dbb65-139">![“翻译”选项卡中的默认语言](../../2014/tutorials/media/l9-translations-5.gif "“翻译”选项卡中的默认语言")</span><span class="sxs-lookup"><span data-stu-id="dbb65-139">![Default language in Translations tab](../../2014/tutorials/media/l9-translations-5.gif "Default language in Translations tab")</span></span>  
  
2.  <span data-ttu-id="dbb65-140">在“翻译”\*\*\*\* 选项卡的工具栏上，单击“新建翻译”\*\*\*\* 按钮。</span><span class="sxs-lookup"><span data-stu-id="dbb65-140">On the toolbar of the **Translations** tab, click the **New Translation** button.</span></span>  
  
     <span data-ttu-id="dbb65-141">语言列表将出现在“选择语言”\*\*\*\* 对话框中。</span><span class="sxs-lookup"><span data-stu-id="dbb65-141">A list of languages appears in the **Select Language** dialog box.</span></span>  
  
3.  <span data-ttu-id="dbb65-142">选择“西班牙语(西班牙)”\*\*\*\*，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="dbb65-142">Select **Spanish (Spain)**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="dbb65-143">将显示一个新列，在其中您可以将要翻译的元数据对象定义为用西班牙语翻译。</span><span class="sxs-lookup"><span data-stu-id="dbb65-143">A new column appears in which you will define the Spanish translations for the metadata objects you want to translate.</span></span> <span data-ttu-id="dbb65-144">在本教程中，仅翻译了少数对象来举例说明此过程。</span><span class="sxs-lookup"><span data-stu-id="dbb65-144">In this tutorial, we will only translate a few objects just to illustrate the process.</span></span>  
  
4.  <span data-ttu-id="dbb65-145">在“翻译”\*\*\*\* 选项卡的工具栏上，单击“新建翻译”\*\*\*\* 按钮，在“选择语言”\*\*\*\* 对话框中选择“法语(法国)”\*\*\*\*，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="dbb65-145">On the toolbar of the **Translations** tab, click the **New Translation** button, select **French (France)** in the **Select Language** dialog box, and then click **OK**.</span></span>  
  
     <span data-ttu-id="dbb65-146">将出现另一个语言列，您将在其中定义法语翻译。</span><span class="sxs-lookup"><span data-stu-id="dbb65-146">Another language column appears in which you will define French translations.</span></span>  
  
5.  <span data-ttu-id="dbb65-147">在 "**日期**" 维度的 "**标题**" 对象行中，在 " `Fecha` \*\*西班牙语 (西班牙") \*\*平移列和 `Temps` \*\*法语 (法国) \*\*翻译 "列中键入。</span><span class="sxs-lookup"><span data-stu-id="dbb65-147">In the row for the **Caption** object for the **Date** dimension, type `Fecha` in the **Spanish (Spain)** translation column and `Temps` in the **French (France)** translation column.</span></span>  
  
6.  <span data-ttu-id="dbb65-148">在 " **Internet 销售**" 度量值组的 "**标题**" 对象行中，在 " `Ventas del lnternet` \*\*西班牙语 (西班牙") \*\*平移列和 `Ventes D'Internet` \*\*法语 (法国) \*\*翻译 "列中键入。</span><span class="sxs-lookup"><span data-stu-id="dbb65-148">In the row for the **Caption** object for the **Internet Sales** measure group, type `Ventas del lnternet` in the **Spanish (Spain)** translation column and `Ventes D'Internet` in the **French (France)** translation column.</span></span>  
  
7.  <span data-ttu-id="dbb65-149">在 "Internet 销售-销售额" 度量值的 "**标题**" 对象行中，在 " `Cantidad de las Ventas del Internet` \*\*西班牙语 (西班牙") \*\*平移列和 `Quantité de Ventes d'Internet` \*\*法语 (法国) \*\*翻译 "列中键入。</span><span class="sxs-lookup"><span data-stu-id="dbb65-149">In the row for the **Caption** object for the Internet Sales-Sales Amount measure, type `Cantidad de las Ventas del Internet` in the **Spanish (Spain)** translation column and `Quantité de Ventes d'Internet` in the **French (France)** translation column.</span></span>  
  
     <span data-ttu-id="dbb65-150">此过程中的步骤阐释了为多维数据集对象定义元数据翻译的过程。</span><span class="sxs-lookup"><span data-stu-id="dbb65-150">The steps in this procedure illustrate the process of defining metadata translations for cube objects.</span></span>  
  
## <a name="browsing-the-cube-by-using-translations"></a><span data-ttu-id="dbb65-151">使用翻译浏览多维数据集</span><span class="sxs-lookup"><span data-stu-id="dbb65-151">Browsing the Cube By Using Translations</span></span>  
  
1.  <span data-ttu-id="dbb65-152">在“生成”\*\*\*\* 菜单上，单击“部署 Analysis Services 教程”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="dbb65-152">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>  
  
2.  <span data-ttu-id="dbb65-153">成功完成部署后，请切换到“浏览器”\*\*\*\* 选项卡，然后单击“重新连接”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="dbb65-153">When deployment has successfully completed, switch to the **Browser** tab, and then click **Reconnect**.</span></span>  
  
3.  <span data-ttu-id="dbb65-154">从“数据”\*\*\*\* 窗格中删除所有层次结构和度量值，然后从“透视”\*\*\*\* 列表中选择“[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial”。</span><span class="sxs-lookup"><span data-stu-id="dbb65-154">Remove all hierarchies and measures from the **Data** pane and select [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial in the **Perspectives** list.</span></span>  
  
4.  <span data-ttu-id="dbb65-155">在“元数据”窗格中，展开“度量值”\*\*\*\*，然后展开“Internet Sales”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="dbb65-155">In the metadata pane, expand **Measures** and then expand **Internet Sales**.</span></span>  
  
     <span data-ttu-id="dbb65-156">请注意，“Internet Sales-Sales Amount”\*\*\*\* 度量值将以英文形式出现在此度量值组中。</span><span class="sxs-lookup"><span data-stu-id="dbb65-156">Notice that the **Internet Sales-Sales Amount** measure appears in English in this measure group.</span></span>  
  
5.  <span data-ttu-id="dbb65-157">在工具栏上，选择“语言”\*\*\*\* 列表中的“西班牙语(西班牙)”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="dbb65-157">On the toolbar, select **Spanish (Spain)** in the **Language** list.</span></span>  
  
     <span data-ttu-id="dbb65-158">注意，“元数据”窗格中的项将重新填充。</span><span class="sxs-lookup"><span data-stu-id="dbb65-158">Notice that the items in the metadata pane are repopulated.</span></span> <span data-ttu-id="dbb65-159">重新填充“元数据”窗格中的项之后，注意“Internet 销售额”度量值将不再出现在“Internet 销售”显示文件夹中。</span><span class="sxs-lookup"><span data-stu-id="dbb65-159">After the items in the metadata pane are repopulated, notice that the Internet Sales-Sales Amount measure no longer appears in the Internet Sales display folder.</span></span> <span data-ttu-id="dbb65-160">相反，它将在名为的新显示文件夹中以西班牙语显示 `Ventas del lnternet` ，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="dbb65-160">Instead, it appears in Spanish in a new display folder named `Ventas del lnternet`, as shown in the following image.</span></span>  
  
     <span data-ttu-id="dbb65-161">![重新填充的元数据窗格](../../2014/tutorials/media/l9-translations-6.gif "重新填充的元数据窗格")</span><span class="sxs-lookup"><span data-stu-id="dbb65-161">![Repopulated metadata pane](../../2014/tutorials/media/l9-translations-6.gif "Repopulated metadata pane")</span></span>  
  
6.  <span data-ttu-id="dbb65-162">在 "元数据" 窗格中，右键单击 `Cantidad de las Ventas del Internet` ，然后选择 "**添加到查询**"。</span><span class="sxs-lookup"><span data-stu-id="dbb65-162">In the metadata pane, right-click `Cantidad de las Ventas del Internet` and then select **Add to Query**.</span></span>  
  
7.  <span data-ttu-id="dbb65-163">在 "元数据" 窗格中，展开 `Fecha` " **Fecha 日期**"，右键单击 " **Fecha 日期**"，然后选择 "**添加到筛选器**"。</span><span class="sxs-lookup"><span data-stu-id="dbb65-163">In the metadata pane, expand `Fecha`, expand **Fecha.Calendar Date**, right-click **Fecha.Calendar Date**, and then select **Add to Filter**.</span></span>  
  
8.  <span data-ttu-id="dbb65-164">在“筛选器”\*\*\*\* 窗格中，选择“CY 2007”\*\*\*\* 作为筛选表达式。</span><span class="sxs-lookup"><span data-stu-id="dbb65-164">In the **Filter** pane, select **CY 2007** as the filter expression.</span></span>  
  
9. <span data-ttu-id="dbb65-165">在“元数据”窗格中，右键单击“Mes del Ano”\*\*\*\*，然后选择“添加到查询”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="dbb65-165">In the metadata pane, right-click **Mes del Ano** and select **Add to Query**.</span></span>  
  
     <span data-ttu-id="dbb65-166">注意，月份名称将以西班牙语显示，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="dbb65-166">Notice that the month names appear in Spanish, as shown in the following image.</span></span>  
  
     <span data-ttu-id="dbb65-167">![数据窗格中以西班牙语表示的月份名称](../../2014/tutorials/media/l9-translations-7.gif "数据窗格中以西班牙语表示的月份名称")</span><span class="sxs-lookup"><span data-stu-id="dbb65-167">![Month names in Spanish in data pane](../../2014/tutorials/media/l9-translations-7.gif "Month names in Spanish in data pane")</span></span>  
  
10. <span data-ttu-id="dbb65-168">在工具栏上，选择“语言”\*\*\*\* 列表中的“法语(法国)”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="dbb65-168">On the toolbar, select **French (France)** in the **Language** list.</span></span>  
  
     <span data-ttu-id="dbb65-169">注意，月份名称现在将以法语显示，并且度量值名称现在也以法语显示。</span><span class="sxs-lookup"><span data-stu-id="dbb65-169">Notice that the month names now appear in French and that the measure name now also appears in French.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="dbb65-170">下一课</span><span class="sxs-lookup"><span data-stu-id="dbb65-170">Next Lesson</span></span>  
 [<span data-ttu-id="dbb65-171">第 10 课：定义管理角色</span><span class="sxs-lookup"><span data-stu-id="dbb65-171">Lesson 10: Defining Administrative Roles</span></span>](lesson-10-defining-administrative-roles.md)  
  
## <a name="see-also"></a><span data-ttu-id="dbb65-172">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dbb65-172">See Also</span></span>  
 <span data-ttu-id="dbb65-173">[维度翻译](multidimensional-models-olap-logical-dimension-objects/dimension-translations.md) </span><span class="sxs-lookup"><span data-stu-id="dbb65-173">[Dimension Translations](multidimensional-models-olap-logical-dimension-objects/dimension-translations.md) </span></span>  
 <span data-ttu-id="dbb65-174">[多维数据集翻译](multidimensional-models-olap-logical-cube-objects/cube-translations.md) </span><span class="sxs-lookup"><span data-stu-id="dbb65-174">[Cube Translations](multidimensional-models-olap-logical-cube-objects/cube-translations.md) </span></span>  
 [<span data-ttu-id="dbb65-175">翻译 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="dbb65-175">Translations &#40;Analysis Services&#41;</span></span>](translations-analysis-services.md)  
  
  
