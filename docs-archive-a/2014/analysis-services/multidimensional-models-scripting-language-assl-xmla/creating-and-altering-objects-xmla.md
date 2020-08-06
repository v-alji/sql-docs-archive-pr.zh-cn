---
title: " (XMLA) 创建和更改对象 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- objects [XML for Analysis]
- subordinate objects [XML for Analysis]
- XML for Analysis, objects
- modifying objects
- removing objects
- deleting objects
- XMLA, objects
ms.assetid: a2080867-e130-440c-92eb-f768869f34a8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2390c0b921368e7e06f0e5563a7eb59769d99c17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589935"
---
# <a name="creating-and-altering-objects-xmla"></a><span data-ttu-id="7f931-102">创建和更改对象 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="7f931-102">Creating and Altering Objects (XMLA)</span></span>
  <span data-ttu-id="7f931-103">可以单独创建、更改和删除主要对象。</span><span class="sxs-lookup"><span data-stu-id="7f931-103">Major objects can be independently created, altered, and deleted.</span></span> <span data-ttu-id="7f931-104">主要对象包括以下对象：</span><span class="sxs-lookup"><span data-stu-id="7f931-104">Major objects include the following objects:</span></span>  
  
-   <span data-ttu-id="7f931-105">服务器</span><span class="sxs-lookup"><span data-stu-id="7f931-105">Servers</span></span>  
  
-   <span data-ttu-id="7f931-106">数据库</span><span class="sxs-lookup"><span data-stu-id="7f931-106">Databases</span></span>  
  
-   <span data-ttu-id="7f931-107">维度</span><span class="sxs-lookup"><span data-stu-id="7f931-107">Dimensions</span></span>  
  
-   <span data-ttu-id="7f931-108">多维数据集</span><span class="sxs-lookup"><span data-stu-id="7f931-108">Cubes</span></span>  
  
-   <span data-ttu-id="7f931-109">度量值组</span><span class="sxs-lookup"><span data-stu-id="7f931-109">Measure groups</span></span>  
  
-   <span data-ttu-id="7f931-110">分区</span><span class="sxs-lookup"><span data-stu-id="7f931-110">Partitions</span></span>  
  
-   <span data-ttu-id="7f931-111">透视</span><span class="sxs-lookup"><span data-stu-id="7f931-111">Perspectives</span></span>  
  
-   <span data-ttu-id="7f931-112">挖掘模型</span><span class="sxs-lookup"><span data-stu-id="7f931-112">Mining models</span></span>  
  
-   <span data-ttu-id="7f931-113">角色</span><span class="sxs-lookup"><span data-stu-id="7f931-113">Roles</span></span>  
  
-   <span data-ttu-id="7f931-114">与服务器或数据库关联的命令</span><span class="sxs-lookup"><span data-stu-id="7f931-114">Commands associated with a server or database</span></span>  
  
-   <span data-ttu-id="7f931-115">数据源</span><span class="sxs-lookup"><span data-stu-id="7f931-115">Data sources</span></span>  
  
 <span data-ttu-id="7f931-116">您可以使用[create](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla)命令来创建实例上的主要对象 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，并使用[alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla)命令来更改实例上的现有主要对象。</span><span class="sxs-lookup"><span data-stu-id="7f931-116">You use the [Create](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla) command to create a major object on an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], and the [Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla) command to alter an existing major object on an instance.</span></span> <span data-ttu-id="7f931-117">这两个命令都使用[Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute)方法运行。</span><span class="sxs-lookup"><span data-stu-id="7f931-117">Both commands are run using the [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) method.</span></span>  
  
## <a name="creating-objects"></a><span data-ttu-id="7f931-118">创建对象</span><span class="sxs-lookup"><span data-stu-id="7f931-118">Creating Objects</span></span>  
 <span data-ttu-id="7f931-119">使用 `Create` 方法创建对象时，必须首先标识包含要创建的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 对象的父对象。</span><span class="sxs-lookup"><span data-stu-id="7f931-119">When you create objects by using the `Create` method, you must first identify the parent object that contains the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] object to be created.</span></span> <span data-ttu-id="7f931-120">可以通过在命令的[ParentObject](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)属性中提供对象引用来标识父对象 `Create` 。</span><span class="sxs-lookup"><span data-stu-id="7f931-120">You identify the parent object by providing an object reference in the [ParentObject](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) property of the `Create` command.</span></span> <span data-ttu-id="7f931-121">每一个对象引用都包含为 `Create` 命令唯一标识父对象时所需的对象标识符。</span><span class="sxs-lookup"><span data-stu-id="7f931-121">Each object reference contains the object identifiers needed to uniquely identify the parent object for the `Create` command.</span></span> <span data-ttu-id="7f931-122">有关对象引用的详细信息，请参阅[&#40;XMLA&#41;定义和标识对象](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects)。</span><span class="sxs-lookup"><span data-stu-id="7f931-122">For more information about object references, see [Defining and Identifying Objects &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects).</span></span>  
  
 <span data-ttu-id="7f931-123">例如，若要为某一多维数据集创建新的度量值组，则必须提供对该多维数据集的对象引用。</span><span class="sxs-lookup"><span data-stu-id="7f931-123">For example, you must provide an object reference to a cube to create a new measure group for the cube.</span></span> <span data-ttu-id="7f931-124">`ParentObject` 属性中多维数据集的对象引用同时包含数据库标识符和多维数据集标识符，因为同一多维数据集标识符可能用于不同的数据库上。</span><span class="sxs-lookup"><span data-stu-id="7f931-124">The object reference for the cube in the `ParentObject` property contains both a database identifier and a cube identifier, as the same cube identifier could potentially be used on a different database.</span></span>  
  
 <span data-ttu-id="7f931-125">[ObjectDefinition](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/objectdefinition-element-xmla)元素包含 Analysis Services 脚本语言 (ASSL) 元素，这些元素定义要创建的主要对象。</span><span class="sxs-lookup"><span data-stu-id="7f931-125">The [ObjectDefinition](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/objectdefinition-element-xmla) element contains Analysis Services Scripting Language (ASSL) elements that define the major object to be created.</span></span> <span data-ttu-id="7f931-126">有关 ASSL 的详细信息，请参阅[&#40;ASSL&#41;Analysis Services 脚本编写语言进行开发](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)。</span><span class="sxs-lookup"><span data-stu-id="7f931-126">For more information about ASSL, see [Developing with Analysis Services Scripting Language &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).</span></span>  
  
 <span data-ttu-id="7f931-127">如果将 `AllowOverwrite` 命令的 `Create` 属性设置为 True，则会覆盖具有指定标识符的现有主要对象。</span><span class="sxs-lookup"><span data-stu-id="7f931-127">If you set the `AllowOverwrite` attribute of the `Create` command to true, you can overwrite an existing major object that has the specified identifier.</span></span> <span data-ttu-id="7f931-128">否则，如果具有指定标识符的主要对象仍存在于父对象中，则会发生错误。</span><span class="sxs-lookup"><span data-stu-id="7f931-128">Otherwise, an error occurs if a major object that has the specified identifier already exists in the parent object.</span></span>  
  
 <span data-ttu-id="7f931-129">有关命令的详细信息 `Create` ，请参阅[Create ELEMENT &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla)。</span><span class="sxs-lookup"><span data-stu-id="7f931-129">For more information about the `Create` command, see [Create Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla).</span></span>  
  
### <a name="creating-session-objects"></a><span data-ttu-id="7f931-130">创建会话对象</span><span class="sxs-lookup"><span data-stu-id="7f931-130">Creating Session Objects</span></span>  
 <span data-ttu-id="7f931-131">会话对象是一些临时对象，它们仅可用于客户端应用程序所使用的显式或隐式会话，且在会话结束后会删除这些会话对象。</span><span class="sxs-lookup"><span data-stu-id="7f931-131">Session objects are temporary objects that are available only to the explicit or implicit session used by a client application and are deleted when the session is ended.</span></span> <span data-ttu-id="7f931-132">可以通过将 `Scope` 命令的属性设置 `Create` 为*session*来创建会话对象。</span><span class="sxs-lookup"><span data-stu-id="7f931-132">You can create session objects by setting the `Scope` attribute of the `Create` command to *Session*.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7f931-133">使用*会话*设置时， `ObjectDefinition` 元素只能包含[Dimension](https://docs.microsoft.com/bi-reference/assl/objects/dimension-element-assl)、 [Cube](https://docs.microsoft.com/bi-reference/assl/objects/cube-element-assl)或[MiningModel](https://docs.microsoft.com/bi-reference/assl/objects/miningmodel-element-assl) ASSL 元素。</span><span class="sxs-lookup"><span data-stu-id="7f931-133">When using the *Session* setting, the `ObjectDefinition` element can only contain [Dimension](https://docs.microsoft.com/bi-reference/assl/objects/dimension-element-assl), [Cube](https://docs.microsoft.com/bi-reference/assl/objects/cube-element-assl), or [MiningModel](https://docs.microsoft.com/bi-reference/assl/objects/miningmodel-element-assl) ASSL elements.</span></span>  
  
## <a name="altering-objects"></a><span data-ttu-id="7f931-134">更改对象</span><span class="sxs-lookup"><span data-stu-id="7f931-134">Altering Objects</span></span>  
 <span data-ttu-id="7f931-135">使用方法修改对象时 `Alter` ，必须先通过在命令的[对象](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)属性中提供对象引用来标识要修改的对象 `Alter` 。</span><span class="sxs-lookup"><span data-stu-id="7f931-135">When modifying objects by using the `Alter` method, you must first identify the object to be modified by providing an object reference in the [Object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) property of the `Alter` command.</span></span> <span data-ttu-id="7f931-136">每一个对象引用都包含为 `Alter` 命令唯一标识该对象时所需的对象标识符。</span><span class="sxs-lookup"><span data-stu-id="7f931-136">Each object reference contains the object identifiers needed to uniquely identify the object for the `Alter` command.</span></span> <span data-ttu-id="7f931-137">有关对象引用的详细信息，请参阅[&#40;XMLA&#41;定义和标识对象](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects)。</span><span class="sxs-lookup"><span data-stu-id="7f931-137">For more information about object references, see [Defining and Identifying Objects &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects).</span></span>  
  
 <span data-ttu-id="7f931-138">例如，若要修改某一多维数据集的结构，必须提供对该多维数据集的对象引用。</span><span class="sxs-lookup"><span data-stu-id="7f931-138">For example, you must provide an object reference to a cube in order to modify the structure of a cube.</span></span> <span data-ttu-id="7f931-139">`Object` 属性中多维数据集的对象引用同时包含数据库标识符和多维数据集标识符，因为同一多维数据集标识符可能用于不同的数据库上。</span><span class="sxs-lookup"><span data-stu-id="7f931-139">The object reference for the cube in the `Object` property contains both a database identifier and a cube identifier, as the same cube identifier could potentially be used on a different database.</span></span>  
  
 <span data-ttu-id="7f931-140">`ObjectDefinition` 元素包含用于定义要修改的主要对象的 ASSL 元素。</span><span class="sxs-lookup"><span data-stu-id="7f931-140">The `ObjectDefinition` element contains ASSL elements that define the major object to be modified.</span></span> <span data-ttu-id="7f931-141">有关 ASSL 的详细信息，请参阅[&#40;ASSL&#41;Analysis Services 脚本编写语言进行开发](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)。</span><span class="sxs-lookup"><span data-stu-id="7f931-141">For more information about ASSL, see [Developing with Analysis Services Scripting Language &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).</span></span>  
  
 <span data-ttu-id="7f931-142">如果将 `AllowCreate` 命令的 `Alter` 属性设置为 True，则当指定的主要对象不存在时，会创建该对象。</span><span class="sxs-lookup"><span data-stu-id="7f931-142">If you set the `AllowCreate` attribute of the `Alter` command to true, you can create the specified major object if the object does not exist.</span></span> <span data-ttu-id="7f931-143">否则，如果指定的主要对象尚不存在，则会出现错误。</span><span class="sxs-lookup"><span data-stu-id="7f931-143">Otherwise, an error occurs if a specified major object does not already exist.</span></span>  
  
### <a name="using-the-objectexpansion-attribute"></a><span data-ttu-id="7f931-144">使用 ObjectExpansion 属性</span><span class="sxs-lookup"><span data-stu-id="7f931-144">Using the ObjectExpansion Attribute</span></span>  
 <span data-ttu-id="7f931-145">如果仅更改主要对象的属性，并且不会重定义主要对象所包含的次要对象，则可以将 `ObjectExpansion` 命令的属性设置 `Alter` 为*ObjectProperties*。</span><span class="sxs-lookup"><span data-stu-id="7f931-145">If you are changing only the properties of the major object and are not redefining minor objects that are contained by the major object, you can set the `ObjectExpansion` attribute of the `Alter` command to *ObjectProperties*.</span></span> <span data-ttu-id="7f931-146">这样，`ObjectDefinition` 属性便只需包含该主要对象的属性的元素，并且 `Alter` 会将与该主要对象关联的次要对象保持不变。</span><span class="sxs-lookup"><span data-stu-id="7f931-146">The `ObjectDefinition` property then only has to contain the elements for the properties of the major object, and the `Alter` command leaves minor objects associated with the major object untouched.</span></span>  
  
 <span data-ttu-id="7f931-147">若要为主要对象重新定义次要对象，必须将 `ObjectExpansion` 属性设置为*updateoptions.expandfull* ，并且对象定义必须包含主要对象所包含的所有次要对象。</span><span class="sxs-lookup"><span data-stu-id="7f931-147">To redefine minor objects for a major object, you must set the `ObjectExpansion` attribute to *ExpandFull* and the object definition must include all minor objects that are contained by the major object.</span></span> <span data-ttu-id="7f931-148">如果 `ObjectDefinition` 命令的 `Alter` 属性未显式包含该主要对象所包含的某一次要对象，则会删除未包含的该次要对象。</span><span class="sxs-lookup"><span data-stu-id="7f931-148">If the `ObjectDefinition` property of the `Alter` command does not explicitly include a minor object that is contained by the major object, the minor object that was not included is deleted.</span></span>  
  
### <a name="altering-session-objects"></a><span data-ttu-id="7f931-149">更改会话对象</span><span class="sxs-lookup"><span data-stu-id="7f931-149">Altering Session Objects</span></span>  
 <span data-ttu-id="7f931-150">若要修改通过命令创建的会话对象 `Create` ，请将 `Scope` 命令的属性设置为 " `Alter` *session*"。</span><span class="sxs-lookup"><span data-stu-id="7f931-150">To modify session objects created by the `Create` command, set the `Scope` attribute of the `Alter` command to *Session*.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7f931-151">使用*会话*设置时， `ObjectDefinition` 元素只能包含[Dimension](https://docs.microsoft.com/bi-reference/assl/objects/dimension-element-assl)、 [Cube](https://docs.microsoft.com/bi-reference/assl/objects/cube-element-assl)或[MiningModel](https://docs.microsoft.com/bi-reference/assl/objects/miningmodel-element-assl) ASSL 元素。</span><span class="sxs-lookup"><span data-stu-id="7f931-151">When using the *Session* setting, the `ObjectDefinition` element can only contain [Dimension](https://docs.microsoft.com/bi-reference/assl/objects/dimension-element-assl), [Cube](https://docs.microsoft.com/bi-reference/assl/objects/cube-element-assl), or [MiningModel](https://docs.microsoft.com/bi-reference/assl/objects/miningmodel-element-assl) ASSL elements.</span></span>  
  
## <a name="creating-or-altering-subordinate-objects"></a><span data-ttu-id="7f931-152">创建或更改从属对象</span><span class="sxs-lookup"><span data-stu-id="7f931-152">Creating or Altering Subordinate Objects</span></span>  
 <span data-ttu-id="7f931-153">尽管 `Create` 或 `Alter` 命令创建或更改的只是一个最顶层的主要对象，但要创建或修改的主要对象可在包含它的 `ObjectDefinition` 属性中包含从属于该主要对象的其他主要对象和次要对象的定义。</span><span class="sxs-lookup"><span data-stu-id="7f931-153">Although a `Create` or `Alter` command creates or alters only one topmost major object, the major object being created or modified can contain definitions within the enclosing `ObjectDefinition` property for other major and minor objects that are subordinate to it.</span></span> <span data-ttu-id="7f931-154">例如，定义某个多维数据集时，可在 `ParentObject` 中指定父数据库，再在 `ObjectDefinition` 的多维数据集定义中定义该多维数据集的度量值组，然后在该度量值组中定义每一个度量值组的分区。</span><span class="sxs-lookup"><span data-stu-id="7f931-154">For example, if you define a cube, you specify the parent database in `ParentObject`, and within the cube definition in `ObjectDefinition` you can define measure groups for the cube, and within the measure groups you can define partitions for each measure group.</span></span> <span data-ttu-id="7f931-155">次要对象只能在其所属的主要对象下定义。</span><span class="sxs-lookup"><span data-stu-id="7f931-155">A minor object can be defined only under the major object that contains it.</span></span> <span data-ttu-id="7f931-156">有关主要和次要对象的详细信息，请参阅[&#40;Analysis Services 多维数据&#41;的数据库对象](../multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="7f931-156">For more information about major and minor objects, see [Database Objects &#40;Analysis Services - Multidimensional Data&#41;](../multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="7f931-157">示例</span><span class="sxs-lookup"><span data-stu-id="7f931-157">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="7f931-158">说明</span><span class="sxs-lookup"><span data-stu-id="7f931-158">Description</span></span>  
 <span data-ttu-id="7f931-159">下面的示例创建引用示例数据库的关系数据源 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="7f931-159">The following example creates a relational data source that references the [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] sample [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  
  
### <a name="code"></a><span data-ttu-id="7f931-160">代码</span><span class="sxs-lookup"><span data-stu-id="7f931-160">Code</span></span>  
  
```  
<Create xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
    <ParentObject>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
    </ParentObject>  
    <ObjectDefinition>  
        <DataSource xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="RelationalDataSource">  
            <ID>AdventureWorksDW2012</ID>  
            <Name>AdventureWorksDW2012</Name>  
            <ConnectionString>Data Source=localhost;Initial Catalog=AdventureWorksDW2008R2;Integrated Security=True</ConnectionString>  
            <ImpersonationInfo>  
                <ImpersonationMode>ImpersonateServiceAccount</ImpersonationMode>  
            </ImpersonationInfo>  
            <ManagedProvider>System.Data.SqlClient</ManagedProvider>  
            <Timeout>PT0S</Timeout>  
        </DataSource>  
    </ObjectDefinition>  
</Create>  
```  
  
### <a name="description"></a><span data-ttu-id="7f931-161">说明</span><span class="sxs-lookup"><span data-stu-id="7f931-161">Description</span></span>  
 <span data-ttu-id="7f931-162">下面的示例对上例中创建的关系数据源进行了更改：将该数据源的查询超时设置为 30 秒。</span><span class="sxs-lookup"><span data-stu-id="7f931-162">The following example alters the relational data source created in the previous example to set the query time-out for the data source to 30 seconds.</span></span>  
  
### <a name="code"></a><span data-ttu-id="7f931-163">代码</span><span class="sxs-lookup"><span data-stu-id="7f931-163">Code</span></span>  
  
```  
<Alter ObjectExpansion="ObjectProperties" xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
    <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <DataSourceID>AdventureWorksDW2012</DataSourceID>  
    </Object>  
    <ObjectDefinition>  
        <DataSource xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="RelationalDataSource">  
            <ID>AdventureWorksDW2012</ID>  
            <Name>AdventureWorksDW2012</Name>  
            <ConnectionString>Data Source=fr-dwk-02;Initial Catalog=AdventureWorksDW2008R2;Integrated Security=True</ConnectionString>  
            <ManagedProvider>System.Data.SqlClient</ManagedProvider>  
            <Timeout>PT30S</Timeout>  
        </DataSource>  
    </ObjectDefinition>  
</Alter>  
```  
  
### <a name="comments"></a><span data-ttu-id="7f931-164">注释</span><span class="sxs-lookup"><span data-stu-id="7f931-164">Comments</span></span>  
 <span data-ttu-id="7f931-165">`ObjectExpansion`命令的属性 `Alter` 已设置为*ObjectProperties*。</span><span class="sxs-lookup"><span data-stu-id="7f931-165">The `ObjectExpansion` attribute of the `Alter` command was set to *ObjectProperties*.</span></span> <span data-ttu-id="7f931-166">此设置允许从中定义的数据源中排除[ImpersonationInfo](https://docs.microsoft.com/bi-reference/assl/properties/impersonationinfo-element-assl)元素（次要对象） `ObjectDefinition` 。</span><span class="sxs-lookup"><span data-stu-id="7f931-166">This setting allows the [ImpersonationInfo](https://docs.microsoft.com/bi-reference/assl/properties/impersonationinfo-element-assl) element, a minor object, to be excluded from the data source defined in `ObjectDefinition`.</span></span> <span data-ttu-id="7f931-167">因此，该数据源的模拟信息仍设置为在第一个示例中所指定的服务帐户。</span><span class="sxs-lookup"><span data-stu-id="7f931-167">Therefore, the impersonation information for that data source remains set to the service account, as specified in the first example.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f931-168">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7f931-168">See Also</span></span>  
 <span data-ttu-id="7f931-169">[&#40;XMLA 的 Execute 方法&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) </span><span class="sxs-lookup"><span data-stu-id="7f931-169">[Execute Method &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) </span></span>  
 <span data-ttu-id="7f931-170">[Analysis Services 脚本语言开发 &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md) </span><span class="sxs-lookup"><span data-stu-id="7f931-170">[Developing with Analysis Services Scripting Language &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md) </span></span>  
 [<span data-ttu-id="7f931-171">在 Analysis Services 中使用 XMLA 开发</span><span class="sxs-lookup"><span data-stu-id="7f931-171">Developing with XMLA in Analysis Services</span></span>](developing-with-xmla-in-analysis-services.md)  
  
  
