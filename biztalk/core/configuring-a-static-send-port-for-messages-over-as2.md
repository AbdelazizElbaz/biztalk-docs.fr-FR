---
title: "Configuration d’un Port d’envoi statique pour les Messages via AS2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2708d6a9-b105-42d3-abe3-7085b39da55a
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 068b7d8295710157af7a8a7358768e85e006beb8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="configuring-a-static-send-port-for-messages-over-as2"></a>Configuration d'un port d'envoi statique pour les messages via AS2
Cette rubrique décrit la configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de manière à envoyer des messages AS2 via un port d'envoi statique. Cette configuration inclut la création du port d'envoi statique ainsi que la configuration de l'accord. Le cas échéant, vous configurerez un certificat de chiffrement utilisé par le port d'envoi.  
  
> [!NOTE]
>  À la place d'un port d'envoi statique, il est également possible de paramétrer un port d'envoi dynamique pour envoyer des messages AS2. Pour plus d’informations, consultez [configuration d’un Port d’envoi dynamique pour les Messages via AS2](../core/configuring-a-dynamic-send-port-for-messages-over-as2.md).  
  
 Pour envoyer un message AS2 avec un message EDI ou non-EDI ou avec un accusé de réception EDI, créez un port d'envoi HTTP avec sollicitation-réponse possédant la configuration suivante :  
  
|Emplacement|Propriété|Paramètre|  
|--------------|--------------|-------------|  
|**Propriétés du Port d’envoi : général**|Type de port|-Réponse de sollicitation statique (si exiger le MDN **accusés de réception (MDN)** est activée sous l’onglet d’accord unidirectionnel page)<br /><br /> -Port d’envoi unidirectionnel statiques (si exiger le MDN **accusés de réception (MDN)** page sous l’onglet d’accord unidirectionnel est désactivée)|  
|**Propriétés du Port d’envoi : général**|Type de transport|HTTP<br /><br /> Remarque :<br /><br /> Seul l'adaptateur HTTP peut être utilisé pour le transport des messages EDIINT/AS2. Ce transport ne fonctionne pas avec les autres types d'adaptateurs.|  
|**Propriétés du Port d’envoi : général**|Gestionnaire d'envoi|BizTalkServerApplication|  
|**Propriétés du Port d’envoi : général**|Pipeline d’envoi|-AS2EdiSend (pour les messages codée au format EDI)<br /><br /> -AS2Send (pour les messages non-EDI)|  
|**Propriétés du Port d’envoi : général**|Gestionnaire de réception<br /><br /> (si exiger le MDN **accusés de réception (MDN)** est activée sous l’onglet d’accord unidirectionnel page)|BizTalkServerApplication|  
|**Propriétés du Port d’envoi : général**|Pipeline de réception<br /><br /> (si exiger le MDN **accusés de réception (MDN)** est activée sous l’onglet d’accord unidirectionnel page)|AS2Receive|  
|**Propriétés du Transport HTTP**|URL de destination|\<Chaîne d’URL de destination\>|  
|**Propriétés du Transport HTTP**|Activer le codage mémorisé en bloc|Désactivé|  
|**Propriétés du Port d’envoi : filtres**|Propriété|BTS.MessageType<br /><br /> Remarque :<br /><br /> Vous pouvez faire appel à plusieurs expressions de filtre, y compris BTS.ReceivePortName.<br /><br /> Remarque :<br /><br /> Pour les messages non-EDI, vous devrez effectuer le filtrage sur une autre propriété.|  
|**Propriétés du Port d’envoi : filtres**|Opérateur|==|  
|**Propriétés du Port d’envoi : filtres**|Valeur|- `http://schemas.microsoft.com/BizTalk/EDI/X12/2006#<schema name>`(pour un message EDI)<br /><br /> -                   `http://schemas.microsoft.com/Edi/X12#X12_<997 or TA1>_Root`(pour un X12 accusé de réception)<br /><br /> -                   `http://schemas.microsoft.com/Edi/Efact#Efact_Contrl_Root`(pour un accusé de réception EDIFACT)|  
|**Propriétés du Port d’envoi : les certificats**|Nom commun et empreinte|Entrez le nom du certificat et son empreinte si vous utilisez un certificat de chiffrement pour un message AS2 sortant.|  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-biztalk-server-to-send-as2-messages-over-a-static-send-port"></a>Pour configurer BizTalk Server de manière à envoyer des messages AS2 via un port d'envoi statique  
  
1.  Dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], créez un port d'envoi unidirectionnel statique ou un port d'envoi avec sollicitation-réponse disposant de la configuration décrite précédemment.  
  
2.  Dans la liste de ports d’envoi sur le **Ports d’envoi** page de l’onglet d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue, entrez le nom du port d’envoi statique.  
  
    > [!NOTE]
    >  La configuration du port d'envoi permet à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] d'effectuer la résolution de l'accord pour un message AS2 sortant.  
  
3.  Dans le **identificateurs** page de l’onglet d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue, définissez AS2-pour la propriété à la destination puis définissez les autres propriétés de l’accord selon les besoins de la des pages différentes de la **propriétés de l’accord** boîte de dialogue.  
  
## <a name="functionality"></a>Fonctionnalité  
 Le port et le pipeline d'envoi effectuent les opérations suivantes pour envoyer un message EDI ou non-EDI synchrone ou un accusé de réception via AS2 et traiter le MDN renvoyé :  
  
-   Lors de l'envoi d'un message EDI, ils récupèrent le message en filtrant sur la propriété `BTS.MessageType` définie sur le schéma du message dans l'espace de noms `http://schemas.microsoft.com/BizTalk/EDI/X12/2006` (par exemple, X12_00401_864 pour un message 864).  
  
-   Lors de l'envoi d'un accusé de réception EDI, ils récupèrent l'accusé de réception en filtrant sur la propriété `BTS.MessageType` définie sur l'un des schémas de contrôle suivants :  
  
    -   `http://schemas.microsoft.com/BizTalk/EDI/X12#X12_997_Root` pour un accusé de réception 997 ;  
  
    -   `http://schemas.microsoft.com/BizTalk/EDI/X12#X12_TA1_Root` pour un accusé de réception TA1 ;  
  
    -   `http://schemas.microsoft.com/BizTalk/EDI/Efact#Efact_Contrl_Root` pour un accusé de réception CONTRL.  
  
-   Lors de l'envoi d'un message non-EDI, ils récupèrent le message à l'aide d'un autre filtre.  
  
-   Ils déploient un message AS2. Pour plus d’informations sur ce processus, consultez [génération d’un Message AS2 sortant](../core/generating-an-outgoing-as2-message.md).  
  
-   Ils envoient le message ou l'accusé de réception à l'URL de destination du port d'envoi.  
  
-   Ils reçoivent la réponse MDN au message ou à l'accusé de réception, si cette fonctionnalité est activée. Pour plus d’informations sur ce processus, consultez [du traitement d’un MDN entrant](../core/processing-an-incoming-mdn.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des Ports pour une Solution AS2](../core/configuring-ports-for-an-as2-solution.md)   
 [Génération d’un Message AS2 sortant](../core/generating-an-outgoing-as2-message.md)   
 [Traitement d’une notification de réception du message entrante](../core/processing-an-incoming-mdn.md)