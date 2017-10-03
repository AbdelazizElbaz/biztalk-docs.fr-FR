---
title: "Programmation sécurisée avec l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c84744a-6595-4d93-afe7-39a7ccf1b6a0
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 44886b490ce63e8c34e1a5bdb41554c96a0873ad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="secure-programming-with-the-sql-adapter"></a>Programmation sécurisée avec l’adaptateur SQL
## <a name="how-do-i-protect-credentials-when-i-use-the-add-adapter-service-reference-visual-studio-plug-in"></a>Comment protéger informations d’identification lorsque vous utilisez l’adaptateur Service Reference Visual Studio plug-in d’ajouter ?  
 Lorsque vous utilisez le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour créer un client WCF, vous devrez peut-être fournir un nom d’utilisateur et un mot de passe pour la base de données SQL Server. Vous devez entrer les informations d’identification à partir de la **sécurité** onglet sur le **configurer l’adaptateur** boîte de dialogue. Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] ne fournit pas une option pour spécifier le nom d’utilisateur et un mot de passe dans le cadre de l’URI de connexion. Cela offre les avantages suivants :  
  
-   Les informations d’identification ne s’affichera pas dans le **configurer un URI** champ le **ajouter adaptateur Service référence un plug-in** boîte de dialogue dans laquelle toute personne ayant accès à l’écran de votre ordinateur peut les lire.  
  
-   Les informations d’identification n’apparaissent pas dans la configuration du fichier qui le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] génère.  
  
 Pour plus d’informations sur la façon de générer un client WCF à l’aide de la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], y compris comment entrer un nom d’utilisateur et un mot de passe pour la base de données SQL Server, consultez [obtenir les métadonnées pour les opérations de SQL Server dans Visual Studio à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md).  
  
## <a name="what-are-best-practices-for-setting-credentials-in-code"></a>Quelles sont les meilleures pratiques pour les informations d’identification du paramètre dans le Code ?  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]Fournit la **ClientCredentials** classe pour vous aider à configurer les informations d’identification que l’objet d’une communication client, tel qu’un **ChannelFactory**, utilise pour s’authentifier auprès d’un service. À l’aide de la **ClientCredentials** (classe), vérifiez que WCF utilise les mécanismes d’authentification sont spécifiées dans la pile de canaux de cet objet et les applique à l’échange entre votre client et le service.  
  
 Étant donné que la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] est hébergé in-process avec son application consommatrice, il n’est pas impératif d’utiliser le **ClientCredentials** classe pour définir les informations d’identification sur le client des objets de communication utilisés par l’application consommatrice. Toutefois, il apparaît conseillé de le faire.  
  
 Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] requiert l’utilisation de la **ClientCredentials** classe pour passer des informations d’identification par programme. Le **AcceptCredentialsInUri** liaison de la propriété est ignorée par le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour empêcher les informations d’identification de passage dans l’URI.  
  
 L’exemple suivant montre comment utiliser le **informations d’identification** propriété à définir les informations d’identification pour la base de données SQL Server sur un **ChannelFactory**.  
  
```  
// Create binding and endpoint  
SqlAdapterBinding binding = new SqlAdapterBinding();  
EndpointAddress address = new EndpointAddress("mssql://mysqlserver//mydatabase?");  
  
// Create the channel factory   
ChannelFactory<IRequestChannel> factory = new ChannelFactory<IRequestChannel>(binding, endpointAddress))  
  
// Set user name and password  
factory.Credentials.UserName.UserName = "myuser";  
factory.Credentials.UserName.Password = "mypassword";  
  
// Open the channel factory  
factory.Open();  
```  
  
 L’exemple suivant montre comment utiliser le **ClientCredentials** classe pour définir les informations d’identification pour la base de données SQL Server sur un client WCF.  
  
```  
// Initialize a new client for the SELECT operation on the Employee table   
SqlAdapterBinding binding = new SqlAdapterBinding();  
EndpointAddress address = new EndpointAddress("mssql://mysqlserver//mydatabase?");  
TableOp_dbo_EmployeeClient client = new TableOp_dbo_EmployeeClient(binding,address);  
  
// Set user name and password  
client.ClientCredentials.UserName.UserName = "myuser";  
client.ClientCredentials.UserName.Password = "mypassword";  
  
// Open the client  
client.Open();  
```  
  
## <a name="how-can-i-provide-for-more-secure-data-exchange-across-process-boundaries"></a>Comment puis-je fournir pour échanger des données plus sécurisée au-delà des limites de processus ?  
 Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] est hébergé in-process avec l’application ou le service qui la consomme. Étant donné que l’adaptateur est hébergé in-process avec le consommateur, il n’est pas nécessaire pour assurer la sécurité des messages échangés entre le client et le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. Toutefois, si l’application consommatrice ou le service envoie des messages qui contiennent des informations de base de données sensibles sur une limite de processus à un autre service ou client, vous devez prendre des mesures pour assurer une protection adéquate pour ces données dans votre environnement. [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]fournit plusieurs options pour aider à sécuriser les messages envoyés entre les clients et services. Pour plus d’informations sur contribue à sécuriser les messages envoyés entre les clients et services dans [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)], consultez [sécurisation des Services et les Clients](https://msdn.microsoft.com/library/ms734736.aspx). Pour plus d’informations générales sur la sécurité des fonctionnalités qui [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] fournit, consultez [Windows Communication Foundation Security](https://msdn.microsoft.com/library/ms732362.aspx).
  
## <a name="see-also"></a>Voir aussi  
[Sécuriser vos applications SQL](../../adapters-and-accelerators/adapter-sql/secure-your-sql-applications.md)  
[Meilleures pratiques pour sécuriser l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/best-practices-to-secure-the-sql-adapter.md)