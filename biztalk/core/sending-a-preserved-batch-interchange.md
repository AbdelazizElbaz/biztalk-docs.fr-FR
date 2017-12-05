---
title: "Envoi d’un échange par lot conservé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9bc2207-e34d-4d06-a224-bd7f8e498c27
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d5813bb4881535290422e2ba01d20d4370f4e604
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="sending-a-preserved-batch-interchange"></a>Envoi d'un échange de lot préservé
Quand le pipeline d'envoi EDI traite un échange de lot préservé sortant, il traite l'échange traité par lot comme un tout. Il réutilise normalement les segments (de contrôle) existants de l'enveloppe pour créer l'échange EDI, plutôt que d'appliquer une enveloppe basée sur l'accord. Cela se produit lorsque le **entrants option de traitement par lots** est définie sur **préserver l’échange : suspendre l’échange en cas d’erreur** ou **préserver l’échange : suspendre les documents informatisés sur Erreur**.  
  
## <a name="schema-validation"></a>Validation de schéma  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] valide l'enveloppe d'un lot préservé en utilisant les schémas de lot et les schémas de service. Le schéma de lot est utilisé pour valider le nœud racine du message préservé : les schémas de service sont utilisés pour valider les en-tête et les codes de fin d'échange, de groupe, et de document informatisé. Pour plus d’informations sur les schémas de lot, consultez [schémas de lot EDI](../core/edi-batch-schemas.md). Pour plus d’informations sur les schémas de service, consultez [Service EDI et des schémas de contrôle](../core/edi-service-and-control-schemas.md).  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] valide les documents dans un échange traité par lot à l'aide des schémas de document de votre projet.  
  
## <a name="send-side-processing"></a>Traitement côté envoi  
 Lorsque l'assembleur EDI traite un échange préservé, il utilise normalement les mêmes en-têtes d'échange, de groupe, et de document informatisé qui existaient dans l'échange traité par lot lorsque celui-ci a été reçu.  
  
-   Pour les échanges de X12, les paramètres de propriété dans différentes pages de l’onglet d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue (qui déterminent comment [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] crée les en-têtes ISA, GS et ST de sortante échange) ne s’appliquent pas.  
  
-   Pour des échanges EDIFACT, les paramètres UNA des propriétés de l'accord sont normalement utilisés. Le segment UNA est facultatif dans un message encodé en EDIFACT, mais il est nécessaire pour sérialiser un échange de lot préservé. S'il n'y a pas de valeur pour le segment UNA dans l'instance XML, les valeurs des propriétés par défaut pour le composant de pipeline d'envoi sont utilisées. Si les propriétés du composant de pipeline d'envoi ne sont pas évaluées, alors le message XML intermédiaire de lot préservé est interrompu.  
  
-   Si vous promouvez la propriété de contexte `EDI.PopulateInterchangeValues` sur "True" dans l'échange en cours de préservation (dans un composant personnalisé), l'EdiAssembler du port d'envoi attribue à tous les en-têtes d'échange, de groupe, et de document informatisé les valeurs établies dans les propriétés de l'accord.  
  
-   Si vous promouvez la propriété de contexte `EDIOverride.OverrideEdiHeader` sur “True” dans l'échange avant qu'il ne soit traité par le pipeline d'envoi, vous pouvez remplacer les valeurs d'enveloppe pour le document sortant en affectant des valeurs appropriées de propriété de contexte `EDIOverride`. Pour plus d’informations, consultez [remplaçant les en-têtes EDI](../core/overriding-edi-headers.md).  
  
 Pour qu'un échange préservé ne présente pas d'erreurs, l'assembleur préserve la séquence des documents informatisés dans un groupe de l'échange et la séquence des groupes dans l'échange.  
  
> [!NOTE]
>  Vous pouvez envoyez un lot préservé avec un pipeline d'envoi XML. Cette manière de faire nécessite cependant que vous changiez l'espace de noms pour le schéma de lot. Pour plus d’informations, consultez [envoi d’un lot conservé avec un Pipeline d’envoi XML](../core/sending-a-preserved-batch-with-an-xml-send-pipeline.md).  
  
## <a name="error-processing"></a>Erreur lors du traitement  
 Grâce à une balise réservée dans le XML, le pipeline d'envoi EDI identifie un échange EDI en tant que lot préservé. Cette balise soit \<X12InterchangeXml\> ou \<EdifactInterchangeXml\>, est appliquée au document XML en EDI pipeline de réception.  
  
 Voici les cas particuliers de suspension des documents informatisés en cas d'erreur :  
  
-   Si tous les documents informatisés d'un groupe ne sont pas valides, alors le pipeline d'envoi EDI inclut des segments de contrôle de groupe dans l'EDI généré, mais le groupe ne contient aucun document informatisé (car ils ont été supprimés). Les totaux de pied de page de groupe sont remis à zéro. Les segments de contrôle d'échange demeurent inchangés.  
  
-   Si tous les documents informatisés d'un échange ne sont pas valides, alors les segments de contrôle d'échange sont toujours inclus dans l'échange EDI généré, mais l'échange ne contient aucun document informatisé (car ils ont été supprimés). Cela constitue un échange vide.  
  
-   Si les segments de contrôle de groupe ou les segments de contrôle d'échange ne sont pas valides, un échange encodé en EDI n'est pas généré. Un journal est créé dans l'observateur d'événements, et indique si l'échange a été rejeté.  
  
## <a name="see-also"></a>Voir aussi  
 [Traitement par lot des messages EDI sortants](../core/batching-outgoing-edi-messages.md)