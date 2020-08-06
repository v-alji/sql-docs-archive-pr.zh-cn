---
title: 调用存储过程 (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- calling stored procedures
- RPC escape sequence
- OLE DB, stored procedures
- parameters [SQL Server Native Client], OLE DB
- ODBC CALL escape sequence
- stored procedures [OLE DB], calling
- SQL Server Native Client OLE DB provider, stored procedures
ms.assetid: 8e5738e5-4bbe-4f34-bd69-0c0633290bdd
author: rothja
ms.author: jroth
ms.openlocfilehash: 695848c8633d310f5e8ee21e9e738749d1550e4a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692344"
---
# <a name="calling-a-stored-procedure-ole-db"></a><span data-ttu-id="1ee4a-102">调用存储过程 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="1ee4a-102">Calling a Stored Procedure (OLE DB)</span></span>
  <span data-ttu-id="1ee4a-103">存储过程可以有零个或多个参数。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-103">A stored procedure can have zero or more parameters.</span></span> <span data-ttu-id="1ee4a-104">它还可以返回值。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-104">It can also return a value.</span></span> <span data-ttu-id="1ee4a-105">使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序时，可以通过以下方式传递存储过程的参数：</span><span class="sxs-lookup"><span data-stu-id="1ee4a-105">When using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider, parameters to a stored procedure can be passed by:</span></span>  
  
-   <span data-ttu-id="1ee4a-106">对数据值进行硬编码。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-106">Hard-coding the data value.</span></span>  
  
-   <span data-ttu-id="1ee4a-107">使用参数标记 (?) 指定参数，将程序变量绑定到参数标记，然后将数据值放在程序变量中。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-107">Using a parameter marker (?) to specify parameters, bind a program variable to the parameter marker, and then place the data value in the program variable.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1ee4a-108">在使用 OLE DB 和命名参数调用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 存储过程时，参数名称必须以“\@”字符开头。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-108">When calling [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] stored procedures using named parameters with OLE DB, the parameter names must start with the '\@' character.</span></span> <span data-ttu-id="1ee4a-109">这是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 特有的限制。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-109">This is a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] specific restriction.</span></span> <span data-ttu-id="1ee4a-110">与 MDAC 相比，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口会更加严格地强制实施此限制。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-110">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider enforces this restriction more strictly than MDAC.</span></span>  
  
 <span data-ttu-id="1ee4a-111">为了支持参数，ICommandWithParameters 接口是对命令对象公开的\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-111">To support parameters, the **ICommandWithParameters** interface is exposed on the command object.</span></span> <span data-ttu-id="1ee4a-112">若要使用参数，使用者首先应通过调用 ICommandWithParameters::SetParameterInfo 方法（或者根据需要准备一个调用 GetParameterInfo 方法的调用语句）来向访问接口描述这些参数\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-112">To use parameters, the consumer first describes the parameters to the provider by calling the **ICommandWithParameters::SetParameterInfo** method (or optionally prepares a calling statement that calls the **GetParameterInfo** method).</span></span> <span data-ttu-id="1ee4a-113">然后，使用者创建一个指定缓冲区结构的取值函数并将参数值放入该缓冲区中。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-113">The consumer then creates an accessor that specifies the structure of a buffer and places parameter values in this buffer.</span></span> <span data-ttu-id="1ee4a-114">最后，它将取值函数的句柄和指向此缓冲区的指针传递给 Execute\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-114">Finally, it passes the handle of the accessor and a pointer to the buffer to **Execute**.</span></span> <span data-ttu-id="1ee4a-115">以后在调用 Execute 时，使用者将新参数值放入此缓冲区并使用取值函数句柄和缓冲区指针调用 Execute\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-115">On later calls to **Execute**, the consumer places new parameter values in the buffer and calls **Execute** with the accessor handle and buffer pointer.</span></span>  
  
 <span data-ttu-id="1ee4a-116">在能成功地准备使用参数调用临时存储过程的命令之前，该命令必须首先调用 ICommandWithParameters::SetParameterInfo 以定义参数信息\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-116">A command that calls a temporary stored procedure using parameters must first call **ICommandWithParameters::SetParameterInfo** to define the parameter information, before the command can be successfully prepared.</span></span> <span data-ttu-id="1ee4a-117">这是因为临时存储过程的内部名称与客户端使用的外部名称不同，并且 SQLOLEDB 无法通过查询系统表来确定临时存储过程的参数信息。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-117">This is because the internal name for a temporary stored procedure differs from the external name used by a client and SQLOLEDB cannot query the system tables to determine the parameter information for a temporary stored procedure.</span></span>  
  
 <span data-ttu-id="1ee4a-118">以下是参数绑定过程涉及的步骤：</span><span class="sxs-lookup"><span data-stu-id="1ee4a-118">These are the steps in the parameter binding process:</span></span>  
  
1.  <span data-ttu-id="1ee4a-119">在 DBPARAMBINDINFO 结构的数组中填写参数信息，即，参数名、参数数据类型特定于访问接口的名称或者标准数据类型名称，等等。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-119">Fill in the parameter information in an array of DBPARAMBINDINFO structures; that is, parameter name, provider-specific name for the data type of the parameter or a standard data type name, and so on.</span></span> <span data-ttu-id="1ee4a-120">数组中的每个结构都描述一个参数。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-120">Each structure in the array describes one parameter.</span></span> <span data-ttu-id="1ee4a-121">然后将此数组传递给 SetParameterInfo 方法\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-121">This array is then passed to the **SetParameterInfo** method.</span></span>  
  
2.  <span data-ttu-id="1ee4a-122">调用 ICommandWithParameters::SetParameterInfo 方法以向访问接口描述参数\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-122">Call the **ICommandWithParameters::SetParameterInfo** method to describe parameters to the provider.</span></span> <span data-ttu-id="1ee4a-123">SetParameterInfo 指定每个参数的本机数据类型\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-123">**SetParameterInfo** specifies the native data type of each parameter.</span></span> <span data-ttu-id="1ee4a-124">SetParameterInfo 参数包括\*\*\*\*：</span><span class="sxs-lookup"><span data-stu-id="1ee4a-124">**SetParameterInfo** arguments are:</span></span>  
  
    -   <span data-ttu-id="1ee4a-125">要设定其类型信息的参数的数量。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-125">The number of parameters for which to set type information.</span></span>  
  
    -   <span data-ttu-id="1ee4a-126">要设定其类型信息的参数序号的数组。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-126">An array of parameter ordinals for which to set type information.</span></span>  
  
    -   <span data-ttu-id="1ee4a-127">DBPARAMBINDINFO 结构的数组。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-127">An array of DBPARAMBINDINFO structures.</span></span>  
  
3.  <span data-ttu-id="1ee4a-128">通过使用 IAccessor::CreateAccessor 命令创建参数取值函数\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-128">Create a parameter accessor by using the **IAccessor::CreateAccessor** command.</span></span> <span data-ttu-id="1ee4a-129">取值函数指定缓冲区的结构并将参数值放在此缓冲区中。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-129">The accessor specifies the structure of a buffer and places parameter values in the buffer.</span></span> <span data-ttu-id="1ee4a-130">CreateAccessor 命令从一组绑定创建取值函数\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-130">The **CreateAccessor** command creates an accessor from a set of bindings.</span></span> <span data-ttu-id="1ee4a-131">使用者使用 DBBINDING 结构数组来描述这些绑定。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-131">These bindings are described by the consumer by using an array of DBBINDING structures.</span></span> <span data-ttu-id="1ee4a-132">每个绑定都将单个参数关联到使用者的缓冲区，并且包含诸如以下所示的信息：</span><span class="sxs-lookup"><span data-stu-id="1ee4a-132">Each binding associates a single parameter to the buffer of the consumer and contains information such as:</span></span>  
  
    -   <span data-ttu-id="1ee4a-133">应用绑定的参数的序号。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-133">The ordinal of the parameter to which the binding applies.</span></span>  
  
    -   <span data-ttu-id="1ee4a-134">所绑定的内容（数据值、其长度以及其状态）。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-134">What is bound (the data value, its length, and its status).</span></span>  
  
    -   <span data-ttu-id="1ee4a-135">缓冲区中到这些部分中每个部分的偏移量。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-135">The offset in the buffer to each of these parts.</span></span>  
  
    -   <span data-ttu-id="1ee4a-136">数据值存在于使用者的缓冲区中时的长度和类型。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-136">The length and type of the data value as it exists in the buffer of the consumer.</span></span>  
  
     <span data-ttu-id="1ee4a-137">取值函数通过其类型为 HACCESSOR 的句柄进行标识。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-137">An accessor is identified by its handle, which is of type HACCESSOR.</span></span> <span data-ttu-id="1ee4a-138">此句柄由 CreateAccessor 方法返回\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-138">This handle is returned by the **CreateAccessor** method.</span></span> <span data-ttu-id="1ee4a-139">只要使用者使用完取值函数，使用者就必须调用 ReleaseAccessor 方法释放它占用的内存\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-139">Whenever the consumer finishes using an accessor, the consumer must call the **ReleaseAccessor** method to release the memory it holds.</span></span>  
  
     <span data-ttu-id="1ee4a-140">当使用者调用某个方法（如 ICommand::Execute）时，会传递取值函数的句柄以及指向缓冲区自身的指针\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-140">When the consumer calls a method, such as **ICommand::Execute**, it passes the handle to an accessor and a pointer to a buffer itself.</span></span> <span data-ttu-id="1ee4a-141">访问接口使用该取值函数确定如何传送缓冲区中包含的数据。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-141">The provider uses this accessor to determine how to transfer the data contained in the buffer.</span></span>  
  
4.  <span data-ttu-id="1ee4a-142">填写 DBPARAMS 结构。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-142">Fill in the DBPARAMS structure.</span></span> <span data-ttu-id="1ee4a-143">在运行时，从中获取输入参数值和向其中写入输出值的使用者变量会在 DBPARAMS 结构中被传递给 ICommand::Execute\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-143">The consumer variables from which input parameter values are taken and to which output parameter values are written are passed at run time to **ICommand::Execute** in the DBPARAMS structure.</span></span> <span data-ttu-id="1ee4a-144">DBPARAMS 结构包括三个元素：</span><span class="sxs-lookup"><span data-stu-id="1ee4a-144">The DBPARAMS structure includes three elements:</span></span>  
  
    -   <span data-ttu-id="1ee4a-145">指向缓冲区的指针，根据取值函数句柄指定的绑定，访问接口将从该缓冲区中检索输入参数数据并将输出参数数据返回到该缓冲区中。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-145">A pointer to the buffer from which the provider retrieves input parameter data and to which the provider returns output parameter data, according to the bindings specified by the accessor handle.</span></span>  
  
    -   <span data-ttu-id="1ee4a-146">缓冲区中参数组的数量。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-146">The number of sets of parameters in the buffer.</span></span>  
  
    -   <span data-ttu-id="1ee4a-147">在步骤 3 中创建的取值函数句柄。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-147">The accessor handle created in Step 3.</span></span>  
  
5.  <span data-ttu-id="1ee4a-148">通过使用 ICommand::Execute 执行命令\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-148">Execute the command by using **ICommand::Execute**.</span></span>  
  
## <a name="methods-of-calling-a-stored-procedure"></a><span data-ttu-id="1ee4a-149">调用存储过程的方法</span><span class="sxs-lookup"><span data-stu-id="1ee4a-149">Methods of Calling a Stored Procedure</span></span>  
 <span data-ttu-id="1ee4a-150">在中执行存储过程时 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序支持：</span><span class="sxs-lookup"><span data-stu-id="1ee4a-150">When executing a stored procedure in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports the:</span></span>  
  
-   <span data-ttu-id="1ee4a-151">ODBC CALL 转义序列。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-151">ODBC CALL escape sequence.</span></span>  
  
-   <span data-ttu-id="1ee4a-152">远程过程调用 (RPC) 转义序列。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-152">Remote procedure call (RPC) escape sequence.</span></span>  
  
-   [!INCLUDE[tsql](../../../includes/tsql-md.md)] <span data-ttu-id="1ee4a-153">EXECUTE 语句。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-153">EXECUTE statement.</span></span>  
  
### <a name="odbc-call-escape-sequence"></a><span data-ttu-id="1ee4a-154">ODBC CALL 转义序列</span><span class="sxs-lookup"><span data-stu-id="1ee4a-154">ODBC CALL Escape Sequence</span></span>  
 <span data-ttu-id="1ee4a-155">如果知道参数信息，可调用 ICommandWithParameters::SetParameterInfo 方法向访问接口描述参数\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-155">If you know parameter information, call **ICommandWithParameters::SetParameterInfo** method to describe the parameters to the provider.</span></span> <span data-ttu-id="1ee4a-156">否则，在使用 ODBC CALL 语法调用存储过程时，访问接口将调用一个 Helper 函数来查找存储过程的参数信息。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-156">Otherwise, when the ODBC CALL syntax is used in calling a stored procedure, the provider calls a helper function to find the stored procedure parameter information.</span></span>  
  
 <span data-ttu-id="1ee4a-157">如果您不知道确切的参数信息（参数元数据），建议使用 ODBC CALL 语法。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-157">If you are not sure about the parameter information (parameter metadata), ODBC CALL syntax is recommended.</span></span>  
  
 <span data-ttu-id="1ee4a-158">使用 ODBC CALL 转义序列调用过程的常用语法是：</span><span class="sxs-lookup"><span data-stu-id="1ee4a-158">The general syntax for calling a procedure by using the ODBC CALL escape sequence is:</span></span>  
  
 <span data-ttu-id="1ee4a-159">{[**？ =**]**调用**_procedure_name_[\*\* (**[*参数*] [**，**[*参数*]] .。。**) \*\*]}</span><span class="sxs-lookup"><span data-stu-id="1ee4a-159">{[**?=**]**call**_procedure_name_[**(**[*parameter*][**,**[*parameter*]]...**)**]}</span></span>  
  
 <span data-ttu-id="1ee4a-160">例如：</span><span class="sxs-lookup"><span data-stu-id="1ee4a-160">For example:</span></span>  
  
```  
{call SalesByCategory('Produce', '1995')}  
```  
  
### <a name="rpc-escape-sequence"></a><span data-ttu-id="1ee4a-161">RPC 转义序列</span><span class="sxs-lookup"><span data-stu-id="1ee4a-161">RPC Escape Sequence</span></span>  
 <span data-ttu-id="1ee4a-162">使用 RPC 转义序列调用存储过程的语法与 ODBC CALL 语法类似。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-162">The RPC escape sequence is similar to the ODBC CALL syntax of calling a stored procedure.</span></span> <span data-ttu-id="1ee4a-163">如果要多次调用过程，则在调用存储过程的三种方法中，RPC 转义序列可以提供最佳的性能。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-163">If you will call the procedure multiple times, the RPC escape sequence provides most optimal performance among the three methods of calling a stored procedure.</span></span>  
  
 <span data-ttu-id="1ee4a-164">如果使用 RPC 转义序列执行存储过程，则访问接口不会调用任何 Helper 函数来确定参数信息（使用 ODBC CALL 语法时则会调用 Helper 函数）。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-164">When the RPC escape sequence is used to execute a stored procedure, the provider does not call any helper function to determine the parameter information (as it does in the case of ODBC CALL syntax).</span></span> <span data-ttu-id="1ee4a-165">RPC 语法比 ODBC CALL 语法简单，因此命令的分析速度更快，从而提高了性能。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-165">The RPC syntax is simpler than the ODBC CALL syntax, so the command is parsed faster, improving performance.</span></span> <span data-ttu-id="1ee4a-166">在这种情况下，需要通过执行 ICommandWithParameters::SetParameterInfo 来提供参数信息\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-166">In this case, you need to provide the parameter information by executing **ICommandWithParameters::SetParameterInfo**.</span></span>  
  
 <span data-ttu-id="1ee4a-167">RPC 转义序列要求您具有返回值。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-167">The RPC escape sequence requires you to have a return value.</span></span> <span data-ttu-id="1ee4a-168">如果存储过程不返回值，则服务器默认返回 0。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-168">If the stored procedure does not return a value, the server returns a 0 by default.</span></span> <span data-ttu-id="1ee4a-169">此外，您无法对存储过程打开 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 游标。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-169">In addition, you cannot open a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cursor on the stored procedure.</span></span> <span data-ttu-id="1ee4a-170">存储过程是隐式准备的，对 ICommandPrepare::Prepare 的调用会失败\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-170">The stored procedure is prepared implicitly and the call to **ICommandPrepare::Prepare** will fail.</span></span> <span data-ttu-id="1ee4a-171">由于无法准备 RPC 调用，因此也就无法查询列元数据；IColumnsInfo::GetColumnInfo 和 IColumnsRowset::GetColumnsRowset 会返回 DB_E_NOTPREPARED。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-171">Because of the inability to prepare an RPC call, you can not query column metadata; IColumnsInfo::GetColumnInfo and IColumnsRowset::GetColumnsRowset will return DB_E_NOTPREPARED.</span></span>  
  
 <span data-ttu-id="1ee4a-172">如果知道所有参数元数据，建议采用 RPC 转义序列方式执行存储过程。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-172">If you know all the parameter metadata, RPC escape sequence is the recommended way to execute stored procedures.</span></span>  
  
 <span data-ttu-id="1ee4a-173">以下是使用 RPC 转义序列调用存储过程的一个例子：</span><span class="sxs-lookup"><span data-stu-id="1ee4a-173">This is an example of RPC escape sequence for calling a stored procedure:</span></span>  
  
```  
{rpc SalesByCategory}  
```  
  
 <span data-ttu-id="1ee4a-174">有关展示 RPC 转义序列的示例应用程序，请参阅[执行存储过程（使用 RPC 语法）并处理返回代码和输出参数 &#40;OLE DB&#41;](../../native-client-ole-db-how-to/results/execute-stored-procedure-with-rpc-and-process-output.md)。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-174">For a sample application that demonstrates an RPC escape sequence, see [Execute a Stored Procedure &#40;Using RPC Syntax&#41; and Process Return Codes and Output Parameters &#40;OLE DB&#41;](../../native-client-ole-db-how-to/results/execute-stored-procedure-with-rpc-and-process-output.md).</span></span>  
  
### <a name="transact-sql-execute-statement"></a><span data-ttu-id="1ee4a-175">Transact-SQL EXECUTE 语句</span><span class="sxs-lookup"><span data-stu-id="1ee4a-175">Transact-SQL EXECUTE Statement</span></span>  
 <span data-ttu-id="1ee4a-176">与 [EXECUTE](/sql/t-sql/language-elements/execute-transact-sql) 语句相比，ODBC CALL 转义序列和 RPC 转义序列是调用存储过程的首选方法。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-176">The ODBC CALL escape sequence and the RPC escape sequence are the preferred methods for calling a stored procedure rather than the [EXECUTE](/sql/t-sql/language-elements/execute-transact-sql) statement.</span></span> <span data-ttu-id="1ee4a-177">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序使用的 RPC 机制 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 来优化命令处理。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-177">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider uses the RPC mechanism of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to optimize command processing.</span></span> <span data-ttu-id="1ee4a-178">此 RPC 协议通过避免在服务器上进行大量参数处理和语句分析来提高性能。</span><span class="sxs-lookup"><span data-stu-id="1ee4a-178">This RPC protocol increases performance by eliminating much of the parameter processing and statement parsing done on the server.</span></span>  
  
 <span data-ttu-id="1ee4a-179">下面是  EXECUTE[!INCLUDE[tsql](../../../includes/tsql-md.md)] \*\*\*\* 语句示例：</span><span class="sxs-lookup"><span data-stu-id="1ee4a-179">This is an example of the [!INCLUDE[tsql](../../../includes/tsql-md.md)] **EXECUTE** statement:</span></span>  
  
```  
EXECUTE SalesByCategory 'Produce', '1995'  
```  
  
## <a name="see-also"></a><span data-ttu-id="1ee4a-180">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1ee4a-180">See Also</span></span>  
 [<span data-ttu-id="1ee4a-181">存储过程</span><span class="sxs-lookup"><span data-stu-id="1ee4a-181">Stored Procedures</span></span>](stored-procedures.md)  
  
  
