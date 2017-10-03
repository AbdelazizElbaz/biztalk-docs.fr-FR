---
title: "Installer et exécuter l’exemple de résolution dynamique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4359987-b18c-44f5-a2cf-e30e17ac5e9f
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04d697028eb76cf922cf4bf5e5db85c561c67d00
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="installing-and-running-the-dynamic-resolution-sample"></a>Installer et exécuter l’exemple de résolution dynamique
L’exemple de résolution dynamique illustre des scénarios d’utilisation classiques pour le répartiteur d’ESB et les composants de pipeline désassembleur de répartiteur ESB. Il montre comment vous pouvez utiliser les composants de dynamiquement résoudre l’emplacement du point de terminaison, définir des propriétés de routage et résoudre et exécuter des mappages de Microsoft BizTalk au niveau de la messagerie sans l’aide d’une orchestration. Il montre également les modèles de messagerie unidirectionnels ou bidirectionnels.  
  
> [!NOTE]
>  Pour un résultat optimal lorsque vous serez familiarisé avec le mécanisme de résolution dans la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)], vous devez exécuter le [installer et exécuter l’exemple de Service de programme de résolution](../esb-toolkit/installing-and-running-the-resolver-service-sample.md) avant d’exécuter l’exemple de résolution dynamique.  
  
 L’exemple d’application contienne deux emplacements de réception et deux ports d’envoi dynamiques, l’exemple utilise pour illustrer plusieurs cas d’usage pour les composants de résolution dynamique. Chaque cas d’usage montre comment les programmes de résolution et les fournisseurs de carte dans la résolution et l’infrastructure du fournisseur de carte, lorsqu’il est utilisé en combinaison, peuvent servir pour diverses solutions de messagerie faiblement couplées.  
  
## <a name="one-way-messaging-scenarios"></a>Scénarios de messagerie unidirectionnels  
 Tous les unidirectionnel de la messagerie scénarios (à l’exception de celle qui utilise le programme de résolution XPATH) le fichier NAOrderDoc.xml, situé dans le dossier \Source\Samples\DynamicResolution\Test\Data, en tant qu’entrée à la réception, emplacement nommé par DynamicResolution_FILE. Il existe sept exemples de messagerie unidirectionnels, tous représentés par une liaison unique de fichier que vous devez importer avant d’exécuter chaque exemple.  
  
## <a name="two-way-messaging-scenarios"></a>Scénarios de messagerie bidirectionnelles  
 Tous les scénarios de messagerie bidirectionnelles utilisent l’exemple ESB. Service de NorthAmericanServices Web situé à http://localhost/ESB.NorthAmericanServices/CustomerOrder.asmx pour publier le message de demande dans BizTalk. Vous pouvez exécuter ce service Web à l’aide de Microsoft InfoPath ou via un utilitaire tel que le Storm disponible à partir [CodePlex](http://go.microsoft.com/fwlink/?LinkID=187762&clcid=0x409) ([http://go.microsoft.com/fwlink/?LinkID=187762&clcid=0x409](http://go.microsoft.com/fwlink/?LinkID=187762&clcid=0x409)).  
  
 Chaque exemple résout dynamiquement l’URL de point de terminaison pour envoyer le message à l’exemple ESB. Service Web de CanadianServices à http://localhost/ESB.CanadianServices/SubmitPOService.asmx. L’exemple exécutera la **submitOrder** action ou le **submitPurchase** action, selon les résultats du processus de résolution. L’emplacement de réception pour les scénarios de messagerie bidirectionnelles est DynamicResolutionReqResp_SOAP. Il existe des exemples de messagerie bidirectionnelles 10, tous représentés par une liaison unique de fichier que vous devez importer avant d’exécuter chaque exemple.  
  
## <a name="binding-files"></a>Fichiers de liaison  
 Les fichiers de liaison pour cet exemple sont situés dans le dossier nommé \Source\Samples\DynamicResolution\Samples\Release.  
  
 Les noms de fichiers de liaison démarrent tous avec GlobalBank.ESB.DynamicResolution_SubmitOrder_To, suivi d’une indication de l’exemple individuel auxquels elles s’appliquent. Par exemple, le fichier de liaison pour l’exemple « Entrant de fichier de sortie de fichier à l’aide du programme de résolution statique » est GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_FILE_STATIC_Bindings.xml.  
  
 Emplacement dans l’exemple d’application est réinitialisé à chaque fois que vous importez un de la liaison de fichiers dans l’application BizTalk de GlobalBank.ESB, sous-jacent de réception. Les filtres de port d’envoi dynamique associés sur le nom de port de réception. Par conséquent, pour exécuter un test, vous simplement importez un des fichiers de liaison et supprimez le message correctement nommé dans le dossier d’entrée (pour les scénarios de messagerie unidirectionnels) ou appelez le service Web de NorthAmerican à l’aide d’InfoPath, l’utilitaire Storm ou tout autre client approprié.  
  
## <a name="sample-dependencies"></a>Dépendances de l’exemple  
 L’exemple de résolution dynamique a des dépendances sur un nombre d’assemblys qui font partie de l’installation d’ESB principaux. Ces assemblys sont les suivants :  
  
-   **Microsoft.Practices.ESB.PipelineComponents.dll**. Contient le composant de Pipeline de répartiteur ESB.  
  
-   **Microsoft.Practices.ESB.Resolver.dll**. Il implémente le Gestionnaire de programme de résolution appelé par le pipeline.  
  
-   **Microsoft.Practices.ESB.Resolver.BRE.dll**. Cela met en œuvre le programme de résolution du moteur de règles métier.  
  
-   **Microsoft.Practices.ESB.Resolver.STATIC.dll**. Cela met en œuvre le programme de résolution statique.  
  
-   **Microsoft.Practices.ESB.Resolver.UDDI.dll**. Cela met en œuvre le programme de résolution UDDI.  
  
-   **Microsoft.Practices.ESB.Resolver.UDDI3.dll**. Cela met en œuvre le programme de résolution UDDI3.  
  
-   **Microsoft.Practices.ESB.Resolver.XPATH.dll**. Cela met en œuvre le programme de résolution de XPATH.  
  
-   **Microsoft.Practices.ESB.Resolver.Schemas.dll**. Contient les schémas de programme de résolution.  
  
-   **Microsoft.Practices.ESB.Adapter.dll**. Il implémente le Gestionnaire d’adaptateur.  
  
-   **Microsoft.Practices.ESB.Adapter.FTP.dll**. Il implémente le fournisseur de l’adaptateur FTP.  
  
-   **Microsoft.Practices.ESB.Adapter.FILE.dll**. Il implémente le fournisseur de l’adaptateur de fichier.  
  
-   **Microsoft.Practices.ESB.Adapter.MQSeries.dll**. Il implémente le fournisseur de l’adaptateur MQSeries.  
  
-   **Microsoft.Practices.ESB.Adapter.WcfBasicHttp.dll**. Il implémente le fournisseur de l’adaptateur WCF-BasicHttp.  
  
-   **Microsoft.Practices.ESB.Adapter.WcfWSHttp.dll**. Il implémente le fournisseur de l’adaptateur WCF-WSHttp.  
  
 L’exemple de résolution dynamique dépend également de la configuration correcte des programmes de résolution et adaptateurs précédent. Assurez-vous que vous complétez le processus de configuration, comme décrit dans l’installation du [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].  
  
 Cette section contient les rubriques suivantes :  
  
-   [Installation de l’exemple de résolution dynamique](../esb-toolkit/installing-the-dynamic-resolution-sample.md)  
  
-   [Exécution de l’exemple de résolution dynamique](../esb-toolkit/running-the-dynamic-resolution-sample.md)