---
title: "Vue d’ensemble de l’adaptateur BizTalk pour SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8e46690e-d5c4-4d6b-b7a0-9a5adf4431cd
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 40d0c1fd3ce3a9f07367b7cc75ffeeb98f84b119
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="overview-of-biztalk-adapter-for-sql-server"></a>Vue d’ensemble de l’adaptateur BizTalk pour SQL Server
Le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] expose la base de données SQL Server comme un service WCF. Les clients de carte peuvent effectuer des opérations sur la base de données SQL Server en échangeant des messages SOAP avec l’adaptateur. L’adaptateur utilise le message SOAP et effectue des appels ADO.NET appropriés pour effectuer l’opération. L’adaptateur renvoie la réponse à partir de la base de données SQL Server au client sous la forme des messages SOAP.  
  
 Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] des métadonnées de surfaces d’artefacts dans la base de données SQL Server (par exemple, les tables, vues et procédures).  Ces métadonnées décrivent la structure d’un message SOAP dans le formulaire de Web Services Description Language (WSDL). Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] utilise le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], et [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] pour permettre aux clients d’adaptateur récupérer des métadonnées pour les opérations. L’adaptateur génère également des artefacts de programmation qui peuvent être utilisés dans votre solution de programmation. Pour plus d’informations sur [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], et [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], consultez [se connecter à SQL Server dans Visual Studio à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-sql-adapter.md).  
  
 Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] utilise ADO.NET pour communiquer avec la base de données SQL Server. Vous pouvez utiliser la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour communiquer avec la base de données SQL Server comme suit :  
  
-   En développant des applications BizTalk. Pour plus d’informations, consultez [BizTalk de développer des applications](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md).  
  
-   À l’aide de la [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] modèle de service. Pour plus d’informations, consultez [développer des applications à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md).  
  
-   À l’aide du modèle de canal WCF. Pour plus d’informations, consultez [développer des applications à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-channel-model.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Comment l’adaptateur effectue la connexion à SQL Server ?](https://msdn.microsoft.com/library/dd788114.aspx) 
  
-   [Quels sont les métadonnées du serveur SQL Surface adaptateur ?](https://msdn.microsoft.com/library/dd787941.aspx)  
  
-  [Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)  
  
-   [Les opérations sont prises en charge par l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/what-operations-are-supported-by-the-sql-adapter.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Comprendre l’adaptateur BizTalk pour SQL Server](../../adapters-and-accelerators/adapter-sql/understand-biztalk-adapter-for-sql-server.md)