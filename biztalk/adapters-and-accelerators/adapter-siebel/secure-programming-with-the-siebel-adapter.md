---
title: "Programmation sécurisée avec l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security considerations, when programming on the adapter
- credentials, best practices for setting in code
- credentials, protecting when using the Add Adapter Service Reference Visual Studio Plug-in
- security, best practices for setting credentials in code
ms.assetid: 8c2b6b36-7bd9-4678-a9c2-450e818f607a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aebe93918741b2603b8090add7ff40ed731097d1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="secure-programming-with-the-siebel-adapter"></a>Programmation sécurisée avec l’adaptateur Siebel
## <a name="how-do-i-protect-credentials-when-i-use-the-add-adapter-service-reference-visual-studio-plug-in"></a>Comment protéger informations d’identification lorsque vous utilisez l’adaptateur Service Reference Visual Studio plug-in d’ajouter ?  
 Lorsque vous utilisez le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour créer un client WCF, vous devez fournir un nom d’utilisateur et un mot de passe pour le système Siebel. Vous devez uniquement le faire à partir de la **sécurité** onglet sur le **configurer l’adaptateur** boîte de dialogue. En entrant le Siebel les informations d’identification à partir de la **sécurité** onglet à la place de directement dans le **Uri** champ, vous vérifiez les points suivants :  
  
-   Les informations d’identification ne s’affichera pas dans le **Uri** champ le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] boîte de dialogue dans laquelle toute personne ayant accès à l’écran de votre ordinateur peut les lire.  
  
-   Les informations d’identification n’apparaissent pas dans la configuration du fichier qui le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] génère.  
  
 Pour plus d’informations sur la façon de générer un client WCF à l’aide de la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], y compris comment entrer un nom d’utilisateur et un mot de passe pour le système Siebel, consultez [obtenir les métadonnées pour les opérations Siebel dans Visual Studio](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md).  
  
## <a name="what-are-best-practices-for-setting-credentials-in-code"></a>Quelles sont les meilleures pratiques pour les informations d’identification du paramètre dans le Code ?  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]Fournit la **ClientCredentials** classe pour vous aider à configurer les informations d’identification que l’objet d’une communication client, tel qu’un **ChannelFactory**, utilise pour s’authentifier auprès d’un service. À l’aide de la **ClientCredentials** (classe), vérifiez que WCF utilise les mécanismes d’authentification sont spécifiées dans la pile de canaux de cet objet et les applique à l’échange entre votre client et le service.  
  
 Étant donné que la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] est hébergé in-process avec son application consommatrice, il n’est pas impératif d’utiliser le **ClientCredentials** classe pour définir les informations d’identification sur le client des objets de communication utilisés par l’application consommatrice. Toutefois, il apparaît conseillé de le faire.  
  
 Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] encourage l’utilisation de la **ClientCredentials** par le biais du **AcceptCredentialsInUri** propriété de liaison. Cette propriété spécifie si l’adaptateur accepte le nom d’utilisateur et un mot de passe pour le système Siebel dans l’URI de connexion. **AcceptCredentialsInUri** par défaut est **false**, ce qui signifie que l’adaptateur lève une exception si l’URI de connexion contient des informations d’identification. Vous pouvez définir **AcceptCredentialsInUri** à **true** pour fournir des informations d’identification dans l’URI de connexion. En fait, vous devez le faire dans certains cas ; par exemple, lorsque vous utilisez le service Model Metadata Utility Tool (svcutil.exe) pour générer une classe de client WCF pour les artefacts du système Siebel.  
  
 L’exemple suivant montre comment utiliser le **informations d’identification** classe pour définir les informations d’identification pour le système Siebel sur un **ChannelFactory**.  
  
```  
// Create binding and endpoint  
SiebelBinding binding = new SiebelBinding();  
EndpointAddress endpointAddress = new EndpointAddress("siebel://Siebel_server:1234?SiebelObjectManager=obj_mgr&SiebelEnterpriseServer=entserver&Language=enu ");  
  
// Create the channel factory   
ChannelFactory<IRequestChannel> factory = new ChannelFactory<IRequestChannel>(binding, endpointAddress))  
  
// Set user name and password  
factory.Credentials.UserName.UserName = "YourUserName";  
factory.Credentials.UserName.Password = "YourPassword";  
  
// Open the channel factory  
factory.Open();  
```  
  
 L’exemple suivant montre comment utiliser le **ClientCredentials** classe pour définir les informations d’identification pour le système Siebel sur un client WCF.  
  
```  
// Initialize a new client for the SQLEXECUTE operation from configuration   
BusinessObjects_Account_Account_OperationClient accountAccountClient = new BusinessObjects_Account_Account_OperationClient ("SiebelBinding_BusinessObjects_Account_Account_Operation");  
  
// Set user name and password  
accountAccountClient.ClientCredentials.UserName.UserName = "YourUserName";  
accountAccountClient.ClientCredentials.UserName.Password = "YourPassword";  
  
// Open the client  
accountAccountClient.Open();  
```  
  
## <a name="how-can-i-provide-for-more-secure-data-exchange-across-process-boundaries"></a>Comment puis-je fournir pour échanger des données plus sécurisée au-delà des limites de processus ?  
 Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] est hébergé in-process avec l’application ou le service qui la consomme. Étant donné que l’adaptateur est hébergé in-process avec le consommateur, il n’est pas nécessaire pour assurer la sécurité des messages échangés entre le client et le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]. Toutefois, si l’application consommatrice ou le service envoie des messages qui contiennent des informations de base de données sensibles sur une limite de processus à un autre service ou client, vous devez prendre des mesures pour assurer une protection adéquate pour ces données dans votre environnement. [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]fournit plusieurs options pour aider à sécuriser les messages envoyés entre les clients et services. Pour plus d’informations sur contribue à sécuriser les messages envoyés entre les clients et services dans [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)], consultez [sécurisation des Services et les Clients](https://msdn.microsoft.com/library/ms734736.aspx). Pour plus d’informations générales sur la sécurité des fonctionnalités qui [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] fournit, consultez [Windows Communication Foundation Security](https://msdn.microsoft.com/library/ms732362.aspx).
  
## <a name="see-also"></a>Voir aussi  
 [Sécuriser vos applications Siebel](../../adapters-and-accelerators/adapter-siebel/secure-your-siebel-applications.md)  
[Meilleures pratiques pour sécuriser l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/best-practices-to-secure-the-siebel-adapter.md)