---
title: "Les scénarios de messagerie unidirectionnels pour l’exemple de résolution dynamique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 38237840-e957-4298-84c9-700ec72f2bc5
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8296c46561a8afa928033ae6002e3de621170234
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="one-way-messaging-scenarios-for-the-dynamic-resolution-sample"></a>Scénarios de messagerie unidirectionnels pour l’exemple de résolution dynamique
Cette rubrique montre comment vous pouvez exécuter les scénarios de messagerie unidirectionnels pour la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] exemple de résolution dynamique.  
  
 **Pour exécuter les scénarios de messagerie unidirectionnels pour l’exemple de résolution dynamique**  
  
1.  Avant d’exécuter cet exemple pour la première fois, assurez-vous que la réception emplacement URL pointe vers le répertoire approprié. Spécifiez le \Source\Samples\DynamicResolution\Test\Filedrop\In sous-dossier source pour le DynamicResolution_FILE emplacement de réception. En outre, assurez-vous que le port d’envoi dynamique nommé DynamicResolutionOneWay existe.  
  
    > [!NOTE]
    >  L’exemple de résolution dynamique utilise le mécanisme de résolution dynamique pour envoyer des messages vers le dossier de sortie, un site FTP ou une file d’attente MQSeries. C’est pourquoi un port d’envoi statique n’est pas défini pour cet exemple. Le composant résolution dynamique récupère l’URL de sortie à partir de la résolution et infrastructure d’adaptateurs du fournisseur lorsqu’elle est appelée par le pipeline ESBReceiveXml, qui est configuré dans le DynamicResolution_FILE l’emplacement de réception.  
  
2.  Si l’application GlobalBank.ESB n’est pas déjà en cours d’exécution, utilisez la Console d’Administration Microsoft BizTalk pour le démarrer.  
  
3.  Décider quel exemple que vous souhaitez exécuter. Unidirectionnel de tous les exemples (à l’exception de celle qui utilise le programme de résolution XPATH) la messagerie le fichier que naorderdoc.xml situé dans le dossier \Source\Samples\DynamicResolution\Test\Data en tant qu’entrée à l’emplacement de réception nommé DynamicResolution_FILE. Il existe sept exemples de messagerie unidirectionnels, chacun représenté par un fichier de liaison unique. Les tableaux suivants répertorient ces exemples, avec leurs fichiers de liaison associés et leurs descriptions.  
  
    |Fichier entrant dans le fichier sortant à l’aide de l’outil de résolution statique|  
    |-------------------------------------------------------------|  
    |Utilise le fichier de liaison nommé GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_FILE_STATIC_Bindings.xml pour définir l’emplacement de réception et les propriétés de port d’envoi.|  
    |Définit les mappages statiquement au niveau du port de réception.|  
    |Utilise le répartiteur ESB à l’emplacement de réception pour la résolution de point de terminaison.|  
  
    |Fichier entrant dans le fichier de sortie à l’aide de l’outil de résolution UDDI|  
    |-----------------------------------------------------------|  
    |Utilise le fichier de liaison nommé GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_FILE_UDDI_Bindings.xml pour définir l’emplacement de réception et les propriétés de port d’envoi.|  
    |Définit les mappages statiquement au niveau du port de réception.|  
    |Utilise le répartiteur ESB à l’emplacement de réception pour la résolution de point de terminaison.|  
  
    |Fichier entrant dans le fichier sortant à l’aide du programme de résolution UDDI via la clé du Service UDDI|  
    |----------------------------------------------------------------------------|  
    |Utilise le fichier de liaison nommé GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_FILE_UDDI_SERVICEKEY_ Bindings.xml pour définir l’emplacement de réception et les propriétés de port d’envoi.|  
    |Définit les mappages statiquement au niveau du port de réception.|  
    |Utilise le répartiteur ESB à l’emplacement de réception pour la résolution de point de terminaison.|  
  
    > [!NOTE]
    >  Pour l’exemple précédent, vous devez modifier la clé de service dans le fichier de liaison à un qui existe sur le serveur UDDI cible.  
  
    |Fichier entrant FTP sortant à l’aide de l’outil de résolution statique|  
    |------------------------------------------------------------|  
    |Utilise le fichier de liaison nommé GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_FTP_STATIC_Bindings.xml pour définir l’emplacement de réception et les propriétés de port d’envoi.|  
    |Définit les mappages statiquement au niveau du port de réception.|  
    |Utilise le répartiteur ESB à l’emplacement de réception pour la résolution de point de terminaison.|  
  
    |Fichier de trafic entrant FTP sortant à l’aide du programme de résolution statique et du paramètre ENDPOINTCONFIG|  
    |-----------------------------------------------------------------------------------------|  
    |Utilise le fichier de liaison nommé GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_FTP_STATIC__ ENDPOINTCONFIG_Bindings.xml pour définir l’emplacement de réception et les propriétés de port d’envoi.|  
    |Définit les mappages statiquement au niveau du port de réception.|  
    |Utilise le répartiteur ESB à l’emplacement de réception pour la résolution de point de terminaison.|  
    |Passe des paires nom/valeur supplémentaires pour le fournisseur de l’adaptateur à définir.|  
  
    |Fichier entrant MQS sortant à l’aide de l’outil de résolution statique|  
    |------------------------------------------------------------|  
    |Utilise le fichier de liaison nommé GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_MQS_STATIC_Bindings.xml pour définir l’emplacement de réception et les propriétés de port d’envoi.|  
    |Définit les mappages statiquement au niveau du port de réception.|  
    |Utilise le répartiteur ESB à l’emplacement de réception pour la résolution de point de terminaison.|  
  
    |Fichier entrant dans le fichier sortant à l’aide de l’outil de résolution XPATH|  
    |------------------------------------------------------------|  
    |Utilise le fichier de liaison nommé GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_XPATH_STATIC_Bindings.xml pour définir l’emplacement de réception et les propriétés de port d’envoi.|  
    |Définit les mappages statiquement au niveau du port de réception.|  
    |Utilise le répartiteur ESB à l’emplacement de réception pour la résolution de point de terminaison.|  
    |Utilise les informations contenues dans le message pour déterminer le point de terminaison approprié. Les fichiers de test que vous pouvez utiliser avec cet exemple sont NAOrderDoc_XPATH_FILE.xml, NAOrderDoc_XPATH_FTP.xml et NAOrderDoc_XPATH_MQS.xml.|  
  
4.  Importez le fichier de liaison pour l’exemple de messagerie que vous souhaitez exécuter dans l’application GlobalBank.ESB.  
  
5.  Dans l’Explorateur Windows, ouvrez le dossier \Source\Samples\DynamicResolution\Test\Data et copiez le fichier d’entrée approprié dans le dossier \Source\Samples\DynamicResolution\Test\Filedrop\In. Le fichier que vous utilisez dépend de l’exemple que vous avez décidé d’exécuter :  
  
    -   Pour l’exemple XPATH, utilisez un des fichiers suivants : NAOrderDoc_XPATH_FILE.xml, NAOrderDoc_XPATH_FTP.xml ou NAOrderDoc_XPATH_MQS.xml.  
  
    -   Pour tous les autres exemples, utilisez le fichier NAOrderDoc.xml.  
  
6.  Recherchez dans l’emplacement approprié pour le message reçu. Le fichier de liaison que vous avez utilisé dépend de l’emplacement. Voici quelques exemples :  
  
    -   Le fichier entrant FTP Outbound exemple remet le message dans le répertoire virtuel FTP appelé Out que vous avez créé lorsque vous avez installé l’exemple.  
  
    -   L’exemple de fichier sortant fichier entrant de remet le message dans le sous-dossier \DynamicResolution\Test\Filedrop\Out.  
  
    -   Le fichier entrant exemple MQS sortant de remet le message au TEST. LES files d’attente que vous avez créé lorsque vous avez installé l’exemple.  
  
    -   Le fichier entrant fichier sortant à l’aide de l’exemple de programme de résolution XPATH de remet le message à l’emplacement spécifié dans le message. Les exemples de documents contient le type de transport et d’emplacement de destination (le type de transport est ajouté au nom du fichier de message ; par exemple, le message NAOrderDoc_XPATH_FTP.xml contient la spécification de type de transport FTP).  
  
 Pour comprendre comment l’exemple utilise le répartiteur d’ESB et les composants de pipeline désassembleur de répartiteur ESB, consultez [dynamique résolution exemple fonctionnement](../esb-toolkit/how-the-dynamic-resolution-sample-works.md).