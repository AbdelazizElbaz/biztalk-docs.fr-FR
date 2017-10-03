---
title: Les Segments de champ REPEATABLE | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- segments, repeatable fields
- QPD
- Table Row Data (RDT)
- Query Parameter Definition (QPD)
- Segments table
- RDT
ms.assetid: 4c31cb56-21e5-4918-aaf6-67e8ceddd74f
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a801e39fac0e0bdf0cfb9ee88811703fd1c4373d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="repeatable-field-segments"></a>Segments répétitifs
La table des Segments dans la base de données HL7 Access contient une colonne pour le dernier champ de segments (ADD, r & DT et QPD) qui [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) définit comme repeatable (**Last_field_repeatable**  =  **True**). [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]ne prend pas en charge les ajouter. Toutefois, r & DT et QPD sont présents pour interroger des tables et répondent avec des valeurs de la table. L’exemple suivant montre comment [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] gère ces colonnes.  
  
 Un client soumet la requête suivante et indique que le client souhaite obtenir une réponse immédiate en définissant **en priorité RCP-1-réponse** à «**I**» :  
  
```  
MSH|^&~\|PCR|Gen Hosp|PIMS||199811201400-0800||QBP^Q42^QBP_Q13|ACK9901|P|2.4||||||||  
QPD|Q42^Tabular Dispense History^HL7nnn|Q0010|555444222111^^^MPI^MR| |19980531|19990531|  
RCP|I|999^RD|  
RDF|3|PatientList^ST^20~PatientName^XPN^48~MedicationDispensed^ST^40~RXD.3^TS^26  
```  
  
 Le serveur répond à une minute plus tard avec le message suivant :  
  
```  
MSH|^&~\|PIMS|Gen Hosp|PCR||199811201401-0800||RTB^K42^RTB_K13|8858|P|2.3||||||||  
MSA|AA|8699|  
QAK|Q010|OK|Q42^Tabular Dispense History^HL7nnn|4  
QPD|Q42^Tabular Dispense History^HL7nnn|Q0010|555444222111^^^MPI^MR||19980531|19990531|  
RDF|7|PatientId^CX^20~PatientName^XPN^48~OrderControlCode^ID^2~ MedicationDispensed^CE^100~DispenseDate^TS^26~QuantityDispensed^NM^20~ OrderingProvider^XCN^120  
RDT|555444222111^^^MPI^MR|Everyman^Adam|RE|525440345^Verapamil Hydrochloride 120 mg TAB^NDC |199805291115-0700|100|77^Hippocrates^Harold^H^III^DR^MD  
RDT|555444222111^^^MPI^MR|Everyman^Adam|RE|00182196901^VERAPAMIL HCL ER TAB 180MG ER^NDC |19980821-0700|100|77^Hippocrates^Harold^H^III^DR^MD  
RDT|555444222111^^^MPI^MR|Everyman^Adam|RE|00172409660^BACLOFEN 10MG TABS^NDC |199809221415-0700|10|88^Semmelweis^Samuel^^^DR^MD  
RDT|555444222111^^^MPI^MR|Everyman^Adam|RE|00054384163^THEOPHYLLINE 80MG/15ML SOLN^NDC|199810121145-0700|10|99^Lister^Lenora^^^DR^MD  
```  
  
 À partir de l’exemple, vous voyez que QPD et r & DT sont personnalisé/site défini. La spécification HL7 définit les segments QPD et r & DT comme suit.  
  
## <a name="qpd---query-parameter-definition"></a>QPD - définition de paramètre de requête  
 Le tableau suivant montre comment la spécification de HL7 définit QPD.  
  
|SEQ|LEN|TYPE DE DONNÉES|S’ABONNER|RP / #|TBL #|ÉLÉMENT #|NOM DE L’ÉLÉMENT|  
|---------|---------|--------|---------|------------|-----------|------------|------------------|  
|1|250|CE|R||0471|01375|Nom de requête de message|  
|2|32|ST|C|||00696|Balise de requête|  
|3-n|256|Varie||||01435|Champs successives des paramètres utilisateur|  
  
## <a name="rdt---table-row-data"></a>R & DT - données de ligne de Table  
 Le tableau suivant montre comment la spécification de HL7 définit r & DT.  
  
|SEQ|LEN|TYPE DE DONNÉES|S’ABONNER|RP / #|TBL #|ÉLÉMENT #|NOM DE L’ÉLÉMENT|  
|---------|---------|--------|---------|------------|-----------|------------|------------------|  
|1-n|Variable|Variable|R|||00703|Valeur de colonne|  
  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]interprète QPD et r & DT sous forme de valeurs définie sur le site qui peuvent se répéter. Étant donné que [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] ne résout pas les types de données et d’autres détails, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] traite QPD.3 et RDT.1 en tant que types de données de chaîne dans les schémas. Vous devrez peut-être modifier ces schémas en fonction de vos propres conditions de site.  
  
## <a name="see-also"></a>Voir aussi  
 [L’utilisation des schémas 2.X HL7](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)