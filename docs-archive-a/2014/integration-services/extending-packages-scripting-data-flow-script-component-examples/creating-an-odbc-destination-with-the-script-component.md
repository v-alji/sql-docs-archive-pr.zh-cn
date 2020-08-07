---
title: 使用脚本组件创建 ODBC 目标 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], destination components
- ODBC destination [Integration Services]
- destinations [Integration Services], components
- Script component [Integration Services], examples
ms.assetid: d198c866-78f4-4a50-ae15-333160645815
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 10adff11a7e1db24d9a244c3e83949a010b606c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587918"
---
# <a name="creating-an-odbc-destination-with-the-script-component"></a><span data-ttu-id="65e01-102">使用脚本组件创建 ODBC 目标</span><span class="sxs-lookup"><span data-stu-id="65e01-102">Creating an ODBC Destination with the Script Component</span></span>
  <span data-ttu-id="65e01-103">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 中，通常使用 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 目标和用于 ODBC 的 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 数据提供程序将数据保存到 ODBC 目标。</span><span class="sxs-lookup"><span data-stu-id="65e01-103">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], you typically save data to an ODBC destination by using an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] destination and the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Data Provider for ODBC.</span></span> <span data-ttu-id="65e01-104">当然，还可以创建供单个包使用的即席 ODBC 目标。</span><span class="sxs-lookup"><span data-stu-id="65e01-104">However, you can also create an ad hoc ODBC destination for use in a single package.</span></span> <span data-ttu-id="65e01-105">若要创建此即席 ODBC 目标，可使用脚本组件，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="65e01-105">To create this ad hoc ODBC destination, you use the Script component as shown in the following example.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="65e01-106">如果希望创建可更方便地重用于多个数据流任务和多个包的组件，请考虑以此脚本组件示例中的代码为基础，创建自定义数据流组件。</span><span class="sxs-lookup"><span data-stu-id="65e01-106">If you want to create a component that you can more easily reuse across multiple Data Flow tasks and multiple packages, consider using the code in this Script component sample as the starting point for a custom data flow component.</span></span> <span data-ttu-id="65e01-107">有关详细信息，请参阅 [开发自定义数据流组件](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="65e01-107">For more information, see [Developing a Custom Data Flow Component](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="65e01-108">示例</span><span class="sxs-lookup"><span data-stu-id="65e01-108">Example</span></span>  
 <span data-ttu-id="65e01-109">下面的示例演示如何创建一个目标组件，该组件使用现有 ODBC 连接管理器将数据流中的数据保存到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表。</span><span class="sxs-lookup"><span data-stu-id="65e01-109">The following example demonstrates how to create a destination component that uses an existing ODBC connection manager to save data from the data flow into a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="65e01-110">本示例是[使用脚本组件创建目标](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)主题中演示的自定义 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 目标的修改版本。</span><span class="sxs-lookup"><span data-stu-id="65e01-110">This example is a modified version of the custom [!INCLUDE[vstecado](../../includes/vstecado-md.md)] destination that was demonstrated in the topic, [Creating a Destination with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md).</span></span> <span data-ttu-id="65e01-111">但是，在此示例中，自定义 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 目标已修改为使用 ODBC 连接管理器并将数据保存到 ODBC 目标。</span><span class="sxs-lookup"><span data-stu-id="65e01-111">However, in this example, the custom [!INCLUDE[vstecado](../../includes/vstecado-md.md)] destination has been modified to work with an ODBC connection manager and save data to an ODBC destination.</span></span> <span data-ttu-id="65e01-112">此外，还包括以下更改：</span><span class="sxs-lookup"><span data-stu-id="65e01-112">These modifications also include the following changes:</span></span>  
  
-   <span data-ttu-id="65e01-113">不能从托管代码调用 ODBC 连接管理器的 `AcquireConnection` 方法，因为它返回的是一个本机对象。</span><span class="sxs-lookup"><span data-stu-id="65e01-113">You cannot call the `AcquireConnection` method of the ODBC connection manager from managed code, because it returns a native object.</span></span> <span data-ttu-id="65e01-114">因此，本示例使用连接管理器的连接字符串通过托管 ODBC [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 数据访问接口直接连接到数据源。</span><span class="sxs-lookup"><span data-stu-id="65e01-114">Therefore, this sample uses the connection string of the connection manager to connect to the data source directly by using the managed ODBC [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Data Provider.</span></span>  
  
-   <span data-ttu-id="65e01-115">`OdbcCommand` 需要位置参数。</span><span class="sxs-lookup"><span data-stu-id="65e01-115">The `OdbcCommand` expects positional parameters.</span></span> <span data-ttu-id="65e01-116">在命令的文本中，参数的位置由问号 (?) 指示。</span><span class="sxs-lookup"><span data-stu-id="65e01-116">The positions of the parameters are indicated by the question marks (?) in the text of the command.</span></span> <span data-ttu-id="65e01-117">（相反，`SqlCommand` 需要命名参数。）</span><span class="sxs-lookup"><span data-stu-id="65e01-117">(In contrast, a `SqlCommand` expects named parameters.)</span></span>  
  
 <span data-ttu-id="65e01-118">本示例使用 **AdventureWorks** 示例数据库中的 **Person.Address** 表。</span><span class="sxs-lookup"><span data-stu-id="65e01-118">This example uses the **Person.Address** table in the **AdventureWorks** sample database.</span></span> <span data-ttu-id="65e01-119">本示例在数据流中传递该表的第一列和第四列：int\*AddressID\*\*\*\*\* 和 nvarchar(30)City\*\*\*\* 列。</span><span class="sxs-lookup"><span data-stu-id="65e01-119">The example passes the first and fourth columns, the **int\*AddressID**\* and **nvarchar(30)City** columns, of this table through the data flow.</span></span> <span data-ttu-id="65e01-120">[开发特定类型的脚本组件](../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md)主题中的源、转换和目标示例使用了相同的数据。</span><span class="sxs-lookup"><span data-stu-id="65e01-120">This same data is used in the source, transformation, and destination samples in the topic, [Developing Specific Types of Script Components](../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md).</span></span>  
  
#### <a name="to-configure-this-script-component-example"></a><span data-ttu-id="65e01-121">配置此脚本组件示例</span><span class="sxs-lookup"><span data-stu-id="65e01-121">To configure this Script Component example</span></span>  
  
1.  <span data-ttu-id="65e01-122">创建连接 **AdventureWorks** 数据库的 ODBC 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="65e01-122">Create an ODBC connection manager that connects to the **AdventureWorks** database.</span></span>  
  
2.  <span data-ttu-id="65e01-123">通过在 **AdventureWorks** 数据库中运行以下 Transact-SQL 命令来创建一个目标表：</span><span class="sxs-lookup"><span data-stu-id="65e01-123">Create a destination table by running the following Transact-SQL command in the **AdventureWorks** database:</span></span>  
  
    ```  
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,  
        [City] [nvarchar](30) NOT NULL)  
    ```  
  
3.  <span data-ttu-id="65e01-124">向数据流设计器图面添加新的脚本组件并将其配置为目标。</span><span class="sxs-lookup"><span data-stu-id="65e01-124">Add a new Script component to the Data Flow designer surface and configure it as a destination.</span></span>  
  
4.  <span data-ttu-id="65e01-125">在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中将上游源或转换的输出连接到目标组件。</span><span class="sxs-lookup"><span data-stu-id="65e01-125">Connect the output of an upstream source or transformation to the destination component in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="65e01-126">（无需任何转换，即可将源直接连接到目标。）为了确保本示例能够正常工作，上游组件的输出必须至少包含 **AdventureWorks** 示例数据库的 **Person.Address** 表中的 **AddressID** 和 **City** 列。</span><span class="sxs-lookup"><span data-stu-id="65e01-126">(You can connect a source directly to a destination without any transformations.) To ensure that this sample works, the output of the upstream component must include at least the **AddressID** and **City** columns from the **Person.Address** table of the **AdventureWorks** sample database.</span></span>  
  
5.  <span data-ttu-id="65e01-127">打开“脚本转换编辑器”  。</span><span class="sxs-lookup"><span data-stu-id="65e01-127">Open the **Script Transformation Editor**.</span></span> <span data-ttu-id="65e01-128">在“输入列”  页中，选择 AddressID  和 City  列。</span><span class="sxs-lookup"><span data-stu-id="65e01-128">On the **Input Columns** page, select the **AddressID** and **City** columns.</span></span>  
  
6.  <span data-ttu-id="65e01-129">在“输入和输出”  页中，用更具说明性的名称（如 **MyAddressInput**）重命名输入。</span><span class="sxs-lookup"><span data-stu-id="65e01-129">On the **Inputs and Outputs** page, rename the input with a more descriptive name such as **MyAddressInput**.</span></span>  
  
7.  <span data-ttu-id="65e01-130">在“连接管理器”  页中，添加或创建一个具有说明性名称（如 **MyODBCConnectionManager**）的 ODBC 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="65e01-130">On the **Connection Managers** page, add or create the ODBC connection manager with a descriptive name such as **MyODBCConnectionManager**.</span></span>  
  
8.  <span data-ttu-id="65e01-131">在 "**脚本**" 页上，单击 "**编辑脚本**"，然后在类中输入下面所示的脚本 `ScriptMain` 。</span><span class="sxs-lookup"><span data-stu-id="65e01-131">On the **Script** page, click **Edit Script**, and then enter the script shown below in the `ScriptMain` class.</span></span>  
  
9. <span data-ttu-id="65e01-132">关闭脚本开发环境和“脚本转换编辑器”  ，然后运行该示例。</span><span class="sxs-lookup"><span data-stu-id="65e01-132">Close the script development environment, close the **Script Transformation Editor**, and then run the sample.</span></span>  
  
    ```vb  
    Imports System.Data.Odbc  
    ...  
    Public Class ScriptMain  
        Inherits UserComponent  
  
        Dim odbcConn As OdbcConnection  
        Dim odbcCmd As OdbcCommand  
        Dim odbcParam As OdbcParameter  
  
        Public Overrides Sub AcquireConnections(ByVal Transaction As Object)  
  
            Dim connectionString As String  
            connectionString = Me.Connections.MyODBCConnectionManager.ConnectionString  
            odbcConn = New OdbcConnection(connectionString)  
            odbcConn.Open()  
  
        End Sub  
  
        Public Overrides Sub PreExecute()  
  
            odbcCmd = New OdbcCommand("INSERT INTO Person.Address2(AddressID, City) " & _  
                "VALUES(?, ?)", odbcConn)  
            odbcParam = New OdbcParameter("@addressid", OdbcType.Int)  
            odbcCmd.Parameters.Add(odbcParam)  
            odbcParam = New OdbcParameter("@city", OdbcType.NVarChar, 30)  
            odbcCmd.Parameters.Add(odbcParam)  
  
        End Sub  
  
        Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)  
  
            With odbcCmd  
                .Parameters("@addressid").Value = Row.AddressID  
                .Parameters("@city").Value = Row.City  
                .ExecuteNonQuery()  
            End With  
  
        End Sub  
  
        Public Overrides Sub ReleaseConnections()  
  
            odbcConn.Close()  
  
        End Sub  
  
    End Class  
    ```  
  
    ```csharp  
    using System.Data.Odbc;  
    ...  
    public class ScriptMain :  
        UserComponent  
    {  
        OdbcConnection odbcConn;  
        OdbcCommand odbcCmd;  
        OdbcParameter odbcParam;  
  
        public override void AcquireConnections(object Transaction)  
        {  
  
            string connectionString;  
            connectionString = this.Connections.MyODBCConnectionManager.ConnectionString;  
            odbcConn = new OdbcConnection(connectionString);  
            odbcConn.Open();  
  
        }  
  
        public override void PreExecute()  
        {  
  
            odbcCmd = new OdbcCommand("INSERT INTO Person.Address2(AddressID, City) " +  
                "VALUES(?, ?)", odbcConn);  
            odbcParam = new OdbcParameter("@addressid", OdbcType.Int);  
            odbcCmd.Parameters.Add(odbcParam);  
            odbcParam = new OdbcParameter("@city", OdbcType.NVarChar, 30);  
            odbcCmd.Parameters.Add(odbcParam);  
  
        }  
  
        public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)  
        {  
  
            {  
                odbcCmd.Parameters["@addressid"].Value = Row.AddressID;  
                odbcCmd.Parameters["@city"].Value = Row.City;  
                odbcCmd.ExecuteNonQuery();  
            }  
  
        }  
  
        public override void ReleaseConnections()  
        {  
  
            odbcConn.Close();  
  
        }  
    }  
    ```  
  
<span data-ttu-id="65e01-133">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="65e01-133">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="65e01-134">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="65e01-134">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="65e01-135">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="65e01-135">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="65e01-136">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="65e01-136">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65e01-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="65e01-137">See Also</span></span>  
 [<span data-ttu-id="65e01-138">使用脚本组件创建目标</span><span class="sxs-lookup"><span data-stu-id="65e01-138">Creating a Destination with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)  
  
  
