---
title: 通过表达式访问自定义程序集 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- expressions [Reporting Services], custom assemblies
- static member calls
- instance member calls [Reporting Services]
- calling class members
- custom assemblies [Reporting Services], expressions
ms.assetid: 917c4d47-1a95-4f54-98b1-e8cb2165d90f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 99497de0456d90fd522ce27c62fd5aa1b812059f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576535"
---
# <a name="accessing-custom-assemblies-through-expressions"></a><span data-ttu-id="319d3-102">通过表达式访问自定义程序集</span><span class="sxs-lookup"><span data-stu-id="319d3-102">Accessing Custom Assemblies Through Expressions</span></span>
  <span data-ttu-id="319d3-103">在创建自定义程序集、使其可用于报表设计器或报表服务器、添加适当的安全策略以及在报表定义中添加对自定义程序集的引用之后，您就可以使用报表表达式访问程序集中类的成员。</span><span class="sxs-lookup"><span data-stu-id="319d3-103">Once you have created a custom assembly, made it available to Report Designer or the report server, added the appropriate security policy, and added a reference to your custom assembly in your report definition, you can access the members of the classes in your assembly using report expressions.</span></span> <span data-ttu-id="319d3-104">若要在表达式中引用自定义代码，您必须调用程序集中某个类的成员。</span><span class="sxs-lookup"><span data-stu-id="319d3-104">To refer to custom code in an expression, you must call the member of a class within the assembly.</span></span> <span data-ttu-id="319d3-105">调用方式取决于该方法是静态方法还是基于实例的方法。</span><span class="sxs-lookup"><span data-stu-id="319d3-105">How you do this depends on whether the method is static or instance-based.</span></span>  
  
## <a name="calling-static-members-from-a-report-definition-file"></a><span data-ttu-id="319d3-106">从报表定义文件调用静态成员</span><span class="sxs-lookup"><span data-stu-id="319d3-106">Calling Static Members from a Report Definition File</span></span>  
 <span data-ttu-id="319d3-107">静态成员属于类或类型本身，而不属于实例化的对象。</span><span class="sxs-lookup"><span data-stu-id="319d3-107">Static members belong to the class or type itself and not to an instantiated object.</span></span> <span data-ttu-id="319d3-108">可以通过从类中调用这些成员直接访问它们。</span><span class="sxs-lookup"><span data-stu-id="319d3-108">These members can be accessed by directly calling them from the class.</span></span> <span data-ttu-id="319d3-109">应尽可能使用静态成员在报表中调用自定义函数，因为静态成员的效果最佳。</span><span class="sxs-lookup"><span data-stu-id="319d3-109">You should use static members to call custom functions in a report whenever possible, because static members perform best.</span></span> <span data-ttu-id="319d3-110">若要调用某个静态成员，需要将其作为表达式（采用 =Namespace.Class.Method\*\* 格式）进行引用。</span><span class="sxs-lookup"><span data-stu-id="319d3-110">To call a static member, you need to reference it as an expression that takes the form =*Namespace.Class.Method*.</span></span>  
  
#### <a name="to-call-static-members"></a><span data-ttu-id="319d3-111">调用静态成员</span><span class="sxs-lookup"><span data-stu-id="319d3-111">To call static members</span></span>  
  
-   <span data-ttu-id="319d3-112">若要调用静态成员，请将表达式设置为等于成员的完全限定名称（包括命名空间、类名称和成员名称）。</span><span class="sxs-lookup"><span data-stu-id="319d3-112">To call a static member, set your expression equal to the fully qualified name of the member, which includes the namespace, class name, and member name.</span></span> <span data-ttu-id="319d3-113">以下示例调用“ToGBP”方法，该方法将“StandardCost”字段值从美元转换为英镑并在报表中显示该值\*\*\*\*\*\*\*\*：</span><span class="sxs-lookup"><span data-stu-id="319d3-113">The following example calls the **ToGBP** method, which converts the **StandardCost** field value from dollars to pounds sterling and displays it in a report:</span></span>  
  
    ```  
    =CurrencyConversion.DollarCurrencyConversion.ToGBP(Fields!StandardCost.Value)  
    ```  
  
### <a name="important-information-regarding-static-fields-and-properties"></a><span data-ttu-id="319d3-114">有关静态字段和属性的重要信息</span><span class="sxs-lookup"><span data-stu-id="319d3-114">Important Information Regarding Static Fields and Properties</span></span>  
 <span data-ttu-id="319d3-115">目前，所有报表都在同一个应用程序域中执行。</span><span class="sxs-lookup"><span data-stu-id="319d3-115">Currently, all reports are executed in the same application domain.</span></span> <span data-ttu-id="319d3-116">这意味着具有用户特定的静态数据的报表将向同一报表的其他实例公开此数据。</span><span class="sxs-lookup"><span data-stu-id="319d3-116">This means that reports with user-specific, static data expose this data to other instances of the same report.</span></span> <span data-ttu-id="319d3-117">这种情况可能会使一个用户的静态数据可用于当前运行特定报表的所有用户。</span><span class="sxs-lookup"><span data-stu-id="319d3-117">This condition might make it possible for the static data of one user to be available to all users currently running a particular report.</span></span> <span data-ttu-id="319d3-118">因此，强烈建议不要在自定义程序集或“Code”元素中使用静态字段或属性；而是在报表中使用实例字段或属性\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="319d3-118">For this reason, it is highly recommended that you not use static fields or properties in custom assemblies or in the **Code** element; instead, use instance fields or properties in your reports.</span></span> <span data-ttu-id="319d3-119">仍可以使用静态方法，因为它们不存储状态或数据。</span><span class="sxs-lookup"><span data-stu-id="319d3-119">Static methods can still be used, because they do not store state or data.</span></span>  
  
## <a name="calling-instance-members-from-a-report-definition-file"></a><span data-ttu-id="319d3-120">从报表定义文件调用实例成员</span><span class="sxs-lookup"><span data-stu-id="319d3-120">Calling Instance Members from a Report Definition File</span></span>  
 <span data-ttu-id="319d3-121">如果您的自定义程序集包含您在报表定义中需要访问的实例成员，则必须将类的实例名称添加到报表中。</span><span class="sxs-lookup"><span data-stu-id="319d3-121">If your custom assembly contains instance members that you need to access in a report definition, you must add an instance name for your class to the report.</span></span> <span data-ttu-id="319d3-122">可以使用“报表属性”对话框中的“代码”选项卡添加类的实例名称\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="319d3-122">You can add an instance name for a class using the **Code** tab of the **Report Properties** dialog.</span></span> <span data-ttu-id="319d3-123">有关向报表添加类的实例的详细信息，请参阅[报表设计器的表达式中的自定义代码和程序集引用 (SSRS)](../report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="319d3-123">For more information about adding instances of classes to a report, see [Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;](../report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).</span></span>  
  
 <span data-ttu-id="319d3-124">若要调用静态成员，需要将其引用为采用 = Code 形式的表达式 *。InstanceName. 方法*。</span><span class="sxs-lookup"><span data-stu-id="319d3-124">To call a static member, you need to reference it as an expression that takes the form = Code *.InstanceName.Method*.</span></span>  
  
#### <a name="to-call-instance-members"></a><span data-ttu-id="319d3-125">调用实例成员</span><span class="sxs-lookup"><span data-stu-id="319d3-125">To call instance members</span></span>  
  
-   <span data-ttu-id="319d3-126">若要调用自定义程序集的实例成员，必须引用“Code”\*\*\*\* 关键字，后跟实例名称和方法。</span><span class="sxs-lookup"><span data-stu-id="319d3-126">To call an instance member of a custom assembly, you must reference the **Code** keyword followed by the instance name and the method.</span></span> <span data-ttu-id="319d3-127">以下示例调用实例方法“ToEUR”，该方法将“StandardCost”字段值从美元转换为欧元并在报表中显示该值\*\*\*\*\*\*\*\*：</span><span class="sxs-lookup"><span data-stu-id="319d3-127">The following example calls an instance method **ToEUR** which converts the **StandardCost** field value from dollars to euros and displays it in a report:</span></span>  
  
    ```  
    =Code.m_myDollarCoversion.ToEUR(Fields!StandardCost.Value)  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="319d3-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="319d3-128">See Also</span></span>  
 [<span data-ttu-id="319d3-129">将自定义程序集用于报表</span><span class="sxs-lookup"><span data-stu-id="319d3-129">Using Custom Assemblies with Reports</span></span>](using-custom-assemblies-with-reports.md)  
  
  
