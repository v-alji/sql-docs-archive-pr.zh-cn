---
title: " (SSAS) 连接到 Microsoft Excel 文件 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connexcelfile.f1
ms.assetid: 126f7d6b-d270-40e7-b23e-8d114f87065b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 79bb3d57470be8acbbb990dde71cf21b62b3cb2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579214"
---
# <a name="connect-to-a-microsoft-excel-file-ssas"></a><span data-ttu-id="985da-102">连接到 Microsoft Excel 文件 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="985da-102">Connect to a Microsoft Excel File (SSAS)</span></span>
  <span data-ttu-id="985da-103">**“表导入向导”** 的这一页可用于连接到在本地计算机上存储的 Microsoft Excel 文件。</span><span class="sxs-lookup"><span data-stu-id="985da-103">This page of the **Table Import Wizard** enables you to connect to a Microsoft Excel file stored on the local machine.</span></span> <span data-ttu-id="985da-104">若要从 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]访问该向导，请在 **“模型”** 菜单上，单击 **“从数据源导入”**。</span><span class="sxs-lookup"><span data-stu-id="985da-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="985da-105">若要连接到 Microsoft Excel 文件，必须在计算机上安装适当的 ACE 访问接口。</span><span class="sxs-lookup"><span data-stu-id="985da-105">To connect to a Microsoft Excel file, you must have the appropriate ACE provider installed on your computer.</span></span> <span data-ttu-id="985da-106">有关详细信息，请参阅[数据源支持（SSAS 表格）](tabular-models/data-sources-supported-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="985da-106">For more information, see [Data Sources Supported &#40;SSAS Tabular&#41;](tabular-models/data-sources-supported-ssas-tabular.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="985da-107">在此页中选择文件时，将使用当前用户的凭据。</span><span class="sxs-lookup"><span data-stu-id="985da-107">The credentials of the current user are used when selecting a file in this page.</span></span> <span data-ttu-id="985da-108">但是，如果在“模拟信息”页中指定的用户没有足够的权限从所选文件中读取，则导入将不会成功。</span><span class="sxs-lookup"><span data-stu-id="985da-108">However, import will not succeed if the user specified in the Impersonation Information page does not have sufficient privileges to read from the selected file.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="985da-109">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="985da-109">UI element list</span></span>  
 <span data-ttu-id="985da-110">**友好的连接名称**</span><span class="sxs-lookup"><span data-stu-id="985da-110">**Friendly connection name**</span></span>  
 <span data-ttu-id="985da-111">键入此数据源连接的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="985da-111">Type a unique name for this data source connection.</span></span> <span data-ttu-id="985da-112">这是必填字段。</span><span class="sxs-lookup"><span data-stu-id="985da-112">This is a required field.</span></span>  
  
 <span data-ttu-id="985da-113">**Excel 文件路径**</span><span class="sxs-lookup"><span data-stu-id="985da-113">**Excel File Path**</span></span>  
 <span data-ttu-id="985da-114">指定 Excel 文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="985da-114">Specify a full path for the Excel file.</span></span>  
  
 <span data-ttu-id="985da-115">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="985da-115">**Browse**</span></span>  
 <span data-ttu-id="985da-116">导航至 Excel 文件可用的位置。</span><span class="sxs-lookup"><span data-stu-id="985da-116">Navigate to a location where an Excel file is available.</span></span>  
  
 <span data-ttu-id="985da-117">**高级**</span><span class="sxs-lookup"><span data-stu-id="985da-117">**Advanced**</span></span>  
 <span data-ttu-id="985da-118">通过使用“设置高级属性”\*\*\*\* 对话框设置附加的连接属性。</span><span class="sxs-lookup"><span data-stu-id="985da-118">Set additional connection properties by using the **Set Advanced Properties** dialog box..</span></span>  
  
 <span data-ttu-id="985da-119">**使用第一行作为列标题**</span><span class="sxs-lookup"><span data-stu-id="985da-119">**Use first row as column headers**</span></span>  
 <span data-ttu-id="985da-120">指定是否要使用第一个数据行作为目标表的列标题。</span><span class="sxs-lookup"><span data-stu-id="985da-120">Specify whether to use the first data row as the column headers of the destination table.</span></span>  
  
 <span data-ttu-id="985da-121">**测试连接**</span><span class="sxs-lookup"><span data-stu-id="985da-121">**Test Connection**</span></span>  
 <span data-ttu-id="985da-122">使用当前设置尝试建立与数据源的连接。</span><span class="sxs-lookup"><span data-stu-id="985da-122">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="985da-123">将显示一个消息，指示连接是否成功。</span><span class="sxs-lookup"><span data-stu-id="985da-123">A message is displayed indicating whether the connection is successful.</span></span>  
  
  
