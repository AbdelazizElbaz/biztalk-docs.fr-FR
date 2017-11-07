---
title: "Créer des artefacts de l’envoi d’adaptateur TIBCO Rendezvous | Documents Microsoft"
description: "Créer un port d’envoi, de configurer les propriétés de transport pour envoyer des messages à TIBCO Rendezvous à partir de BizTalk"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad996c4f-e6ed-4582-a768-0cb1ad25b1d8
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed6d03885423582c2657c9cb624c63f26ce1c6f3
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="create-tibco-rendezvous-send-handlers"></a>Créer des gestionnaires d’envoi TIBCO Rendezvous
Cette section décrit la création d'un schéma pour utiliser TIBCO Rendezvous dans une orchestration BizTalk Server.  
  
## <a name="create-a-send-port"></a>Créer un port d'envoi
  
1.  Dans **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez votre application.  
  
2.  Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**.  
  
3.  Dans le **propriétés de Port d’envoi** boîte de dialogue zone, procédez comme suit :  
  
    1.  Tapez un nom pour le port d’envoi, par exemple, `SendToTIBCORV`.  
  
    2.  À partir de la **Type** la liste déroulante, sélectionnez **TIBCO Rendezvous**.  
  
    3.  À partir de la **Gestionnaire d’envoi** liste déroulante, sélectionnez l’URI.  
  
    4.  Dans la liste déroulante Pipeline d’envoi, sélectionnez **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.  À partir de la **Pipeline de réception** la liste déroulante, sélectionnez **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.  

        > [!NOTE]
        > L’adaptateur Microsoft BizTalk pour TIBCO Rendezvous requiert que vous sélectionnez pipeline XMLTransmit pour l’envoi et le pipeline XMLReceive de réception.
        
    6.  Cliquez sur **configurer** pour configurer le port d’envoi.  
  
4.  Dans le **propriétés du Transport TIBCO Rendezvous** boîte de dialogue zone, procédez comme suit :  
  
    1.  Saisissez les propriétés.  
  
         Il n'est pas nécessaire de définir les informations de connexion.  
  
    2.  Dans la liste, sélectionnez l'application SSO associée que vous avez créée pour représenter le système TIBCO Rendezvous.  
  
    3.  Pour **utiliser SSO**, sélectionnez **Oui**.  
  
    4.  Cliquez sur **OK**.  
  
5.  Cliquez sur **OK**.  

## <a name="set-the-transport-properties"></a>Définir les propriétés de transport
La boîte de dialogue Propriétés du transport TIBCO Rendezvous est utilisée pour l'exécution. Dans le **propriétés du Transport**, vous définissez les paramètres de connexion qui identifient le domaine TIBCO Rendezvous où vous souhaitez publier les messages générés.  
  
 
1.  Sur le **propriétés du Transport TIBCO Rendezvous** écran, développez **propriétés d’expéditeur certifié** et entrez les informations suivantes.  
  
     ![](../core/media/sadp-tibcoren-transs.gif "SAdp_TibcoRen_Transs")  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom de comptabilité**|Par défaut, cette option n'est pas renseignée. Nom du fichier de comptabilité à utiliser pour la remise des messages certifiés persistants. Utilisez des lecteurs locaux uniquement.|  
    |**Nom réutilisable**|Par défaut, cette option n'est pas renseignée. Nom de destinataire réutilisable à utiliser pour la remise des messages certifiés. Le nom doit être unique parmi les noms de destinataires de messages certifiés sur le réseau.|  
  
2.  Développez **informations d’identification** et entrez les informations suivantes pour la connexion au serveur.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Mot de passe**|Par défaut, cette option n'est pas renseignée. Mot de passe de connexion à un démon TIBCO Rendezvous.|  
    |**Nom d'utilisateur**|Par défaut, cette option n'est pas renseignée. Nom d'utilisateur du démon TIBCO Rendezvous.|  
  
3.  Développez **paramètres généraux** et entrez les informations suivantes pour la connexion au serveur TIBCO Rendezvous.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Numéro de Page de codes**|La valeur par défaut est 65001 (page de code du codage UTF-8). Il s'agit de la page de codes qu'utilise le Kit de développement logiciel (SDK) TIBCO Rendezvous pour le codage des chaînes.|  
    |**Nom de l’objet par défaut**|Valeur par défaut est vide. Le nom du sujet est défini dans l'orchestration. Si un port est utilisé pour un type de message, vous pouvez fournir un nom de sujet par défaut et indiquer simplement les orchestrations en évitant d'avoir à définir la propriété Nom du sujet.|  
    |**Activer l’heure par lot**|La valeur par défaut est False. Fonctionnalité Activer/Désactiver l'heure par lot TIBCO Rendezvous.|  
    |**Mapper les types non pris en charge à la chaîne**|Valeur par défaut est True. Si la valeur est True, les types non pris en charge sont mappés si possible. Si la valeur est False, une erreur d'exécution est générée.|  
    |**Chemin d’accès aux données binaires, tels que les assemblys TIBCO Rendezvous**|Fournissez ces informations si elles ne figurent pas dans la variable d'environnement PATH.|  
    |**Préserver l’ordre**|Valeur par défaut est True. Active la logique d'envoi de messages à TIBCO Rendezvous dans l'ordre dans lequel ils ont été reçus de BizTalk Server. Ce paramètre force la publication des messages dans le même ordre, mais il ne signifie pas que les abonnés les reçoivent dans ce même ordre.|  
    |**Identificateur de Port d’envoi**|Cet identificateur apparaît dans les messages de journal associés à ce port. Il est fourni à titre informatif.|  
  
4.  Développez **Transport Rendezvous** et entrez les informations de connexion au serveur TIBCO Rendezvous, cliquez sur **appliquer**, puis cliquez sur **OK**.  
  
     Vous devez définir les paramètres de connexion de l'adaptateur Microsoft BizTalk pour accéder à TIBCO Rendezvous.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Démon**|Valeur par défaut est vide.<br /><br /> Paramètre Daemon du transport Rendezvous.|  
    |**Réseau**|Valeur par défaut est vide.<br /><br /> Paramètre Réseau du transport Rendezvous.|  
    |**Service**|Valeur par défaut est vide.<br /><br /> Paramètre Service du transport Rendezvous.|  
  
5.  Indiquez les informations d'identification à l'aide de l'authentification unique (SSO).  
  
     Vous pouvez utiliser deux méthodes pour accéder au système TIBCO Rendezvous. Vous pouvez utiliser les informations d'identification (paramètres Nom d'utilisateur et Mot de passe) ou l'authentification unique.  
  
    1.  Sélectionnez **Oui** dans les **utiliser SSO** à utiliser l’authentification unique.  
  
        > [!NOTE]
        >  Consultez [sécurité](../core/security-in-biztalk-adapter-for-tibco-rendezvous.md) pour plus d’informations sur la façon de configurer l’authentification unique.  
  
    2.  Sélectionnez une application associée dans la liste.  
  
         Une application associée (créée par les outils d'authentification unique de l'entreprise) représente une application telle que TIBCO Rendezvous. L'adaptateur Microsoft BizTalk pour TIBCO Rendezvous utilise les informations d'identification d'un utilisateur de l'application. Celles-ci sont extraites de la base de données SSO pour le système de serveur pour une application associée spécifiée.  
  
        > [!NOTE]
        >  Pour plus d’informations sur la création d’une application associée, consultez [création d’Applications associées](../core/creating-affiliate-applications1.md).  
  
6.  Cliquez sur **appliquer**, puis cliquez sur **OK** après avoir entré toutes les informations requises pour accepter les informations de connexion.  
  
     Vous devez définir les paramètres de connexion pour l’adaptateur BizTalk pour TIBCO Rendezvous pour accéder à TIBCO Rendezvous.  


## <a name="next-steps"></a>Étapes suivantes
  
-   [Utilisation des ports d’envoi TIBCO Rendezvous à partir de BizTalk Server](../core/using-tibco-rendezvous-send-ports-from-biztalk-server.md)  
  
-   [Mappage de types de données pour les gestionnaires d’envoi dans TIBCO Rendezvous](../core/data-type-mapping-for-send-handlers-in-tibco-rendezvous.md)  
  
-   [Propriétés de contexte de message BizTalk Server (gestionnaires d’envoi)](../core/biztalk-server-message-context-properties-send-handlers.md)