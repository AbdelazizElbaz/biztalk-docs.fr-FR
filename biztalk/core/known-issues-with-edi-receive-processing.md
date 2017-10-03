---
title: "Connu des problèmes avec EDI de traitement de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbb3fd6a-381b-479e-a9f2-7b6371fac39e
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 75ab2769ab4a6eacf885dbf675a6bd3fda371007
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-edi-receive-processing"></a>Problèmes connus avec le traitement de réception EDI
Cette rubrique décrit les problèmes connus relatifs au traitement dans le pipeline de réception EDI.  
  
## <a name="receive-side-processing-of-trailing-separators-fails"></a>Échec du traitement côté réception des séparateurs de fin  
 **Symptôme**  
  
 Un document informatisé avec un séparateur de fin échoue avec le code d'erreur AK403= 6 pour un message X12 ou les codes d'erreur UCM3=4/UCD1=45 pour un message EDIFACT.  
  
 **Cause possible**  
  
 Le traitement des séparateurs de fin n'est pas activé.  
  
 **Résolution**  
  
 Ouvrez les propriétés EDI du tiers qui a envoyé le message. Dans la page Génération d'accusés de réception et paramètres de validation de la boîte de dialogue Propriétés EDI (pour X12 ou EDIFACT), activez la case à cocher « Autoriser les délimiteurs/séparateurs de fin ». Vous pouvez ensuite spécifier que des balises XML vides sont créées pour les séparateurs de fin du fichier XML intermédiaire en cliquant sur « Créer des balises XML vides pour les séparateurs de fin ».  
  
## <a name="contrl-ack-is-enabled-but-not-generated"></a>L'accusé de réception CONTRL est activé, mais pas généré  
 **Symptôme**  
  
 La case à cocher Générer accusé de réception fonctionnel de la page Génération d'accusés de réception et paramètres de validation pour le tiers expéditeur est activée, mais le pipeline de réception EDI n'a pas généré d'accusé de réception CONTRL.  
  
 **Cause possible**  
  
 Le message CONTRL contient plusieurs éléments de données obligatoires qui doivent être copiés à partir de l'échange. Lorsqu'un élément de données de l'échange est manquant ou syntaxiquement non valide, le pipeline de réception ne peut pas générer de message CONTRL valide du point de vue syntaxique.  
  
 **Résolution**  
  
 Signalez la condition d'erreur autrement que par le biais d'un accusé de réception CONTRL.  
  
## <a name="there-was-a-failure-executing-the-receive-pipeline-error-message"></a>« Il était un échec de l’exécution du Pipeline de réception... » Message d'erreur  
 **Symptôme**  
  
 Lorsqu'un pipeline de réception AS2 est exécuté, une erreur 80040154 est générée.  
  
 **Cause possible**  
  
 Les pipelines ne sont pas pris en charge sur les instances d'hôte 64 bits.  
  
 **Résolution**  
  
 Associez le pipeline à un hôte 32 bits.  
  
## <a name="an-x12-encoded-message-is-suspended-if-port-based-authentication-is-enabled-and-biztalk-server-does-not-have-access-to-the-authorization-and-security-information"></a>Un message X12 est suspendu si l'authentification basée sur un port est activée et que BizTalk Server n'a pas accès aux informations d'autorisation et de sécurité  
 **Symptôme**  
  
 Lorsqu'un message est reçu sur un port de réception pour lequel l'authentification est activée, et si le tiers qui envoie le message ne peut être identifié, BizTalk Server suspend le message.  
  
 **Cause possible**  
  
 Si l'authentification est activée pour un port de réception (la propriété « Aucune authentification » du port de réception est désactivée), BizTalk Server requiert la configuration des propriétés « SA1-2 (Qualificateur et informations d'autorisation) » et « ISA3-4 (Qualificateur et informations de sécurité) » pour traiter l'échange. Ces propriétés sont définies pour un tiers dans la page Propriétés du processus d'échange X12 du tiers en tant qu'expéditeur de l'échange. Si BizTalk Server ne peut pas déterminer les valeurs de ces propriétés, il suspend le message.  
  
 Ceci peut se produire de deux manières. Dans le premier cas, si BizTalk Server ne peut pas déterminer le tiers qui envoie le message, il utilise les propriétés globales EDI et n'a pas accès aux paramètres d'autorisation et de sécurité. Il suspend donc le message. Dans le deuxième cas, si BizTalk Server identifie le tiers mais que les propriétés ISA1-2 et ISA3-4 du tiers ne sont pas configurées, BizTalk Server n'a pas davantage accès aux informations d'autorisation et de sécurité, et suspend le message.  
  
 **Résolution**  
  
 Assurez-vous que le tiers expéditeur du message peut être identifié et que les propriétés ISA1-2 et ISA3-4 sont définies dans l'accord du tiers.  
  
## <a name="incorrect-se01-in-a-split-hipaa-subdocument"></a>SE01 incorrect dans un sous-document HIPAA fractionné  
 **Symptôme**  
  
 L'en-tête de document informatisé (champ SE01) fournit le nombre de segments de données, y compris les segments d'en-tête et de code de fin d'un document X12/HIPAA. Toutefois, pour un sous-document HIPAA fractionné, le pipeline de réception EDI applique la même valeur SE01 que le document d'origine, plutôt que de la recalculer.  
  
 **Cause**  
  
 Le pipeline de réception EDI copie la valeur de SE01 du document HIPAA d'origine vers un sous-document fractionné.  
  
## <a name="error-message-for-duplicate-unb5-or-unh1-is-not-descriptive"></a>Le message d'erreur relatif à des numéros UNB5 ou UNH1 dupliqués n'est pas descriptif  
 Si BizTalk Server reçoit un message dont le numéro UNB5 (numéro de contrôle de l'échange) ou UNH1 (numéro de référence du document informatisé) est dupliqué, le code d'erreur et la description publiés n'indiquent pas clairement la nature du problème.  
  
## <a name="biztalk-server-will-suspend-a-very-large-interchange-if-it-runs-out-of-memory"></a>Si la mémoire de BizTalk Server est insuffisante, il interrompt un échange très volumineux  
 BizTalk Server risque de ne plus disposer de suffisamment de mémoire lorsqu'il analyse un échange très volumineux. Dans ce cas, il publie une erreur et interrompt l'échange. Dans la page Hub du groupe, vous ne pouvez pas afficher l'intégralité du contenu d'un échange très volumineux qui a été interrompu. Vous pouvez voir la partie initiale du message, mais la quantité de données d'un échange interrompu que BizTalk Server peut afficher est limitée.  
  
## <a name="korean-characters-added-to-an-enumeration-in-a-kedifact-schema-must-be-in-unicode"></a>Les caractères coréens ajoutés à une énumération dans un schéma KEDIFACT doivent être au format UNICODE  
 Lorsque BizTalk Server reçoit un échange KEDIFACT contenant des caractères coréens, il utilise la valeur jeu de caractères/page de codes du champ UNB2 pour traiter l'échange. Toutefois, si vous modifiez un schéma KEDIFACT en ajoutant un caractère coréen avec un type de données d'ID à une énumération, vous devez ajouter la valeur dans le code UNICODE UTF-16, tel que spécifié en haut du schéma.  
  
## <a name="executing-an-edi-receive-pipeline-from-within-an-orchestration-is-not-supported"></a>L'exécution d'un pipeline de réception EDI à partir d'une orchestration n'est pas prise en charge  
 Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous pouvez généralement exécuter les pipelines de réception dans une forme Expression d'une orchestration. Cette fonctionnalité n'ayant pas été testée pour le pipeline EDIReceive ou AS2EdiReceive, elle n'est pas prise en charge.  
  
## <a name="biztalk-edi-application-must-not-be-modified"></a>L'application EDI BizTalk ne doit pas être modifiée  
 Les artefacts de l'application EDI BizTalk ne doivent pas être modifiés ou supprimés. Si cette application est modifiée, vous ne pouvez pas revenir à l'application d'origine en annulant la configuration et en reconfigurant les fonctionnalités EDI et AS2.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes connus avec le traitement EDI](../core/known-issues-with-edi-processing.md)   
 [Réception des Messages EDI dans BizTalk Server](../core/how-biztalk-server-receives-edi-messages.md)   
 [Procédure pas à pas (X12) : Réception des échanges EDI et envoi d’un accusé](../core/walkthrough-x12--receive-edi-interchanges-and-send-back-an-acknowledgement.md)