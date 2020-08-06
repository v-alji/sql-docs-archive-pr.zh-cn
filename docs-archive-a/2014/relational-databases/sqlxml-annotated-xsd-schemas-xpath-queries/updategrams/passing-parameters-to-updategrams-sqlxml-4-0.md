---
title: 将参数传递给 Updategram (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- nullvalue attribute
- passing parameters [SQLXML]
- parameters [SQLXML]
- updategrams [SQLXML], passing parameters
- null values [SQLXML]
ms.assetid: 2354e6e7-1860-471f-8711-4e374c5a4ed2
author: rothja
ms.author: jroth
ms.openlocfilehash: 4bc29de2dab3d0bc3587cb21b7005c0c23dcf7c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588439"
---
# <a name="passing-parameters-to-updategrams-sqlxml-40"></a><span data-ttu-id="7365a-102">将参数传递给 Updategram (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="7365a-102">Passing Parameters to Updategrams (SQLXML 4.0)</span></span>
  <span data-ttu-id="7365a-103">Updategram 为模板，因此您可以向其传递参数。</span><span class="sxs-lookup"><span data-stu-id="7365a-103">Updategrams are templates; therefore, you can pass them parameters.</span></span> <span data-ttu-id="7365a-104">有关将参数传递到模板的详细信息，请参阅[&#40;SQLXML 4.0&#41;的 Updategram 安全注意事项](../security/updategram-security-considerations-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="7365a-104">For more information about passing parameters to templates, see [Updategram Security Considerations &#40;SQLXML 4.0&#41;](../security/updategram-security-considerations-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="7365a-105">Updategram 允许您将 NULL 作为参数值传递。</span><span class="sxs-lookup"><span data-stu-id="7365a-105">Updategrams allow you to pass NULL as a parameter value.</span></span> <span data-ttu-id="7365a-106">若要传递 NULL 参数值，应指定 `nullvalue` 属性。</span><span class="sxs-lookup"><span data-stu-id="7365a-106">To pass the NULL parameter value, you specify the `nullvalue` attribute.</span></span> <span data-ttu-id="7365a-107">然后，赋给 `nullvalue` 属性的值将作为参数值提供。</span><span class="sxs-lookup"><span data-stu-id="7365a-107">The value that is assigned to the `nullvalue` attribute is then provided as the parameter value.</span></span> <span data-ttu-id="7365a-108">Updategram 将该值视为 NULL。</span><span class="sxs-lookup"><span data-stu-id="7365a-108">Updategrams treat this value as NULL.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7365a-109">在 `<sql:header>` 和 `<updg:header>` 中，应将 `nullvalue` 指定为非限定的；而在 `<updg:sync>` 中，应将 `nullvalue` 指定为限定的（例如 `updg:nullvalue`）。</span><span class="sxs-lookup"><span data-stu-id="7365a-109">In `<sql:header>` and `<updg:header>`, you should specify the `nullvalue` as unqualified; whereas, in `<updg:sync>`, you specify the `nullvalue` as qualified (for example, `updg:nullvalue`).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="7365a-110">示例</span><span class="sxs-lookup"><span data-stu-id="7365a-110">Examples</span></span>  
 <span data-ttu-id="7365a-111">若要创建使用以下示例的工作示例，必须满足[运行 SQLXML 示例的要求](../../sqlxml/requirements-for-running-sqlxml-examples.md)中指定的要求。</span><span class="sxs-lookup"><span data-stu-id="7365a-111">To create working samples using the following examples, you must meet the requirements specified in [Requirements for Running SQLXML Examples](../../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
 <span data-ttu-id="7365a-112">在使用 updategram 示例前，请注意以下事项：</span><span class="sxs-lookup"><span data-stu-id="7365a-112">Before using the updategram examples, note the following:</span></span>  
  
-   <span data-ttu-id="7365a-113">此示例使用默认映射（即未在 updategram 中指定映射架构）。</span><span class="sxs-lookup"><span data-stu-id="7365a-113">The examples use default mapping (that is, no mapping schema is specified in the updategram).</span></span> <span data-ttu-id="7365a-114">有关使用映射架构的 updategram 的更多示例，请参阅[在 Updategram &#40;SQLXML 4.0&#41;中指定带批注的映射架构](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="7365a-114">For more examples of updategrams that use mapping schemas, see [Specifying an Annotated Mapping Schema in an Updategram &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).</span></span>  
  
### <a name="a-passing-parameters-to-an-updategram"></a><span data-ttu-id="7365a-115">A.</span><span class="sxs-lookup"><span data-stu-id="7365a-115">A.</span></span> <span data-ttu-id="7365a-116">将参数传递给 updategram</span><span class="sxs-lookup"><span data-stu-id="7365a-116">Passing parameters to an updategram</span></span>  
 <span data-ttu-id="7365a-117">在本示例中，updategram 更改了 HumanResources.Shift 表中一位雇员的姓氏。</span><span class="sxs-lookup"><span data-stu-id="7365a-117">In this example, the updategram changes the last name of an employee in the HumanResources.Shift table.</span></span> <span data-ttu-id="7365a-118">向 updategram 传递了两个参数：ShiftID（用于唯一标识轮班）和 Name。</span><span class="sxs-lookup"><span data-stu-id="7365a-118">The updategram is passed two parameters: ShiftID, which is used to uniquely identify a shift, and Name.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:header>  
  <updg:param name="ShiftID"/>  
  <updg:param name="Name" />  
</updg:header>  
  <updg:sync >  
    <updg:before>  
       <HumanResources.Shift ShiftID="$ShiftID" />  
    </updg:before>  
    <updg:after>  
      <HumanResources.Shift Name="$Name" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="7365a-119">测试 updategram</span><span class="sxs-lookup"><span data-stu-id="7365a-119">To test the updategram</span></span>  
  
1.  <span data-ttu-id="7365a-120">将上面的 updategram 复制到记事本中并将其另存为 UpdategramWithParameters.xml 文件。</span><span class="sxs-lookup"><span data-stu-id="7365a-120">Copy the updategram above into Notepad and save it to file as UpdategramWithParameters.xml.</span></span>  
  
2.  <span data-ttu-id="7365a-121">使用 ADO () Sqlxml4test.vbs 准备 SQLXML 4.0 测试脚本，以便通过在以下内容后添加以下行来[执行 sqlxml 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)以执行 updategram `cmd.Properties("Output Stream").Value = outStream` ：</span><span class="sxs-lookup"><span data-stu-id="7365a-121">Prepare the SQLXML 4.0 test script (Sqlxml4test.vbs) in [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md) to execute the updategram by adding the following lines after the `cmd.Properties("Output Stream").Value = outStream`:</span></span>  
  
    ```  
    cmd.NamedParameters = True  
    ' CreateParameter arguments: Name, Type, Direction, Size, Value  
    cmd.Parameters.Append cmd.CreateParameter("@ShiftID",  2, 1,  0, 1)  
    cmd.Parameters.Append cmd.CreateParameter("@Name",   200, 1, 50, "New Name")  
    ```  
  
### <a name="b-passing-null-as-a-parameter-value-to-an-updategram"></a><span data-ttu-id="7365a-122">B.</span><span class="sxs-lookup"><span data-stu-id="7365a-122">B.</span></span> <span data-ttu-id="7365a-123">将 NULL 作为参数值传递给 updategram</span><span class="sxs-lookup"><span data-stu-id="7365a-123">Passing NULL as a parameter value to an updategram</span></span>  
 <span data-ttu-id="7365a-124">在执行 updategram 的过程中，会将“isnull”值赋给要设置为 NULL 的参数。</span><span class="sxs-lookup"><span data-stu-id="7365a-124">In executing an updategram, the "isnull" value is assigned to the parameter that you want to set to NULL.</span></span> <span data-ttu-id="7365a-125">Updategram 将“isnulll”参数值转换为 NULL 并对其进行相应处理。</span><span class="sxs-lookup"><span data-stu-id="7365a-125">Updategram converts the "isnulll" parameter value to NULL and processes it accordingly.</span></span>  
  
 <span data-ttu-id="7365a-126">以下 updategram 将员工职务设置为 NULL：</span><span class="sxs-lookup"><span data-stu-id="7365a-126">The following updategram sets an employee title to NULL:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:header nullvalue="isnull" >  
  <updg:param name="EmployeeID"/>  
  <updg:param name="ManagerID" />  
</updg:header>  
  <updg:sync >  
    <updg:before>  
       <HumanResources.Employee EmployeeID="$EmployeeID" />  
    </updg:before>  
    <updg:after>  
      <HumanResources.Employee ManagerID="$ManagerID" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="7365a-127">测试 updategram</span><span class="sxs-lookup"><span data-stu-id="7365a-127">To test the updategram</span></span>  
  
1.  <span data-ttu-id="7365a-128">将上面的 updategram 复制到记事本中并将其另存为 UpdategramPassingNullvalues.xml 文件。</span><span class="sxs-lookup"><span data-stu-id="7365a-128">Copy the updategram above into Notepad and save it to file as UpdategramPassingNullvalues.xml.</span></span>  
  
2.  <span data-ttu-id="7365a-129">使用 ADO () Sqlxml4test.vbs 准备 SQLXML 4.0 测试脚本，以便通过在以下内容后添加以下行来[执行 sqlxml 4.0 查询](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)以执行 updategram `cmd.Properties("Output Stream").Value = outStream` ：</span><span class="sxs-lookup"><span data-stu-id="7365a-129">Prepare the SQLXML 4.0 test script (Sqlxml4test.vbs) in [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md) to execute the updategram by adding the following lines after the `cmd.Properties("Output Stream").Value = outStream`:</span></span>  
  
    ```  
    cmd.NamedParameters = True  
    ' CreateParameter arguments: Name, Type, Direction, Size, Value   
    cmd.Parameters.Append cmd.CreateParameter("@EmployeeID", 3, 1, 0, 1)  
    cmd.Parameters.Append cmd.CreateParameter("@ManagerID",  3, 1, 0, Null)  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="7365a-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7365a-130">See Also</span></span>  
 [<span data-ttu-id="7365a-131">&#40;SQLXML 4.0&#41;的 Updategram 安全注意事项</span><span class="sxs-lookup"><span data-stu-id="7365a-131">Updategram Security Considerations &#40;SQLXML 4.0&#41;</span></span>](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
