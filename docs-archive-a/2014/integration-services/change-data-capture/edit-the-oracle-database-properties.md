---
title: 编辑 Oracle 数据库属性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- oraProp
ms.assetid: 58dc99f1-ee6b-4508-bb66-2bc589611ff7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d3cad2735e6cd6095f9730f3b4e7228526451d34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580331"
---
# <a name="edit-the-oracle-database-properties"></a><span data-ttu-id="0d473-102">编辑 Oracle 数据库属性</span><span class="sxs-lookup"><span data-stu-id="0d473-102">Edit the Oracle Database Properties</span></span>
  <span data-ttu-id="0d473-103">使用属性编辑器中的“Oracle”选项卡可对在新建实例向导的“创建 CDC 数据库”页中提供的说明进行更改，以及对 Oracle 日志挖掘数据库连接信息进行更改。</span><span class="sxs-lookup"><span data-stu-id="0d473-103">Use the Oracle tab in the Properties editor to make changes to the description you provided in the Create CDC database page in the New Instance wizard and to make changes to the Oracle Log Mining database connection information.</span></span>  
  
 <span data-ttu-id="0d473-104">下表对 **“Oracle”** 选项卡中的信息进行了说明。</span><span class="sxs-lookup"><span data-stu-id="0d473-104">The following describes the information in the **Oracle** tab.</span></span>  
  
 <span data-ttu-id="0d473-105">**名称**</span><span class="sxs-lookup"><span data-stu-id="0d473-105">**Name**</span></span>  
 <span data-ttu-id="0d473-106">在新建实例向导的“创建 CDC 数据库”页中输入的 CDC 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="0d473-106">The name of the CDC Instance that you entered in the Create CDC Database page in the New Instance wizard.</span></span> <span data-ttu-id="0d473-107">此字段是只读的，不能编辑此信息。</span><span class="sxs-lookup"><span data-stu-id="0d473-107">This field is read only and you cannot edit this information.</span></span>  
  
 <span data-ttu-id="0d473-108">**说明**</span><span class="sxs-lookup"><span data-stu-id="0d473-108">**Description**</span></span>  
 <span data-ttu-id="0d473-109">您可以编辑新实例的说明或者添加说明（如果您在创建 CDC 实例时未添加说明）。</span><span class="sxs-lookup"><span data-stu-id="0d473-109">You can edit the description of the new instance or add one if you did not do so when creating the CDC Instance.</span></span>  
  
 <span data-ttu-id="0d473-110">**Oracle 连接字符串**</span><span class="sxs-lookup"><span data-stu-id="0d473-110">**Oracle Connect String**</span></span>  
 <span data-ttu-id="0d473-111">正使用 Oracle 数据库的计算机的 Oracle 连接字符串。</span><span class="sxs-lookup"><span data-stu-id="0d473-111">The Oracle connect string to the computer with the Oracle database you are using.</span></span> <span data-ttu-id="0d473-112">此字段是只读的，不能编辑此信息。</span><span class="sxs-lookup"><span data-stu-id="0d473-112">This field is read only and you cannot edit this information.</span></span> <span data-ttu-id="0d473-113">其原因在于，对连接字符串的某些更改可能会将 Oracle CDC 实例完全指向其他 Oracle 数据库，从而破坏在 **cdc.xdbcdc_config** 表中存储的 CDC 实例状态。</span><span class="sxs-lookup"><span data-stu-id="0d473-113">This is because some changes to the connect string may point the Oracle CDC Instance to another Oracle database entirely, corrupting the CDC Instance state as stored in the **cdc.xdbcdc_config** table.</span></span> <span data-ttu-id="0d473-114">如果需要较小的更改，您可以使用 SQL Server Management Studio 直接在配置表中更改连接字符串。</span><span class="sxs-lookup"><span data-stu-id="0d473-114">If minor changes are needed, you can change the connect string directly in the configuration table using SQL Server Management Studio.</span></span>  
  
 <span data-ttu-id="0d473-115">**Oracle 日志挖掘身份验证**</span><span class="sxs-lookup"><span data-stu-id="0d473-115">**Oracle Log Mining Authentication**</span></span>  
 <span data-ttu-id="0d473-116">若要为包含日志挖掘器的 Oracle 数据库输入身份验证凭据，请在“身份验证”  下选择以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="0d473-116">To enter the authentication credentials for the Oracle database that contains the log miner, select one of the following under **Authentication**:</span></span>  
  
-   <span data-ttu-id="0d473-117">**Windows 身份验证**：选择此选项可使用当前的 Windows 域凭据。</span><span class="sxs-lookup"><span data-stu-id="0d473-117">**Windows Authentication**: Select this to use the current Windows domain credentials.</span></span> <span data-ttu-id="0d473-118">只有当 Oracle 数据库配置为使用 Windows 身份验证时，才可以使用此选项。</span><span class="sxs-lookup"><span data-stu-id="0d473-118">You can use this option only if the Oracle database is configured to work with Windows authentication.</span></span>  
  
-   <span data-ttu-id="0d473-119">**Oracle 身份验证**：如果选择此选项，则必须在您连接到的 Oracle 数据库中为用户键入 **“用户名”** 和 **“密码”** 。</span><span class="sxs-lookup"><span data-stu-id="0d473-119">**Oracle Authentication**: If you select this option, you must type the **User Name** and **Password** for the user in the Oracle database you are connecting to.</span></span>  
  
 <span data-ttu-id="0d473-120">您可以在查看器中查看 Oracle 数据库属性。</span><span class="sxs-lookup"><span data-stu-id="0d473-120">You can view the Oracle database properties in the viewer.</span></span> <span data-ttu-id="0d473-121">在使用查看器时，信息是只读的。</span><span class="sxs-lookup"><span data-stu-id="0d473-121">When using the viewer the information is read only.</span></span> <span data-ttu-id="0d473-122">查看器还在表中包括捕获列的列表。</span><span class="sxs-lookup"><span data-stu-id="0d473-122">The viewer also includes a list of the captured columns in the table.</span></span> <span data-ttu-id="0d473-123">有关如何访问查看器的信息，请参阅 [How to Manage a CDC Instance](manage-a-cdc-instance.md)。</span><span class="sxs-lookup"><span data-stu-id="0d473-123">For information on how to access the viewer, see [How to Manage a CDC Instance](manage-a-cdc-instance.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d473-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0d473-124">See Also</span></span>  
 <span data-ttu-id="0d473-125">[如何从 CDC 设计器控制台管理 CDC 服务](how-to-manage-a-cdc-service-from-the-cdc-designer-console.md) </span><span class="sxs-lookup"><span data-stu-id="0d473-125">[How to Manage a CDC Service from the CDC Designer Console](how-to-manage-a-cdc-service-from-the-cdc-designer-console.md) </span></span>  
 <span data-ttu-id="0d473-126">[连接到 Oracle 源数据库](connect-to-an-oracle-source-database.md) </span><span class="sxs-lookup"><span data-stu-id="0d473-126">[Connect to an Oracle Source Database](connect-to-an-oracle-source-database.md) </span></span>  
 [<span data-ttu-id="0d473-127">连接到 Oracle</span><span class="sxs-lookup"><span data-stu-id="0d473-127">Connect to Oracle</span></span>](connect-to-oracle.md)  
  
  
