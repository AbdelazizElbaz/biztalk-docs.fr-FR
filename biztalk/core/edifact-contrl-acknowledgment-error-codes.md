---
title: "Codes d’erreur d’accusé de réception EDIFACT CONTRL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0c5ab75-d83d-4c3e-a054-8fe079219b61
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e492b4c7092ec1561354fe772b11e16ea6c093ee
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edifact-contrl-acknowledgment-error-codes"></a>Codes d'erreur d'accusé de réception EDIFACT CONTRL
Cette rubrique répertorie les codes d'erreur utilisés dans les segments d'un accusé de réception EDIFACT CONTRL. Pour plus d’informations sur ces segments, consultez [accusé de réception EDIFACT CONTRL](../core/edifact-contrl-acknowledgment.md).  
  
 Ces erreurs s'appliquent au niveau de l'échange, du groupe, du message et des données. Si une erreur prise en charge survient, l'intégralité de l'échange, du groupe ou du document informatisé est rejeté. La condition « Accepté avec erreurs » n'existe pas pour les échanges EDIFACT.  
  
 **Codes d’erreur EDIFACT standard**  
  
 Le tableau suivant répertorie les codes d'erreur utilisés dans le champ UCI5 de l'accusé de réception EDIFACT CONTRL. Le tableau suivant indique les codes d'erreur définis par la spécification EDIFACT pris en charge et non pris en charge par les fonctionnalités EDI et AS2 de [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].  
  
|Code d'erreur|Condition|Cause|Pris en charge ?|  
|----------------|---------------|-----------|----------------|  
|2|Version ou niveau de la syntaxe non pris en charge|Indique que la version et/ou le niveau de la syntaxe n'est pas pris en charge par le destinataire.|Non|  
|7|Le destinataire de l'échange n'est pas le destinataire réel|Indique que le destinataire de l'échange (S003) est différent du destinataire réel.|Non|  
|12|Valeur non valide|Indique que la valeur d'un élément de données autonomes ou composites n'est pas conforme aux spécifications appropriées pour cette valeur.|Oui|  
|13|Manquant|Indique qu'un service, un segment utilisateur, un élément de données ou un élément de données composites obligatoire est manquant.|Oui|  
|14|Valeur non prise en charge à cette position|Indique que le destinataire ne prend pas en charge l'utilisation de la valeur spécifique d'un élément de données autonomes ou composites identifié à cette position. La valeur peut être valide selon les spécifications appropriées et peut être prise en charge si elle est utilisée à une autre position.|Non|  
|15|Non pris en charge à cette position|Indique que le destinataire ne prend pas en charge l'utilisation du type de segment, ou du type d'élément de données autonomes ou composites à cette position.|Oui|  
|16|Trop de composants|Indique que le segment identifié contient trop d'éléments de données ou que l'élément de données composites identifié contient trop de composants.|Oui|  
|17|Aucun accord|Aucun accord n'existe pour autoriser la réception d'un échange, d'un groupe, d'un message ou d'un package avec la valeur de l'élément de données autonomes ou composites identifié.|Non|  
|18|Erreur inconnue|Indique qu'une erreur a été identifiée, mais que la nature de celle-ci n'est pas signalée.|Non|  
|19|Notation décimale non valide|Indique que le caractère indiqué en tant que notation décimale dans le segment UNA est non valide, ou que la notation décimale utilisée dans un élément de données n'est pas cohérente avec celle indiquée dans le segment UNA.|Non|  
|20|Caractère non valide en tant que caractère de service|Indique qu'un caractère détecté dans le segment UNA est non valide en tant que caractère de service.|Non|  
|21|Caractère(s) non valide(s)|Indique qu'un ou plusieurs caractères de l'échange sont considérés comme non valides par l'identificateur de syntaxe indiqué dans le segment UNB. Le caractère non valide fait partie du niveau référencé, ou est immédiatement suivi par la partie identifiée de l'échange.|Oui|  
|22|Caractère(s) de service non valide(s)|Indique que les caractères de service utilisés dans l'échange ne sont pas valides pour le segment UNA ou ne correspondent pas à ceux par défaut. Si le code est utilisé dans le segment UCS ou UCD, le caractère non valide est suivi immédiatement par une partie identifiée de l'échange.|Non|  
|23|Expéditeur de l'échange inconnu|Indique que l'expéditeur de l'échange (S002) est inconnu.|Non|  
|24|Trop ancien|Indique que l'échange ou le groupe reçu est antérieur à la limite spécifiée dans l'IA ou déterminée par le destinataire.|Non|  
|25|L'indicateur Test n'est pas pris en charge|Indique que le traitement du test ne peut pas être effectué pour l'échange, le groupe, le message ou le package identifié.|Non|  
|26|Doublon détecté|Indique qu'un éventuel doublon d'un échange, d'un groupe, d'un message ou d'un package précédemment reçu a été détecté. La transmission précédente peut avoir été rejetée.|Oui|  
|27|La fonction de sécurité n'est pas prise en charge|Indique qu'une fonction de sécurité associée au niveau référencé ou à l'élément de données n'est pas prise en charge.|Non|  
|28|Les références ne correspondent pas|Indique que le contrôle de référence du segment UNB, UNG, UNH, UNO, USH ou USD ne correspond pas, respectivement, au contrôle de référence du segment UNZ, UNE, UNT, UNP, UST ou USU.|Non|  
|29|Le nombre de contrôles ne correspond pas au nombre d'instances reçues|Indique que le nombre de groupes, de messages ou de segments ne correspond pas au nombre donné dans le segment UNZ, UNE, UNT ou UST ; ou que la longueur d'un objet ou des données chiffrées est différente de la longueur définie dans le segment UNO, UNP, USD ou USU.|Oui|  
|30|Groupes et messages/packages mélangés|Indique que les groupes ont été mélangés avec les messages/packages hors des groupes de l'échange.|Non|  
|31|Plusieurs types de messages dans le groupe|Indique que différents types de messages sont contenus dans un groupe fonctionnel.|Oui|  
|32|Niveau inférieur vide|Indique que l'échange ne contient aucun message, package ni groupe ; ou qu'un groupe ne contient aucun message ni package.|Non|  
|33|Occurrence non valide hors du message, du package ou du groupe|Indique la présence d'un segment ou d'un élément de données non valide dans l'échange, entre les messages, les packages ou les groupes. Le rejet est signalé au niveau supérieur.|Oui|  
|34|Indicateur d'imbrication non autorisé|Indique que l'imbrication explicite a été utilisée dans un message dans lequel elle ne doit pas l'être.|Non|  
|35|Trop d'éléments de données ou de répétitions de segments|Indique qu'un élément de données autonomes ou composites, ou un segment, est répété trop souvent.|Oui|  
|36|Trop de répétitions de groupes de segments|Indique qu'un groupe de segments est répété trop souvent.|Oui|  
|37|Type de caractère non valide|Indique qu'au moins un caractère numérique est utilisé dans un élément de données (composites) alphabétique ou qu'au moins un caractère alphabétique est utilisé dans un élément de données (composites) numérique.|Oui|  
|38|Chiffre manquant devant le signe décimal|Indique qu'un signe décimal n'est pas précédé d'un ou plusieurs chiffres.|Oui|  
|39|Élément de données trop long|Indique que la longueur de l'élément de données reçu dépasse la longueur maximale spécifiée dans la description de l'élément de données.|Oui|  
|40|Élément de données trop court|Indique que la longueur de l'élément de données reçu est inférieure à la longueur minimale spécifiée dans la description de l'élément de données.|Oui|  
|41|Erreur permanente du réseau de communication|Indique qu'une erreur permanente a été signalée par le réseau de communication utilisé pour le transfert de l'échange. La retransmission d'un échange identique avec les mêmes paramètres au niveau du réseau va échouer.|Non|  
|42|Erreur temporaire du réseau de communication|Indique qu'une erreur temporaire a été signalée par le réseau de communication utilisé pour le transfert de l'échange. La retransmission d'un échange identique peut réussir.|Non|  
|43|Destinataire de l'échange inconnu|Indique que le destinataire de l'échange est inconnu du fournisseur réseau.|Non|  
|45|Séparateur de fin|Indique ce qui suit :<br /><br /> -Le dernier caractère avant le terminateur de segment est un séparateur d’éléments de données, un séparateur d’éléments de données composites ou un séparateur d’éléments de données extensible, ou<br /><br /> -Le dernier caractère avant un séparateur d’éléments de données est un séparateur d’éléments de données composites ou un séparateur d’éléments de données extensible.|Oui|  
|46|Jeu de caractères non pris en charge|Indique qu'un ou plusieurs caractères utilisés ne font pas partie du jeu de caractères défini par l'identificateur de syntaxe ; ou que le jeu de caractère identifié par la séquence d'échappement pour la technique d'extension du code n'est pas pris en charge par le destinataire.|Oui|  
|47|La fonctionnalité d'enveloppe n'est pas prise en charge.|Indique que la structure d'enveloppe rencontrée n'est pas prise en charge par le destinataire.|Oui|  
|48|Condition des notes de dépendance violée|Indique qu'une violation de condition de dépendance a produit une condition d'erreur.|Non|  
  
 **Codes d’erreur EDIFACT spécifiques à BizTalk Server**  
  
 Le tableau suivant répertorie les codes d'erreur utilisés dans le champ UCI5 de l'accusé de réception EDIFACT CONTRL qui ne font pas partie des spécifications EDIFACT. Il s'agit de codes personnalisés spécifiques à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
|Code d'erreur|Condition|Cause|  
|----------------|---------------|-----------|  
|70|Document informatisé manquant ou identificateur de document informatisé non valide|Indique que l'identificateur de document informatisé est manquant ou non valide.|  
|71|Document informatisé ou numéro de contrôle du groupe incohérent|Indique une incohérence entre le document informatisé ou les numéros de contrôle du groupe|  
|72|ID de segment non reconnu|Indique que l'ID du segment n'est pas reconnu.|  
|73|XML n'est pas à la position correcte|Indique qu'un problème est survenu lors de la sérialisation de l'élément racine XML.|  
|74|Répétitions de groupes de segments insuffisantes|Indique que le nombre de répétitions d'un groupe de segments est inférieur au nombre requis.|  
|75|Répétitions de segments insuffisantes|Indique que le nombre de répétitions de segments est inférieur au nombre requis.|  
|76|Éléments de données trouvés insuffisants|Indique que le nombre d'éléments de données trouvés est insuffisant.|