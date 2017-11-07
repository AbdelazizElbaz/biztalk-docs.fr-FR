---
title: "Créer des artefacts d’envoi TIBCO EMS | Documents Microsoft"
description: "Créer le port d’envoi, puis configurez les propriétés de transport pour utiliser l’adaptateur TIBCO Enterprise Message Service dans BizTalk Server"
ms.custom: 
ms.date: 10/23/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8f82609c-1847-4796-a24c-28cb350ec739
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 570693f4d5644f0ea850a53ec537ce30db5ca568
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="creating--tibco-enterprise-message-service-send-handlers"></a>Création des gestionnaires d'envoi TIBCO Enterprise Message Service
Cette section décrit la configuration du port d'envoi pour la connexion à TIBCO Enterprise Message Service (EMS) et l'utilisation d'un fichier XML dans votre orchestration pour interagir avec TIBCO EMS lors de l'exécution.  


## <a name="create-a-send-port"></a>Créer un port d'envoi  
  
1.  Dans la Console Administration de BizTalk Server, développez **groupe BizTalk**, développez **Applications**, puis développez votre application.  
  
2.  Avec le bouton droit **Ports d’envoi**, sélectionnez **nouveau**, puis sélectionnez **Port d’envoi statique avec sollicitation-réponse**.  
  
3.  Dans le **propriétés de Port d’envoi**, procédez comme suit :  
  
    1.  Tapez un nom pour le port d’envoi, par exemple, `SendToTIBCOEMS`.  
  
    2.  À partir de la **Type** la liste déroulante, sélectionnez **TIBCO EMS**.  
  
    3.  À partir de la **Gestionnaire d’envoi** liste déroulante, sélectionnez l’URI.  
  
    4.  À partir de la **Pipeline d’envoi** la liste déroulante, sélectionnez **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**. À partir de la **Pipeline de réception** la liste déroulante, sélectionnez **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.  

        > [!NOTE]
        > L’adaptateur BizTalk pour TIBCO Enterprise Message Service requiert la sélection de XMLTransmit pour envoyer et XMLReceive pour la réception.  
  
    6.  Sélectionnez **configurer** pour configurer le port d’envoi.  
  
4.  Dans le **propriétés du Transport TIBCO EMS** boîte de dialogue zone, procédez comme suit :  
  
    1.  Entrez **la gestion des messages**, **définition de la connexion serveur**, **prise en charge des transactions**, **nom d’utilisateur**et le  **mot de passe**.  
  
         Il n'est pas nécessaire de définir les informations de connexion.  
  
    2.  Dans la liste, sélectionnez l'application associée que vous avez créée pour représenter le système TIBCO EMS.  
  
    3.  Pour **utiliser SSO**, sélectionnez **Oui**.  
  
    4.  Sélectionnez **OK**.  
  
5.  Sélectionnez **OK**. 

## <a name="set-send-port-transport-properties"></a>Définir les propriétés de port d’envoi
Les propriétés de transport de l'adaptateur TIBCO Enterprise Message Service sont configurées au moment de la conception et utilisées lors de l'exécution. Dans le **propriétés du Transport**, vous définir les paramètres de connexion et les informations d’identification spécifiques au système du serveur et les objets que vous essayez d’accéder.  
  
 ![](../core/media/tib-tibcoemssendtransportpropertiess.gif "TIB_TIBCOEMSSendTransportPropertiess")  
  
  
1.  Dans le **propriétés du Transport**, développez **définition système**et entrez les informations requises pour la connexion au serveur TIBCO EMS.  
  
     Vous devez définir les paramètres de configuration pour connecter l'adaptateur Microsoft BizTalk pour TIBCO Enterprise Message Service à TIBCO EMS. **Ces données respecte la casse.**  
  
2.  Développez **gestion des messages**et entrez les informations requises.  
  
    |Paramètre| Description|  
    |---------------|-----------------|  
    |`Message Expiration Time`|Nombre entier décrivant le délai pendant lequel le message est conservé dans la file d'attente ou la rubrique. À l'expiration du délai, le message est supprimé par le serveur TIBCO EMS.<br /><br /> Il s'agit d'un synonyme de l'en-tête de propriété de message EMS.Expiration. Il peut être remplacé par l'orchestration.<br /><br /> La valeur par défaut est 0 milliseconde, ce qui signifie que le message n'expire pas à partir de la destination.|  
    |`Message is Persistent`|Les messages sont écrits sur le disque par le serveur TIBCO EMS avant de faire l'objet d'un accusé de réception.<br /><br /> Il s'agit de la propriété d'en-tête TibcoEMS.DeliveryMode. Celle-ci spécifie la conservation des messages envoyés dans la file d'attente par le serveur, avant l'envoi d'un accusé de réception du message à l'adaptateur.<br /><br /> La valeur par défaut est **True**.|  
    |`Message Priority`|Classement numérique de 0 à 9 qui définit la priorité du message. Une valeur élevée indique une priorité élevée.<br /><br /> La priorité affecte l'ordre dans lequel le serveur remet les messages aux consommateurs (valeurs plus élevées remises en premier).<br /><br /> La spécification JMS définit dix niveaux de valeur de priorité, de zéro (priorité la plus basse) à 9 (priorité la plus élevée). Elle suggère que les clients considèrent les niveaux 0 à 4 comme priorité normale, et ceux de 5 à 9 comme priorité accélérée.<br /><br /> Valeur par défaut est **4**.|  
  
3.  Développez **définition de la connexion serveur** et entrez les informations requises.  
  
    |Paramètre| Description|  
    |---------------|-----------------|  
    |`Destination`|Paramètre obligatoire. Définit le nom et le type de la destination. Par exemple : staticqueue [Q1].<br /><br /> Définit la file d’attente ou rubrique au format suivant : {static} {dynamic] Queue [nom_file_attente] ou {static} {[dynamic] Topic [nom_rubrique]. **Remarque :** vous pouvez envoyer un message vers une destination qui n’existe pas. Dans ce cas, TIBCO Enterprise Message Service crée la destination ; Cela est appelé un *Destination dynamique*. Celle-ci est créée par un producteur et supprimée une fois le message consommé et le producteur déconnecté. A *destination statique* est une destination qui peuvent uniquement créés par un administrateur de Service TIBCO Enterprise Message. Vous ne pouvez pas vous connecter à un port dynamique lorsque vous ouvrez une connexion à une destination car l'adaptateur BizTalk pour TIBCO Enterprise Message Service utilise un mécanisme de recherche de nom sur le serveur. Seuls les ports statiques sont visibles lorsque vous utilisez la recherche de nom. Lors de la connexion à un port dynamique, vous pouvez utiliser des destinations statiques. Si aucune destination de ce nom n'existe, une destination est toutefois créée. La destination permet de spécifier de manière explicite le type de destination à utiliser lors de la définition du port. La syntaxe pour la Destination n’est pas respecter la casse : staticqueue [nom_file_attente], statictopic [nom_rubrique], dynamicqueue [nom_file_attente] ; dynamictopic [nom_rubrique].|  
    |`Port Number`|Port sur lequel le serveur TIBCO EMS écoute.|  
    |`Server Name`|Paramètre obligatoire. Nom du système qui héberge le serveur TIBCO EMS.|  
  
4.  Indiquez les informations d'identification à l'aide de l'authentification unique (SSO).  
  
     Deux méthodes permettent d'accéder au système TIBCO EMS. Vous pouvez utiliser les informations d'identification (paramètres Nom d'utilisateur et Mot de passe) ou l'authentification unique.  
  
    -   Sélectionnez **Oui** dans les **utiliser SSO** à utiliser l’authentification unique.  
  
    -   Sélectionnez une application associée dans la liste.  
  
         Une application associée (créée par les outils d'authentification unique de l'entreprise) représente une application telle que TIBCO EMS. L'adaptateur BizTalk pour TIBCO EMS utilise les informations d'identification d'un utilisateur d'application. Celles-ci sont extraites de la base de données SSO pour le système de serveur pour une application associée spécifiée.  
  
         Pour plus d’informations sur la création d’une application associée, consultez [création d’Applications associées](../core/creating-affiliate-applications5.md).  
  
5.  Dans **prend en charge les transactions**, sélectionnez **Oui** si ce port d’envoi prend en charge les transactions.  
  
     Si vous activez la prise en charge des transactions sur le port, toutes les orchestrations qui utilisent ce port doivent être transactionnelles, sans quoi tous les appels sont annulés (par exemple, ils ne sont pas validés). L'objet d'étendue ajouté à l'orchestration contrôle le cycle de vie des transactions.  
  
6.  Développez **informations d’identification utilisateur** et entrez le **nom d’utilisateur** et **mot de passe** pour accéder au serveur TIBCO EMS.  
  
    |Paramètre| Description|  
    |---------------|-----------------|  
    |`Password`|Mot de passe de l'utilisateur utilisé pour communiquer avec un démon TIBCO EMS.<br /><br /> Si vous n’avez pas sélectionné **utiliser SSO**, vous devez définir les paramètres d’informations d’identification pour l’adaptateur BizTalk pour TIBCO EMS communiquer avec un démon TIBCO EMS.|  
    |`User Name`|Nom d'un utilisateur utilisé pour communiquer avec un démon TIBCO EMS.<br /><br /> Si vous n’avez pas sélectionné **utiliser SSO**, vous devez définir les paramètres d’informations d’identification pour l’adaptateur BizTalk pour TIBCO EMS communiquer avec un démon TIBCO EMS.|  
  
7.  Cliquez sur **appliquer**, puis cliquez sur **OK**.  

   
## <a name="next-steps"></a>Étapes suivantes
[Créer des artefacts de réception](../core/creating-tibco-enterprise-message-service-receive-handlers.md)  
[Propriétés de contexte de message TIBCO EMS](../core/message-context-properties-in-biztalk-server.md)