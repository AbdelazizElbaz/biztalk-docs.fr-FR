---
title: "Le rôle des accords dans AS2 traitement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb6a6fe1-8fb4-4998-a1b4-aadad7e672c4
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 712c086cd02eedfd1995e5f378a05d2edd34bb6e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-role-of-agreements-in-as2-processing"></a>Rôle des accords dans le traitement AS2
Une organisation utilise [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour le transfert (réception et envoi) des messages AS2 vers un ou plusieurs partenaires commerciaux. Ceux-ci définissent ensuite des entités de profils d'entreprise au sein d'une organisation. Vous définissez des propriétés AS2 dans des accords de partenariat commercial bidirectionnels entre des profils d'entreprise spécifiques des différents partenaires commerciaux.  
  
 Vous pouvez créer des accords de partenariat commercial dans l'interface utilisateur de gestion des partenaires commerciaux (GPC). Les écrans du module de plateforme sécurisée se trouvent dans le **Parties** nœud de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration.  
  
 Pour plus d’informations sur comment des partenaires commerciaux, les profils d’entreprise et des accords le cadre du traitement dans une solution GPC, consultez [blocs de construction d’une Solution de gestion des partenaires commerciaux](../core/building-blocks-of-a-trading-partner-management-solution.md).  
  
## <a name="configuring-an-agreement-for-as2-processing"></a>Configuration d'un accord pour le traitement AS2  
 Chaque fois qu'un partenaire commercial reçoit un message AS2 d'un autre partenaire commercial ou lui en envoie un, le pipeline de réception AS2 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou le pipeline d'envoi AS2 du serveur BizTalk Server traite le message d'après les propriétés des accords AS2 entre les deux partenaires commerciaux. Vous pouvez configurer les propriétés AS2 qui définissent la façon dont [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] effectuera les communications AS2, aussi bien entrantes que sortantes.  
  
> [!NOTE]
>  Contrairement au traitement EDI, il n'existe pas d'accords AS2 de secours que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] peut utiliser s'il n'arrive pas à déterminer l'accord. Le pipeline de réception ou d'envoi AS2 ne traitera le message que si un accord est déterminé.  
  
> [!NOTE]
>  L'accord AS2 est configuré séparément de l'accord EDI. A la réception des documents, l'accord AS2 est résolu lors du traitement AS2, puis l'accord  EDI est résolu séparément lors du traitement EDI. Les deux accords conjoints forment un partenariat. Pour plus d’informations, consultez [accord de partenariat commercial](../core/trading-partner-agreement.md).  
  
> [!NOTE]
>  Les propriétés de tiers qui définissent les aspects généraux du tiers tels que le nom et les alias, les ports d'envoi et le certificat de signature font partie intégrante des propriétés du partenaire commercial.  
  
 Vous pouvez utiliser le transport HTTP/HTTPS pour les messages codés EDIINT/AS2 ou les messages codés non-EDI sur AS2. Si vous transmettez des messages codés EDIINT/AS2 sur le transport HTTP/HTTPS, les propriétés EDI de l'accord s'appliqueront.  
  
 Le certificat de signature pour l’organisation d’origine est défini dans le **certificat** page de la **groupe BizTalk - propriétés du groupe** boîte de dialogue. De plus, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet de remplacer le certificat de signature par défaut pour les messages AS2 en définissant un certificat intégré aux propriétés de l'accord.  Pour définir un certificat différent pour un contrat spécifique, utilisez la **le certificat de Signature** page de l’accord AS2 unidirectionnel dans la **propriétés de l’accord** boîte de dialogue. Pour obtenir des instructions sur la façon de spécifier un autre certificat, consultez [configuration des certificats de Signature (AS2)](../core/configuring-signature-certificates-as2.md).  
  
## <a name="determining-an-agreement-for-as2-processing"></a>Détermination d'un accord pour le traitement AS2  
 Lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] reçoit un message codé AS2, il tente de déterminer le tiers qui l'a expédié en faisant correspondre l'en-tête AS2-From avec les propriétés de l'accord AS2-From dans l'accord unidirectionnel du tiers. Lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] reçoit un message codé AS2, il tente de déterminer le tiers qui le recevra en faisant correspondre l'en-tête AS2-To avec les propriétés de l'accord AS2-To dans l'accord unidirectionnel du tiers. Pour plus d’informations, consultez [résolution d’accord pour les Messages AS2 entrants](../core/agreement-resolution-for-incoming-as2-messages.md) ou [résolution de l’accord pour les Messages AS2 sortants](../core/agreement-resolution-for-outgoing-as2-messages.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Résolution de l’accord pour les Messages AS2 entrants](../core/agreement-resolution-for-incoming-as2-messages.md)   
 [Résolution de l’accord pour les Messages AS2 sortants](../core/agreement-resolution-for-outgoing-as2-messages.md)   
 [Configuration des propriétés AS2](../core/configuring-as2-properties.md)