---
title: "Configuration d’un Port d’envoi dynamique pour les Messages via AS2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 246d64e8-70ca-48f4-8b72-d43b0964dbb4
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de6df553a3f03e9d2e60b78de9877ad6113b04e3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-a-dynamic-send-port-for-messages-over-as2"></a>Configuration d'un port d'envoi dynamique pour les messages via AS2
Cette rubrique décrit la configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour l'envoi de messages AS2 via un port d'envoi dynamique. Cette configuration inclut la création d'un port d'envoi dynamique et d'une application principale pour définir les propriétés de contexte appropriées. Lors de la création d'un port d'envoi dynamique pour l'envoi d'un message AS2, vous devez promouvoir certaines propriétés pour que le port d'envoi fonctionne. Pour plus d’informations, consultez [pour configurer BizTalk Server pour envoyer AS2 messages via un dynamique port d’envoi](../core/configuring-a-dynamic-send-port-for-messages-over-as2.md#BKMK_Proc) ci-dessous.  
  
 Un port d'envoi dynamique permet d'envoyer des messages à plusieurs tiers sans coder en dur la configuration du tiers. L'accord et la destination à utiliser lors de l'envoi du message sont déterminés dynamiquement via les propriétés de contexte. Il n'est pas nécessaire de créer un port d'envoi statique pour chaque client.  
  
 Pour envoyer un message AS2 accompagné d'un message EDI ou non-EDI, ou d'un accusé de réception EDI, créez un port d'envoi HTTP de réponse dynamique avec la configuration suivante :  
  
|Emplacement|Propriété|Paramètre|  
|--------------|--------------|-------------|  
|**Propriétés du Port d’envoi : général**|Type de port|-Réponse de sollicitation dynamique (si exiger le MDN **accusés de réception (MDN)** est activée sous l’onglet d’accord unidirectionnel page)<br /><br /> -Port d’envoi unidirectionnel dynamique (si exiger le MDN **accusés de réception (MDN)** page sous l’onglet d’accord unidirectionnel est désactivée)|  
|**Propriétés du Port d’envoi : général**|Pipeline d’envoi|-AS2EdiSend (pour les messages codée au format EDI)<br /><br /> -AS2Send (pour les messages non-EDI)|  
|**Propriétés du Port d’envoi : général**|Pipeline de réception<br /><br /> (si exiger le MDN **accusés de réception (MDN)** est activée sous l’onglet d’accord unidirectionnel page)|AS2Receive (pour un port d'envoi dynamique avec sollicitation-réponse)|  
|**Propriétés du Port d’envoi : filtres**|Propriété|BTS.MessageType|  
|**Propriétés du Port d’envoi : filtres**|Opérateur|==|  
|**Propriétés du Port d’envoi : filtres**|Valeur|- `http://schemas.microsoft.com/BizTalk/EDI/X12/2006#<schema name>`(pour un message EDI)<br /><br /> - `http://schemas.microsoft.com/Edi/X12#X12_<997 or TA1>_Root`(pour un X12 accusé de réception)<br /><br /> - `http://schemas.microsoft.com/Edi/Efact#Efact_Contrl_Root`(pour un accusé de réception EDIFACT)|  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
##  <a name="BKMK_Proc"></a>Pour configurer BizTalk Server pour envoyer AS2 port d’envoi de messages via un dynamique  
  
1.  Dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], créez un port d'envoi unidirectionnel dynamique (si aucun MDN n'est demandé) ou un port d'envoi dynamique avec sollicitation-réponse (si un MDN est demandé) avec la configuration précédente.  
  
2.  Pour l'accord qui s'applique à ce message, définissez les propriétés AS2 et EDI requises.  
  
3.  Faites la promotion des propriétés suivantes vers le contexte de message :  
  
    -   `BTS.MessageType`  
  
    -   `EdiIntAS.MessageID`  
  
4.  Ajoutez des fonctionnalités à une application principale pour écrire les propriétés suivantes pour le contexte de message, en les définissant sur les valeurs appropriées :  
  
    -   `EdiIntAS.AS2To`  
  
    -   `BTS.OutboundTransportLocation`  
  
    -   `HTTP.EnableChunkedEncoding`  
  
    -   `BTS.EncryptionCert`  
  
    > [!NOTE]
    >  Les propriétés de contexte `AS2To` et `OutboundTransportLocation` doivent être écrites vers le contexte de message afin que le port d'envoi dynamique fonctionne correctement. La propriété `AS2To` est requise par le port pour déterminer l'accord à utiliser dans le traitement du message sortant et la propriété `OutboundTransportLocation` est requise par le port d'envoi pour déterminer la destination du message. Pour plus d’informations, consultez [génération d’un Message AS2 sortant](../core/generating-an-outgoing-as2-message.md).  
  
## <a name="functionality"></a>Fonctionnalité  
 Le port d'envoi dynamique et le pipeline effectuent les tâches suivantes pour envoyer un message EDI ou non-EDI synchrone ou un accusé de réception via AS2 et traiter le MDN renvoyé :  
  
-   Lors de l'envoi d'un message EDI, ils récupèrent celui-ci en filtrant sur la propriété `BTS.MessageType` définie sur le schéma de message dans `http://schemas.microsoft.com/BizTalk/EDI/X12/2006 namespace` (par exemple, X12_00401_864 pour un message 864).  
  
-   Lors de l'envoi d'un accusé de réception EDI, ils récupèrent l'accusé de réception en filtrant sur la propriété `BTS.MessageType` définie sur l'un des schémas de contrôle suivants :  
  
    -   `http://schemas.microsoft.com/BizTalk/EDI/X12#X12_997_Root` pour un accusé de réception 997 ;  
  
    -   `http://schemas.microsoft.com/BizTalk/EDI/X12#X12_TA1_Root` pour un accusé de réception TA1 ;  
  
    -   `http://schemas.microsoft.com/BizTalk/EDI/Efact#Efact_Contrl_Root` pour un accusé de réception CONTRL.  
  
-   Lors de l'envoi d'un message non-EDI, ils récupèrent le message à l'aide d'un filtre approprié.  
  
-   Ils déploient un message AS2. Pour plus d’informations sur ce processus, consultez [génération d’un Message AS2 sortant](../core/generating-an-outgoing-as2-message.md).  
  
    > [!NOTE]
    >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] détermine le type de transport utilisé par le port d'envoi dynamique selon le format de l'URL (http, smtp, ftp, etc.).  
  
-   Ils acheminent le message ou l'accusé de réception jusqu'à son URL de destination pour le port d'envoi.  
  
-   Si l'option a été activée et si le port est un port d'envoi avec sollicitation-réponse, ils réceptionnent la réponse MDN au message ou à l'accusé de réception. Pour plus d’informations sur ce processus, consultez [du traitement d’un MDN entrant](../core/processing-an-incoming-mdn.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des Ports pour une Solution AS2](../core/configuring-ports-for-an-as2-solution.md)