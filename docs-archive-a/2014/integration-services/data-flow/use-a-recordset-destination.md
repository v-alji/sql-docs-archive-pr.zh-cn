---
title: 使用记录集目标 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Recordset destination
ms.assetid: a7b143dc-8008-404f-83b0-b45ffbca6029
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 34d1d5a7aa76876a9d8718b691b1d24a8835e2e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589773"
---
# <a name="use-a-recordset-destination"></a><span data-ttu-id="c5208-102">使用记录集目标</span><span class="sxs-lookup"><span data-stu-id="c5208-102">Use a Recordset Destination</span></span>
  <span data-ttu-id="c5208-103">记录集目标不会将数据保存到外部数据源中，</span><span class="sxs-lookup"><span data-stu-id="c5208-103">The Recordset destination does not save data to an external data source.</span></span> <span data-ttu-id="c5208-104">而是将数据保存在內存中的一个记录集中，该记录集存储在数据类型为 `Object` 的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包变量中。</span><span class="sxs-lookup"><span data-stu-id="c5208-104">Instead, the Recordset destination saves data in memory in a recordset that is stored in an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package variable of the `Object` data type.</span></span> <span data-ttu-id="c5208-105">在记录集目标保存数据之后，通常使用具有 Foreach ADO 枚举器的 Foreach 循环容器来每次处理记录集的一行。</span><span class="sxs-lookup"><span data-stu-id="c5208-105">After the Recordset destination saves the data, you typically use a Foreach Loop container with the Foreach ADO enumerator to process one row of the recordset at a time.</span></span> <span data-ttu-id="c5208-106">Foreach ADO 枚举器将当前行中每列的值保存到单独的包变量中。</span><span class="sxs-lookup"><span data-stu-id="c5208-106">The Foreach ADO enumerator saves the value from each column of the current row into a separate package variable.</span></span> <span data-ttu-id="c5208-107">然后，您在 Foreach 循环容器中配置的任务会从变量中读取这些值，并对它们执行某些操作。</span><span class="sxs-lookup"><span data-stu-id="c5208-107">Then, the tasks that you configure inside the Foreach Loop container read those values from the variables and perform some action with them.</span></span>  
  
 <span data-ttu-id="c5208-108">可以在很多不同情况下使用记录集目标。</span><span class="sxs-lookup"><span data-stu-id="c5208-108">You can use the Recordset destination in many different scenarios.</span></span> <span data-ttu-id="c5208-109">下面是一些示例：</span><span class="sxs-lookup"><span data-stu-id="c5208-109">Here are some examples:</span></span>  
  
-   <span data-ttu-id="c5208-110">可以使用发送邮件任务和 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 表达式语言来为记录集中的每一行发送一封自定义电子邮件。</span><span class="sxs-lookup"><span data-stu-id="c5208-110">You can use a Send Mail task and the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] expression language to send a customized e-mail message for each row in the recordset.</span></span>  
  
-   <span data-ttu-id="c5208-111">可以使用在数据流任务中配置为源的脚本组件，将列值读入到数据流的相应列中。</span><span class="sxs-lookup"><span data-stu-id="c5208-111">You can use a Script component configured as a source, inside a Data Flow task, to read the column values into the columns of the data flow.</span></span> <span data-ttu-id="c5208-112">然后，可以使用转换和目标来转换和保存该行。</span><span class="sxs-lookup"><span data-stu-id="c5208-112">Then, you can use transformations and destinations to transform and save the row.</span></span> <span data-ttu-id="c5208-113">在本示例中，将针对每行运行一次数据流任务。</span><span class="sxs-lookup"><span data-stu-id="c5208-113">In this example, the Data Flow task runs once for each row.</span></span>  
  
 <span data-ttu-id="c5208-114">以下各节首先介绍使用记录集目标的一般过程，然后介绍如何使用目标的特定示例。</span><span class="sxs-lookup"><span data-stu-id="c5208-114">The following sections first describe the general process of using the Recordset destination and then show a specific example of how to use the destination.</span></span>  
  
## <a name="general-steps-to-using-a-recordset-destination"></a><span data-ttu-id="c5208-115">使用记录集目标的一般步骤</span><span class="sxs-lookup"><span data-stu-id="c5208-115">General Steps to Using a Recordset Destination</span></span>  
 <span data-ttu-id="c5208-116">以下过程总结了将数据保存到记录集目标然后使用 Foreach 循环容器来处理每行所需的步骤。</span><span class="sxs-lookup"><span data-stu-id="c5208-116">The following procedure summarizes the steps that are required to save data to a Recordset destination, and then use the Foreach Loop container to process each row.</span></span>  
  
#### <a name="to-save-data-to-a-recordset-destination-and-process-each-row-by-using-the-foreach-loop-container"></a><span data-ttu-id="c5208-117">将数据保存到记录集目标，然后使用 Foreach 循环容器来处理每行</span><span class="sxs-lookup"><span data-stu-id="c5208-117">To save data to a Recordset destination and process each row by using the Foreach Loop container</span></span>  
  
1.  <span data-ttu-id="c5208-118">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，创建或打开 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="c5208-118">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], create or open an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package.</span></span>  
  
2.  <span data-ttu-id="c5208-119">创建一个用来包含由记录集目标保存到内存中的记录集的变量，然后将该变量的类型设置为 `Object`。</span><span class="sxs-lookup"><span data-stu-id="c5208-119">Create a variable that will contain the recordset saved into memory by the Recordset destination, and set the variable's type to `Object`.</span></span>  
  
3.  <span data-ttu-id="c5208-120">创建适当类型的其他变量，用来包含您要使用的记录集的每列的值。</span><span class="sxs-lookup"><span data-stu-id="c5208-120">Create additional variables of the appropriate types to contain the values of each column in the recordset that you want to use.</span></span>  
  
4.  <span data-ttu-id="c5208-121">添加和配置您计划在数据流中使用的数据源所需的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="c5208-121">Add and configure the connection manager required by the data source that you plan to use in your data flow.</span></span>  
  
5.  <span data-ttu-id="c5208-122">向包中添加数据流任务，然后在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器的“数据流”选项卡上配置源和转换，以加载并转换数据。</span><span class="sxs-lookup"><span data-stu-id="c5208-122">Add a Data Flow task to the package, and on the Data Flow tab of [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, configure sources and transformations to load and transform the data.</span></span>  
  
6.  <span data-ttu-id="c5208-123">向数据流中添加记录集目标，并将其连接到转换。</span><span class="sxs-lookup"><span data-stu-id="c5208-123">Add a Recordset destination to the data flow and connect it to the transformations.</span></span> <span data-ttu-id="c5208-124">对于记录集目标的 `VariableName` 属性，输入您创建的用来保存该记录集的变量的名称。</span><span class="sxs-lookup"><span data-stu-id="c5208-124">For the `VariableName` property of the Recordset destination, enter the name of the variable that you created to hold the recordset.</span></span>  
  
7.  <span data-ttu-id="c5208-125">在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器的“控制流”选项卡上，添加 Foreach 循环容器，并在数据流任务之后连接此容器。</span><span class="sxs-lookup"><span data-stu-id="c5208-125">On the Control Flow tab of [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, add a Foreach Loop container and connect this container after the Data Flow task.</span></span> <span data-ttu-id="c5208-126">然后，打开 **“Foreach 循环编辑器”** ，使用以下设置来配置容器：</span><span class="sxs-lookup"><span data-stu-id="c5208-126">Then, open the **Foreach Loop Editor** to configure the container with the following settings:</span></span>  
  
    1.  <span data-ttu-id="c5208-127">在 **“集合”** 页上，选择 Foreach ADO 枚举器。</span><span class="sxs-lookup"><span data-stu-id="c5208-127">On the **Collection** page, select the Foreach ADO Enumerator.</span></span> <span data-ttu-id="c5208-128">然后，对于 **“ADO 对象源变量”** ，选择包含该记录集的变量。</span><span class="sxs-lookup"><span data-stu-id="c5208-128">Then, for **ADO object source variable**, select the variable that contains the recordset.</span></span>  
  
    2.  <span data-ttu-id="c5208-129">在“变量映射”  页上，将你要使用的每列的基于零的索引映射到适当的变量。</span><span class="sxs-lookup"><span data-stu-id="c5208-129">On the **Variable Mappings** page, map the zero-based index of each column that you want to use to the appropriate variable.</span></span>  
  
         <span data-ttu-id="c5208-130">在循环的每次迭代中，枚举器使用当前行的列值来填充这些变量。</span><span class="sxs-lookup"><span data-stu-id="c5208-130">On each iteration of the loop, the enumerator populates these variables with the column values from the current row.</span></span>  
  
8.  <span data-ttu-id="c5208-131">在 Foreach 循环容器中，添加并配置任务以通过从变量读取值来每次处理记录集的一行。</span><span class="sxs-lookup"><span data-stu-id="c5208-131">Inside the Foreach Loop container, add and configure tasks to process one row of the recordset at a time by reading the values from the variables.</span></span>  
  
## <a name="example-of-using-the-recordset-destination"></a><span data-ttu-id="c5208-132">使用记录集目标的示例</span><span class="sxs-lookup"><span data-stu-id="c5208-132">Example of Using the Recordset Destination</span></span>  
 <span data-ttu-id="c5208-133">在以下示例中，数据流任务将有关 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 雇员的信息从 Sales.SalesPerson 表加载到记录集目标中。</span><span class="sxs-lookup"><span data-stu-id="c5208-133">In the following example, the Data Flow task loads information about [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] employees from the Sales.SalesPerson table into a Recordset destination.</span></span> <span data-ttu-id="c5208-134">然后，Foreach 循环容器每次读取一行数据，并调用发送邮件任务。</span><span class="sxs-lookup"><span data-stu-id="c5208-134">Then, a Foreach Loop container reads one row of data at a time, and calls a Send Mail task.</span></span> <span data-ttu-id="c5208-135">发送邮件任务使用表达式将有关奖金额的自定义电子邮件发送给每位销售人员。</span><span class="sxs-lookup"><span data-stu-id="c5208-135">The Send Mail task uses expressions to send a customized e-mail message to each salesperson about the amount of his or her bonus.</span></span>  
  
#### <a name="to-create-the-project-and-configure-the-variables"></a><span data-ttu-id="c5208-136">创建项目和配置变量</span><span class="sxs-lookup"><span data-stu-id="c5208-136">To create the project and configure the variables</span></span>  
  
1.  <span data-ttu-id="c5208-137">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中，创建新的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="c5208-137">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], create a new [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project.</span></span>  
  
2.  <span data-ttu-id="c5208-138">在 **SSIS** 菜单上，选择 **“变量”** 。</span><span class="sxs-lookup"><span data-stu-id="c5208-138">On the **SSIS** menu, select **Variables**.</span></span>  
  
3.  <span data-ttu-id="c5208-139">在 **“变量”** 窗口中，创建用来保存记录集和当前行的列值的变量：</span><span class="sxs-lookup"><span data-stu-id="c5208-139">In the **Variables** window, create the variables that will hold the recordset and the column values from the current row:</span></span>  
  
    1.  <span data-ttu-id="c5208-140">创建名为 `BonusRecordset` 的变量，然后将其类型设置为 `Object`。</span><span class="sxs-lookup"><span data-stu-id="c5208-140">Create a variable named, `BonusRecordset`, and set its type to `Object`.</span></span>  
  
         <span data-ttu-id="c5208-141">`BonusRecordset` 变量保存记录集。</span><span class="sxs-lookup"><span data-stu-id="c5208-141">The `BonusRecordset` variable holds the recordset.</span></span>  
  
    2.  <span data-ttu-id="c5208-142">创建名为 `EmailAddress` 的变量，然后将其类型设置为 `String`。</span><span class="sxs-lookup"><span data-stu-id="c5208-142">Create a variable named, `EmailAddress`, and set its type to `String`.</span></span>  
  
         <span data-ttu-id="c5208-143">`EmailAddress` 变量保存销售人员的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="c5208-143">The `EmailAddress` variable holds the salesperson's e-mail address.</span></span>  
  
    3.  <span data-ttu-id="c5208-144">创建名为 `FirstName` 的变量，然后将其类型设置为 `String`。</span><span class="sxs-lookup"><span data-stu-id="c5208-144">Create a variable named, `FirstName`, and set its type to `String`.</span></span>  
  
         <span data-ttu-id="c5208-145">`FirstName` 变量保存销售人员的名字。</span><span class="sxs-lookup"><span data-stu-id="c5208-145">The `FirstName` variable holds the salesperson's first name.</span></span>  
  
    4.  <span data-ttu-id="c5208-146">创建名为 `Bonus` 的变量，然后将其类型设置为 `Double`。</span><span class="sxs-lookup"><span data-stu-id="c5208-146">Create a variable named, `Bonus`, and set its type to `Double`.</span></span>  
  
         <span data-ttu-id="c5208-147">`Bonus` 变量保存销售人员的奖金额。</span><span class="sxs-lookup"><span data-stu-id="c5208-147">The `Bonus` variable holds the amount of the salesperson's bonus.</span></span>  
  
#### <a name="to-configure-the-connection-managers"></a><span data-ttu-id="c5208-148">配置连接管理器</span><span class="sxs-lookup"><span data-stu-id="c5208-148">To configure the connection managers</span></span>  
  
1.  <span data-ttu-id="c5208-149">在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器的“连接管理器”区域中，添加并配置连接到 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 示例数据库的新 OLE DB 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="c5208-149">In the Connection Managers area of the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, add and configure a new OLE DB connection manager that connects to the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] sample database.</span></span>  
  
     <span data-ttu-id="c5208-150">数据流任务中的 OLE DB 源将使用此连接管理器来检索数据。</span><span class="sxs-lookup"><span data-stu-id="c5208-150">The OLE DB source in the Data Flow task will use this connection manager to retrieve data.</span></span>  
  
2.  <span data-ttu-id="c5208-151">在“连接管理器”区域中，添加并配置连接到可用 SMTP 服务器的新 SMTP 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="c5208-151">In the Connection Managers area, add and configure a new SMTP connection manager that connects to an available SMTP server.</span></span>  
  
     <span data-ttu-id="c5208-152">Foreach 循环容器中的发送邮件任务将使用此连接管理器来发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="c5208-152">The Send Mail task inside the Foreach Loop container will use this connection manager to send emails.</span></span>  
  
#### <a name="to-configure-the-data-flow-and-the-recordset-destination"></a><span data-ttu-id="c5208-153">配置数据流和记录集目标</span><span class="sxs-lookup"><span data-stu-id="c5208-153">To configure the data flow and the Recordset Destination</span></span>  
  
1.  <span data-ttu-id="c5208-154">在 **设计器的** “控制流” [!INCLUDE[ssIS](../../includes/ssis-md.md)] 选项卡上，将数据流任务添加到设计图面中。</span><span class="sxs-lookup"><span data-stu-id="c5208-154">On the **Control Flow** tab of [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, add a Data Flow task to the design surface.</span></span>  
  
2.  <span data-ttu-id="c5208-155">在 **“数据流”** tab, add an OLE DB source to the “数据流” task, and then open the **“OLE DB 源编辑器”** 。</span><span class="sxs-lookup"><span data-stu-id="c5208-155">On the **Data Flow** tab, add an OLE DB source to the Data Flow task, and then open the **OLE DB Source Editor.**</span></span>  
  
3.  <span data-ttu-id="c5208-156">在编辑器的 **“连接管理器”** 页上，使用以下设置来配置源：</span><span class="sxs-lookup"><span data-stu-id="c5208-156">On the **Connection Manager** page of the editor, configure the source with the following settings:</span></span>  
  
    1.  <span data-ttu-id="c5208-157">对于 **“OLE DB 连接管理器”** ，选择以前创建的 OLE DB 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="c5208-157">For **OLE DB connection manager**, select the OLE DB connection manager that you previously created.</span></span>  
  
    2.  <span data-ttu-id="c5208-158">对于 **“数据访问模式”** ，选择 **“SQL 命令”** 。</span><span class="sxs-lookup"><span data-stu-id="c5208-158">For **Data access mode**, select **SQL command**.</span></span>  
  
    3.  <span data-ttu-id="c5208-159">对于 **“SQL 命令文本”** ，输入以下查询：</span><span class="sxs-lookup"><span data-stu-id="c5208-159">For **SQL command text**, enter the following query:</span></span>  
  
        ```  
        SELECT     Person.Contact.EmailAddress, Person.Contact.FirstName, CONVERT(float, Sales.SalesPerson.Bonus) AS Bonus  
        FROM         Sales.SalesPerson INNER JOIN  
                              Person.Contact ON Sales.SalesPerson.SalesPersonID = Person.Contact.ContactID  
        ```  
  
        > [!NOTE]  
        >  <span data-ttu-id="c5208-160">必须先将 Bonus 列中 `currency` 值转换为 `float` 类型，然后才可以将该值加载到类型为 `Double` 的包变量中。</span><span class="sxs-lookup"><span data-stu-id="c5208-160">You have to convert the `currency` value in the Bonus column to a `float` before you can load that value into a package variable whose type is `Double`.</span></span>  
  
4.  <span data-ttu-id="c5208-161">在 **“数据流”** 选项卡上，添加记录集目标，并在 OLE DB 源之后连接该目标。</span><span class="sxs-lookup"><span data-stu-id="c5208-161">On the **Data Flow** tab, add a Recordset destination, and connect the destination after the OLE DB source.</span></span>  
  
5.  <span data-ttu-id="c5208-162">打开 **“记录集目标编辑器”** ，并使用以下设置来配置目标：</span><span class="sxs-lookup"><span data-stu-id="c5208-162">Open the **Recordset Destination Editor**, and configure the destination with the following settings:</span></span>  
  
    1.  <span data-ttu-id="c5208-163">在 "**组件属性**" 选项卡上，为 `VariableName` "属性" 选择 `User::BonusRecordset` 。</span><span class="sxs-lookup"><span data-stu-id="c5208-163">On the **Component Properties** tab, for `VariableName` property, select `User::BonusRecordset`.</span></span>  
  
    2.  <span data-ttu-id="c5208-164">在 **“输入列”** 选项卡上，选择所有三个可用列。</span><span class="sxs-lookup"><span data-stu-id="c5208-164">On the **Input Columns** tab, select all three of the available columns.</span></span>  
  
#### <a name="to-configure-the-foreach-loop-container-and-run-the-package"></a><span data-ttu-id="c5208-165">配置 Foreach 循环容器并运行包</span><span class="sxs-lookup"><span data-stu-id="c5208-165">To configure the Foreach Loop container and run the package</span></span>  
  
1.  <span data-ttu-id="c5208-166">在 **设计器的** “控制流” [!INCLUDE[ssIS](../../includes/ssis-md.md)] 选项卡上，添加 Foreach 循环容器，并在数据流任务之后连接该容器。</span><span class="sxs-lookup"><span data-stu-id="c5208-166">On the **Control Flow** tab of [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, add a Foreach Loop container, and connect the container after the Data Flow task.</span></span>  
  
2.  <span data-ttu-id="c5208-167">打开 **“Foreach 循环编辑器”** ，并使用以下设置来配置容器：</span><span class="sxs-lookup"><span data-stu-id="c5208-167">Open the **Foreach Loop Editor**, and configure the container with the following settings:</span></span>  
  
    1.  <span data-ttu-id="c5208-168">在 "**集合**" 页上，为 "**枚举器**" 选择 " **Foreach ADO 枚举器**"，对于 " **ADO 对象源变量**"，选择 `User::BonusRecordset` 。</span><span class="sxs-lookup"><span data-stu-id="c5208-168">On the **Collection** page, for **Enumerator**, select **Foreach ADO Enumerator**, and for **ADO object source variable**, select `User::BonusRecordset`.</span></span>  
  
    2.  <span data-ttu-id="c5208-169">在 "**变量映射**" 页上，将索引0映射到索引 `User::EmailAddress` `User::FirstName` 1，并映射到 `User::Bonus` 索引2。</span><span class="sxs-lookup"><span data-stu-id="c5208-169">On the **Variable Mappings** page, map `User::EmailAddress` to index 0, `User::FirstName` to index 1, and `User::Bonus` to index 2.</span></span>  
  
3.  <span data-ttu-id="c5208-170">在 **“控制流”** 选项卡的 Foreach 循环容器中，添加发送邮件任务。</span><span class="sxs-lookup"><span data-stu-id="c5208-170">On the **Control Flow** tab, inside the Foreach Loop container, add a Send Mail task.</span></span>  
  
4.  <span data-ttu-id="c5208-171">打开 **“发送邮件任务编辑器”** ，然后在 **“邮件”** 页上使用以下设置来配置任务：</span><span class="sxs-lookup"><span data-stu-id="c5208-171">Open the **Send Mail Task Editor**, and then on the **Mail** page, configure the task with the following settings:</span></span>  
  
    1.  <span data-ttu-id="c5208-172">对于 **SmtpConnection**，选择以前配置的 SMTP 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="c5208-172">For **SmtpConnection**, select the SMTP connection manager that was configured previously.</span></span>  
  
    2.  <span data-ttu-id="c5208-173">对于“发件人”，输入适当的电子邮件地址。 </span><span class="sxs-lookup"><span data-stu-id="c5208-173">For **From**, enter an appropriate e-mail address.</span></span>  
  
         <span data-ttu-id="c5208-174">如果使用自己的电子邮件地址，则可以确认包成功运行。</span><span class="sxs-lookup"><span data-stu-id="c5208-174">If you use your own e-mail address, you will be able to confirm that the package runs successfully.</span></span> <span data-ttu-id="c5208-175">对于由发送邮件任务发送到 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]中的虚构销售人员的邮件，您将收到关于无法投递的回执。</span><span class="sxs-lookup"><span data-stu-id="c5208-175">You will receive undeliverable receipts for the messages sent by the Send Mail task to the fictitious salespersons of [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].</span></span>  
  
    3.  <span data-ttu-id="c5208-176">对于“收件人”，输入默认电子邮件地址。 </span><span class="sxs-lookup"><span data-stu-id="c5208-176">For **To**, enter a default e-mail address.</span></span>  
  
         <span data-ttu-id="c5208-177">此值不会使用，但在运行时将替换为每位销售人员的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="c5208-177">This value will not be used, but will be replaced at run time by the e-mail address of each salesperson.</span></span>  
  
    4.  <span data-ttu-id="c5208-178">对于 **“主题”** ，输入“Your annual bonus”。</span><span class="sxs-lookup"><span data-stu-id="c5208-178">For **Subject**, enter "Your annual bonus".</span></span>  
  
    5.  <span data-ttu-id="c5208-179">对于 **MessageSourceType**，选择 **“直接输入”** 。</span><span class="sxs-lookup"><span data-stu-id="c5208-179">For **MessageSourceType**, select **Direct Input**.</span></span>  
  
5.  <span data-ttu-id="c5208-180">在“发送邮件任务编辑器”的“表达式”页上，单击省略号按钮 ( **...** )，以打开“属性表达式编辑器”。  </span><span class="sxs-lookup"><span data-stu-id="c5208-180">On the **Expressions** page of the **Send Mail Task Editor**, click the ellipsis button (**...**) to open the **Property Expressions Editor**.</span></span>  
  
6.  <span data-ttu-id="c5208-181">在 **“属性表达式编辑器”** 中，输入以下信息：</span><span class="sxs-lookup"><span data-stu-id="c5208-181">In the **Property Expressions Editor**, enter the following information:</span></span>  
  
    1.  <span data-ttu-id="c5208-182">对于 **ToLine**，添加以下表达式：</span><span class="sxs-lookup"><span data-stu-id="c5208-182">For **ToLine**, add the following expression:</span></span>  
  
        ```  
        @[User::EmailAddress]  
        ```  
  
    2.  <span data-ttu-id="c5208-183">对于 **MessageSource** 属性，添加以下表达式：</span><span class="sxs-lookup"><span data-stu-id="c5208-183">For the **MessageSource** property, add the following expression:</span></span>  
  
        ```  
        "Dear " +  @[User::FirstName] + ": The amount of your bonus for this year is $" +  (DT_WSTR, 12) @[User::Bonus] + ". Thank you!"  
        ```  
  
7.  <span data-ttu-id="c5208-184">运行包。</span><span class="sxs-lookup"><span data-stu-id="c5208-184">Run the package.</span></span>  
  
     <span data-ttu-id="c5208-185">如果已经指定有效的 SMTP 服务器并提供了自己的电子邮件地址，则对于由发送邮件任务发送到 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]中的虚构销售人员的邮件，您将收到关于无法投递的回执。</span><span class="sxs-lookup"><span data-stu-id="c5208-185">If you have specified a valid SMTP server and provided your own e-mail address, you will receive undeliverable receipts for the messages that the Send Mail task sends to the fictitious salespersons of [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].</span></span>  
  
  
