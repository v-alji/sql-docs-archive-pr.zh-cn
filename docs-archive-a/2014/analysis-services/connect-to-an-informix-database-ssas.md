---
title: " (SSAS) 连接到 Informix 数据库 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.conninformixdb.f1
ms.assetid: b01d537c-1c04-4d7d-9146-051c249b08e4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 35c7263ce9b0432802cd24b6df9165151b279d83
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579209"
---
# <a name="connect-to-an-informix-database-ssas"></a><span data-ttu-id="1c379-102">连接到 Informix 数据库 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="1c379-102">Connect to an Informix Database (SSAS)</span></span>
  <span data-ttu-id="1c379-103">**“表导入向导”** 的这一页可用于指定用于连接到 Informix 数据库的设置。</span><span class="sxs-lookup"><span data-stu-id="1c379-103">This page of the **Table Import Wizard** enables you to specify settings to connect to an Informix database.</span></span> <span data-ttu-id="1c379-104">若要从 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]访问该向导，请在 **“模型”** 菜单上，单击 **“从数据源导入”**。</span><span class="sxs-lookup"><span data-stu-id="1c379-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="1c379-105">若要连接到数据源，必须在计算机上安装适当的访问接口。</span><span class="sxs-lookup"><span data-stu-id="1c379-105">To connect to a data source, you must have the appropriate provider installed on your computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1c379-106">在此页中选择数据库时，将使用当前用户的凭据。</span><span class="sxs-lookup"><span data-stu-id="1c379-106">The credentials of the current user are used when selecting a database in this page.</span></span> <span data-ttu-id="1c379-107">但是，如果在“模拟信息”页中指定的用户没有足够的权限从所选数据库中读取，则导入将不会成功。</span><span class="sxs-lookup"><span data-stu-id="1c379-107">However, import will not succeed if the user specified in the Impersonation Information page does not have sufficient privileges to read from the selected database.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="1c379-108">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="1c379-108">UI element list</span></span>  
 <span data-ttu-id="1c379-109">**友好的连接名称**</span><span class="sxs-lookup"><span data-stu-id="1c379-109">**Friendly connection name**</span></span>  
 <span data-ttu-id="1c379-110">键入此数据源连接的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="1c379-110">Type a unique name for this data source connection.</span></span> <span data-ttu-id="1c379-111">这是必填字段。</span><span class="sxs-lookup"><span data-stu-id="1c379-111">This is a required field.</span></span>  
  
 <span data-ttu-id="1c379-112">**服务器名称**</span><span class="sxs-lookup"><span data-stu-id="1c379-112">**Server name**</span></span>  
 <span data-ttu-id="1c379-113">键入或选择要连接到的服务器实例的名称。</span><span class="sxs-lookup"><span data-stu-id="1c379-113">Type or select the name of the server instance to connect to.</span></span>  
  
 <span data-ttu-id="1c379-114">**用户名**</span><span class="sxs-lookup"><span data-stu-id="1c379-114">**User name**</span></span>  
 <span data-ttu-id="1c379-115">为数据库连接指定用户名。</span><span class="sxs-lookup"><span data-stu-id="1c379-115">Specify a user name for the database connection.</span></span>  
  
 <span data-ttu-id="1c379-116">在为数据源构造连接字符串时，将使用该用户名。</span><span class="sxs-lookup"><span data-stu-id="1c379-116">This user name is used when constructing the connection string for the data source.</span></span> <span data-ttu-id="1c379-117">在“表格属性”窗口和“导入向导”中预览和筛选数据时，也使用这些凭据。</span><span class="sxs-lookup"><span data-stu-id="1c379-117">These credentials are also used when previewing and filtering data in the Table Properties window and in the Import Wizard.</span></span> <span data-ttu-id="1c379-118">这些凭据不用于导入或刷新数据；而是使用在“模拟信息”页中指定的 Windows 凭据。</span><span class="sxs-lookup"><span data-stu-id="1c379-118">These credentials are not used to import or refresh data; the Windows credentials specified on the Impersonation Information page are used instead.</span></span>  
  
 <span data-ttu-id="1c379-119">**密码**</span><span class="sxs-lookup"><span data-stu-id="1c379-119">**Password**</span></span>  
 <span data-ttu-id="1c379-120">为数据库连接指定密码。</span><span class="sxs-lookup"><span data-stu-id="1c379-120">Specify a password for the database connection.</span></span>  
  
 <span data-ttu-id="1c379-121">**保存密码**</span><span class="sxs-lookup"><span data-stu-id="1c379-121">**Save my password**</span></span>  
 <span data-ttu-id="1c379-122">指定是否存储已在“密码”\*\*\*\* 框中输入的密码。</span><span class="sxs-lookup"><span data-stu-id="1c379-122">Specify whether the password you have entered in the **Password** box is stored.</span></span>  
  
 <span data-ttu-id="1c379-123">**高级**</span><span class="sxs-lookup"><span data-stu-id="1c379-123">**Advanced**</span></span>  
 <span data-ttu-id="1c379-124">使用 "**设置高级属性**" 对话框设置附加的连接属性。</span><span class="sxs-lookup"><span data-stu-id="1c379-124">Set additional connection properties by using the **Set Advanced Properties** dialog box.</span></span> <span data-ttu-id="1c379-125">有关详细信息，请参阅[设置高级属性 (SSAS)](set-advanced-properties-ssas.md)。</span><span class="sxs-lookup"><span data-stu-id="1c379-125">For more information, see [Set Advanced Properties &#40;SSAS&#41;](set-advanced-properties-ssas.md).</span></span>  
  
 <span data-ttu-id="1c379-126">**测试连接**</span><span class="sxs-lookup"><span data-stu-id="1c379-126">**Test Connection**</span></span>  
 <span data-ttu-id="1c379-127">使用当前设置尝试建立与数据源的连接。</span><span class="sxs-lookup"><span data-stu-id="1c379-127">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="1c379-128">将显示一个消息，指示连接是否成功。</span><span class="sxs-lookup"><span data-stu-id="1c379-128">A message is displayed indicating whether the connection is successful.</span></span>  
  
  
