---
title: "Les en-têtes EDI et codes de fin | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5cf1dae3-9570-413d-a85d-94dcbb561906
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 655a7261da5dc66687fdf0cd623802854c0fa4ef
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edi-headers-and-trailers"></a>En-têtes et codes de fin EDI
Les parties d'un échange EDI sont délimitées par des en-têtes et des codes de fin qui doivent être conformes aux standards X12 et EDIFACT. L'en-tête et le code de fin de contrôle d'un échange n'apparaissent qu'une fois. Les en-têtes et les codes de fin d'un groupe fonctionnel et d'un document informatisé sont répétés si les documents informatisés et les groupes sont traités par lot dans l'échange. Chaque en-tête et code de fin est constitué de plusieurs éléments de données contenant des informations sur le contenu de l'en-tête et du code de fin.  
  
 Les en-têtes et les codes de fin pour X12 et EDIFACT sont similaires. La principale différence est l'en-tête des options de l'échange (UNA) pour EDIFACT, qui définit les séparateurs utilisés dans l'échange. Dans le codage X12, les séparateurs sont définis dans l'en-tête de contrôle d'échange ISA.  
  
 Les en-têtes et codes de fin de contrôle des échanges et des groupes fonctionnels sont indiqués comme segments d'enveloppe. Lorsque BizTalk Server fractionne un échange entrant en documents informatisés, il enregistre ces segments d'enveloppe sous forme de propriétés de contexte. Les principales propriétés d'enveloppe utiles au routage sont disponibles en tant que propriétés individuelles. Ce n'est pas le cas lorsque l'échange est conservé : les données de l'enveloppe font alors partie du message.  
  
 Lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] génère un message sortant, il crée les en-têtes et codes de fin sur la base des accords de partenariat commercial (ou des accords globaux, si aucun tiers n'a été identifié).  
  
 Les champs d'en-tête et de code de fin, ainsi que les caractères de séparation utilisés pour les séparer dans les échanges, sont définis dans l'accord entre les deux tiers. Les caractères de séparation ne doivent pas être utilisés dans la définition des champs d'en-tête ou de code de fin d'un échange, d'un groupe ou d'un document informatisé, tel que défini pour l'accord. S'ils sont utilisés, le traitement de l'échange échoue soit dans l'Assembleur EDI du [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] expéditeur, soit dans le désassembleur du tiers récepteur. L'échange échoue dans l'Assembleur EDI s'il s'agit d'un lot sortant parce que l'Assembleur valide l'enveloppe par rapport au schéma (service) de contrôle d'en-tête. Si l'échange n'est pas regroupé, l'Assembleur EDI le sérialise, mais le traitement dans le désassembleur de l'accord récepteur échoue.  
  
## <a name="x12-headers-and-trailers"></a>En-têtes et codes de fin X12  
 Les en-têtes et codes de fin d'un message X12 sont les suivants :  
  
```  
ISA Interchange Control Header  
  GS Functional Group Header  
    ST Transaction Set Header  
    SE Transaction Set Trailer  
  GE Functional Group Trailer  
IEA Interchange Control Trailer  
```  
  
 Si un en-tête ISA est immédiatement suivi d'un code de fin IEA, l'échange est vide. Si un document informatisé existe, l'en-tête GS et le code de fin GE doivent être présents ; sinon, ils sont conditionnels.  
  
 Les champs d'en-tête de contrôle d'échange ISA dans un message X12 sont de longueur fixe. Pour certains champs, vous pouvez entrer une valeur inférieure à celle du champ. Dans ce cas, l'échange doit contenir des espaces de fin (pour un champ de chaîne) ou des zéros de début (pour un champ numérique) afin que chaque champ soit conforme à la longueur requise. Lors de la création d'un échange sortant, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] entre des espaces de fin ou des zéros de début pour définir un en-tête de contrôle de l'échange de longueur appropriée. Les champs d'en-tête de groupe GS et les champs d'en-tête de document informatisé ST ne sont pas de longueur fixe.  
  
 Dans le codage X12, l'en-tête de sécurité fonctionnel, l'en-tête d'assurance fonctionnel, le segment de valeur de sécurité fonctionnel et les segments de code de fin de sécurité n'entrent pas dans le cadre de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI et AS2. Si un échange avec ces segments est reçu, il est interrompu avec un journal des erreurs indiquant qu'il s'agit de segments non identifiés.  
  
 Le champ ST01 correspond au code d'ID du document informatisé. Le champ ST02 correspond au numéro de contrôle du document informatisé. Le champ ST03 correspond à l'identificateur de version du schéma. Le champ SE01 indique le nombre de segments inclus dans le document informatisé. Le champ SE02 est équivalent au champ ST02 (numéro de contrôle du document informatisé). Lors de l'analyse d'un message entrant, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vérifie que le nombre de segments dans le document informatisé correspond à la valeur du champ SE01. Lors de la génération d'un message sortant, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] définit le champ SE01 sur le nombre correct de segments dans le document informatisé.  
  
 Un document informatisé XML en cours de sérialisation dans un échange EDI sortant doit avoir un en-tête et un code de fin de document informatisé. L'Assembleur EDI traite toutefois le message même s'il n'inclut pas d'en-tête et de code de fin de document informatisé. Les segments d'en-tête et de code de fin de document informatisé dans les schémas X12 et EDIFACT sont facultatifs pour les documents informatisés XML. Si un document informatisé n'inclut pas d'en-tête ou de code de fin, l'Assembleur EDI dans le pipeline d'envoi EDISend ou AS2EDISend lui ajoute les valeurs d'en-tête et de code de fin de document informatisé. Ces valeurs sont basées sur les mappages ou calculs. L'Assembleur EDI procède ainsi pour le fichier XML d'échange (un lot conservé), le fichier XML de document informatisé par lot et le fichier XML de document informatisé. Pour plus d’informations, consultez [X12 en-tête de Transaction et les Segments de code de fin](../core/how-the-edi-assembler-works.md#BKMK_X12) ou [en-tête de document informatisé EDIFACT et Segments de code de fin](../core/how-the-edi-assembler-works.md#BKMK_EDIFACT).  
  
## <a name="edifact-headers-and-trailers"></a>En-têtes et codes de fin EDIFACT  
 Les en-têtes et codes de fin d'un message EDIFACT sont les suivants :  
  
```  
UNA Service String Advice  
UNB Interchange Control Header  
  UNG Functional Group Header  
    UNH Message Header  
    UNT Message Trailer  
  UNE Functional Group Trailer  
UNZ Interchange Control Trailer  
```  
  
 L'en-tête UNA est facultatif. L'en-tête UNB est obligatoire. Si l'en-tête UNA est présent, il contient les délimiteurs à utiliser lors du traitement du message entrant ; sinon les séparateurs définis pour la propriété de pipeline EfactDelimiters sont utilisés.  
  
 Si un en-tête UNB est immédiatement suivi d'un code de fin UNZ, l'échange est vide. Si un en-tête UNG est immédiatement suivi d'un code de fin UNE, le groupe est vide. La paire en-tête UNG/code de fin UNE est conditionnelle et sa présence dans un message est facultative.  
  
## <a name="see-also"></a>Voir aussi  
 [Structure des messages EDI](../core/edi-message-structure.md)