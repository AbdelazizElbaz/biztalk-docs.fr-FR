---
title: Encodages de message | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, encodings
- messages, code samples
- encoding [messages]
- code samples
ms.assetid: 360638c0-4094-428f-a7c7-306a5f95a6bf
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36063416e1c5d1f30c9cb9c26056299f0b926a50
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-encodings"></a>Encodages de message
Il n’est pas suffisante pour définir une sémantique de message dans l’ordre pour HL7 être utile. Une fois que le contenu du message a été déterminé, la norme doit expliquer comment représenter ce contenu dans une interface réelle. Autrement dit, il doit être spécifié « encodage de message ». HL7 Version 2 prend en charge deux formes d’encodage de message, un encodage d’en fonction du délimiteur personnalisé et un encodage XML.  
  
 HL7 a choisi le codage d’origine en fonction du délimiteur pour réduire la taille des messages autant que possibles. Par exemple, si vous comparez une structure de données dans laquelle délimiteurs de séparer les éléments vers une structure qui positionne chaque élément dans un ensemble fixe de positions, la structure en fonction du délimiteur est beaucoup plus économique si des messages a) ne contiennent pas certains éléments et (b) certaines éléments ne remplissent pas tout l’espace autorisé. La seule surcharge dans les structures en fonction du délimiteur est les délimiteurs eux-mêmes.  
  
 L’encodage HL7 d’origine définit cinq séparateurs, qui déclare de chaque message dans le segment MSH. Celles-ci indiquent :  
  
-   Segments  
  
-   Champs  
  
-   Components  
  
-   Sous-composants  
  
-   Répétition (d’un champ, un composant ou un sous-composant)  
  
 Notez que puisque les délimiteurs sont un aspect fondamental de l’encodage, vous devez les définir tout d’abord. Il en découle est qu’il ne peut y avoir aucun sous-répertoire sub-séparateur de. Dans certains cas, cette limitation a des effets fâcheux lors de la conception de nouveaux types de données.  
  
 En juin 2003, HL7 publié HL7 Version 2, syntaxe d’encodage XML, version 1. Cette norme définit d’autres règles de codage pour les messages HL7 Version 2.3.1 et 2.4 et fournit un mécanisme permettant de déterminer les autres règles de codage pour HL7 ultérieures versions 2.X. Fondamentalement, cette nouvelle norme définit les balises d’éléments XML pour la Version 2.3.1 V2.4 messages abstraits, segments, les champs et les types de données et crée des règles pour définir les balises nécessaires pour les nouvelles structures créés pour les versions ultérieures de la Version 2 standards. Le processus de définition de cette norme conduit à une série d’améliorations dans les versions 2.4 et 2.5. Cela s’est produite, car la création de balises XML a conduit à la nécessité de prendre quelques ambiguïtés commune dans la norme sous-jacent. As a result, les codes de structure de message a) bien définis ont été créés pour indiquer les variations dans les messages abstraites associés aux événements de déclencheur, (b) répétition de groupes de segments avec un message abstrait ont été officiellement identifiés et nommés et c) localement type de données défini, CM a été remplacée par des types plus spécifiques.  
  
 Voici, par exemple, un message d’accusé de réception simple en utilisant le format de canal traditionnel délimitée par des :  
  
```  
MSH|^~\&|LAB|767543|ADT|767543|199003141304-0500||ACK^^ACK|XX3657|P|2.4  
MSA|AR|ZZ9380  
ERR|PID^1^16^103&Table value not found&HL70357  
```  
  
 Le même message représenté sous la forme d’un document XML sont en revanche, les éléments suivants :  
  
```  
<ACK  
xmlns="urn:hl7-org:v2xml"  
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
xsi:schemaLocation="urn:hl7-org:v2xml ACK.xsd">  
   <MSH>  
      <MSH.1>|</MSH.1>  
      <MSH.2>^~\&</MSH.2>  
      <MSH.3>  
         <HD.1>LAB</HD.1>  
      </MSH.3>  
      <MSH.4>  
         <HD.1>767543</HD.1>  
      </MSH.4>  
      <MSH.5>  
         <HD.1>ADT</HD.1>  
      </MSH.5>  
      <MSH.6>  
         <HD.1>767543</HD.1>  
      </MSH.6>  
      <MSH.7>  
         <TS.1>199003141304-0500</TS.1>  
      </MSH.7>  
      <MSH.9>  
         <MSG.1>ACK</MSG.1>  
         <MSG.3>ACK</MSG.3>  
      </MSH.9>  
      <MSH.10>XX3657</MSH.10>  
      <MSH.11>  
         <PT.1>P</PT.1>  
      </MSH.11>  
      <MSH.12>  
         <VID.1>2.4</VID.1>  
      </MSH.12>  
   </MSH>  
   <MSA>  
      <MSA.1>AR</MSA.1>  
      <MSA.2>ZZ9380</MSA.2>  
   </MSA>  
   <ERR>  
      <ERR.1>  
         <ELD.1>PID</ELD.1>  
         <ELD.2>1</ELD.2>  
         <ELD.3>16</ELD.3>  
         <ELD.4>  
            <CE.1>103</CE.1>  
            <CE.2>Table value not found</CE.2>  
            <CE.3>HL70357</CE.3>  
         </ELD.4>  
      </ERR.1>  
   </ERR>  
</ACK>  
```  
  
 Les fonctions suivantes de [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) prend en charge ces exigences :  
  
-   Prise en charge de canal délimités et l’encodage XML.  
  
-   Prise en charge de la traduction entre XML et canal délimitée par des encodages.  
  
## <a name="see-also"></a>Voir aussi  
 [Le traitement des Messages HL7](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [Traitement des messages](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [L’utilisation des schémas 2.X HL7](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)