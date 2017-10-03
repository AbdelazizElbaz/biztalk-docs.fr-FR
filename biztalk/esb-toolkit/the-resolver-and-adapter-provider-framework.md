---
title: "Le programme de résolution et l’infrastructure d’adaptateurs fournisseur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb7ea42e-b32c-40a8-b36b-c349f56f6edd
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 717e7919b3f822ba582ea3c1e50f251eea18a06b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-resolver-and-adapter-provider-framework"></a>Le programme de résolution et l’infrastructure d’adaptateurs fournisseur
Le programme de résolution et l’infrastructure d’adaptateurs fournisseur prend en charge la résolution de point de terminaison, de transformation et d’itinéraire et le routage. L’infrastructure peut résoudre les points de terminaison et définir les propriétés de l’adaptateur de sortie dynamiquement. Après un programme de résolution composant résout un point de terminaison (par exemple, à l’aide de Universal Description, Discovery and Integration [UDDI] pour rechercher un point de terminaison de service Web sortants), inscrit un adaptateur fournisseur composant définit des propriétés spécifiques de [!INCLUDE[prague](../includes/prague-md.md)] cartes. Par exemple, le fournisseur de l’adaptateur WCF-BasicHttp est chargé de définir les propriétés de contexte pour le point de terminaison URI qui utilisera l’adaptateur BizTalk spécifique ; le message spécifiques à BizTalk le fournisseur de l’adaptateur FTP est chargé de définir les propriétés spécifiques à l’adaptateur FTP.  
  
 Un des objectifs de l’infrastructure de fournisseur de carte et de programme de résolution sont prise en charge de résolution et de routage au niveau messagerie, sans exiger l’utilisation des orchestrations BizTalk, ou au niveau de l’orchestration. Dans les deux cas, le framework enfichable fournit le développement, le déploiement et l’inscription de nouveaux programmes de résolution et les fournisseurs de carte. Tous les fournisseurs de carte et les programmes de résolution implémentent des interfaces bien définies et sont chargées à la demande à l’aide de l’inscription dans les fichiers de configuration.  
  
 Les composants de pipeline le répartiteur d’ESB et le désassemblage de répartiteur ESB utilisent le programme de résolution et l’infrastructure d’adaptateurs fournisseur en passant la chaîne de connexion à partir de la feuille de route en-tête SOAP ou la configuration de pipeline pour le Gestionnaire de programme de résolution.  
  
 Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] configuration contient les détails d’inscrits tous les programmes de résolution et les fournisseurs de carte. Au moment de l’exécution, les gestionnaires de programme de résolution et les gestionnaires d’adaptateur lire les détails des programmes de résolution inscrits et des fournisseurs de carte à partir des fichiers de configuration, charger les assemblys appropriées et les stocker dans un cache de niveau hôte BizTalk. Cette technique de mise en cache supprime la nécessité de répétées lors de la lecture des fichiers de configuration et le chargement des assemblys pour chaque message envoyé.  
  
 Pour plus d’informations sur la façon dont le programme de résolution et l’infrastructure d’adaptateurs fournisseur fonctionne et comment vous pouvez l’étendre en créant des programmes de résolution personnalisés et les fournisseurs de carte, consultez [modification et l’extension de BizTalk ESB Toolkit](../esb-toolkit/modifying-and-extending-the-biztalk-esb-toolkit.md).  
  
## <a name="supported-resolution-mechanisms-resolvers"></a>Mécanismes de résolution prise en charge (résolution)  
 BizTalk ESB Toolkit inclut les programmes de résolution suivants : **statique, UDDI, UDDI3, XPATH, BRE, BRI, itinéraire, itinéraire statique** et **LDAP**.  
  
 Chaîne de connexion d’un programme de résolution est toujours constitué d’un **moniker** (tel que **BRE**) suivi de « :\\\\» et les détails de connexion ou le traitement. Le moniker correspond à la définition de la résolution associée dans le fichier de configuration. Les propriétés associées à chaque chaîne de connexion sont uniques, et toutes les propriétés ne sont nécessaires. Vous trouverez le schéma pour chacun des programmes de résolution dans l’architecture ESB. Resolvers.Schemas projet.  
  
 Voici quelques exemples de chaînes de connexion :  
  
-   **STATIQUE**  
  
     STATIQUE :\\\TransportType= ;  
  
     TransportLocation = http://localhost/ESB.CanadianServices/SubmitPOService.asmx;  
  
     Action = ;  
  
     EndPointConfig = ;  
  
     JaxRpcResponse = false ;  
  
     MessageExchangePattern = ;  
  
     TargetNamespace = http://globalbank.esb.dynamicresolution.com/canadianservices/;  
  
     TransformType = ;  
  
-   **UDDI**  
  
     UDDI :\\\serverUrl= http://localhost : 9901/rmengine ;  
  
     serviceName = OrderPurchaseWebService ;  
  
     serviceProvider = ESB pratiques de Microsoft  
  
-   **XPATH**  
  
     \\\TransportType= ;  
  
     TransportLocation = /*[local-name () = 'OrderDoc' et namespace-uri() = 'http://globalbank.esb.dynamicresolution.com/northamericanservices/'] /*[local-name () = 'ID' et namespace-uri() = 'http://globalbank.esb.dynamicresolution.com/northamericanservices/'] ;  
  
     Action = ;  
  
     EndPointConfig = ;  
  
     JaxRpcResponse = ;  
  
     MessageExchangePattern = ;  
  
     TargetNamespace = /*[local-name () = 'OrderDoc' et namespace-uri() = 'http://globalbank.esb.dynamicresolution.com/northamericanservices/'] /*[local-name () = 'customerName' and namespace-uri () ='http : / / globalbank.ESB.dynamicresolution.com/northamericanservices/'] ;  
  
     TransformType = ;  
  
-   **BRE**  
  
     BRE :\\\policy=GetCanadaEndPoint ;  
  
     version = ;  
  
     useMsg = ;  
  
-   **BRI**  
  
     BRI :\\\policy=ResolveItinerary ;  
  
     version = ;  
  
     useMsg = ;  
  
-   **FEUILLE DE ROUTE**  
  
     ITINÉRAIRE :\\\name=TwoWayTestItinerary ;  
  
     version = ;  
  
-   **ITINÉRAIRE STATIQUE**  
  
     ITINÉRAIRE statique :\\\name=TwoWayTestItinerary ;  
  
     version = ;  
  
-   **LDAP**  
  
     LDAP :\\\TransportType=SMTP ;  
  
     TransportLocation = {message}  
  
     Filtre = (&amp;(objectClass = User) (&#124; (userPrincipalName =yourname@domain.com))) ;  
  
     SearchRoot = ;  
  
     SearchScope = sous-arborescence ;  
  
     EndpointConfig = Subject = Message de Test d’itinéraire à la messagerie de {}&amp;  
  
     SMTPAuthenticate = 0&amp;  
  
     SMTPHost = 127.0.0.1&amp;  
  
     FROM =test@globalbank.com&amp;  
  
     DeliveryReceipt = false&amp;  
  
     MessagePartsAttachments = 0&amp;  
  
     ReadReceipt = false ;  
  
     ThrowErrorIfNotFound = false ;  
  
     Action = ;  
  
     JaxRpcResponse = false ;  
  
     MessageExchangePattern = ;  
  
     TargetNamespace = ;  
  
     TransformType = ;  
  
 Pas de tous les attributs dans la chaîne de connexion sont obligatoires. En outre, **EndPointConfig** est un attribut spécial qui n’importe quel programme de résolution peut remplir et retourner. Si vous le souhaitez, le programme de résolution peut stocker les paires nom/valeur qui correspondent aux propriétés de contexte de l’adaptateur BizTalk spécifiques, lequel il peut, à son tour, écrire dans le contexte du message BizTalk.  
  
 Dans ce cas, le **ResolverDictionary** instance qui contient toutes les propriétés résolues retourné par le processus de résolution, puis passe au gestionnaire d’adaptateur. Le Gestionnaire d’adaptateur transmet le dictionnaire pour le fournisseur de l’adaptateur spécifique qui définira le contexte de BizTalk spécifique à l’adaptateur et le point de terminaison spécifique de propriétés du message. Rechercher les programmes de résolution le **EndPointConfig** propriété, extraire les paires nom/valeur qui correspondent à leurs propriétés respectives de carte, puis définissez ces valeurs sur le message.  
  
## <a name="supported-adapter-providers"></a>Fournisseurs de carte pris en charge  
 Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] inclut les fournisseurs de carte intégrés suivants : **fichier, FTP, SMTP, MQSeries, WCF-BasicHttp, WCF-WSHttp,** et **WCF-Custom**. Le nom de chaque fournisseur de l’adaptateur est identique au nom de la carte associée (type de transport) dans BizTalk Server.  
  
 Un avantage majeur de l’infrastructure de fournisseur de carte et de programme de résolution est que vous pouvez l’étendre en créant et en enregistrant vos propres programmes de résolution personnalisés pour résoudre les informations de point de terminaison et les fournisseurs d’adaptateur personnalisé pour définir des propriétés spécifiques d’adaptateurs BizTalk inscrits. Pour plus d’informations, consultez [modification et l’extension de BizTalk ESB Toolkit](../esb-toolkit/modifying-and-extending-the-biztalk-esb-toolkit.md).