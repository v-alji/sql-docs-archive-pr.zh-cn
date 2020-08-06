---
title: 自定义工作流示例 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: dfd1616c-a75c-4f32-bdb1-7569e367bf41
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ee9d6e18bf4e54ae5eb6af6a56494fff0db28684
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682913"
---
# <a name="custom-workflow-example-master-data-services"></a><span data-ttu-id="a1221-102">自定义工作流示例 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="a1221-102">Custom Workflow Example (Master Data Services)</span></span>
  <span data-ttu-id="a1221-103">在中 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] ，创建自定义工作流类库时，会创建一个实现[MasterDataServices](/previous-versions/sql/sql-server-2016/hh758785(v=sql.130))接口的类。</span><span class="sxs-lookup"><span data-stu-id="a1221-103">In [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], when you create a custom workflow class library, you create a class that implements the [Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender](/previous-versions/sql/sql-server-2016/hh758785(v=sql.130)) interface.</span></span> <span data-ttu-id="a1221-104">此接口包含一个方法[IWorkflowTypeExtender StartWorkflow \*](/previous-versions/sql/sql-server-2016/hh759009(v=sql.130))，在工作流启动时 SQL Server MDS Workflow Integration Service 调用此方法。</span><span class="sxs-lookup"><span data-stu-id="a1221-104">This interface includes one method, [Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow\*](/previous-versions/sql/sql-server-2016/hh759009(v=sql.130)), that is called by SQL Server MDS Workflow Integration Service when a workflow starts.</span></span> <span data-ttu-id="a1221-105">[MasterDataServices. WorkflowTypeExtender. IWorkflowTypeExtender. StartWorkflow \*](/previous-versions/sql/sql-server-2016/hh759009(v=sql.130))方法包含两个参数： *workflowType*包含在中的 "**工作流类型**" 文本框中输入的文本 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] ， *dataElement*包含触发工作流业务规则的项的元数据和项数据。</span><span class="sxs-lookup"><span data-stu-id="a1221-105">The [Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow\*](/previous-versions/sql/sql-server-2016/hh759009(v=sql.130)) method contains two parameters: *workflowType* contains the text you entered in the **Workflow type** text box in [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], and *dataElement* contains metadata and item data for the item that triggered the workflow business rule.</span></span>  
  
## <a name="custom-workflow-example"></a><span data-ttu-id="a1221-106">自定义工作流示例</span><span class="sxs-lookup"><span data-stu-id="a1221-106">Custom Workflow Example</span></span>  
 <span data-ttu-id="a1221-107">下面的代码示例演示如何实现[MasterDataServices. StartWorkflow \*](/previous-versions/sql/sql-server-2016/hh759009(v=sql.130))方法，以便从触发工作流业务规则的元素的 XML 数据中提取 Name、Code 和 LastChgUserName 特性，以及如何调用存储过程将其插入到另一个数据库中。</span><span class="sxs-lookup"><span data-stu-id="a1221-107">The following code example shows how you how to implement the [Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow\*](/previous-versions/sql/sql-server-2016/hh759009(v=sql.130)) method to extract the Name, Code, and LastChgUserName attributes from the XML data for the element that triggered the workflow business rule, and how to call a stored procedure to insert them into another database.</span></span> <span data-ttu-id="a1221-108">有关项数据 XML 的示例和其包含的标记的说明，请参阅[自定义工作流 XML 说明 &#40;Master Data Services&#41;](create-a-custom-workflow-xml-description.md)。</span><span class="sxs-lookup"><span data-stu-id="a1221-108">For an example of the item data XML and an explanation of the tags it contains, see [Custom Workflow XML Description &#40;Master Data Services&#41;](create-a-custom-workflow-xml-description.md).</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.IO;  
using System.Data.SqlClient;  
using System.Xml;  
  
using Microsoft.MasterDataServices.Core.Workflow;  
  
namespace MDSWorkflowTestLib  
{  
    public class WorkflowTester : IWorkflowTypeExtender  
    {  
        #region IWorkflowTypeExtender Members  
  
        public void StartWorkflow(string workflowType, System.Xml.XmlElement dataElement)  
        {  
            // Extract the attributes we want out of the element data.  
            XmlNode NameNode = dataElement.SelectSingleNode("//ExternalAction/MemberData/Name");  
            XmlNode CodeNode = dataElement.SelectSingleNode("//ExternalAction/MemberData/Code");  
            XmlNode EnteringUserNode = dataElement.SelectSingleNode("//ExternalAction/MemberData/LastChgUserName");  
  
            // Open a connection on the workflow database.  
            SqlConnection workflowConn = new SqlConnection(@"Data Source=<Server instance>; Initial Catalog=WorkflowTest; Integrated Security=True");  
  
            // Create a command to call the stored procedure that adds a new user to the workflow database.  
            SqlCommand addCustomerCommand = new SqlCommand("AddNewCustomer", workflowConn);  
            addCustomerCommand.CommandType = System.Data.CommandType.StoredProcedure;  
            addCustomerCommand.Parameters.Add(new SqlParameter("@Name", NameNode.InnerText));  
            addCustomerCommand.Parameters.Add(new SqlParameter("@Code", CodeNode.InnerText));  
            addCustomerCommand.Parameters.Add(new SqlParameter("@EnteringUser", EnteringUserNode.InnerText));  
  
            // Execute the command.  
            workflowConn.Open();  
            addCustomerCommand.ExecuteNonQuery();  
            workflowConn.Close();  
        }  
  
        #endregion  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a1221-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a1221-109">See Also</span></span>  
 [<span data-ttu-id="a1221-110">创建自定义工作流 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a1221-110">Create a Custom Workflow &#40;Master Data Services&#41;</span></span>](create-a-custom-workflow-master-data-services.md)  
  
  
