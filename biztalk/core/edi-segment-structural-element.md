---
title: "Élément structurel d’un Segment EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1f474a3d-004a-4981-b155-b0a5775918ba
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b05d7a793fe515b8d0254d63b9b96994ddb35d9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edi-segment-structural-element"></a>Élément structurel d'un segment EDI
Le segment contient un ou plusieurs éléments de données. Il s'agit d'une unité d'information intermédiaire dans le message. Chaque segment commence par un identificateur de segment de données de trois caractères et se termine par un terminateur de segment (apostrophe (') par défaut). Les éléments de données au sein du segment sont séparées par un séparateurs d'éléments de données (signe plus (+) par défaut). Les segments peuvent être obligatoires ou facultatifs. Les séparateurs pour les échanges sortants peuvent être définis dans les accords entre deux partenaires commerciaux ou en tant qu'accord de partenariat commercial de secours.  
  
## <a name="nesting"></a>Imbrication  
 Segments peuvent être regroupés dans une relation hiérarchique appelée **d’imbrication**. Il existe deux types d’imbrications : explicites et implicites. Un seul type d'imbrication peut être utilisé dans un échange.  
  
-   L'imbrication explicite indique de façon explicite que la boucle est imbriquée. Lorsque l'imbrication explicite est utilisée, le segment de code est le premier élément de données composites dans la balise de segment. Il est suivi d'éléments de données composites conditionnels indiquant le niveau et la fréquence de répétition du segment. Le nombre d'éléments de données composites utilisés à cette fin dépend du niveau hiérarchique de la structure de message dans lequel le segment apparaît. Si le segment apparaît au premier niveau, l'élément de données composites juste après le segment de code est utilisé. Si le segment apparaît au deuxième niveau, l'élément de données composites juste après le segment de code et l'élément de données composites suivant sont utilisés. Si le segment apparaît au troisième niveau, les trois éléments de données composites juste après le segment de code sont utilisés. Les pipelines ne peuvent pas effectuer de vérification structurelle par comparaison des données à la hiérarchie.  
  
-   Dans une imbrication implicite, l'ordre des segments spécifiés dans la structure de message est strictement suivi. La relation d'imbrication entre les segments est évidente et aucune indication supplémentaire n'est requise pour le traitement.  
  
## <a name="loops"></a>Boucles  
 Un ou plusieurs segments peuvent être répétés sous un **boucle** à l’intérieur d’une transaction définie. Il existe deux types de boucles : non liée et liée.  
  
### <a name="unbounded-loops"></a>Boucles non liées  
 Une boucle non liée ne contient pas de segment d'identification unique marquant le début et la fin de la boucle. La répétition d'une boucle non liée est déterminée par un nombre. Si ce nombre n'est pas défini, la boucle est répétée deux fois. Chaque segment de la boucle ne peut apparaître qu'une fois dans un ordre spécifié.  
  
 Un premier élément de données unique établit le début d'une boucle non liée. Il ne peut apparaître qu'une fois dans chaque occurrence. Les boucles non liées peuvent être imbriquées dans d'autres boucles. Dans ce cas, la boucle non liée interne ne peut pas débuter à la même position ordinale ou avec le même ID de segment que les autres boucles externes. La boucle imbriquée ne peut pas contenir de segment débutant une boucle externe au sein de la même structure d'imbrication.  
  
### <a name="bounded-loops"></a>Boucles liées  
 Une boucle liée commence par le segment de début de boucle (LS, Loop Start) prédéfini et se termine par le segment de fin de boucle (LE, Loop End) prédéfini. Le caractère facultatif du segment LS doit correspondre à celui du premier segment de la boucle. Une boucle liée peut contenir une autre boucle liée.  
  
> [!NOTE]
>  Une boucle liée dans un échange X12 et une boucle explicite dans un échange EDIFACT sont équivalentes.  
  
 Une liaison permet de résoudre les ambiguïtés dans une boucle. L'indicateur du caractère obligatoire des segments LS/LE correspond à celui du premier segment de la boucle. Une liaison minimise les restrictions structurelles imposées sur l'utilisation de certains segments fréquemment répétés. Segments liés n’ont aucune restriction en ce qui concerne l’ID de segment de début. Cela permet le même segment débuter une boucle liée et être utilisé en dehors de la boucle, comme dans l’exemple suivant :  
  
```  
AA  
LS  
BB  
CC  
LE  
BB  
```  
  
 Les boucles subordonnées (boucles au sein de boucles) sont autorisées. Si des boucles liées sont imbriquées au sein d'autres boucles, la boucle interne ne peut pas débuter à la même position ordinale que les autres boucles externes. La boucle liée interne doit se terminer avant la boucle externe la plus proche.  
  
 Pour chaque boucle liée dans un document informatisé, une valeur <ID_boucle> unique doit être définie. Celle-ci peut inclure de un à quatre chiffres ou lettres majuscules. Il est recommandé d'utiliser la même valeur <ID_boucle> pour les segments LS et LE correspondants. L’élément de données < id_boucle > est traité comme un élément de données « standard » et validé pour le type de données, la longueur minimale/maximale, caractère facultatif, etc.. Validation de segment croisé (segments LS et LE) n’est pas effectuée. BizTalk Server vérifie uniquement la résolution des ambiguïtés via les segments LS et LE. En cas de violation d'une règle applicable aux éléments de données, le document informatisé est accepté avec des erreurs et BizTalk Server renvoie la valeur AK501=E et l'évaluation appropriée AK2/AK3 dans l'accusé de réception.  
  
 Les segments LS/LE doivent également être associés par paire. En cas de non concordance, le document informatisé est rejeté en raison d'un problème de résolution des ambiguïtés, les valeurs AK501 = E et AK502 = 5 sont renvoyées dans l'Observateur d'événements et l'accusé de réception 997. Si les segments LS et/ou LE sont manquants, mais que le document informatisé est dénué d'ambiguïté, celui-ci est accepté avec des erreurs et les valeurs AK501 = E et AK502 = 5 sont renvoyées.  
  
 Une paire de segments LS/LE peut être facultative ou obligatoire. La paire n'est toutefois jamais renouvelée, à moins d'être contenue dans une boucle parent renouvelable. Dans les deux cas, la valeur MaxOccurs d'une paire de segments LS/LE peut être égale à 1, mais pas supérieure à 1. Cette condition est vérifiée dans le cadre de la validation de schéma.  
  
 Le Désassembleur EDI et l'Assembleur EDI gèrent les segments LS et LE. Au cours de l'analyse, le Désassembleur crée des nœuds XML pour les segments LS et LE, puis valide les segments. Au cours de la sérialisation, l'Assembleur crée les segments LS et LE à partir des nœuds XML, puis valide ceux-ci. Si une LS attendu ou LE segment manquant, le document informatisé est rejeté/suspendu avec les valeurs AK501 = E et AK502 = 5. Si les segments LS/LE sont présents sans élément de données correspondant, et la validation EDI est activée, le document informatisé est accepté avec des erreurs et les valeurs AK501 = E et AK502 = 5 sont renvoyées dans l’Observateur d’événements et le 997 accusé de réception.