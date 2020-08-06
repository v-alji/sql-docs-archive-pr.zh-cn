---
title: " (SSAS) 连接到 Microsoft SQL Server 并行数据仓库 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connsqlparadatawh.f1
ms.assetid: 98c879ee-7257-40c9-bc85-6766bd3b4885
author: minewiskan
ms.author: owend
ms.openlocfilehash: 082d6b34077d1bde11b527d3bfff907073eed16e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579208"
---
# <a name="connect-to-a-microsoft-sql-server-parallel-data-warehouse-ssas"></a><span data-ttu-id="0bba9-102">连接到 Microsoft SQL Server Parallel Data Warehouse (SSAS)</span><span class="sxs-lookup"><span data-stu-id="0bba9-102">Connect to a Microsoft SQL Server Parallel Data Warehouse (SSAS)</span></span>
  <span data-ttu-id="0bba9-103">“表导入向导”\*\*\*\* 的这一页可用于指定用于连接到 Microsoft SQL Server Parallel Data Warehouse (PDW) 的设置。</span><span class="sxs-lookup"><span data-stu-id="0bba9-103">This page of the **Table Import Wizard** enables you to specify settings to connect to a Microsoft SQL Server Parallel Data Warehouse (PDW).</span></span> <span data-ttu-id="0bba9-104">若要从 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]访问该向导，请在 **“模型”** 菜单上，单击 **“从数据源导入”**。</span><span class="sxs-lookup"><span data-stu-id="0bba9-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="0bba9-105">SQL Server PDW 是一种扩展性很强的工具，它通过大规模并行处理以很低的成本提供高性能。</span><span class="sxs-lookup"><span data-stu-id="0bba9-105">SQL Server PDW is a highly scalable appliance that delivers performance at low cost through massively parallel processing.</span></span> <span data-ttu-id="0bba9-106">有关 SQL Server PDW 的详细信息，请参阅网站 [SQL Server 2008 R2 Parallel Data Warehouse](https://go.microsoft.com/fwlink/?LinkId=150895)。</span><span class="sxs-lookup"><span data-stu-id="0bba9-106">For more information about SQL Server PDW, see the web site [SQL Server 2008 R2 Parallel Data Warehouse](https://go.microsoft.com/fwlink/?LinkId=150895).</span></span> <span data-ttu-id="0bba9-107">可以使用 SQL Server 身份验证连接到的数据仓库。</span><span class="sxs-lookup"><span data-stu-id="0bba9-107">You connect to the data warehouse by using SQL Server Authentication.</span></span> <span data-ttu-id="0bba9-108">若要连接到数据源，必须在计算机上安装适当的访问接口。</span><span class="sxs-lookup"><span data-stu-id="0bba9-108">To connect to a data source, you must have the appropriate provider installed on your computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0bba9-109">在此页中选择数据库时，将使用当前用户的凭据。</span><span class="sxs-lookup"><span data-stu-id="0bba9-109">The credentials of the current user are used when selecting a database in this page.</span></span> <span data-ttu-id="0bba9-110">但是，如果在“模拟信息”页中指定的用户没有足够的权限从所选数据库中读取，则导入将不会成功。</span><span class="sxs-lookup"><span data-stu-id="0bba9-110">However, import will not succeed if the user specified in the Impersonation Information page does not have sufficient privileges to read from the selected database.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="0bba9-111">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="0bba9-111">UI element list</span></span>  
 <span data-ttu-id="0bba9-112">**友好的连接名称**</span><span class="sxs-lookup"><span data-stu-id="0bba9-112">**Friendly connection name**</span></span>  
 <span data-ttu-id="0bba9-113">键入此数据源连接的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="0bba9-113">Type a unique name for this data source connection.</span></span> <span data-ttu-id="0bba9-114">这是必填字段。</span><span class="sxs-lookup"><span data-stu-id="0bba9-114">This is a required field.</span></span>  
  
 <span data-ttu-id="0bba9-115">**服务器名称**</span><span class="sxs-lookup"><span data-stu-id="0bba9-115">**Server name**</span></span>  
 <span data-ttu-id="0bba9-116">键入要连接到的服务器的名称或 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="0bba9-116">Type the name, or IP address, of the server to connect to.</span></span>  
  
 <span data-ttu-id="0bba9-117">**用户名**</span><span class="sxs-lookup"><span data-stu-id="0bba9-117">**User name**</span></span>  
 <span data-ttu-id="0bba9-118">为数据库连接指定用户名。</span><span class="sxs-lookup"><span data-stu-id="0bba9-118">Specify a user name for the database connection.</span></span>  
  
 <span data-ttu-id="0bba9-119">在为数据源构造连接字符串时，将使用该用户名。</span><span class="sxs-lookup"><span data-stu-id="0bba9-119">This user name is used when constructing the connection string for the data source.</span></span> <span data-ttu-id="0bba9-120">在“表格属性”窗口和“导入向导”中预览和筛选数据时，也使用这些凭据。</span><span class="sxs-lookup"><span data-stu-id="0bba9-120">These credentials are also used when previewing and filtering data in the Table Properties window and in the Import Wizard.</span></span> <span data-ttu-id="0bba9-121">这些凭据不用于导入或刷新数据；而是使用在“模拟信息”页中指定的 Windows 凭据。</span><span class="sxs-lookup"><span data-stu-id="0bba9-121">These credentials are not used to import or refresh data; the Windows credentials specified on the Impersonation Information page are used instead.</span></span>  
  
 <span data-ttu-id="0bba9-122">**密码**</span><span class="sxs-lookup"><span data-stu-id="0bba9-122">**Password**</span></span>  
 <span data-ttu-id="0bba9-123">为数据库连接指定密码。</span><span class="sxs-lookup"><span data-stu-id="0bba9-123">Specify a password for the database connection.</span></span>  
  
 <span data-ttu-id="0bba9-124">**保存密码**</span><span class="sxs-lookup"><span data-stu-id="0bba9-124">**Save my password**</span></span>  
 <span data-ttu-id="0bba9-125">指定是否存储已在“密码”\*\*\*\* 框中输入的密码。</span><span class="sxs-lookup"><span data-stu-id="0bba9-125">Specify whether the password you have entered in the **Password** box is stored.</span></span>  
  
 <span data-ttu-id="0bba9-126">**数据库名称**</span><span class="sxs-lookup"><span data-stu-id="0bba9-126">**Database name**</span></span>  
 <span data-ttu-id="0bba9-127">从数据库列表中选择数据库。</span><span class="sxs-lookup"><span data-stu-id="0bba9-127">Select a database from the list of databases.</span></span>  
  
 <span data-ttu-id="0bba9-128">**高级**</span><span class="sxs-lookup"><span data-stu-id="0bba9-128">**Advanced**</span></span>  
 <span data-ttu-id="0bba9-129">使用 "**设置高级属性**" 对话框设置附加的连接属性。</span><span class="sxs-lookup"><span data-stu-id="0bba9-129">Set additional connection properties by using the **Set Advanced Properties** dialog box.</span></span> <span data-ttu-id="0bba9-130">有关详细信息，请参阅[设置高级属性 (SSAS)](set-advanced-properties-ssas.md)。</span><span class="sxs-lookup"><span data-stu-id="0bba9-130">For more information, see [Set Advanced Properties &#40;SSAS&#41;](set-advanced-properties-ssas.md).</span></span>  
  
 <span data-ttu-id="0bba9-131">**测试连接**</span><span class="sxs-lookup"><span data-stu-id="0bba9-131">**Test Connection**</span></span>  
 <span data-ttu-id="0bba9-132">使用当前设置尝试建立与数据源的连接。</span><span class="sxs-lookup"><span data-stu-id="0bba9-132">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="0bba9-133">将显示一个消息，指示连接是否成功。</span><span class="sxs-lookup"><span data-stu-id="0bba9-133">A message displays and indicates whether the connection is successful.</span></span>  
  
  
