---
title: "Comment définir les propriétés du Transport TIBCO Rendezvous | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- setting transport properties
- transport properties, setting
ms.assetid: db8e8a57-a942-44d7-a651-623aa614c6be
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c9ff40d5319daa0a71d67aa3fd132c3d115923e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-set-tibco-rendezvous-transport-properties"></a>Définition des propriétés de transport TIBCO Rendezvous
La boîte de dialogue Propriétés du transport TIBCO Rendezvous est utilisée pour l'exécution. Dans le **propriétés du Transport** écran, vous définissez les paramètres de connexion qui identifient le domaine TIBCO Rendezvous où vous souhaitez publier les messages générés.  
  
### <a name="to-specify-tibco-rendezvous-transport-properties"></a>Pour spécifier les propriétés de transport TIBCO Rendezvous  
  
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
        >  Consultez [à l’aide de l’authentification unique sur](../core/using-single-sign-on5.md) pour plus d’informations sur la façon de configurer l’authentification unique.  
  
    2.  Sélectionnez une application associée dans la liste.  
  
         Une application associée (créée par les outils d'authentification unique de l'entreprise) représente une application telle que TIBCO Rendezvous. L'adaptateur Microsoft BizTalk pour TIBCO Rendezvous utilise les informations d'identification d'un utilisateur de l'application. Celles-ci sont extraites de la base de données SSO pour le système de serveur pour une application associée spécifiée.  
  
        > [!NOTE]
        >  Pour plus d’informations sur la création d’une application associée, consultez [création d’Applications associées](../core/creating-affiliate-applications1.md).  
  
6.  Cliquez sur **appliquer**, puis cliquez sur **OK** après avoir entré toutes les informations requises pour accepter les informations de connexion.  
  
     Vous devez définir les paramètres de connexion pour l’adaptateur BizTalk pour TIBCO Rendezvous pour accéder à TIBCO Rendezvous.  
  
## <a name="see-also"></a>Voir aussi  
 [Création gestionnaires d’envoi TIBCO Rendezvous](../core/creating-tibco-rendezvous-send-handlers.md)