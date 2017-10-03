---
title: "X12 des Codes d’erreur d’accusé de réception 997 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f73ca2c-cfff-444b-ae80-fb724f067fcc
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 89627cc793000fa6bb9c11c5e15dc78423fcb0ca
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="x12-997-acknowledgment-error-codes"></a>Codes d'erreur d'accusé de réception X12 997
Cette rubrique répertorie les codes d'erreur utilisés dans les segments d'un accusé de réception 997 X12. Pour plus d’informations sur ces segments, consultez [X12 accusé de réception 997](../core/x12-997-acknowledgment.md).  
  
 Chaque tableau indique les codes d'erreur définis par la spécification X12 pris en charge et non pris en charge par les fonctionnalités EDI et AS2 de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 **AK304 Codes d’erreur**  
  
 Le tableau suivant répertorie les codes d'erreur utilisés dans l'élément de données AK304 du segment AK3 (note de segment de données).  
  
|Code d'erreur|Condition|Pris en charge ?|  
|----------------|---------------|----------------|  
|1|ID de segment non reconnu|Oui|  
|2|Segment inattendu|Oui|  
|3|Segment obligatoire manquant|Oui|  
|4|Boucle se produit sur le nombre maximal de fois|Oui|  
|5|Segment dépasse l’utilisation maximale|Oui|  
|6|Segment pas de document informatisé défini|Oui|  
|7|Pas dans l’ordre approprié de segment|Oui|  
|8|Segment comporte des erreurs d’élément de données|Oui|  
|511|Séparateurs de fin détectés (code personnalisé)|Oui|  
  
 **AK403 Codes d’erreur**  
  
 Le tableau suivant répertorie les codes d'erreur utilisés dans l'élément de données AK403 du segment AK4 (note d'élément de données).  
  
|Code d'erreur|Condition|Pris en charge ?|  
|----------------|---------------|----------------|  
|1|Élément de données obligatoire manquant|Oui|  
|2|Élément de données obligatoire conditionnel manquant|Oui|  
|3|Trop d'éléments de données|Oui|  
|4|L'élément de données est trop court|Oui|  
|5|L'élément de données est trop long|Oui|  
|6|Caractère non valide dans l'élément de données|Oui|  
|7|Valeur de code non valide|Oui|  
|8|Date non valide|Oui|  
|9|Heure non valide|Oui|  
|10|Condition d’exclusion violée|Oui|  
  
 **AK501 Codes d’erreur**  
  
 Le tableau suivant répertorie les codes d'erreur utilisés dans l'élément de données AK501 du segment AK5 (code de fin de réponse du document informatisé).  
  
|Code d'erreur|Condition|Pris en charge ?|  
|----------------|---------------|----------------|  
|Un|Accepté|Oui|  
|E|Accepté mais des erreurs ont été relevées|Oui<br /><br /> Remarque : Aucun des codes d’erreur génère l’état « E ».|  
|M|Rejeté, échec du code d'authentification de message (MAC)|Non|  
|P|Partiellement accepté, au moins un document informatisé a été rejeté|Oui|  
|R|Rejeté|Oui|  
|W|Rejeté, l'assurance a échoué les tests de validité|Non|  
|X|Rejeté, impossible d'analyser le contenu après le déchiffrement|Non|  
  
 **AK502 à AK506 des Codes d’erreur**  
  
 Le tableau suivant répertorie les codes d'erreur utilisés dans les éléments de données AK502 à AK506 du segment AK5 (code de fin de réponse du document informatisé).  
  
|Code d'erreur|Condition|Prise en charge ? /<br />Corrélé avec AK501 ?|  
|----------------|---------------|------------------------------------------|  
|1|Document informatisé non pris en charge|Oui/R|  
|2|Code de fin de jeu de transactions manquante|Oui/R|  
|3|Le numéro de contrôle de document informatisé dans l'en-tête et le code de fin ne correspondent pas|Oui/R|  
|4|Le nombre de segments inclus ne correspond pas au nombre réel|Oui/R|  
|5|Un ou plusieurs segments erronés|Oui/R|  
|6|Identificateur de document informatisé manquant ou non valide|Oui/R|  
|7|Numéro de contrôle de document informatisé manquant ou non valide (il y a peut-être un numéro de transaction en double)|Oui/R|  
|8 à 27|-|Non|  
  
 **AK901 Codes d’erreur**  
  
 Le tableau suivant répertorie les codes d'erreur utilisés dans les éléments de données AK901 du segment AK9 (code de fin de réponse du groupe fonctionnel).  
  
|Code d'erreur|Condition|Prise en charge ? /<br />Corrélé avec AK501 ?|  
|----------------|---------------|------------------------------------------|  
|Un|Accepté|Oui|  
|E|Accepté, mais des erreurs ont été relevées|Oui|  
|M|Rejeté, échec du code d'authentification de message (MAC)|Non|  
|P|Partiellement accepté, au moins un document informatisé a été rejeté|Oui|  
|R|Rejeté|Oui|  
|W|Rejeté, l'assurance a échoué les tests de validité|Non|  
|X|Rejeté, impossible d'analyser le contenu après le déchiffrement|Non|  
  
 **AK905 à AK909 des Codes d’erreur**  
  
 Le tableau suivant répertorie les codes d'erreur utilisés dans les éléments de données AK905 à AK909 du segment AK9 (code de fin de réponse du groupe fonctionnel).  
  
|Code d'erreur|Condition|Prise en charge ? /<br />Corrélé avec AK501 ?|  
|----------------|---------------|------------------------------------------|  
|1|Groupe fonctionnel non pris en charge|Non|  
|2|Version de groupe fonctionnel non pris en charge.|Non|  
|3|Code de fin de groupe fonctionnel manquant|Oui|  
|4|Le numéro de contrôle de groupe dans l'en-tête et le code de fin du groupe fonctionnel ne correspondent pas|Oui|  
|5|Le nombre de documents informatisés inclus ne correspond pas au nombre réel|Oui|  
|6|Ce numéro de contrôle de groupe ne respecte pas la syntaxe (il y a peut-être un numéro de contrôle de groupe en double)|Oui|  
|7 à 26|-|Non|  
  
## <a name="see-also"></a>Voir aussi  
 [X12 accusé de réception 997](../core/x12-997-acknowledgment.md)