---
title: 任务6：设置同义词 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: b7d35ee9-d1c9-41d9-bbc5-0ca7db93e54d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: bde0c0ec7f230ba2325aa01328b191fd8fd67fa6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577141"
---
# <a name="task-6-setting-synonyms"></a><span data-ttu-id="d1517-102">任务 6：设置同义词</span><span class="sxs-lookup"><span data-stu-id="d1517-102">Task 6: Setting Synonyms</span></span>
  <span data-ttu-id="d1517-103">在此任务中，您将**国家/地区**域的两个域值（ **USA**和**美国**）设置为具有**美国**作为前导值的同义词。</span><span class="sxs-lookup"><span data-stu-id="d1517-103">In this task, you set two domain values, **USA** and **United States**, of the **Country** domain as synonyms with **United States** as the leading value.</span></span> <span data-ttu-id="d1517-104">由于在创建**国家/地区**域时选择了 "**使用前导值**" 选项，因此**国家/地区**域的任何**USA**值都将作为**美国** (输出，美国是前导值) 。</span><span class="sxs-lookup"><span data-stu-id="d1517-104">Since the **Use Leading Values** option was selected when creating the **Country** domain, any **USA** values for the **Country** domain will be output as **United States** (as United States is the leading value).</span></span> <span data-ttu-id="d1517-105">有关更多详细信息，请参阅[更改域值](https://msdn.microsoft.com/library/hh510408.aspx)。</span><span class="sxs-lookup"><span data-stu-id="d1517-105">See [Change Domain Values](https://msdn.microsoft.com/library/hh510408.aspx) for more details.</span></span>

1.  <span data-ttu-id="d1517-106">从域列表中选择 "**国家/地区**"。</span><span class="sxs-lookup"><span data-stu-id="d1517-106">Select **Country** from the list of domains.</span></span>

2.  <span data-ttu-id="d1517-107">切换到 "**域值**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="d1517-107">Switch to the **Domain Values** tab.</span></span>

3.  <span data-ttu-id="d1517-108">单击工具栏上的 "**添加新的域值**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="d1517-108">Click **Add new domain value** button on the toolbar.</span></span>

4.  <span data-ttu-id="d1517-109">键入**USA**作为值，然后按**enter**。</span><span class="sxs-lookup"><span data-stu-id="d1517-109">Type **USA** for the value and press **ENTER**.</span></span>

5.  <span data-ttu-id="d1517-110">使用 CTRL 或 SHIFT 键的多选项**美国**和**美国**，右键单击所选项，然后单击 "**设为同义词**"。</span><span class="sxs-lookup"><span data-stu-id="d1517-110">Multiselect **United States** and **USA** using CTRL or SHIFT keys, right-click the selected items, and then click **Set as Synonyms**.</span></span> <span data-ttu-id="d1517-111">DQS 将对这些值进行分组，然后将这些值之一指定为将用来替换其他值的前导值。</span><span class="sxs-lookup"><span data-stu-id="d1517-111">DQS groups these values and designate one of the values as the leading value that the other values are replaced with.</span></span>

     <span data-ttu-id="d1517-112">![“设为同义词”菜单](../../2014/tutorials/media/et-settingsynonyms-01.jpg "“设为同义词”菜单")</span><span class="sxs-lookup"><span data-stu-id="d1517-112">![Set as Synonyms Menu](../../2014/tutorials/media/et-settingsynonyms-01.jpg "Set as Synonyms Menu")</span></span>

6.  <span data-ttu-id="d1517-113">请注意，**美国**设置为前导值。</span><span class="sxs-lookup"><span data-stu-id="d1517-113">Notice that **United States** is set as the leading value.</span></span> <span data-ttu-id="d1517-114">如果希望 USA 成为前导值，则可以右键单击 "USA"，然后选择 "**设置为前导**" 选项。</span><span class="sxs-lookup"><span data-stu-id="d1517-114">If you want USA to be the leading value, you can right-click on USA and select **Set as Leading** option.</span></span> <span data-ttu-id="d1517-115">对于本教程，我们将**美国**用作前导值。</span><span class="sxs-lookup"><span data-stu-id="d1517-115">For this tutorial, we use **United States** as the leading value.</span></span>

     <span data-ttu-id="d1517-116">![美国和 USA 为同义词](../../2014/tutorials/media/et-settingsynonyms-02.jpg "美国和 USA 为同义词")</span><span class="sxs-lookup"><span data-stu-id="d1517-116">![United States and USA as Synonyms](../../2014/tutorials/media/et-settingsynonyms-02.jpg "United States and USA as Synonyms")</span></span>

## <a name="next-step"></a><span data-ttu-id="d1517-117">下一步</span><span class="sxs-lookup"><span data-stu-id="d1517-117">Next Step</span></span>
 [<span data-ttu-id="d1517-118">任务 7：创建复合域</span><span class="sxs-lookup"><span data-stu-id="d1517-118">Task 7: Creating a Composite Domain</span></span>](../../2014/tutorials/task-7-creating-a-composite-domain.md)


