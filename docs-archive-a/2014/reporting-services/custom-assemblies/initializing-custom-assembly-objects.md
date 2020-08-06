---
title: 初始化自定义程序集对象 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- initializing custom assemblies [Reporting Services]
- custom assemblies [Reporting Services], initializing
- OnInit method
ms.assetid: 26fd74dc-d02f-40f7-aeb3-50ce05e9e6b9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2aba0bd8b71b26651067a2370728dcdff521ceaa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586492"
---
# <a name="initializing-custom-assembly-objects"></a><span data-ttu-id="edb88-102">初始化自定义程序集对象</span><span class="sxs-lookup"><span data-stu-id="edb88-102">Initializing Custom Assembly Objects</span></span>
  <span data-ttu-id="edb88-103">在某些情况下，您可能需要在实例化自定义程序集类中的属性值和字段值时初始化它们。</span><span class="sxs-lookup"><span data-stu-id="edb88-103">In some cases, you may need to initialize property and field values in your custom assembly classes when you instantiate them.</span></span> <span data-ttu-id="edb88-104">您最可能需要使用从报表的全局对象集合中提供给您的值来初始化自定义类。</span><span class="sxs-lookup"><span data-stu-id="edb88-104">You will most likely need to initialize your custom classes with values available to you from the report's global object collections.</span></span> <span data-ttu-id="edb88-105">为此，需要覆盖报表的 Code 对象的 OnInit 方法\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="edb88-105">You do this by overriding the **OnInit** method of the **Code** object of a report.</span></span> <span data-ttu-id="edb88-106">若要访问 OnInit，请使用报表定义的 Code 元素\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="edb88-106">To access **OnInit**, use the **Code** element of the report definition.</span></span> <span data-ttu-id="edb88-107">有两种方法可用于初始化你计划要在报表中使用的自定义程序集中类的属性值或字段值：可以使用 OnInit 声明和创建类的新实例，或者可以使用 OnInit 调用可以公共使用的方法\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="edb88-107">There are two techniques for initializing property or field values of the classes in a custom assembly that you plan to use in your report: You can either declare and create a new instance of your class using **OnInit**, or you can call a publicly available method using **OnInit**.</span></span>  
  
## <a name="global-object-collections-and-initialization"></a><span data-ttu-id="edb88-108">全局对象集合和初始化</span><span class="sxs-lookup"><span data-stu-id="edb88-108">Global Object Collections and Initialization</span></span>  
 <span data-ttu-id="edb88-109">若干集合可用于初始化您的自定义类变量。</span><span class="sxs-lookup"><span data-stu-id="edb88-109">Several collections are available to you for initializing your custom class variables.</span></span> <span data-ttu-id="edb88-110">可以使用 Globals 和 User 集合\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="edb88-110">You can use the **Globals** and **User** collections.</span></span> <span data-ttu-id="edb88-111">在调用 OnInit 方法时，Parameters、Fields 和 ReportItems 集合在报表生命周期中都不可用\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="edb88-111">The **Parameters**, **Fields** and **ReportItems** collections are not available to you at the point in the report lifecycle when the **OnInit** method is invoked.</span></span> <span data-ttu-id="edb88-112">若要使用共享集合（Globals 或 User），需要包括 Report 对象引用\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="edb88-112">To use the shared collections, **Globals** or **User**, you need to include the **Report** object reference.</span></span> <span data-ttu-id="edb88-113">例如，若要基于访问报表的用户的当前语言初始化自定义类，则 Code 元素可能如下\*\*\*\*：</span><span class="sxs-lookup"><span data-stu-id="edb88-113">For example, to initialize your custom class based on the current language of the user accessing the report, your **Code** element might look like the following:</span></span>  
  
```  
<Code>  
   Dim m_myClass As MyClass  
  
   Protected Overrides Sub OnInit()  
      m_myClass = new MyClass(Report.User!Language, _  
         Report.Globals!ExecutionTime)  
   End Sub  
</Code>  
```  
  
 <span data-ttu-id="edb88-114">初始化上述类的属性值和字段值的一个方法就是声明您的类并通过调用某一覆盖的构造函数创建其新实例。</span><span class="sxs-lookup"><span data-stu-id="edb88-114">One way to initialize the property and field values of a class as shown previously is to declare your class and create a new instance of it by calling an overridden constructor.</span></span>  
  
 <span data-ttu-id="edb88-115">初始化自定义程序集中类的属性值和字段值的另一个方法是调用从 OnInit 方法定义的可以公共使用的方法\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="edb88-115">Another way to initialize the property and field values of the classes in your custom assemblies is to call a publicly available method that you define from the **OnInit** method.</span></span> <span data-ttu-id="edb88-116">您首先需要在报表定义文件中为您的类添加一个实例名称。</span><span class="sxs-lookup"><span data-stu-id="edb88-116">You first need to add an instance name for your class in the report definition file.</span></span> <span data-ttu-id="edb88-117">一旦添加了相应的程序集引用和实例名称后，可以调用您的初始化方法以初始化类的属性值和字段值。</span><span class="sxs-lookup"><span data-stu-id="edb88-117">Once you have added the appropriate assembly reference and instance name, you can call your initialization method to initialize property and field values for your class.</span></span> <span data-ttu-id="edb88-118">OnInit 方法可能如下\*\*\*\*：</span><span class="sxs-lookup"><span data-stu-id="edb88-118">Your **OnInit** method might look like the following:</span></span>  
  
```  
<Code>  
   Protected Overrides Sub OnInit()  
      m_myClass.MyInitializationMethod(Report.User!Language, _  
         Report.Globals!ExecutionTime)  
   End Sub  
</Code>  
```  
  
 <span data-ttu-id="edb88-119">有关为自定义类添加程序集引用和实例名称的详细信息，请参阅[向报表添加程序集引用 (SSRS)](../report-design/add-an-assembly-reference-to-a-report-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="edb88-119">For more information about adding an assembly reference and instance name for your custom class, see [Add an Assembly Reference to a Report &#40;SSRS&#41;](../report-design/add-an-assembly-reference-to-a-report-ssrs.md).</span></span>  
  
 <span data-ttu-id="edb88-120">有关全局对象集合的详细信息，请参阅[表达式中的内置集合（报表生成器和 SSRS）](../report-design/built-in-collections-in-expressions-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="edb88-120">For more information about the global object collections, see [Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edb88-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="edb88-121">See Also</span></span>  
 [<span data-ttu-id="edb88-122">将自定义程序集用于报表</span><span class="sxs-lookup"><span data-stu-id="edb88-122">Using Custom Assemblies with Reports</span></span>](using-custom-assemblies-with-reports.md)  
  
  
