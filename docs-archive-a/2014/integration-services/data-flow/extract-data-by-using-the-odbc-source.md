---
title: 使用 ODBC 源提取数据 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 10f25703-49a2-4d45-abab-6b4da2a57ba5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c05efe2b0479047280fc093ee555e037c77d82e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694054"
---
# <a name="extract-data-by-using-the-odbc-source"></a><span data-ttu-id="58345-102">使用 ODBC 源提取数据</span><span class="sxs-lookup"><span data-stu-id="58345-102">Extract Data by Using the ODBC Source</span></span>
  <span data-ttu-id="58345-103">本过程说明如何通过使用 ODBC 源来提取数据。</span><span class="sxs-lookup"><span data-stu-id="58345-103">This procedure describes how to extract data by using an ODBC source.</span></span> <span data-ttu-id="58345-104">若要添加和配置 ODBC 源，包中必须已经包含至少一个数据流任务。</span><span class="sxs-lookup"><span data-stu-id="58345-104">To add and configure an ODBC source, the package must already include at least one Data Flow task.</span></span>  
  
### <a name="to-extract-data-using-an-odbc-source"></a><span data-ttu-id="58345-105">使用 ODBC 源提取数据</span><span class="sxs-lookup"><span data-stu-id="58345-105">To extract data using an ODBC source</span></span>  
  
1.  <span data-ttu-id="58345-106">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中，打开所需的 [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="58345-106">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] package you want.</span></span>  
  
2.  <span data-ttu-id="58345-107">单击 **“数据流”** 选项卡，然后从 **“工具箱”** 把 ODBC 源拖动到设计图面。</span><span class="sxs-lookup"><span data-stu-id="58345-107">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the ODBC source to the design surface.</span></span>  
  
3.  <span data-ttu-id="58345-108">双击此 ODBC 源。</span><span class="sxs-lookup"><span data-stu-id="58345-108">Double-click the ODBC source.</span></span>  
  
4.  <span data-ttu-id="58345-109">在 **“ODBC 源编辑器”** 对话框中的 **“连接管理器”** 页上，选择现有的 ODBC 连接管理器，或单击 **“新建”** 创建新的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="58345-109">In the **ODBC Source Editor** dialog box, on the **Connection Manager** page, select an existing ODBC connection manager or click **New** to create a new connection manager.</span></span>  
  
5.  <span data-ttu-id="58345-110">选择数据访问方法。</span><span class="sxs-lookup"><span data-stu-id="58345-110">Select the data access method.</span></span>  
  
    -   <span data-ttu-id="58345-111">**表名**：在数据库中选择某个表或视图，或者键入一个正则表达式以便标识 ODBC 连接管理器连接到的表。</span><span class="sxs-lookup"><span data-stu-id="58345-111">**Table Name**: Select a table or view in the database or type a regular expression to identify the table to which the ODBC connection manager connects.</span></span>  
  
         <span data-ttu-id="58345-112">该列表仅包含前 1000 个表。</span><span class="sxs-lookup"><span data-stu-id="58345-112">This list contains the first 1000 tables only.</span></span> <span data-ttu-id="58345-113">如果您的数据库包含超过 1000 个表，则可以键入表名的开头，或者使用 (\*) 通配符输入名称的任何部分以便显示要使用的表。</span><span class="sxs-lookup"><span data-stu-id="58345-113">If your database contains more than 1000 tables, you can type the beginning of a table name or use the (\*) wild card to enter any part of the name to display the table or tables you want to use.</span></span>  
  
    -   <span data-ttu-id="58345-114">**SQL 命令**：键入 SQL 命令，或单击 **“浏览”** 从文本文件中加载 SQL 查询。</span><span class="sxs-lookup"><span data-stu-id="58345-114">**SQL Command**: Type an SQL Command or click **Browse** to load the SQL query from a text file.</span></span>  
  
6.  <span data-ttu-id="58345-115">可以单击 **“预览”** ，查看最多 200 行 ODBC 源所提取的数据。</span><span class="sxs-lookup"><span data-stu-id="58345-115">You can click **Preview** to view up to 200 rows of the data extracted by the ODBC source.</span></span>  
  
7.  <span data-ttu-id="58345-116">若要更新外部列和输出列之间的映射，请单击 **“列”** ，并在 **“外部列”** 列表中选择其他列。</span><span class="sxs-lookup"><span data-stu-id="58345-116">To update the mapping between external and output columns, click **Columns** and select different columns in the **External Column** list.</span></span>  
  
8.  <span data-ttu-id="58345-117">如果需要，可以通过编辑 **“输出列”** 列表中的值来更新输出列的名称。</span><span class="sxs-lookup"><span data-stu-id="58345-117">If necessary, update the names of output columns by editing values in the **Output Column** list.</span></span>  
  
9. <span data-ttu-id="58345-118">若要配置错误输出，请单击 **“错误输出”** 。</span><span class="sxs-lookup"><span data-stu-id="58345-118">To configure the error output, click **Error Output**.</span></span>  
  
10. <span data-ttu-id="58345-119">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="58345-119">Click **OK**.</span></span>  
  
11. <span data-ttu-id="58345-120">若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="58345-120">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58345-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="58345-121">See Also</span></span>  
 <span data-ttu-id="58345-122">[ODBC 源编辑器（“连接管理器”页）](../odbc-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="58345-122">[ODBC Source Editor &#40;Connection Manager Page&#41;](../odbc-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="58345-123">[ODBC 源编辑器（“列”页）](../odbc-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="58345-123">[ODBC Source Editor &#40;Columns Page&#41;](../odbc-source-editor-columns-page.md) </span></span>  
 [<span data-ttu-id="58345-124">ODBC 源编辑器（“错误输出”页）</span><span class="sxs-lookup"><span data-stu-id="58345-124">ODBC Source Editor &#40;Error Output Page&#41;</span></span>](../odbc-source-editor-error-output-page.md)  
  
  
