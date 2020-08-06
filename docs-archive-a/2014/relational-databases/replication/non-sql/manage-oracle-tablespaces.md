---
title: 管理 Oracle 表空间 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], managing tablespaces
- tablespaces [SQL Server replication]
ms.assetid: b8ea6c3b-01d6-4efc-bbfb-03b264530bbd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a3624aed38a7a5bf75e0c0807aa8d3657156264f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690536"
---
# <a name="manage-oracle-tablespaces"></a><span data-ttu-id="520c5-102">管理 Oracle 表空间</span><span class="sxs-lookup"><span data-stu-id="520c5-102">Manage Oracle Tablespaces</span></span>
  <span data-ttu-id="520c5-103">表空间是一个数据库存储单元，大致相当于 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的文件组。</span><span class="sxs-lookup"><span data-stu-id="520c5-103">A tablespace is a unit of database storage that is roughly equivalent to a file group in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="520c5-104">表空间允许存储和管理各个组内的数据库对象。</span><span class="sxs-lookup"><span data-stu-id="520c5-104">Tablespaces allow storage and management of database objects within individual groups.</span></span> <span data-ttu-id="520c5-105">有关详细信息，请参阅 Oracle 文档。</span><span class="sxs-lookup"><span data-stu-id="520c5-105">For more information, see the Oracle documentation.</span></span>  
  
 <span data-ttu-id="520c5-106">如果将表配置为 Oracle 发布的一部分，则可以选择指定在存储复制记录信息时使用现有的 Oracle 表空间。</span><span class="sxs-lookup"><span data-stu-id="520c5-106">When you configure a table as part of an Oracle publication, you can optionally specify an existing Oracle tablespace to be used when storing replication logging information.</span></span> <span data-ttu-id="520c5-107">如果未指定，则复制对象的表空间就是与配置发布服务器时配置的复制管理用户架构相关联的默认表空间。</span><span class="sxs-lookup"><span data-stu-id="520c5-107">If unspecified, the tablespace for the replication objects is the default tablespace associated with the replication administrative user schema that was configured when configuring the Publisher.</span></span>  
  
 <span data-ttu-id="520c5-108">**为项目记录表指定表空间**：</span><span class="sxs-lookup"><span data-stu-id="520c5-108">**To specify a tablespace for an article logging table**:</span></span>  
  
-   <span data-ttu-id="520c5-109">在 **“项目属性”** 对话框中指定表空间。</span><span class="sxs-lookup"><span data-stu-id="520c5-109">Specify a tablespace in the **Article Properties** dialog box.</span></span> <span data-ttu-id="520c5-110">有关访问此对话框的详细信息，请参阅 [View and Modify Publication Properties](../publish/view-and-modify-publication-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="520c5-110">For more information about accessing this dialog box, see [View and Modify Publication Properties](../publish/view-and-modify-publication-properties.md).</span></span>  
  
-   <span data-ttu-id="520c5-111">使用 [sp_changearticle (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="520c5-111">Use [sp_changearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql).</span></span> <span data-ttu-id="520c5-112">若要使用 **sp_changearticle**，请指定下列内容：</span><span class="sxs-lookup"><span data-stu-id="520c5-112">To use **sp_changearticle**, specify the following:</span></span>  
  
    -   <span data-ttu-id="520c5-113">参数的 Oracle 发布服务器的名称 **@publisher** 。</span><span class="sxs-lookup"><span data-stu-id="520c5-113">The name of the Oracle Publisher for the parameter **@publisher**.</span></span>  
  
    -   <span data-ttu-id="520c5-114">参数的 Oracle 发布的名称 **@publication** 。</span><span class="sxs-lookup"><span data-stu-id="520c5-114">The name of the Oracle publication for the parameter **@publication**.</span></span>  
  
    -   <span data-ttu-id="520c5-115">参数的项目名称 **@article** 。</span><span class="sxs-lookup"><span data-stu-id="520c5-115">The name of the article for the parameter **@article**.</span></span>  
  
    -   <span data-ttu-id="520c5-116">参数的 "表空间" 的值 **@property** 。</span><span class="sxs-lookup"><span data-stu-id="520c5-116">A value of 'tablespace' for the parameter **@property**.</span></span>  
  
    -   <span data-ttu-id="520c5-117">参数表空间的名称 **@value** 。</span><span class="sxs-lookup"><span data-stu-id="520c5-117">The name of the tablespace for the parameter **@value**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="520c5-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="520c5-118">See Also</span></span>  
 <span data-ttu-id="520c5-119">[配置 Oracle 发布服务器](configure-an-oracle-publisher.md) </span><span class="sxs-lookup"><span data-stu-id="520c5-119">[Configure an Oracle Publisher](configure-an-oracle-publisher.md) </span></span>  
 [<span data-ttu-id="520c5-120">在 Oracle 发布服务器上创建的对象</span><span class="sxs-lookup"><span data-stu-id="520c5-120">Objects Created on the Oracle Publisher</span></span>](objects-created-on-the-oracle-publisher.md)  
  
  
