---
title: " (SSAS) 指定连接字符串 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.speconnstring.f1
ms.assetid: 3f89b55b-2659-4e9f-a3ad-ab9a23b6942d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9333c239504a79184e08776acb3f1d845f06cc4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691897"
---
# <a name="specify-a-connection-string-ssas"></a><span data-ttu-id="d9476-102">指定连接字符串 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="d9476-102">Specify a connection string (SSAS)</span></span>
  <span data-ttu-id="d9476-103">**“表导入向导”** 的这一页可用于指定要连接到 OLE DB 或 ODBC 数据源的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="d9476-103">This page of the **Table Import Wizard** enables you to specify a connection string to connect to an OLE DB or ODBC data source.</span></span> <span data-ttu-id="d9476-104">若要从 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]访问该向导，请在 **“模型”** 菜单上，单击 **“从数据源导入”**。</span><span class="sxs-lookup"><span data-stu-id="d9476-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="d9476-105">若要连接到数据源，必须在计算机上安装适当的访问接口。</span><span class="sxs-lookup"><span data-stu-id="d9476-105">To connect to a data source, you must have the appropriate provider installed on your computer.</span></span> <span data-ttu-id="d9476-106">有关支持的数据源和提供程序的详细信息，请参阅 [支持的数据源（SSAS 表格）](tabular-models/data-sources-supported-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="d9476-106">For more information about supported data sources and providers, see [Data Sources Supported &#40;SSAS Tabular&#41;](tabular-models/data-sources-supported-ssas-tabular.md).</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="d9476-107">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="d9476-107">UI element list</span></span>  
 <span data-ttu-id="d9476-108">**该连接的友好名称**</span><span class="sxs-lookup"><span data-stu-id="d9476-108">**Friendly name for this connection**</span></span>  
 <span data-ttu-id="d9476-109">键入此数据源连接的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="d9476-109">Type a unique name for this data source connection.</span></span> <span data-ttu-id="d9476-110">这是必填字段。</span><span class="sxs-lookup"><span data-stu-id="d9476-110">This is a required field.</span></span>  
  
 <span data-ttu-id="d9476-111">**连接字符串**</span><span class="sxs-lookup"><span data-stu-id="d9476-111">**Connection String**</span></span>  
 <span data-ttu-id="d9476-112">键入用于连接到 OLE DB 或 ODBC 数据源的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="d9476-112">Type a connection string to connect to an OLE DB or ODBC data source.</span></span>  
  
 <span data-ttu-id="d9476-113">**生成**</span><span class="sxs-lookup"><span data-stu-id="d9476-113">**Build**</span></span>  
 <span data-ttu-id="d9476-114">通过使用“数据链接属性”\*\*\*\* 对话框，指定连接字符串的属性。</span><span class="sxs-lookup"><span data-stu-id="d9476-114">Specify the properties for a connection string by using the **Data Link Properties** dialog box.</span></span> <span data-ttu-id="d9476-115">有关详细信息，请参阅 Microsoft 数据链接帮助，可以从该对话框找到该帮助。</span><span class="sxs-lookup"><span data-stu-id="d9476-115">For more information, see the Microsoft Data Link Help, which is available from that dialog box.</span></span>  
  
 <span data-ttu-id="d9476-116">**测试连接**</span><span class="sxs-lookup"><span data-stu-id="d9476-116">**Test Connection**</span></span>  
 <span data-ttu-id="d9476-117">使用指定的连接字符串尝试建立与数据源的连接。</span><span class="sxs-lookup"><span data-stu-id="d9476-117">Attempt to establish a connection to the data source using the specified connection string.</span></span> <span data-ttu-id="d9476-118">将显示一个消息，指示连接是否成功。</span><span class="sxs-lookup"><span data-stu-id="d9476-118">A message is displayed indicating whether the connection is successful.</span></span>  
  
  
