---
title: 实现外部元数据 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- disconnected validation [Integration Services]
- connected validation [Integration Services]
- custom data flow components [Integration Services], validating
- validation [Integration Services], components
- metadata [Integration Services]
- data flow components [Integration Services], validating
- data flow components [Integration Services], external metadata
- custom data flow components [Integration Services], external metadata
- external metadata [Integration Services]
ms.assetid: 8f5bd3ed-3e79-43a4-b6c1-435e4c2cc8cc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7a6b77229c528bc08057e662a4b3761d1daf732f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688064"
---
# <a name="implementing-external-metadata"></a><span data-ttu-id="b5e14-102">实现外部元数据</span><span class="sxs-lookup"><span data-stu-id="b5e14-102">Implementing External Metadata</span></span>
  <span data-ttu-id="b5e14-103">组件与其数据源断开连接后，可以使用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100> 接口，针对组件的外部数据源中的列验证输入和输出列集合中的列。</span><span class="sxs-lookup"><span data-stu-id="b5e14-103">When a component is disconnected from its data source, you can validate the columns in the input and output column collections against the columns at its external data source by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100> interface.</span></span> <span data-ttu-id="b5e14-104">使用此接口可以保留一份外部数据源中的列的快照，并可以将这些列映射到组件的输入和输出列集合中的列。</span><span class="sxs-lookup"><span data-stu-id="b5e14-104">This interface lets you maintain a snapshot of the columns at the external data source and map these columns to the columns in the input and output column collection of the component.</span></span>  
  
 <span data-ttu-id="b5e14-105">实现外部元数据列会增加组件开发的开销和复杂度，因为您必须额外保留和验证列集合，但这却能节省往返于服务器进行验证的昂贵开销，从而使得这项开发工作是值得的。</span><span class="sxs-lookup"><span data-stu-id="b5e14-105">Implementing external metadata columns adds a layer of overhead and complexity to component development, because you must maintain and validate against an additional column collection, but the ability to avoid expensive round trips to the server for validation may make this development work worthwhile.</span></span>  
  
## <a name="populating-external-metadata-columns"></a><span data-ttu-id="b5e14-106">填充外部元数据列</span><span class="sxs-lookup"><span data-stu-id="b5e14-106">Populating External Metadata Columns</span></span>  
 <span data-ttu-id="b5e14-107">通常，外部元数据列在创建相应的输入或输出列时即添加到集合中。</span><span class="sxs-lookup"><span data-stu-id="b5e14-107">External metadata columns are typically added to the collection when the corresponding input or output column is created.</span></span> <span data-ttu-id="b5e14-108">新列是通过调用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100.New%2A> 方法创建的。</span><span class="sxs-lookup"><span data-stu-id="b5e14-108">New columns are created by calling the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100.New%2A> method.</span></span> <span data-ttu-id="b5e14-109">然后，设置列的属性，使其与外部数据源相匹配。</span><span class="sxs-lookup"><span data-stu-id="b5e14-109">The properties of the column are then set to match the external data source.</span></span>  
  
 <span data-ttu-id="b5e14-110">通过向输入或输出列的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.ExternalMetadataColumnID%2A> 属性分配外部元数据列的 ID，外部元数据列即可映射到相应的输入或输出列。</span><span class="sxs-lookup"><span data-stu-id="b5e14-110">The external metadata column is mapped to the corresponding input or output column by assigning the ID of the external metadata column to the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.ExternalMetadataColumnID%2A> property of the input or output column.</span></span> <span data-ttu-id="b5e14-111">这使您可以使用集合的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100.GetObjectByID%2A> 方法，轻松地查找与特定输入或输出列对应的外部元数据列。</span><span class="sxs-lookup"><span data-stu-id="b5e14-111">This lets you locate the external metadata column easily for a specific input or output column by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100.GetObjectByID%2A> method of the collection.</span></span>  
  
 <span data-ttu-id="b5e14-112">下面的示例演示如何创建一个外部元数据列，然后通过设置 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.ExternalMetadataColumnID%2A> 属性将其映射到一个输出列。</span><span class="sxs-lookup"><span data-stu-id="b5e14-112">The following example shows how to create an external metadata column and then map the column to an output column by setting the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.ExternalMetadataColumnID%2A> property.</span></span>  
  
```csharp  
public void CreateExternalMetaDataColumn(IDTSOutput100 output, int outputColumnID )  
{  
    IDTSOutputColumn100 oColumn = output.OutputColumnCollection.GetObjectByID(outputColumnID);  
    IDTSExternalMetadataColumn100 eColumn = output.ExternalMetadataColumnCollection.New();  
  
    eColumn.DataType = oColumn.DataType;  
    eColumn.Precision = oColumn.Precision;  
    eColumn.Scale = oColumn.Scale;  
    eColumn.Length = oColumn.Length;  
    eColumn.CodePage = oColumn.CodePage;  
  
    oColumn.ExternalMetadataColumnID = eColumn.ID;  
}  
```  
  
```vb  
Public Sub CreateExternalMetaDataColumn(ByVal output As IDTSOutput100, ByVal outputColumnID As Integer)   
 Dim oColumn As IDTSOutputColumn100 = output.OutputColumnCollection.GetObjectByID(outputColumnID)   
 Dim eColumn As IDTSExternalMetadataColumn100 = output.ExternalMetadataColumnCollection.New   
 eColumn.DataType = oColumn.DataType   
 eColumn.Precision = oColumn.Precision   
 eColumn.Scale = oColumn.Scale   
 eColumn.Length = oColumn.Length   
 eColumn.CodePage = oColumn.CodePage   
 oColumn.ExternalMetadataColumnID = eColumn.ID   
End Sub  
```  
  
## <a name="validating-with-external-metadata-columns"></a><span data-ttu-id="b5e14-113">使用外部元数据列进行验证</span><span class="sxs-lookup"><span data-stu-id="b5e14-113">Validating with External Metadata Columns</span></span>  
 <span data-ttu-id="b5e14-114">对于保留外部元数据列集合的组件，验证还需要完成其他步骤，因为必须验证附加的列集合。</span><span class="sxs-lookup"><span data-stu-id="b5e14-114">Validation requires additional steps for components that maintain an external metadata column collection, because you must validate against an additional collection of columns.</span></span> <span data-ttu-id="b5e14-115">验证可分为连接下的验证和断开连接下的验证。</span><span class="sxs-lookup"><span data-stu-id="b5e14-115">Validation can be divided into connected validation or disconnected validation.</span></span>  
  
### <a name="connected-validation"></a><span data-ttu-id="b5e14-116">连接下的验证</span><span class="sxs-lookup"><span data-stu-id="b5e14-116">Connected Validation</span></span>  
 <span data-ttu-id="b5e14-117">组件与外部数据源处于连接状态时，输入或输出集合中的列是直接与外部数据源相验证的。</span><span class="sxs-lookup"><span data-stu-id="b5e14-117">When a component is connected to an external data source, the columns in the input or output collections are verified directly against the external data source.</span></span> <span data-ttu-id="b5e14-118">另外，还必须验证外部元数据集合中的列。</span><span class="sxs-lookup"><span data-stu-id="b5e14-118">Additionally, the columns in the external metadata collection must be validated.</span></span> <span data-ttu-id="b5e14-119">如此要求的原因是，外部元数据集合可使用 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 中的“高级编辑器”来修改，而且对该集合所做的更改是无法检测的。</span><span class="sxs-lookup"><span data-stu-id="b5e14-119">This is required because the external metadata collection can be modified by using the **Advanced Editor** in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], and changes made to the collection are not detectable.</span></span> <span data-ttu-id="b5e14-120">因此，处于连接状态时，组件必须确保外部元数据列集合中的列始终反映外部数据源中的列。</span><span class="sxs-lookup"><span data-stu-id="b5e14-120">Therefore, when connected, components must make sure that the columns in the external metadata column collection continue to reflect the columns at the external data source.</span></span>  
  
 <span data-ttu-id="b5e14-121">您可以选择在**高级编辑器**中隐藏外部元数据集合，方法是将 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100.IsUsed%2A> 该集合的属性设置 `false` 为。</span><span class="sxs-lookup"><span data-stu-id="b5e14-121">You may choose to hide the external metadata collection in the **Advanced Editor** by setting the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100.IsUsed%2A> property of the collection to `false`.</span></span> <span data-ttu-id="b5e14-122">但这也会隐藏编辑器的“列映射”  选项卡，该选项卡允许用户将输入或输出集合中的列映射到外部元数据列集合中的列。</span><span class="sxs-lookup"><span data-stu-id="b5e14-122">However this also hides the **Column Mapping** tab of the editor, which lets users map columns from the input or output collection to the columns in the external metadata column collection.</span></span> <span data-ttu-id="b5e14-123">将此属性设置为 `false` 不会阻止开发人员以编程方式修改外部元数据列集合，而会为在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 中独占使用的组件的外部元数据列集合提供一定程度的保护。</span><span class="sxs-lookup"><span data-stu-id="b5e14-123">Setting this property to `false` does not prevent developers from programmatically modifying the collection, but it does provide a level of protection for the external metadata column collection of a component that is used exclusively in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
### <a name="disconnected-validation"></a><span data-ttu-id="b5e14-124">断开连接下的验证</span><span class="sxs-lookup"><span data-stu-id="b5e14-124">Disconnected Validation</span></span>  
 <span data-ttu-id="b5e14-125">组件与外部数据源断开连接后，验证即可简化，因为输入或输出集合中的列将直接与外部元数据集合中的列相验证，而不会验证外部源。</span><span class="sxs-lookup"><span data-stu-id="b5e14-125">When a component is disconnected from an external data source, validation is simplified because the columns in the input or output collection are verified directly against the columns in the external metadata collection and not against the external source.</span></span> <span data-ttu-id="b5e14-126">如果组件与其外部数据源之间的连接尚未建立，或者 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ValidateExternalMetadata%2A> 属性为 `false`，则组件应执行断开连接下的验证。</span><span class="sxs-lookup"><span data-stu-id="b5e14-126">A component should perform disconnected validation when the connection to its external data source has not been established, or when the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ValidateExternalMetadata%2A> property is `false`.</span></span>  
  
 <span data-ttu-id="b5e14-127">下面的代码示例演示了执行与其外部元数据列集合相验证的组件的实现。</span><span class="sxs-lookup"><span data-stu-id="b5e14-127">The following code example demonstrates an implementation of a component that performs validation against its external metadata column collection.</span></span>  
  
```csharp  
public override DTSValidationStatus Validate()  
{  
    if( this.isConnected && ComponentMetaData.ValidateExternalMetaData )  
    {  
        // TODO: Perform connected validation.  
    }  
    else  
    {  
        // TODO: Perform disconnected validation.  
    }  
}  
```  
  
```vb  
Public  Overrides Function Validate() As DTSValidationStatus   
 If Me.isConnected AndAlso ComponentMetaData.ValidateExternalMetaData Then   
  ' TODO: Perform connected validation.  
 Else   
  ' TODO: Perform disconnected validation.  
 End If   
End Function  
```  
  
<span data-ttu-id="b5e14-128">![Integration Services 图标 (小型) ](../../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="b5e14-128">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="b5e14-129">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="b5e14-129">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="b5e14-130">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="b5e14-130">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="b5e14-131">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="b5e14-131">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5e14-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b5e14-132">See Also</span></span>  
 [<span data-ttu-id="b5e14-133">数据流</span><span class="sxs-lookup"><span data-stu-id="b5e14-133">Data Flow</span></span>](../../data-flow/data-flow.md)  
  
  
