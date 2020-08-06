---
title: 为表格模型数据库配置内存中或 DirectQuery 访问权限 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a5d439a9-5be1-4145-90e8-90777d80e98b
author: minewiskan
ms.author: owend
ms.openlocfilehash: a607bc6c11f35736487932bdf10d239afc8b5355
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687243"
---
# <a name="configure-in-memory-or-directquery-access-for-a-tabular-model-database"></a><span data-ttu-id="1727a-102">为表格模型数据库配置内存中或 DirectQuery 访问</span><span class="sxs-lookup"><span data-stu-id="1727a-102">Configure In-Memory or DirectQuery Access for a Tabular Model Database</span></span>
  <span data-ttu-id="1727a-103">本主题介绍如何更改已部署的表格模型的连接属性，以便能在直接查询模式下使用模型。</span><span class="sxs-lookup"><span data-stu-id="1727a-103">This topic describes how to change the connection properties of a tabular model that has already been deployed, to enable use of the model in Direct Query mode.</span></span>  
  
 <span data-ttu-id="1727a-104">有关这些属性以及最常见方案的配置的详细信息，请参阅[DirectQuery 部署方案 &#40;SSAS 表格&#41;](../directquery-deployment-scenarios-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="1727a-104">For more information about these properties, and configuration for the most common scenarios, see [DirectQuery Deployment Scenarios &#40;SSAS Tabular&#41;](../directquery-deployment-scenarios-ssas-tabular.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1727a-105">要求</span><span class="sxs-lookup"><span data-stu-id="1727a-105">Requirements</span></span>  
 <span data-ttu-id="1727a-106">允许在表格模型中使用直接查询模式是一个多步骤过程。</span><span class="sxs-lookup"><span data-stu-id="1727a-106">Enabling the use of Direct Query mode on a tabular model is a multistep process.</span></span> <span data-ttu-id="1727a-107">必须具备以下条件：</span><span class="sxs-lookup"><span data-stu-id="1727a-107">You must:</span></span>  
  
1.  <span data-ttu-id="1727a-108">确保该模型具有的功能不会导致直接查询模式中出现验证错误。</span><span class="sxs-lookup"><span data-stu-id="1727a-108">Ensure that the model does not have features which might cause validation errors in Direct Query mode.</span></span>  
  
2.  <span data-ttu-id="1727a-109">更改模型中的存储模式以支持直接查询。</span><span class="sxs-lookup"><span data-stu-id="1727a-109">Change the storage mode on the model to support Direct Query.</span></span>  
  
3.  <span data-ttu-id="1727a-110">在支持混合或纯直接查询模式中的查询的模式下部署该模型。</span><span class="sxs-lookup"><span data-stu-id="1727a-110">Deploy the model in a mode that supports queries in either a hybrid or pure Direct Query mode.</span></span>  
  
4.  <span data-ttu-id="1727a-111">在已部署的数据库上编辑连接字符串以支持直接查询模式。</span><span class="sxs-lookup"><span data-stu-id="1727a-111">Edit the connection string on the deployed database to support Direct Query mode.</span></span>  
  
 <span data-ttu-id="1727a-112">本主题假定您已创建并验证您的模型，且只需从客户端（如 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]）启用直接查询访问。</span><span class="sxs-lookup"><span data-stu-id="1727a-112">This topic assumes that you have created and validated your model, and only need to enable Direct Query access from a client such as [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="1727a-113">过程</span><span class="sxs-lookup"><span data-stu-id="1727a-113">Procedure</span></span>  
  
#### <a name="change-the-connection-string-properties-of-the-model"></a><span data-ttu-id="1727a-114">更改模型的连接字符串属性</span><span class="sxs-lookup"><span data-stu-id="1727a-114">Change the Connection String Properties of the Model</span></span>  
  
1.  <span data-ttu-id="1727a-115">在 SQL Server Management Studio 中，打开已将模型部署到的实例。</span><span class="sxs-lookup"><span data-stu-id="1727a-115">In SQL Server Management Studio, open the instance to which you deployed the model.</span></span>  
  
2.  <span data-ttu-id="1727a-116">在对象资源管理器中，右键单击 model 数据库的名称，然后选择 "**属性**"。</span><span class="sxs-lookup"><span data-stu-id="1727a-116">In Object Explorer, right-click the name of the model database, and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="1727a-117">找到 " **DirectQueryMode**" 属性。</span><span class="sxs-lookup"><span data-stu-id="1727a-117">Locate the property, **DirectQueryMode**.</span></span> <span data-ttu-id="1727a-118">若要允许使用关系数据源，则必须将此属性设置为下列值之一：</span><span class="sxs-lookup"><span data-stu-id="1727a-118">To enable use of the relational data source, this property must be set to one of these values:</span></span>  
  
    -   <span data-ttu-id="1727a-119">**DirectQuery**</span><span class="sxs-lookup"><span data-stu-id="1727a-119">**DirectQuery**</span></span>  
  
    -   <span data-ttu-id="1727a-120">**InMemoryWithDirectQuery**</span><span class="sxs-lookup"><span data-stu-id="1727a-120">**InMemoryWithDirectQuery**</span></span>  
  
    -   <span data-ttu-id="1727a-121">**DirectQueryWithInMemory**</span><span class="sxs-lookup"><span data-stu-id="1727a-121">**DirectQueryWithInMemory**</span></span>  
  
  
