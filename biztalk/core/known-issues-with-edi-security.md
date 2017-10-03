---
title: "Problèmes connus avec la sécurité EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d7f68bc-8460-4656-b9f2-955337458d78
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9517f6c5b1aeae06b5989eef12fe269f81a27c74
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-edi-security"></a>Problèmes connus avec la sécurité EDI
Cette rubrique décrit les problèmes connus liés à la sécurité des solutions EDI et AS2 de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="biztalk-will-not-suspend-a-signed-message-from-a-party-for-which-no-certificate-is-set"></a>BizTalk ne suspend pas un message signé d'un tiers pour lequel aucun certificat n'est défini  
 Si vous ne définissez pas de certificat de signature sur un tiers (dans le nœud Certificat de la page Propriétés du tiers), mais qu'un message entrant de ce tiers est signé, BizTalk Server ne suspend pas le message ni ne génère d'exception en raison de l'absence du certificat.  
  
 Si vous remplacez les propriétés du message entrant (dans la page Tiers considéré comme expéditeur des messages AS2) et désactivez la propriété « Le message doit être signé », BizTalk Server suspend un message entrant signé.  
  
## <a name="access-to-program-files-folder-can-be-limited-to-prevent-file-tampering"></a>L'accès au dossier Program Files peut être limité pour empêcher la falsification de fichiers  
 Si le dossier Program Files qui contient les exécutables de BizTalk Server et les schémas EDI est accessible aux utilisateurs non authentifiés, ceux-ci peuvent modifier ces fichiers. Pour vous prémunir contre cette menace, vous pouvez utiliser les listes de contrôle d'accès dans le dossier Program Files afin de limiter l'accès aux seuls utilisateurs approuvés.  
  
## <a name="a-schema-with-a-long-field-can-be-susceptible-to-a-denial-of-service-attack"></a>Un schéma avec un champ long peut faire l'objet d'une attaque par déni de service  
 Un schéma personnalisé doté d'un champ très long peut faire l'objet d'une attaque par déni de service. Les schémas inclus dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'ont pas de champs longs, aussi ne font-ils généralement pas l'objet d'une telle attaque.  
  
## <a name="message-processing-will-be-aborted-if-a-control-number-exceeds-its-maximum-length"></a>Le traitement des messages est abandonné si un numéro de contrôle dépasse sa longueur maximale  
 Un numéro de contrôle d'échange, de groupe ou de document informatisé a une longueur maximale limitée. Si la longueur de l'un de ces numéros de contrôle dépasse la longueur maximale, le traitement des messages associés à ce type de codage pour un seul tiers est abandonné. Un message d'un autre type de codage (EDIFACT au lieu de X12, par exemple) n'est pas affecté. Ceci peut représenter une faille de sécurité.  
  
 Si la longueur d'un numéro de séquence dépasse la longueur maximale, l'utilisateur doit réinitialiser le numéro de séquence dans la propriété EDI du tiers affecté. Une fois le numéro réinitialisé, tous les messages de ce type de codage peuvent à nouveau être traités.  
  
 Pour les messages X12, la longueur maximale d'un numéro de contrôle est de neuf chiffres. Pour les messages EDIFACT, la longueur maximale d'un numéro de contrôle est de 14 chiffres répartis dans trois champs.  
  
## <a name="using-the-edi-receive-pipeline-with-an-http-adapter-will-leave-the-connection-open-if-no-ack-is-sent"></a>L'utilisation du pipeline de réception EDI avec un adaptateur HTTP laisse la connexion ouverte si aucun accusé de réception n'est envoyé  
 Un problème de sécurité peut survenir si vous créez un emplacement de réception utilisant le pipeline EDIReceive et le type de transport HTTP. Le pipeline EdiReceive ne génèrera aucun accusé de réception HTTP "200 OK". Si aucun accusé de réception EDI n'est renvoyé, la connexion n'est pas interrompue correctement et reste ouverte. La connexion se termine à l'expiration du délai d'attente.  
  
 Ce problème ne concerne pas le pipeline AS2EdiREceive.  
  
## <a name="an-x12-encoded-message-is-suspended-if-port-based-authentication-is-enabled-and-biztalk-server-does-not-have-access-to-the-authorization-and-security-information"></a>Un message X12 est suspendu si l'authentification basée sur un port est activée et que BizTalk Server n'a pas accès aux informations d'autorisation et de sécurité  
 **Symptôme**  
  
 Lorsqu'un message est reçu sur un port de réception pour lequel l'authentification est activée, et si le tiers qui envoie le message ne peut être identifié, BizTalk Server suspend le message.  
  
 **Cause possible**  
  
 Si l'authentification est activée pour un port de réception (la propriété « Aucune authentification » du port de réception est désactivée), BizTalk Server requiert la configuration des propriétés « SA1-2 (Qualificateur et informations d'autorisation) » et « ISA3-4 (Qualificateur et informations de sécurité) » pour traiter l'échange. Ces propriétés sont définies pour un tiers dans la page Propriétés du processus d'échange X12 du tiers en tant qu'expéditeur de l'échange. Si BizTalk Server ne peut pas déterminer les valeurs de ces propriétés, il suspend le message.  
  
 Ceci peut se produire de deux manières. Dans le premier cas, si BizTalk Server ne peut pas déterminer le tiers qui envoie le message, il utilise les propriétés globales EDI et n'a pas accès aux paramètres d'autorisation et de sécurité. Il suspend donc le message. Dans le deuxième cas, si BizTalk Server identifie le tiers mais que les propriétés ISA1-2 et ISA3-4 du tiers ne sont pas configurées, BizTalk Server n'a pas davantage accès aux informations d'autorisation et de sécurité, et suspend le message.  
  
 **Résolution**  
  
 Assurez-vous que le tiers expéditeur du message peut être identifié et que les propriétés ISA1-2 et ISA3-4 sont définies dans l'accord du tiers.  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage des Solutions EDI et AS2](../core/troubleshooting-edi-and-as2-solutions.md)