---
title: " (SSAS) 连接到 Azure SQL 数据库 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connsqlazure.f1
ms.assetid: 4e0344e9-1822-4698-ad22-05f1f341ced7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 91ae6f0f5ab95d3013b6348bd43ddb746fff1c22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579205"
---
# <a name="connect-to-an-azure-sql-database-ssas"></a><span data-ttu-id="06cd5-102">连接到 Azure SQL Database (SSAS)</span><span class="sxs-lookup"><span data-stu-id="06cd5-102">Connect to an Azure SQL Database (SSAS)</span></span>
  <span data-ttu-id="06cd5-103">“表导入向导”\*\*\*\* 的这一页可用于连接到 [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="06cd5-103">This page of the **Table Import Wizard** enables you to connect to a [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)].</span></span> <span data-ttu-id="06cd5-104">若要从 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]访问该向导，请在 **“模型”** 菜单上，单击 **“从数据源导入”**。</span><span class="sxs-lookup"><span data-stu-id="06cd5-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="06cd5-105">若要连接到 Azure DataMarket 数据集，请参阅[连接到报表或数据馈送 (SSAS)](connect-to-a-report-or-data-feed-ssas.md)。</span><span class="sxs-lookup"><span data-stu-id="06cd5-105">If you are connecting to an Azure DataMarket dataset, see [Connect to a Report or Data Feed &#40;SSAS&#41;](connect-to-a-report-or-data-feed-ssas.md).</span></span>  
  
 <span data-ttu-id="06cd5-106">[!INCLUDE[ssSDS](../includes/sssds-md.md)] 是一个托管的关系数据库，您可以使用 SQL Server 身份验证连接到该数据库。</span><span class="sxs-lookup"><span data-stu-id="06cd5-106">The [!INCLUDE[ssSDS](../includes/sssds-md.md)] is a hosted, relational database that you connect to by using SQL Server Authentication.</span></span> <span data-ttu-id="06cd5-107">有关 [!INCLUDE[ssSDS](../includes/sssds-md.md)]的详细信息，请参阅网站 [SQL Database](https://go.microsoft.com/fwlink/?LinkID=157856)。</span><span class="sxs-lookup"><span data-stu-id="06cd5-107">For more information about [!INCLUDE[ssSDS](../includes/sssds-md.md)], see the web site [SQL Database](https://go.microsoft.com/fwlink/?LinkID=157856).</span></span> <span data-ttu-id="06cd5-108">若要连接到数据源，必须在计算机上安装适当的访问接口。</span><span class="sxs-lookup"><span data-stu-id="06cd5-108">To connect to a data source, you must have the appropriate provider installed on your computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="06cd5-109">在此页中选择数据库时，将使用当前用户的凭据。</span><span class="sxs-lookup"><span data-stu-id="06cd5-109">The credentials of the current user are used when selecting a database in this page.</span></span> <span data-ttu-id="06cd5-110">但是，如果在“模拟信息”页中指定的用户没有足够的权限从所选数据库中读取，则导入将不会成功。</span><span class="sxs-lookup"><span data-stu-id="06cd5-110">However, import will not succeed if the user specified in the Impersonation Information page does not have sufficient privileges to read from the selected database.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="06cd5-111">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="06cd5-111">UI element list</span></span>  
 <span data-ttu-id="06cd5-112">**友好的连接名称**</span><span class="sxs-lookup"><span data-stu-id="06cd5-112">**Friendly connection name**</span></span>  
 <span data-ttu-id="06cd5-113">键入此数据源连接的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="06cd5-113">Type a unique name for this data source connection.</span></span> <span data-ttu-id="06cd5-114">这是必填字段。</span><span class="sxs-lookup"><span data-stu-id="06cd5-114">This is a required field.</span></span>  
  
 <span data-ttu-id="06cd5-115">**服务器名称**</span><span class="sxs-lookup"><span data-stu-id="06cd5-115">**Server name**</span></span>  
 <span data-ttu-id="06cd5-116">键入要连接到的服务器的名称或 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="06cd5-116">Type the name, or IP address, of the server to connect to.</span></span>  
  
 <span data-ttu-id="06cd5-117">**用户名**</span><span class="sxs-lookup"><span data-stu-id="06cd5-117">**User name**</span></span>  
 <span data-ttu-id="06cd5-118">为数据库连接指定用户名。</span><span class="sxs-lookup"><span data-stu-id="06cd5-118">Specify a user name for the database connection.</span></span>  
  
 <span data-ttu-id="06cd5-119">在为数据源构造连接字符串时，将使用该用户名。</span><span class="sxs-lookup"><span data-stu-id="06cd5-119">This user name is used when constructing the connection string for the data source.</span></span> <span data-ttu-id="06cd5-120">在“表格属性”窗口和“导入向导”中预览和筛选数据时，也使用这些凭据。</span><span class="sxs-lookup"><span data-stu-id="06cd5-120">These credentials are also used when previewing and filtering data in the Table Properties window and in the Import Wizard.</span></span> <span data-ttu-id="06cd5-121">这些凭据不用于导入或刷新数据；而是使用在“模拟信息”页中指定的 Windows 凭据。</span><span class="sxs-lookup"><span data-stu-id="06cd5-121">These credentials are not used to import or refresh data; the Windows credentials specified on the Impersonation Information page are used instead.</span></span>  
  
 <span data-ttu-id="06cd5-122">**密码**</span><span class="sxs-lookup"><span data-stu-id="06cd5-122">**Password**</span></span>  
 <span data-ttu-id="06cd5-123">为数据库连接指定密码。</span><span class="sxs-lookup"><span data-stu-id="06cd5-123">Specify a password for the database connection.</span></span>  
  
 <span data-ttu-id="06cd5-124">**保存密码**</span><span class="sxs-lookup"><span data-stu-id="06cd5-124">**Save my password**</span></span>  
 <span data-ttu-id="06cd5-125">指定是否存储已在“密码”\*\*\*\* 框中输入的密码。</span><span class="sxs-lookup"><span data-stu-id="06cd5-125">Specify whether the password you have entered in the **Password** box is stored.</span></span>  
  
 <span data-ttu-id="06cd5-126">**数据库名称**</span><span class="sxs-lookup"><span data-stu-id="06cd5-126">**Database name**</span></span>  
 <span data-ttu-id="06cd5-127">从数据库列表中选择数据库。</span><span class="sxs-lookup"><span data-stu-id="06cd5-127">Select a database from the list of databases.</span></span>  
  
 <span data-ttu-id="06cd5-128">**高级**</span><span class="sxs-lookup"><span data-stu-id="06cd5-128">**Advanced**</span></span>  
 <span data-ttu-id="06cd5-129">使用 "**设置高级属性**" 对话框设置附加的连接属性。</span><span class="sxs-lookup"><span data-stu-id="06cd5-129">Set additional connection properties by using the **Set Advanced Properties** dialog box.</span></span> <span data-ttu-id="06cd5-130">有关详细信息，请参阅[设置高级属性 (SSAS)](set-advanced-properties-ssas.md)。</span><span class="sxs-lookup"><span data-stu-id="06cd5-130">For more information, see [Set Advanced Properties &#40;SSAS&#41;](set-advanced-properties-ssas.md).</span></span>  
  
 <span data-ttu-id="06cd5-131">**测试连接**</span><span class="sxs-lookup"><span data-stu-id="06cd5-131">**Test Connection**</span></span>  
 <span data-ttu-id="06cd5-132">使用当前设置尝试建立与数据源的连接。</span><span class="sxs-lookup"><span data-stu-id="06cd5-132">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="06cd5-133">将显示一个消息，指示连接是否成功。</span><span class="sxs-lookup"><span data-stu-id="06cd5-133">A message is displayed indicating whether the connection is successful.</span></span>  
  
  
