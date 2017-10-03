---
title: "Le rôle des accords dans le traitement EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d81b0449-6656-49f7-a781-5fd60031b3d5
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9986f22108382f1b1128079b8ff8c31902ca2979
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-role-of-agreements-in-edi-processing"></a>Rôle des accords dans le traitement EDI
Une organisation utilise [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour le transfert (réception et envoi) des messages EDI vers un ou plusieurs partenaires commerciaux. Ceux-ci définissent ensuite des entités de profils d'entreprise au sein d'une organisation. La méthode d'échange des messages utilisée par les profils d'entreprise est définie dans le cadre des accords de partenariat commercial entre deux profils d'entreprise. Pour plus d’informations, consultez [blocs de construction d’une Solution de gestion des partenaires commerciaux](../core/building-blocks-of-a-trading-partner-management-solution.md).  
  
 Créez un accord de partenariat commercial dans l'interface utilisateur de gestion des partenaires commerciaux (GPC). Les écrans du module de plateforme sécurisée se trouvent dans le **Parties** nœud de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration.  
  
## <a name="configuring-an-agreement-for-edi-processing"></a>Configuration d'un accord pour le traitement EDI  
 Tous les partenaires commerciaux qui échangent des messages EDI à l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] doivent s'accorder sur les paramètres de communication. Une fois l'accord effectif, l'organisation hébergeant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] doit créer les partenaires commerciaux dans l'interface utilisateur GPC (en se comptant parmi ces partenaires commerciaux), créer les profils d'entreprise et l'accord de partenariat commercial entre ceux-ci. Dans le cadre de l'accord de partenariat commercial, définissez les propriétés indiquant la fréquence de réception et d'envoi de messages EDI entre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et le profil d'entreprise du partenaire commercial. De leur côté, les autres partenaires commerciaux doivent faire de même et les configurations de l'échange des messages doivent être compatibles.  
  
 Vous devez définir les jeux de propriétés suivants pour les communications EDI.  
  
-   Les propriétés des partenaires commerciaux qui définissent les aspects généraux du partenaire commercial (nom, ports d'envoi, certificat de signature).  
  
-   Les propriétés des profils d'entreprise qui définissent les identités de l'entreprise.  
  
-   Les propriétés EDI de l'accord de partenariat commercial, qui définissent la manière dont [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] va traiter un message provenant d'un partenaire commercial et dont il va générer un message sortant lié à un partenaire commercial.  
  
-   Les propriétés AS2 de l'accord de partenariat commercial, qui définissent la manière dont [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] va traiter les communications AS2 entrantes et sortantes. Ces propriétés affectent les communications EDI uniquement lorsqu'un message EDI est envoyé via AS2.  
  
    > [!NOTE]
    >  L'accord AS2 et l'accord de messagerie EDI entre les mêmes profils d'entreprise sont spécifiés séparément. Ensemble, les deux accords forment un partenariat.  
  
 Les propriétés de l'accord de partenariat commercial déterminent les traitements spécifiques suivants :  
  
-   génération et traitement de l'enveloppe EDI ;  
  
-   génération et traitement des accusés de réception (ACK) ;  
  
-   validation des messages EDI entrants et sortants ;  
  
-   création de lot ;  
  
-   rapport d'état.  
  
 Pour les identités d’entreprise, il peut y avoir des valeurs spécifiques, telles que **D-U-N-S (DUN and Bradstreet)**. Les noms spécifiques ont des qualificateurs spécifiques, comme « 01 » pour Duns. Lorsqu'un nom d'identité d'entreprise n'est pas spécifique, « ZZ » est utilisé pour les messages X12 et « ZZZ » est utilisé pour les messages EDIFACT, ce qui indique un nom mutuellement défini par des entités distinctes. La valeur et le qualificateur identifient ensuite le profil d'entreprise. Le nom de l'identité d'entreprise existe uniquement à titre indicatif ; il n'est pas utilisé par le composant d'exécution BizTalk pour le traitement.  
  
## <a name="determining-an-agreement-for-edi-processing"></a>Détermination d'un accord pour le traitement EDI  
 À chaque fois que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] reçoit un message EDI, il tente de déterminer l'accord de partenariat commercial correspondant au message. Il recherche l'accord de partenariat commercial associé en faisant correspondre le message, ainsi que les qualificateurs et identificateurs du récepteur et de l'expéditeur définis dans le cadre de l'accord. Pour plus d’informations sur ce processus, consultez [résolution de l’accord, détection de schéma et l’autorisation pour les Messages EDI reçus](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md).  
  
 À chaque fois que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] génère un message EDI à envoyer, il recherche l'accord associé avec le profil d'entreprise destinataire du message. Il recherche l'accord en faisant correspondre le message et l'accord à l'aide des éléments suivants :  
  
-   la propriété de contexte AgreementPartIdForSend ;  
  
-   les propriétés de contexte AgreementNameForSend, SenderPartyNameForSend et ReceiverPartyNameForSend ;  
  
-   les qualificateurs et identificateurs de l'expéditeur et du récepteur ;  
  
-   le nom du port d'envoi.  
  
 Pour plus d’informations sur ce processus, consultez [résolution de l’accord et détermination du schéma pour les Messages EDI sortants](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md).  
  
## <a name="using-edi-global-properties"></a>Utilisation des propriétés globales EDI  
 Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne peut pas déterminer l'accord pour un message entrant ou sortant, il utilise l'accord de secours pour traiter l'échange entrant ou générer l'échange sortant. Les accords de secours sont définies en cliquant sur le **Parties** nœud dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration et en cliquant sur **X12 paramètres de secours** (pour les messages encodés en X12) ou **Paramètres de secours EDIFACT** (messages encodé en EDIFACT). Pour plus d’informations sur les propriétés globales, consultez [configuration globale ou propriétés de l’accord de secours](../core/configuring-global-or-fallback-agreement-properties.md).  
  
> [!NOTE]
>  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise l'accord de secours uniquement s'il ne peut pas déterminer l'accord d'un échange. Si un accord a été déterminé, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'utilise pas de valeur de propriété issue de l'accord de secours pour une propriété qui n'a pas été définie pour l'accord entre les deux partenaires commerciaux.  
  
 Les accords de secours ne sont pas utilisés si les paramètres du port requièrent une authentification. Si les paramètres de port pour un port de réception requièrent l’authentification (si le paramètre **supprimer les messages si l’authentification échoue** ou **conserver les messages si l’authentification échoue** est sélectionné dans le **général**  page de la **propriétés du Port de réception** boîte de dialogue), un accord est obligatoire pour chaque échange reçu par le port de réception. Dans ce cas, les accords de secours ne sont pas utilisés. Si aucun accord n'a été déterminé pour un échange, celui-ci est traité comme si l'authentification avait échoué : il est donc interrompu.  
  
## <a name="see-also"></a>Voir aussi  
 [Résolution de l’accord, détection de schéma et l’autorisation des Messages EDI reçus](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md)   
 [Résolution de l’accord et détermination du schéma pour les Messages EDI sortants](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md)   
 [Configuration des propriétés EDI](../core/configuring-edi-properties.md)   
 [Configuration des propriétés de l’accord Global ou de secours](../core/configuring-global-or-fallback-agreement-properties.md)   
 [Problèmes connus avec les tiers EDI](../core/known-issues-with-edi-parties.md)