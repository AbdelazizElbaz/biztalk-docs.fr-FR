---
title: HL7 Structure de Message | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, segments
- messages, fields
- trigger events
- messages, trigger events
- segments, messages
- messages, message structure
ms.assetid: 4dbef56d-97ae-466d-bc8a-dc96c40896f6
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d3e705d3c8a72b5ca1072157a227bf6f218035d5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="hl7-message-structure"></a>HL7 Structure de Message
Un message HL7 est une structure hiérarchique associée à un événement déclencheur. Le HL7 standard définit un événement déclencheur « en tant qu’événement dans le monde réel de soins de santé (qui) crée le besoin de données de circuler entre les systèmes ». Chaque événement déclencheur est associé à un message abstrait qui définit le type de données que le message doit prendre en charge de l’événement déclencheur. Le message abstrait est une collection de segments et inclut des règles de répétition et d’inclusion pour ces segments. Le tableau suivant montre un exemple d’un message abstrait associé à l’événement déclencheur A04 : inscrire un Patient.  
  
|Événement déclencheur|Message abstraite|  
|-------------------|----------------------|  
|ADT ^ A04 ^ ADT_A01|Admission décharge et transfert|  
|MSH|En-tête de message|  
|EVN|Type d’événement|  
|PID|Identification de patient|  
|[PD1]|Données démographiques supplémentaires|  
|[{RÔLE}]|Rôle|  
|[{NK1}]|Suivant des Parties proche parent / associés|  
|PV1|Visitez patient|  
|[PV2]|Visitez patient - informations supplémentaires|  
|[{RÔLE}]|Rôle|  
|[]|Informations d’invalidité|  
|[{OBX}]|Observation/résultat|  
|[{AL1}]|Informations allergies|  
|[{DG1}]|Informations de diagnostic|  
|[DRG]|Groupe connexe de diagnostic|  
|[{||  
|PR1|Procédures|  
|[{RÔLE}]|Rôle|  
|}]||  
|[{GT1}]|Caution|  
|[{||  
|IN1|Assurance|  
|[2]|Informations supplémentaires|  
|[{IN3}]|Informations supplémentaires d’assurance - Cert.|  
|[{RÔLE}]|Rôle|  
|}]||  
|[C]|Informations accident|  
|[UB1]|Informations de facture universel|  
|[UB2]|Informations de 92 facture universel|  
|[PDA]|Autopsie et décès patient|  
  
 Les crochets ci-dessus » [ », «] » indiquent qu’un segment ou un groupe de segments est facultative, accolades lors de la « { », «} » indiquent le segment ou groupe de segments de répétitions.  
  
 Un segment est un groupe de champs, chacun d’eux est conforme à un type de données particulier. Champs peuvent avoir une structure simple ou complexe. Il s’agit des composants selon les règles définies dans leur définition de type de données. Pour prendre en charge les types de données plus complexes, certains composants peuvent contenir des sous-composants.  
  
> [!NOTE]
>  Le fait que le message HL7 utilise l’encodage spécifié délimiteurs qui limite la capacité d’un développeur d’introduire de nouvelles façons de subdiviser les données. Il ne peut y avoir aucun sous-composant secondaire, car cela nécessiterait invention d’un nouveau type de délimiteur.  
  
 Les spécifications HL7 premier n’ont pas défini le message abstrait. Le message abstrait est un modèle de segments associés à un événement déclencheur. De même, les messages HL7 contiennent des collections de segments de répéter l’ensemble ou groupes de segments. Les spécifications HL7 premier n’ont pas défini les groupes de segments. En commençant par V2.3.1 et continuer dans les versions ultérieures, cette modifiée en raison de la nécessité de prendre en charge l’encodage XML. Par exemple, dans la table d’événement déclencheur ci-dessus, le nom de la structure du message est « ADT_A01 ». Il s’agit du même modèle de segments utilisés pour prendre en charge A01 – admettre un Patient. Pour plus de commodité, les noms des structures de message correspondant à la première (en termes de placement dans le document HL7) déclencher l’événement qui les utilise. De même, le groupe de segments dans la table d’événement de déclencheur ci-dessus qui commence par IN1, y compris les 2 IN3 et le rôle, est utilisée en tant que groupe. Son nom, en commençant par la Version 2.5 est groupe « Insurance ».  
  
 Dans la Version 2, les règles de compatibilité des versions entre prend en charge l’évolution des interfaces en exigeant que les versions suivantes de la norme n'incluent pas les structures qui invalident les versions antérieures. Ceci nécessite que vous ne supprimez pas un événement déclencheur et que vous n’utilisez pas un événement déclencheur dans un but différent ou avec un autre message abstrait que prévu initialement. Pour les messages abstraites, cela implique que vous ne pouvez pas supprimer un segment d’un message, ni vous pouvez rendre un segment obligatoire facultatif ou un extensible segment non extensible. Si vous ajoutez un segment, vous devez le faire à la fin d’un message ou à la fin d’un groupe extensible au sein d’un message.  
  
 Les fonctions suivantes de [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) prend en charge ces exigences :  
  
-   Prise en charge de tous les événements déclencheurs et les structures de message commençant par V2.1 et en continuant 2.5.  
  
-   Prise en charge de la localisation et ajouter des segments et éventuellement de personnalisation segment répétition.  
  
## <a name="see-also"></a>Voir aussi  
 [Le traitement des Messages HL7](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [Traitement des messages](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [L’utilisation des schémas 2.X HL7](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)