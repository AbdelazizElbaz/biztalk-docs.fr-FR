---
title: "Problèmes connus avec le traitement AS2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 941111d8-b394-4648-a675-e4a8f118a84b
caps.latest.revision: "40"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64899c184f8cbe405684387b8f1c2a6230204624
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-as2-processing"></a>Problèmes connus avec le traitement AS2
Cette section contient des rubriques qui décrivent les problèmes connus avec les solutions AS2 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].  
  
## <a name="as2-processing-not-supported-on-64-bit-computers"></a>Le traitement AS2 n'est pas pris en charge sur les ordinateurs 64 bits  
 La solution AS2 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] n'est pas prise en charge sur les ordinateurs 64 bits. Le traitement AS2 ne fonctionne que sur les ordinateurs 32 bits ou lorsqu'il est exécuté sous l'émulateur WOW64 sur des ordinateurs 64 bits.  
  
## <a name="the-as2-receive-pipelines-require-the-account-that-the-biztalk-isolated-host-instance-process-is-running-under-to-be-part-of-the-biztalk-application-users-group"></a>Les pipelines de réception AS2 requièrent que le compte sous lequel le processus d'instance de l'hôte BizTalk isolé est exécuté fasse partie du groupe Utilisateurs d'applications BizTalk  
 Si vous utilisez le pipeline AS2EdiReceive ou AS2Receive, vous devez ajouter le compte d'utilisateur que le processus d'instance de l'hôte BizTalk isolé exécute sous le groupe Utilisateurs d'applications BizTalk. Les pipelines AS2EdiReceive et AS2Receive sont exécutés dans le processus d'instance de l'hôte BizTalk isolé.  
  
## <a name="an-empty-receipt-delivery-option-header-will-cause-an-mdn-to-be-sent-synchronously"></a>Un en-tête Receipt-Delivery-Option vide provoque l'envoi d'un MDN de façon synchrone  
 Si le pipeline AS2Receive reçoit un message avec un en-tête Receipt-Delivery-Option vide et qu'un MDN asynchrone est demandé, le pipeline ignore la demande de MDN asynchrone. Il renvoie un MDN synchrone et consigne une erreur dans le journal des événements et le rapport d'état AS2 (le cas échéant). Ce problème survient si la propriété « Remplacer les propriétés du message entrant » n'est pas activée. Si cette propriété est activée, elle remplace l'en-tête Receipt-Delivery-Option dans le message avec la valeur de la propriété Receipt-Delivery-Option dans la page Tiers considéré comme expéditeur des messages AS2 de la boîte de dialogue Propriétés AS2.  
  
 Dans ce cas, comme l'en-tête Receipt-Delivery-Option est vide, le pipeline AS2Receive n'a pas d'adresse vers laquelle envoyer la réponse MDN via une connexion asynchrone. Toutefois, le pipeline dispose toujours d'une connexion synchrone ouverte, de sorte qu'il renvoie le MDN via cette connexion. S'il s'agit d'un port de réception unidirectionnel, BizTalk Server ferme la connexion après avoir envoyé le message HTTP 200OK.  
  
## <a name="use-of-unfolded-and-folded-http-line-headers"></a>Utilisation des en-têtes de ligne HTTP déroulés et non déroulés  
 Pour garantir une interopérabilité maximale, vous devez utiliser des en-têtes de ligne HTTP déroulés pour les messages AS2. Information Services (IIS) 7.0 ne prend en charge que les en-têtes HTTP déroulés. IIS 6.0 prend en charge les en-têtes déroulés et non déroulés. En revanche, certains systèmes ne prennent pas en charge les en-têtes incluant plus de 80 caractères par ligne, de sorte que des lignes non déroulées doivent être utilisées.  
  
 Par défaut, AS2 dans [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] utilise des en-têtes de ligne HTTP déroulés.  
  
## <a name="party-resolution-can-be-affected-by-a-localized-name"></a>La résolution du tiers peut être affectée par un nom localisé  
 Lorsque BizTalk Server effectue une résolution de tiers sur un message AS2 sortant, cette opération peut être affectée par une valeur localisée dans les en-têtes de message. Si la propriété de tiers AS2-To dans la page Tiers considéré comme récepteur des messages AS2 de la boîte de dialogue Propriétés est définie par défaut sur un nom de tiers anglais et que la valeur dans l'en-tête AS2-To du message AS2 est définie sur un nom non anglais, la correspondance n'est pas trouvée.  
  
## <a name="as2-message-size-limitation"></a>Limitation de la taille des messages AS2  
 La taille des messages AS2 chiffrés doit être inférieure à 96 mégaoctets pour que ceux-ci soient traités. Cette limitation est imposée par le Décodeur AS2, qui fait partie des pipelines AS2Receive et AS2EdiReceive.  
  
 Pour contourner cette limitation, vous pouvez utiliser la compression car un message AS2 est compressé avant d'être chiffré.  
  
## <a name="biztalk-edi-application-must-not-be-modified"></a>L'application EDI BizTalk ne doit pas être modifiée  
 Les artefacts de l'application EDI BizTalk ne doivent pas être modifiés ou supprimés. Si cette application est modifiée, vous ne pouvez pas revenir à l'application d'origine en annulant la configuration et en reconfigurant les fonctionnalités EDI et AS2.  
  
## <a name="partner-may-reject-multipart-messages"></a>Le partenaire peut rejeter les messages à parties multiples  
 **Symptôme**  
  
 Lors de l'envoi de messages à parties multiples à l'aide du pipeline d'envoi AS2, votre partenaire peut rejeter le message en raison de l'absence d'un en-tête MIME de type de contenu.  
  
 **Cause possible**  
  
 Cet en-tête facultatif peut être présent pour chaque partie du corps dans un message à parties multiples. Certains partenaires requièrent que cet en-tête soit présent pour chaque partie du corps et défini sur un en-tête de type de contenu spécifique.  
  
> [!NOTE]
>  La propriété de type de contenu du corps du message est définie par le pipeline d'envoi AS2, contrairement à celle des pièces jointes.  
  
 **Résolution**  
  
 Si votre partenaire requiert la valeur de l'en-tête de type de contenu pour chaque corps, vous devez créer un composant de pipeline personnalisé qui définit cette propriété et utiliser le composant dans le pipeline d'envoi.  
  
## <a name="when-receiving-multipart-messages-the-first-part-is-considered-the-body"></a>Dans le cadre de la réception de messages à parties multiples, la première partie est considérée comme étant le corps  
 **Symptôme**  
  
 Lors de la réception d'un message AS2 à parties multiples, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] peut identifier de manière incorrecte l'une des pièces jointes comme étant le corps du message.  
  
 **Cause possible**  
  
 L'en-tête MIME d'un message à parties multiples/associé peut contenir un paramètre facultatif de début indiquant les parties devant être traitées comme corps du message en spécifiant l'ID de contenu de la partie. Si le paramètre de début n’est pas présent, la première partie doit être considéré comme le corps du message. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]ne respecte pas le paramètre de début s’il est présent et traite toujours la première partie comme corps du message.  
  
 **Résolution**  
  
 Si votre partenaire ne peut pas envoyer le corps comme étant la première partie du message à parties multiples/associé, vous devez créer un composant de pipeline qui identifie correctement le corps du message.  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage des Solutions EDI et AS2](../core/troubleshooting-edi-and-as2-solutions.md)   
 [AS2 Architecture de la Solution](../core/as2-solution-architecture.md)   
 [Développement et la configuration des Solutions AS2 BizTalk Server](../core/developing-and-configuring-biztalk-server-as2-solutions.md)