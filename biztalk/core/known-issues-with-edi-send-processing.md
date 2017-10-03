---
title: "Connu des problèmes avec EDI le traitement d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1325dcd9-5dbb-48bb-b5a3-1502d1424d4e
caps.latest.revision: "31"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fbebfa213aa125252a8c58e246df376e2a36527d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-edi-send-processing"></a>Problèmes connus avec le traitement d'envoi EDI
Cette rubrique décrit les problèmes connus relatifs au traitement dans le pipeline d'envoi EDI.  
  
## <a name="x12-implied-decimal-point-causes-length-validation-to-fail"></a>Le point décimal implicite X12 entraîne l'échec de la validation de la longueur  
 **Symptôme**  
  
 Lorsque le pipeline d'envoi EDI convertit une valeur numérique de base 10 d'un fichier XML intermédiaire au format Nn dans l'échange EDI sortant, la validation de la longueur de l'échange XML échoue.  
  
 **Cause possible**  
  
 Lors de la sérialisation d'un échange EDI X12, les pipelines d'envoi EDI convertissent toujours une valeur numérique de base 10 au format Nn avec un point décimal implicite. Par exemple, si le fichier XML intermédiaire contient la valeur 12.34, le pipeline d'envoi EDI convertit cette valeur dans l'échange EDI en 1234 lorsqu'elle est spécifiée comme type numérique N2. La longueur de la valeur numérique de base 10 est supérieure à celle du nombre au format Nn. Si le nombre au format Nn correspond à la longueur maximale, la validation de la longueur de la valeur numérique de base 10 dans le fichier XML intermédiaire peut échouer.  
  
 Ce problème concerne uniquement les échanges X12.  
  
 **Résolution**  
  
 Ajoutez la valeur 1 à la valeur de longueur maximale du nombre XML.  
  
## <a name="control-numbers-may-need-to-be-reset-archived-or-purged"></a>Il peut être nécessaire de réinitialiser, d'archiver ou de purger les numéros de contrôle  
 Lorsqu'un numéro de contrôle atteint la longueur maximale autorisée pour le champ, BizTalk Server génère une erreur et interrompt l'échange. Dans ce cas, vous devez réinitialiser le numéro de contrôle entré dans la boîte de dialogue Propriétés EDI ou Propriétés globales EDI.  
  
 Les numéros de contrôle sont enregistrés dans la table dbo.EdiSequenceNumbers de la base de données MessageBox de BizTalk. Vous devez gérer cette table de base de données en purgeant les numéros de contrôle de la table ou en archivant les numéros de contrôle, selon vos besoins.  
  
 Vous pouvez également activer la réinitialisation automatique des numéros de contrôle en sélectionnant **réinitialiser à la limite inférieure lorsque la limite** dans la boîte de dialogue Propriétés EDI.  
  
## <a name="the-data-element-name-in-a-context-property-name-contains-an-underscore-not-a-period"></a>Trait de soulignement au lieu d'un point dans le nom d'un élément de données dans un nom de propriété de contexte  
 Le nom d'un élément de données dans un segment EDI contient un point (par exemple, UNB2.1, qui correspond au champ d'identification du segment d'expéditeur UNB2). Toutefois, lorsque le nom d'un élément de données est inclus comme propriété de contexte EDI (par exemple, dans l'expression de filtre d'un port d'envoi), le point est remplacé par un trait de soulignement. Par exemple, la propriété de contexte de l'élément d'identification de l'expéditeur est « EDI.UNB2_1 » et non « EDI.UNB2.1 ». En effet, le point n'est pas pris en charge dans le nom d'une propriété de contexte.  
  
## <a name="context-property-values-from-data-elements-must-not-contain-leading-or-trailing-spaces-in-filter-expressions"></a>Dans les expressions de filtre, les valeurs de propriété de contexte des éléments de données ne doivent pas contenir d'espace de début ou de fin  
 Si un élément de données dans l'enveloppe d'un échange EDI contient un espace de début ou de fin, et qu'un pipeline de réception promeut une propriété de contexte avec la valeur de cet élément, le pipeline de réception supprime les espaces de début ou de fin de la propriété de contexte. Ainsi, si vous créez une expression de filtre avec cette propriété de contexte, vous devez entrer la valeur de la propriété sans espace de début ou de fin. Si l'expression de filtre comporte des espaces de début ou de fin, elle ne peut pas être rapprochée de la propriété de contexte, qui ne contient pas d'espace de début ou de fin.  
  
## <a name="default-party-as-interchange-receiver-properties-for-preserved-interchange-will-cause-the-send-pipeline-to-fail"></a>Les propriétés Tiers en tant que récepteur d'échanges par défaut pour un échange préservé provoquent l'échec du pipeline d'envoi  
 Si BizTalk Server reçoit un échange par lot qui doit être préservé (l'échange étant suspendu en cas d'erreur), le pipeline d'envoi qui s'abonne à l'échange échoue si les propriétés du tiers en tant que récepteur d'échanges sont définies sur leurs valeurs par défaut. Ces propriétés (telles que ISA5, Qualificateur de l'expéditeur et ISA6, Identificateur de l'expéditeur) doivent être définies sur des valeurs valides. BizTalk Server génère une erreur indiquant que le message n'a pas été sérialisé en raison d'une configuration du tiers non valide. Ce traitement est incorrect car un échange préservé inclut les paramètres de configuration requis (Qualificateur de l'expéditeur et Identificateur de l'expéditeur) dans ses en-têtes.  
  
## <a name="the-decimal-notation-in-a-message-will-be-changed-if-the-send-side-party-or-global-setting-specifies-a-different-decimal-notation"></a>La notation décimale dans un message est modifiée si le tiers côté envoi ou le paramètre global spécifie une autre notation décimale  
 Si la notation décimale utilisée dans un échange diffère de la notation décimale spécifiée par la propriété de tiers UNA3 pour les messages sortants, BizTalk Server modifie la notation décimale utilisée dans l'enveloppe de l'échange lorsqu'il sérialise celle-ci pour l'expédition. Il en va de même si la propriété globale UNA3 est utilisée à la place de la propriété de tiers UNA3. Par exemple, si la notation décimale utilisée dans un message entrant est un point, et que la propriété de tiers UNA3 ou la propriété globale UNA3 qui détermine la notation décimale d'un message sortant spécifie une virgule, BizTalk Server modifie la notation décimale dans le message sortant en utilisant une virgule.  
  
## <a name="edi-send-pipelines-cannot-be-executed-from-within-an-orchestration"></a>Les pipelines d'envoi EDI ne peuvent pas être exécutés dans une orchestration  
 Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous pouvez exécuter normalement les pipelines d'envoi dans une forme Expression d'une orchestration. Toutefois, ceci ne fonctionne pas avec le pipeline EDISend ou le pipeline AS2EdiSend. Ces pipelines doivent être exécutés dans un port d'envoi. Si vous tentez d'exécuter le pipeline EDISend ou le pipeline AS2EdiSend dans une forme Expression au sein d'une orchestration, le pipeline n'est pas lié à un port d'envoi et le message est suspendu.  
  
## <a name="biztalk-edi-application-must-not-be-modified"></a>L'application EDI BizTalk ne doit pas être modifiée  
 Les artefacts de l'application EDI BizTalk ne doivent pas être modifiés ou supprimés. Si cette application est modifiée, vous ne pouvez pas revenir à l'application d'origine en annulant la configuration et en reconfigurant les fonctionnalités EDI et AS2.  
  
## <a name="using-the-default-row-in-the-functional-group-header-grid-can-result-in-a-message-type-mismatch-between-the-interchange-header-and-the-group-header"></a>L'utilisation de la ligne par défaut dans la grille d'en-tête de groupe fonctionnel peut provoquer une incompatibilité des types de messages entre les en-têtes de l'échange et du groupe  
 Si la valeur de UNH2.1 d'un échange EDIFACT sortant ne correspond pas à la valeur de « Pour le type de message UNH2.1 » dans la grille de la page Définition des segments UNG et UNH, il se peut que la valeur de UNG1 entrée dans le message ne corresponde pas à la valeur de UNH2.1.  
  
 Cela peut se produire car BizTalk renseigne le message avec les valeurs de UNG1 dans la ligne par défaut de la grille, même si le message n'a pas de correspondance avec l'élément UNH2.1 de cette ligne.  
  
 Si la valeur de ST1 d'un échange X12 sortant ne correspond pas à la valeur de « Pour ST1 » dans la grille de la page Définition des segments GS et ST, la valeur de GS1 entrée dans le message est déterminée de façon dynamique en fonction de la valeur de ST1.  
  
## <a name="invalid-character-in-data-element"></a>Caractère non valide dans un élément de données  
 **Symptôme**  
  
 Lors de l'envoi d'un échange EDI via le pipeline d'envoi EDI, une erreur indiquant la présence d'un caractère non valide dans l'élément de données peut être générée dans le journal des événements d'applications.  
  
 **Cause possible**  
  
 Cette erreur peut survenir si un caractère contenu dans les données de charge est également utilisé comme séparateur. Par exemple, si vous utilisez le ' :' caractère en tant que le séparateur de composants, mais les données de charge contient également le ' :' caractères.  
  
 Ce problème concerne uniquement les échanges X12.  
  
 **Résolution**  
  
 Utilisez le **remplacer les séparateurs dans la charge utile avec** définition dans le **définition des segments ISA** page des propriétés de tiers EDI pour spécifier que les caractères de séparation trouvant dans les données de charge doit être remplacé par le caractère de remplacement spécifié lors de l’envoi de l’échange.  
  
 Par exemple, la sélection **remplacer les séparateurs dans la charge utile avec** et en entrant le ' &#124;' caractère remplace toute occurrence d’un caractère de séparation dans les données de charge avec le ' &#124;' caractère lorsque l’échange est envoyé à l’aide du pipeline d’envoi EDI.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes connus avec le traitement EDI](../core/known-issues-with-edi-processing.md)   
 [Envoi des Messages EDI dans BizTalk Server](../core/how-biztalk-server-sends-edi-messages.md)   
 [Procédure pas à pas (X12) : Envoi d’échanges EDI](../core/walkthrough-x12-sending-edi-interchanges.md)