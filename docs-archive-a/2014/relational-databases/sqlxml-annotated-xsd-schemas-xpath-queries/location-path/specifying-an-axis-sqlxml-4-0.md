---
title: " (SQLXML 4.0) 指定轴 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], axes
- XPath queries [SQLXML], location paths
- self axis
- attribute axis [SQLXML]
- axis [SQLXML]
- child axis
- parent axis
- location path for XPath query
- axes [SQLXML]
ms.assetid: 65631795-3389-40cf-90ea-85e9438956c5
author: rothja
ms.author: jroth
ms.openlocfilehash: 5e43281fe31d323a7eea19e749b80b59458752b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587283"
---
# <a name="specifying-an-axis-sqlxml-40"></a><span data-ttu-id="f431c-102">指定轴 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="f431c-102">Specifying an Axis (SQLXML 4.0)</span></span>
    
-   <span data-ttu-id="f431c-103">轴指定根据位置步骤和上下文节点选择的节点之间的树关系。</span><span class="sxs-lookup"><span data-stu-id="f431c-103">The axis specifies the tree relationship between the nodes selected by the location step and the context node.</span></span> <span data-ttu-id="f431c-104">支持以下轴：`child`</span><span class="sxs-lookup"><span data-stu-id="f431c-104">The following axes are supported:  `child`</span></span>  
  
     <span data-ttu-id="f431c-105">包含上下文节点的子级。</span><span class="sxs-lookup"><span data-stu-id="f431c-105">Contains the child of the context node.</span></span>  
  
     <span data-ttu-id="f431c-106">以下 XPath 表达式 (位置路径) 从当前上下文节点选择所有 **\<Customer>** 子级：</span><span class="sxs-lookup"><span data-stu-id="f431c-106">The following XPath expression (location path) selects from the current context node all the **\<Customer>** children:</span></span>  
  
    ```  
    child::Customer  
    ```  
  
     <span data-ttu-id="f431c-107">在下面的 XPath 查询中，`child` 为轴。</span><span class="sxs-lookup"><span data-stu-id="f431c-107">In the following XPath query, `child` is the axis.</span></span> <span data-ttu-id="f431c-108">`Customer` 是节点测试。</span><span class="sxs-lookup"><span data-stu-id="f431c-108">`Customer` is the node test.</span></span>  
  
-   `parent`  
  
     <span data-ttu-id="f431c-109">包含上下文节点的父级。</span><span class="sxs-lookup"><span data-stu-id="f431c-109">Contains the parent of the context node.</span></span>  
  
     <span data-ttu-id="f431c-110">下面的 XPath 表达式选择子级的所有 **\<Customer>** 父级 **\<Order>** ：</span><span class="sxs-lookup"><span data-stu-id="f431c-110">The following XPath expression selects all the **\<Customer>** parents of the **\<Order>** children:</span></span>  
  
    ```  
    child::Customer/child::Order[parent::Customer/@customerID="ALFKI"]  
    ```  
  
     <span data-ttu-id="f431c-111">这与指定 `child::Customer` 的作用相同。</span><span class="sxs-lookup"><span data-stu-id="f431c-111">This is the same as specifying `child::Customer`.</span></span> <span data-ttu-id="f431c-112">在此 XPath 查询中，`child` 和 `parent` 为轴。</span><span class="sxs-lookup"><span data-stu-id="f431c-112">In this XPath query, `child` and `parent` are the axes.</span></span> <span data-ttu-id="f431c-113">`Customer` 和 `Order` 是节点测试。</span><span class="sxs-lookup"><span data-stu-id="f431c-113">`Customer` and `Order` are the node tests.</span></span>  
  
-   `attribute`  
  
     <span data-ttu-id="f431c-114">包含上下文节点的属性。</span><span class="sxs-lookup"><span data-stu-id="f431c-114">Contains the attribute of the context node.</span></span>  
  
     <span data-ttu-id="f431c-115">下面的 XPath 表达式选择上下文节点的**CustomerID**属性：</span><span class="sxs-lookup"><span data-stu-id="f431c-115">The following XPath expression selects the **CustomerID** attribute of the context node:</span></span>  
  
    ```  
    attribute::CustomerID  
    ```  
  
-   `self`  
  
     <span data-ttu-id="f431c-116">包含上下文节点本身。</span><span class="sxs-lookup"><span data-stu-id="f431c-116">Contains the context node itself.</span></span>  
  
     <span data-ttu-id="f431c-117">下面的 XPath 表达式选择当前节点（如果它是 **\<Order>** 节点）：</span><span class="sxs-lookup"><span data-stu-id="f431c-117">The following XPath expression selects the current node if it is the **\<Order>** node:</span></span>  
  
    ```  
    self::Order  
    ```  
  
     <span data-ttu-id="f431c-118">在此 XPath 查询中，`self` 为轴，`Order` 为节点测试。</span><span class="sxs-lookup"><span data-stu-id="f431c-118">In this XPath query, `self` is the axis and `Order` is the node test.</span></span>  
  
  
