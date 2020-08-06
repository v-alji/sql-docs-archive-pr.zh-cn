---
title: " (SSAS) 连接到 Microsoft Access 数据库 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connaccessdb.f1
ms.assetid: 9fa81839-dd8b-41d3-915e-c774a707ed53
author: minewiskan
ms.author: owend
ms.openlocfilehash: fbb180a754b6bc276d588997117eb84fd1a5a873
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579216"
---
# <a name="connect-to-a-microsoft-access-database-ssas"></a><span data-ttu-id="b2f98-102">连接到 Microsoft Access 数据库 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="b2f98-102">Connect to a Microsoft Access Database (SSAS)</span></span>
  <span data-ttu-id="b2f98-103">**“表导入向导”** 的这一页可用于指定用于连接到 Microsoft Access 数据库的设置。</span><span class="sxs-lookup"><span data-stu-id="b2f98-103">This page of the **Table Import Wizard** enables you to specify settings to connect to a Microsoft Access database.</span></span> <span data-ttu-id="b2f98-104">若要从 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]访问该向导，请在 **“模型”** 菜单上，单击 **“从数据源导入”**。</span><span class="sxs-lookup"><span data-stu-id="b2f98-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="b2f98-105">若要连接到 Microsoft Access 数据库，必须在计算机上安装适当的 ACE 访问接口。</span><span class="sxs-lookup"><span data-stu-id="b2f98-105">To connect to a Microsoft Access database, you must have the appropriate ACE provider installed on your computer.</span></span> <span data-ttu-id="b2f98-106">有关详细信息，请参阅[数据源支持（SSAS 表格）](tabular-models/data-sources-supported-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="b2f98-106">For more information, see [Data Sources Supported &#40;SSAS Tabular&#41;](tabular-models/data-sources-supported-ssas-tabular.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b2f98-107">在此页中选择文件时，将使用当前用户的凭据。</span><span class="sxs-lookup"><span data-stu-id="b2f98-107">The credentials of the current user are used when selecting a file in this page.</span></span> <span data-ttu-id="b2f98-108">但是，如果在“模拟信息”页中指定的用户没有足够的权限从所选文件中读取，则导入将不会成功。</span><span class="sxs-lookup"><span data-stu-id="b2f98-108">However, import will not succeed if the user specified in the Impersonation Information page does not have sufficient privileges to read from the selected file.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="b2f98-109">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="b2f98-109">UI element list</span></span>  
 <span data-ttu-id="b2f98-110">**友好的连接名称**</span><span class="sxs-lookup"><span data-stu-id="b2f98-110">**Friendly connection name**</span></span>  
 <span data-ttu-id="b2f98-111">键入此数据源连接的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="b2f98-111">Type a unique name for this data source connection.</span></span> <span data-ttu-id="b2f98-112">这是必填字段。</span><span class="sxs-lookup"><span data-stu-id="b2f98-112">This is a required field.</span></span>  
  
 <span data-ttu-id="b2f98-113">**数据库名称**</span><span class="sxs-lookup"><span data-stu-id="b2f98-113">**Database name**</span></span>  
 <span data-ttu-id="b2f98-114">指定 Microsoft Access 数据库文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="b2f98-114">Specify the full path for a Microsoft Access database file.</span></span>  
  
 <span data-ttu-id="b2f98-115">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="b2f98-115">**Browse**</span></span>  
 <span data-ttu-id="b2f98-116">导航至 Microsoft Access 数据库文件可用的位置。</span><span class="sxs-lookup"><span data-stu-id="b2f98-116">Navigate to a location where a Microsoft Access database file is available.</span></span>  
  
 <span data-ttu-id="b2f98-117">**用户名**</span><span class="sxs-lookup"><span data-stu-id="b2f98-117">**User name**</span></span>  
 <span data-ttu-id="b2f98-118">为数据库连接指定用户名。</span><span class="sxs-lookup"><span data-stu-id="b2f98-118">Specify a user name for the database connection.</span></span>  
  
 <span data-ttu-id="b2f98-119">**密码**</span><span class="sxs-lookup"><span data-stu-id="b2f98-119">**Password**</span></span>  
 <span data-ttu-id="b2f98-120">为数据库连接指定密码。</span><span class="sxs-lookup"><span data-stu-id="b2f98-120">Specify a password for the database connection.</span></span>  
  
 <span data-ttu-id="b2f98-121">**保存密码**</span><span class="sxs-lookup"><span data-stu-id="b2f98-121">**Save my password**</span></span>  
 <span data-ttu-id="b2f98-122">指定是否存储已在“密码”\*\*\*\* 框中输入的密码。</span><span class="sxs-lookup"><span data-stu-id="b2f98-122">Specify whether the password you have entered in the **Password** box is stored.</span></span>  
  
 <span data-ttu-id="b2f98-123">**高级**</span><span class="sxs-lookup"><span data-stu-id="b2f98-123">**Advanced**</span></span>  
 <span data-ttu-id="b2f98-124">使用 "**设置高级属性**" 对话框设置附加的连接属性。</span><span class="sxs-lookup"><span data-stu-id="b2f98-124">Set additional connection properties by using the **Set Advanced Properties** dialog box.</span></span>  
  
 <span data-ttu-id="b2f98-125">**测试连接**</span><span class="sxs-lookup"><span data-stu-id="b2f98-125">**Test Connection**</span></span>  
 <span data-ttu-id="b2f98-126">使用当前设置尝试建立与数据源的连接。</span><span class="sxs-lookup"><span data-stu-id="b2f98-126">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="b2f98-127">将显示一个消息，指示连接是否成功。</span><span class="sxs-lookup"><span data-stu-id="b2f98-127">A message is displayed indicating whether the connection is successful.</span></span>  
  
  
