---
title: "Comment configurer un gestionnaire d’envoi HTTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send handlers, HTTP adapters
- configuring [HTTP adapters], send handlers
- HTTP adapters, send handlers
ms.assetid: 821bf30c-b220-4ded-953d-7e745c0698b9
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c63d9a6035ccb9c9c309f43dba9ba0a45bec547
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-an-http-send-handler"></a>Comment configurer un gestionnaire d’envoi HTTP
La procédure suivante permet de modifier l'hôte auquel le gestionnaire d'envoi HTTP est associé.  
  
> [!NOTE]
>  Un seul gestionnaire d'envoi peut être associé à chaque hôte.  
  
> [!CAUTION]
>  Pour utiliser des gestionnaires d'adaptateurs HTTP ou SOAP, il est recommandé d'installer les instances d'hôtes de ces gestionnaires sur des ordinateurs Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] ou [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)].  
  
### <a name="to-change-global-variables-for-an-http-send-handler"></a>Pour modifier des variables globales d'un gestionnaire d'envoi HTTP  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis développez **Cartes**.  
  
2.  Dans la liste développée des adaptateurs, cliquez sur **HTTP**, dans le Gestionnaire d’envoi que vous souhaitez configurer clic droit volet droit, puis cliquez sur **propriétés**.  
  
3.  Dans le **propriétés du Gestionnaire d’adaptateur** boîte de dialogue le **général** sous l’onglet du **nom d’hôte** , sélectionnez l’hôte auquel associer le Gestionnaire d’envoi.  
  
4.  Sur le **propriétés** onglet, procédez comme suit.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Délai de demande (s)**|Indiquez le délai (exprimé en secondes) pendant lequel une réponse est attendue du serveur.<br /><br /> Si la valeur définie est zéro (0), l'adaptateur HTTP calcule le délai en fonction de la taille du message de requête.<br /><br /> Si vous n'indiquez pas de valeur, le système utilise celle du gestionnaire.<br /><br /> **Valeur par défaut :** 0<br /><br /> **Type :** Long<br /><br /> **Valeur minimale :** 0<br /><br /> **Valeur maximale :** MAX_LONG|  
    |**Nombre maximal de redirections**|Indiquez le nombre maximal de redirections autorisé pour le message envoyé.<br /><br /> **Valeur par défaut :** 5<br /><br /> **Type :** Int<br /><br /> **Valeur minimale :** 0<br /><br /> **Valeur maximale :** 10|  
    |**Type de contenu**|Indiquez le type de contenu des messages de requête.<br /><br /> Si vous n'indiquez pas de valeur, le système utilise celle du gestionnaire.<br /><br /> **Valeur par défaut :** Text/XML<br /><br /> **Type :** chaîne<br /><br /> **Longueur minimale :** 0<br /><br /> **Longueur maximale :** 256|  
  
5.  Sur le **Proxy** onglet, procédez comme suit.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Utiliser le proxy**|Indiquez si le gestionnaire d'envoi HTTP fait appel ou non au serveur proxy.<br /><br /> **Valeur par défaut :** False<br /><br /> **Type :** booléenne|  
    |**Server**|Indiquer l'adresse du serveur proxy pour ce port d'envoi.<br /><br /> Cette propriété exige une valeur si **utiliser le proxy** est **True**.<br /><br /> **Type :** chaîne<br /><br /> **Longueur minimale :** 0<br /><br /> **Longueur maximale :** 256|  
    |**Port**|Indiquer le port du serveur proxy pour ce port d'envoi.<br /><br /> Cette propriété exige une valeur si **utiliser le proxy** est **True**.<br /><br /> **Valeur par défaut :** 80<br /><br /> **Type :** Long<br /><br /> **Valeur minimale :** 0<br /><br /> **Valeur maximale :** 65535|  
    |**Nom d'utilisateur**|Spécifiez le nom d’utilisateur à utiliser pour l’authentification auprès du serveur proxy.<br /><br /> Cette propriété exige une valeur si **utiliser le proxy** est **True**.<br /><br /> **Type :** chaîne<br /><br /> **Longueur minimale :** 0<br /><br /> **Longueur maximale :** 256|  
    |**Mot de passe**|Indiquer le mot de passe utilisé pour l'authentification sur le serveur proxy.<br /><br /> Cette propriété exige une valeur si **utiliser le proxy** est **True**.<br /><br /> **Type :** chaîne<br /><br /> **Longueur minimale :** 0<br /><br /> **Longueur maximale :** 256|  
  
6.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de l’adaptateur HTTP](../core/configuring-the-http-adapter.md)