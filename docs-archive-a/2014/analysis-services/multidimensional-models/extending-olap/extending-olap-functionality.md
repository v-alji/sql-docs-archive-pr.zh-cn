---
title: 扩展 OLAP 功能 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 49a17ff3-94e9-4969-84fc-37d49e63933b
author: minewiskan
ms.author: owend
ms.openlocfilehash: d64d1ac46e2571aa6f8065a8ea42e4cc43aa589e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591601"
---
# <a name="extending-olap-functionality"></a><span data-ttu-id="f291e-102">扩展 OLAP 功能</span><span class="sxs-lookup"><span data-stu-id="f291e-102">Extending OLAP functionality</span></span>
  <span data-ttu-id="f291e-103">作为一名程序员，您可以通过编写程序集、个性化扩展插件和存储过程来扩展 Analysis Services，以便提供您要在多个数据库应用程序中使用并重新确定其用途的功能。</span><span class="sxs-lookup"><span data-stu-id="f291e-103">As a programmer, you can extend Analysis Services by writing assemblies, personalized extensions, and stored procedures that provide functionality you want to use and repurpose in multiple database applications.</span></span> <span data-ttu-id="f291e-104">程序集用于通过向 MDX 语言添加新的过程和函数或通过个性化外接程序来扩展多维模型功能。</span><span class="sxs-lookup"><span data-stu-id="f291e-104">Assemblies are used to extend multidimensional models functionality by adding new procedures and functions to the MDX language or by means of the personalization addin.</span></span>  
  
 <span data-ttu-id="f291e-105">存储过程可用于调用外部例程，并通过允许一次性开发常用代码并将其存储在单个位置来简化 Analysis Services 数据库的开发和实现。</span><span class="sxs-lookup"><span data-stu-id="f291e-105">Stored procedures can be used to call external routines, simplifying Analysis Services database development and implementation by allowing common code to be developed once and stored in a single location.</span></span> <span data-ttu-id="f291e-106">存储过程可用来向应用程序中添加 MDX 的本机功能未提供的商业功能。</span><span class="sxs-lookup"><span data-stu-id="f291e-106">Stored procedures can be used to add business functionality to your applications that is not provided by the native functionality of MDX.</span></span>  
  
 <span data-ttu-id="f291e-107">个性化设置是添加到多维数据集的自定义对象，可提供随用户的不同而不同的行为。</span><span class="sxs-lookup"><span data-stu-id="f291e-107">Personalizations are custom objects that you add to a cube to provide a behavior that varies by user.</span></span> <span data-ttu-id="f291e-108">个性化设置并不是多维数据集中的永久对象，而是在用户会话期间客户端应用程序动态应用的对象。</span><span class="sxs-lookup"><span data-stu-id="f291e-108">Personalizations are not permanent objects in the cube, but are objects that the client application applies dynamically during the user's session.</span></span> <span data-ttu-id="f291e-109">例如，根据访问数据的人员更改货币值的币种、提供单个 KPI 或为网上购物的老客户提供针对性建议的列表。</span><span class="sxs-lookup"><span data-stu-id="f291e-109">Examples include changing the currency of a monetary value depending on the person accessing the data, providing individualized KPIs, or a targeted suggestion list for regular customers who purchase online.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f291e-110">本节内容</span><span class="sxs-lookup"><span data-stu-id="f291e-110">In This Section</span></span>  
 [<span data-ttu-id="f291e-111">通过个性化设置扩展 OLAP</span><span class="sxs-lookup"><span data-stu-id="f291e-111">Extending OLAP through personalizations</span></span>](extending-olap-through-personalizations.md)  
  
 [<span data-ttu-id="f291e-112">Analysis Services 个性化设置扩展</span><span class="sxs-lookup"><span data-stu-id="f291e-112">Analysis Services Personalization Extensions</span></span>](analysis-services-personalization-extensions.md)  
  
 [<span data-ttu-id="f291e-113">定义存储过程</span><span class="sxs-lookup"><span data-stu-id="f291e-113">Defining Stored Procedures</span></span>](../../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
