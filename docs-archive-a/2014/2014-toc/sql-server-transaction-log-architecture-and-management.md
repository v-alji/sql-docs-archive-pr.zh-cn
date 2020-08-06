---
title: SQL Server 2014 事务日志体系结构和管理 |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 4d1a4f97-3fe4-44af-9d4f-f884a6eaa457
author: rothja
ms.author: jroth
ms.openlocfilehash: 8d32950d94bff22d6549c468e8fe8db3f30fd09a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578548"
---
# <a name="sql-server-2014-transaction-log-architecture-and-management"></a>SQL Server 2014 事务日志体系结构和管理

**适用于：** 从2008开始 SQL Server () 

  每个 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 数据库都具有事务日志，用于记录所有事务以及每个事务对数据库所做的修改。 事务日志是数据库的重要组件，如果系统出现故障，则可能需要使用事务日志将数据库恢复到一致状态。 本指南提供有关事务日志的物理和逻辑体系结构的信息。 了解该体系结构可以提高您在管理事务日志时的效率。  

  
##  <a name="transaction-log-logical-architecture"></a><a name="Logical_Arch"></a> 事务日志逻辑体系结构  

 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 事务日志按逻辑运行，就好像事务日志是一串日志记录一样。 每条日志记录由一个日志序列号 (LSN) 标识。 每条新日志记录均写入日志的逻辑结尾处，并使用一个比前面记录的 LSN 更高的 LSN。 日志记录按创建时的串行序列存储。 每条日志记录都包含其所属事务的 ID。 对于每个事务，与事务相关联的所有日志记录通过使用可提高事务回滚速度的向后指针挨个链接在一个链中。  
  
 数据修改的日志记录或者记录所执行的逻辑操作，或者记录已修改数据的前像和后像。 前像是执行操作前的数据副本；后像是执行操作后的数据副本。  
  
 操作的恢复步骤取决于日志记录的类型：  
  
-   记录逻辑操作  
  
    -   若要前滚逻辑操作，请再次执行该操作。  
  
    -   若要回滚逻辑操作，请执行相反的逻辑操作。  
  
-   记录前像和后像  
  
    -   若要前滚操作，请应用后像。  
  
    -   若要回滚操作，请应用前像。  
  
 许多类型的操作都记录在事务日志中。 这些操作包括：  
  
-   每个事务的开始和结束。  
  
-   每次数据修改（插入、更新或删除）。 这包括系统存储过程或数据定义语言 (DDL) 语句对包括系统表在内的任何表所做的更改。  
  
-   每次分配或释放区和页。  
  
-   创建或删除表或索引。  
  
 回滚操作也记录在日志中。 每个事务都在事务日志中保留空间，以确保存在足够的日志空间来支持由显式回滚语句或遇到错误引起的回滚。 保留的空间量取决于在事务中执行的操作，但通常等于用于记录每个操作的空间量。 事务完成后将释放此保留空间。  
  
  日志文件中从必须存在以确保数据库范围内成功回滚的第一条日志记录到最后写入的日志记录之间的部分称为日志的活动部分，即“活动日志”**。 这是进行数据库完整恢复所需的日志部分。 永远不能截断活动日志的任何部分。 此第一条日志记录的日志序列号 (LSN) 称为最小恢复 LSN (*MinLSN*) 。  
  
##  <a name="transaction-log-physical-architecture"></a><a name="physical_arch"></a> 事务日志物理体系结构  

 数据库中的事务日志映射在一个或多个物理文件上。 从概念上讲，日志文件是一系列日志记录。 从物理上讲，日志记录序列被有效地存储在实现事务日志的物理文件集中。 每个数据库必须至少有一个日志文件。  
  
 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] 在内部将每一物理日志文件分成多个虚拟日志文件。 虚拟日志文件没有固定大小，且物理日志文件所包含的虚拟日志文件数不固定。 [!INCLUDE[ssDE](../includes/ssde-md.md)] 在创建或扩展日志文件时动态选择虚拟日志文件的大小。 [!INCLUDE[ssDE](../includes/ssde-md.md)] 尝试维护少量的虚拟文件。 在扩展日志文件后，虚拟文件的大小是现有日志大小和新文件增量大小之和。 管理员不能配置或设置虚拟日志文件的大小或数量。  
  
 只有当物理日志文件使用较小的 size** 和 growth_increment** 值定义时，虚拟日志文件才会影响系统性能。 size** 值为日志文件的初始大小，growth_increment** 值则为每次需要新空间时为文件增加的空间大小。 如果这些日志文件由于许多微小增量而增长到很大，则它们将具有很多虚拟日志文件。 这会降低数据库启动以及日志备份和还原操作的速度。 建议你为日志文件分配一个接近于最终所需大小的 size** 值，并且还要分配一个相对较大的 growth_increment** 值。 有关这些参数的详细信息，请参阅 [ALTER DATABASE 文件和文件组选项 (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options)。  
  
 事务日志是一种回绕的文件。 例如，假设有一个数据库，它包含一个分成四个虚拟日志文件的物理日志文件。 当创建数据库时，逻辑日志文件从物理日志文件的始端开始。 新日志记录被添加到逻辑日志的末端，然后向物理日志的末端扩张。 日志截断将释放记录全部在最小恢复日志序列号 (MinLSN) 之前出现的所有虚拟日志。 MinLSN** 是成功进行数据库范围内回滚所需的最早日志记录的日志序列号。 示例数据库中的事务日志的外观与下图所示相似。  
  
 ![分为四个虚拟日志文件的日志文件](media/tranlog3.gif "分为四个虚拟日志文件的日志文件")  
  
 当逻辑日志的末端到达物理日志文件的末端时，新的日志记录将回绕到物理日志文件的始端。  
  
 ![日志记录回绕到日志文件的开头](media/tranlog4.gif "日志记录回绕到日志文件的开头")  
  
 这个循环不断重复，只要逻辑日志的末端不到达逻辑日志的始端。 如果经常截断旧的日志记录，始终为到下一个检查点前创建的所有新日志记录保留足够的空间，则日志永远不会填满。 但是，如果逻辑日志的末端真的到达了逻辑日志的始端，将发生以下两种情况之一：  
  
-   如果对日志启用了 FILEGROWTH 设置且磁盘上有可用空间，则文件就按 growth_increment** 参数指定的数量增大，并且新的日志记录将添加到增大的空间中。 有关 FILEGROWTH 设置的详细信息，请参阅 [ALTER DATABASE 文件和文件组选项 (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options)。  
  
-   如果未启用 FILEGROWTH 设置，或保存日志文件的磁盘的可用空间比 growth_increment** 中指定的数量少，则会出现 9002 错误。  
  
 如果日志包含多个物理日志文件，则逻辑日志在回绕到首个物理日志文件始端之前，将沿着所有物理日志文件移动。  
  
### <a name="log-truncation"></a>日志截断  

 日志截断主要用于阻止日志填充。 日志截断从 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 数据库的逻辑事务日志中删除不活动的虚拟日志文件，释放逻辑日志中的空间以便物理事务日志重用这些空间。 如果事务日志从不截断，它最终将填满分配给物理日志文件的所有磁盘空间。 但是，在截断日志前，必须执行检查点操作。 检查点将当前内存中已修改的页（称为“脏页”）和事务日志信息从内存写入磁盘。 执行检查点时，事务日志的不活动部分将标记为可重用。 此后，日志截断可以释放不活动的部分。 有关检查点的详细信息，请参阅[数据库检查点 (SQL Server)](../relational-databases/logs/database-checkpoints-sql-server.md)。  
  
 下列各图显示了截断前后的事务日志。 第一个图显示了从未截断的事务日志。 当前，逻辑日志使用四个虚拟日志文件。 逻辑日志开始于第一个逻辑日志文件的前面，并结束于虚拟日志 4。 MinLSN 记录位于虚拟日志 3 中。 虚拟日志 1 和虚拟日志 2 仅包含不活动的日志记录。 这些记录可以截断。 虚拟日志 5 仍未使用，不属于当前逻辑日志。  
  
 ![具有四个虚拟日志的事务日志](media/tranlog2.gif "具有四个虚拟日志的事务日志")  
  
 第二个图显示了日志截断后的情形。 已释放虚拟日志 1 和虚拟日志 2 以供重新使用。 现在，逻辑日志开始于虚拟日志 3 的开头。 虚拟日志 5 仍未使用，它不属于当前逻辑日志。  
  
 ![分为四个虚拟日志文件的日志文件](media/tranlog3.gif "分为四个虚拟日志文件的日志文件")  
  
 除非由于某些原因导致延迟，否则将在以下事件后自动发生日志截断：  
  
-   简单恢复模式下，在检查点之后发生。  
  
-   完整恢复模式或大容量日志恢复模式下，在日志备份之后发生（如果自上次备份后出现检查点）。  
  
 日志截断会由于多种因素发生延迟。 如果日志截断延迟的时间较长，则事务日志可能会填满磁盘空间。 有关信息，请参阅[可能延迟日志截断的因素](../relational-databases/logs/the-transaction-log-sql-server.md#FactorsThatDelayTruncation)和[解决事务日志完全 &#40;SQL Server 错误 9002&#41;](../relational-databases/logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md)的因素。  
  
##  <a name="write-ahead-transaction-log"></a><a name="WAL"></a> 预写事务日志  

 本节说明预写事务日志在将数据修改记录到磁盘的过程中所起的作用。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 使用预写日志 (WAL)，此日志确保在将关联的日志记录写入磁盘后再将数据修改写入磁盘。 这维护了事务的 ACID 属性。  
  
 要了解预写日志的工作方式，了解如何将修改的数据写入磁盘很重要。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 维护一个缓冲区缓存，在必须检索数据时从其中读取数据页。 当在缓冲区缓存中修改某个页面时，它不会立即写回磁盘;相反，该页标记为已*更新*。 在将数据页物理写入磁盘之前，可以将其逻辑写入多次。 对于每次逻辑写入，都会在记录修改的日志缓存中插入一条事务日志记录。 在将关联的脏页从缓冲区缓存中删除并写入磁盘之前，必须将这条些日志记录写入磁盘。 检查点进程定期在缓冲区高速缓存中扫描包含来自指定数据库的页的缓冲区，然后将所有脏页写入磁盘。 CHECKPOINT 可创建一个检查点，在该点保证全部脏页都已写入磁盘，从而在以后的恢复过程中节省时间。  
  
 将修改后的数据页从高速缓冲存储器写入磁盘的操作称为刷新页。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 具有一个逻辑，它可以在写入关联的日志记录前防止刷新脏页。 日志记录将在提交事务时写入磁盘。  
  
##  <a name="transaction-log-backups"></a><a name="Backups"></a>事务日志备份  

 本节介绍了有关如何备份和还原（应用）事务日志的概念。 在完整恢复模式和批量日志恢复模式下，执行例行事务日志备份（“日志备份”**）对于恢复数据十分必要。 可以在任何完整备份运行的时候备份日志。 有关恢复模型的详细信息，请参阅 [SQL Server 数据库的备份和还原](../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)。  
  
 在创建第一个日志备份之前，必须先创建完整备份（如数据库备份或一组文件备份中的第一个备份）。 仅使用文件备份还原数据库会较复杂。 因此，建议您尽可能从完整数据库备份开始。 此后，必须定期备份事务日志。 这不仅能最小化工作丢失风险，还有助于事务日志的截断。 通常，事务日志在每次常规日志备份之后截断。  
  
 建议经常进行日志备份，其频率应足够支持您的业务需求，尤其是您对损坏的日志驱动器可能导致的数据丢失的容忍程度。 适当的日志备份频率取决于您对工作丢失风险的容忍程度与所能存储、管理和潜在还原的日志备份数量之间的平衡。 每 15 到 30 分钟进行一次日志备份可能就已足够。 但是如果您的业务要求将工作丢失的风险最小化，请考虑进行更频繁的日志备份。 频繁的日志备份还有增加日志截断频率的优点，其结果是日志文件较小。  
  
 若要限制需要还原的日志备份的数量，必须定期备份数据。 例如，可以制定这样一个计划：每周进行一次完整数据库备份，每天进行若干次差异数据库备份。  
  
### <a name="the-log-chain"></a>日志链  

 日志备份的连续序列称为“日志链”**。 日志链从数据库的完整备份开始。 通常，仅当第一次备份数据库时，或者将恢复模式从简单恢复模式切换到完整恢复模式或大容量日志恢复模式之后，才会开始一个新的日志链。 除非在创建完整数据库备份时选择覆盖现有备份集，否则现有的日志链将保持不变。 在该日志链保持不变的情况下，便可从介质集中的任何完整数据库备份还原数据库，然后再还原相应恢复点之前的所有后续日志备份。 恢复点可以是上次日志备份的结尾，也可以是任何日志备份中的特定恢复点。 有关详细信息，请参阅[事务日志备份 (SQL Server)](../relational-databases/backup-restore/transaction-log-backups-sql-server.md)。  
  
 若要将数据库还原到故障点，必须保证日志链是完整的。 也就是说，事务日志备份的连续序列必须能够延续到故障点。 此日志序列的开始位置取决于您所还原的数据备份类型：数据库备份、部分备份或文件备份。 对于数据库备份或部分备份，日志备份序列必须从数据库备份或部分备份的结尾处开始延续。 对于一组文件备份，日志备份序列必须从整组文件备份的开头开始延续。 有关详细信息，请参阅[应用事务日志备份 (SQL Server)](../relational-databases/backup-restore/apply-transaction-log-backups-sql-server.md)。  
  
### <a name="restore-log-backups"></a>还原日志备份  

 还原日志备份将前滚事务日志中记录的更改，使数据库恢复到开始执行日志备份操作时的状态。 还原数据库时，必须还原在所还原完整数据库备份之后创建的日志备份，或者从您还原的第一个文件备份的开始处进行还原。 通常情况下，在还原最新数据或差异备份后，必须还原一系列日志备份直到到达恢复点。 然后恢复数据库。 这将回滚所有在恢复开始时未完成的事务并使数据库联机。 恢复数据库后，不得再还原任何备份。 有关详细信息，请参阅[应用事务日志备份 (SQL Server)](../relational-databases/backup-restore/apply-transaction-log-backups-sql-server.md)。  
  
## <a name="additional-reading"></a>附加阅读材料  

 有关事务日志的其他信息，我们建议阅读以下文章和书籍。  
  
 [了解 SQL Server 中的日志记录和恢复（作者：Paul Randall）](https://technet.microsoft.com/magazine/2009.02.logging.aspx)  
  
 [SQL Server 事务日志管理（作者：Tony Davis 和 Gail Shaw）](http://www.simple-talk.com/books/sql-books/sql-server-transaction-log-management-by-tony-davis-and-gail-shaw/)  
  
  