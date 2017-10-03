---
title: "Programmation avec l’adaptateur Oracle eBusiness Suite sécurisée | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35b494f8-cb21-45c2-9bb4-097ba59ec52c
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 89a51a163c12a14fc58bdcefc5ffe6aab7df6d9f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="secure-programming-with-the-oracle-ebs-adapter"></a>Programmation sécurisée avec l’adaptateur Oracle eBusiness Suite
## <a name="how-do-i-protect-credentials-when-i-use-the-add-adapter-service-reference-visual-studio-plug-in"></a>Comment protéger informations d’identification lorsque vous utilisez l’adaptateur Service Reference Visual Studio plug-in d’ajouter ?  
 Lorsque vous utilisez le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour créer un client WCF, vous devez fournir un nom d’utilisateur et un mot de passe pour Oracle E-Business Suite. Vous devez uniquement le faire à partir de la **sécurité** onglet sur le **configurer l’adaptateur** boîte de dialogue. En entrant le Oracle les informations d’identification à partir de la **sécurité** onglet à la place de directement dans le **configurer un URI** champ, vous vérifiez les points suivants :  
  
-   Les informations d’identification ne s’affichera pas dans le **configurer un URI** champ le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] boîte de dialogue dans laquelle toute personne ayant accès à l’écran de votre ordinateur peut les lire.  
  
-   Les informations d’identification n’apparaissent pas dans la configuration du fichier qui le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] génère.  
  
 Pour plus d’informations sur la façon de générer un client WCF à l’aide de la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], y compris comment entrer un nom d’utilisateur et un mot de passe pour Oracle E-Business Suite, consultez [obtenir les métadonnées pour les opérations Oracle E-Business Suite dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md).  
  
## <a name="what-are-best-practices-for-setting-credentials-in-code"></a>Quelles sont les meilleures pratiques pour les informations d’identification du paramètre dans le Code ?  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]Fournit la **ClientCredentials** classe pour vous aider à configurer les informations d’identification que l’objet d’une communication client, tel qu’un **ChannelFactory**, utilise pour s’authentifier auprès d’un service. À l’aide de la **ClientCredentials** (classe), vérifiez que WCF utilise les mécanismes d’authentification sont spécifiées dans la pile de canaux de cet objet et les applique à l’échange entre votre client et le service.  
  
 Étant donné que la [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] est hébergé in-process avec son application consommatrice, il n’est pas impératif d’utiliser le **ClientCredentials** classe pour définir les informations d’identification sur le client des objets de communication utilisés par l’application consommatrice. Toutefois, il apparaît conseillé de le faire.  
  
 Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] encourage l’utilisation de la **ClientCredentials** classe. Cette propriété spécifie si l’adaptateur accepte le nom d’utilisateur et un mot de passe pour la base de données Oracle dans l’URI de connexion. **AcceptCredentialsInUri** par défaut est **false**, ce qui signifie que l’adaptateur lève une exception si l’URI de connexion contient des informations d’identification. Vous pouvez définir **AcceptCredentialsInUri** à **true** pour fournir des informations d’identification dans l’URI, de connexion si nécessaire dans l’application cliente.  
  
 L’exemple suivant montre comment utiliser le **informations d’identification** propriété à définir les informations d’identification pour Oracle E-Business Suite dans un **ChannelFactory**.  
  
```  
// Create binding and endpoint  
OracleEBSBinding binding = new OracleEBSBinding();  
EndpointAddress address = new EndpointAddress("oracleebs://ebs-instance");  
  
// Create the channel factory   
ChannelFactory<IRequestChannel> factory = new ChannelFactory<IRequestChannel>(binding, address);  
  
// Set user name and password  
factory.Credentials.UserName.UserName = "myuser";  
factory.Credentials.UserName.Password = "mypassword";  
  
// Open the channel factory  
factory.Open();  
```  
  
 L’exemple suivant montre comment utiliser le **ClientCredentials** classe pour définir les informations d’identification d’Oracle E-Business Suite sur un client WCF.  
  
```  
// Initialize a new client for the SQLEXECUTE operation from configuration   
ConcurrentPrograms_ARClient client =   
  new ConcurrentPrograms_ARClient("OracleEBSBinding_ConcurrentPrograms_AR");  
  
// Set user name and password  
client.ClientCredentials.UserName.UserName = "myuser";  
client.ClientCredentials.UserName.Password = "mypassword";  
  
// Open the client  
client.Open();  
```  
  
## <a name="how-can-i-provide-for-more-secure-data-exchange-across-process-boundaries"></a>Comment puis-je fournir pour échanger des données plus sécurisée au-delà des limites de processus ?  
 Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] est hébergé in-process avec l’application ou le service qui la consomme. Étant donné que l’adaptateur est hébergé in-process avec le consommateur, il n’est pas nécessaire pour assurer la sécurité des messages échangés entre le client et le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. Toutefois, si l’application consommatrice ou le service envoie des messages qui contiennent des informations de base de données sensibles sur une limite de processus à un autre service ou client, vous devez prendre des mesures pour assurer une protection adéquate pour ces données dans votre environnement. [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]fournit plusieurs options pour aider à sécuriser les messages envoyés entre les clients et services. Pour plus d’informations sur contribue à sécuriser les messages envoyés entre les clients et services dans [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)], consultez « Sécurisation des Services et des Clients » à l’adresse [http://go.microsoft.com/fwlink/?LinkId=89725](http://go.microsoft.com/fwlink/?LinkId=89725). Pour plus d’informations générales sur la sécurité des fonctionnalités qui [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] fournit, consultez « Windows Communication Foundation Security » à [http://go.microsoft.com/fwlink/?LinkId=89726](http://go.microsoft.com/fwlink/?LinkId=89726).  
  
## <a name="see-also"></a>Voir aussi  
 [Sécuriser vos applications Oracle eBusiness Suite](secure-your-oracle-ebs-applications.md)