---
title: "Programmation sécurisée avec l’adaptateur SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, considerations when programming on the adapter
- security, secure data exchange
- security, setting credentials in code
ms.assetid: bd5da271-90f1-4a64-9138-a51048a16648
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a2be84abdc7b645d9b2aaeea87e5ccabf0075e76
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="secure-programming-with-the-sap-adapter"></a>Programmation sécurisée avec l’adaptateur SAP
## <a name="how-do-i-protect-credentials-when-i-use-the-add-adapter-service-reference-visual-studio-plug-in"></a>Comment protéger informations d’identification lorsque vous utilisez l’adaptateur Service Reference Visual Studio plug-in d’ajouter ?  
 Lorsque vous utilisez le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour créer un client WCF, vous devez fournir un nom d’utilisateur et un mot de passe pour le système SAP. Vous devez uniquement le faire à partir de la **sécurité** onglet sur le **configurer l’adaptateur** boîte de dialogue. En entrant la SAP, informations d’identification à partir de la **sécurité** onglet à la place de directement dans le **Uri** champ, vous vérifiez les points suivants :  
  
-   Les informations d’identification ne s’affichera pas dans le **Uri** champ le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] boîte de dialogue dans laquelle toute personne ayant accès à l’écran de votre ordinateur peut les lire.  
  
-   Les informations d’identification n’apparaissent pas dans la configuration du fichier qui le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] génère.  
  
 Pour plus d’informations sur la façon de générer un client WCF à l’aide de la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], y compris comment entrer un nom d’utilisateur et un mot de passe pour le système SAP, consultez [obtenir les métadonnées pour les opérations de SAP dans Visual Studio](../../adapters-and-accelerators/adapter-sap/get-metadata-for-sap-operations-in-visual-studio.md)  
  
## <a name="what-are-best-practices-for-setting-credentials-in-code"></a>Quelles sont les meilleures pratiques pour les informations d’identification du paramètre dans le Code ?  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]Fournit la **ClientCredentials** classe pour vous aider à configurer les informations d’identification que l’objet d’une communication client, tel qu’un **ChannelFactory**, utilise pour s’authentifier auprès d’un service. À l’aide de la **ClientCredentials** (classe), vérifiez que WCF utilise les mécanismes d’authentification sont spécifiées dans la pile de canaux de cet objet et les applique à l’échange entre votre client et le service.  
  
 Étant donné que la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] est hébergé in-process avec son application consommatrice, il n’est pas impératif d’utiliser le **ClientCredentials** classe pour définir les informations d’identification sur le client des objets de communication utilisés par l’application consommatrice. Toutefois, il apparaît conseillé de le faire.  
  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] encourage l’utilisation de la **ClientCredentials** par le biais du **AcceptCredentialsInUri** propriété de liaison. Cette propriété spécifie si l’adaptateur accepte le nom d’utilisateur et un mot de passe pour le système SAP dans l’URI de connexion. **AcceptCredentialsInUri** par défaut est **false**, ce qui signifie que l’adaptateur lève une exception si l’URI de connexion contient des informations d’identification. Vous pouvez définir **AcceptCredentialsInUri** à **true** pour fournir des informations d’identification dans l’URI de connexion. En fait, vous devez le faire dans certains cas ; par exemple, lorsque vous spécifiez un URI de connexion pour un point de terminaison de service hôte ou un **IReplyChannel** dans les scénarios de trafic entrants.  
  
 L’exemple suivant montre comment utiliser le **ClientCredentials** classe pour définir les informations d’identification pour le système SAP sur un client WCF.  
  
```  
SAPBinding binding = new SAPBinding();  
  
// Set endpoint address  
EndpointAddress endpointAddress = new EndpointAddress("sap://CLIENT=800;LANG=EN;@a/YourSAPHost/00?RfcSdkTrace=False&AbapDebug=False&UseSapGui=Without");  
  
// Create client and set credentials  
RfcClient rfcClient = new RfcClient(binding, endpointAddress);  
rfcClient.ClientCredentials.UserName.UserName = "YourUserName";  
rfcClient.ClientCredentials.UserName.Password = "YourPassword";  
```  
  
## <a name="how-can-i-provide-for-more-secure-data-exchange-across-process-boundaries"></a>Comment puis-je fournir pour échanger des données plus sécurisée au-delà des limites de processus ?  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] est hébergé in-process avec l’application ou le service qui la consomme. Étant donné que l’adaptateur est hébergé in-process avec le consommateur, il n’est pas nécessaire pour assurer la sécurité des messages échangés entre le client et le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. Toutefois, si l’application consommatrice ou le service envoie des messages qui contiennent des informations de base de données sensibles sur une limite de processus à un autre service ou client, vous devez prendre des mesures pour assurer une protection adéquate pour ces données dans votre environnement. [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]fournit plusieurs options pour aider à sécuriser les messages envoyés entre les clients et services. Pour plus d’informations sur contribue à sécuriser les messages envoyés entre les clients et services dans [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)], consultez [sécurisation des Services et les Clients](https://msdn.microsoft.com/library/ms734736.aspx). Pour plus d’informations générales sur la sécurité des fonctionnalités qui [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] fournit, consultez [Windows Communication Foundation Security](https://msdn.microsoft.com/library/ms732362.aspx).  
  
## <a name="see-also"></a>Voir aussi  
[Meilleures pratiques pour sécuriser l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/best-practices-to-secure-the-sap-adapter.md)  
[Sécuriser vos applications SAP](../../adapters-and-accelerators/adapter-sap/secure-your-sap-applications.md)   