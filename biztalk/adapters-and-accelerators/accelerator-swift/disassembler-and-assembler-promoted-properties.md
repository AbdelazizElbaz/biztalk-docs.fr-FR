---
title: "Propriétés promues du désassembleur et assembleur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disassembler, promoted properties
- promoted properties, assembler
- promoted properties, disassembler
- assembler, promoted properties
ms.assetid: 342b0250-bdf7-45ce-8964-3aeda89989b1
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ab1e0cab902ded34f10cf03bc6e8229d28123be2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="disassembler-and-assembler-promoted-properties"></a>Propriétés promues du désassembleur et assembleur
Les propriétés du désassembleur et assembleur se répartissent en deux catégories : les propriétés de routage pour le routage et le filtrage ; et les propriétés d’exécution, pour le traitement interne.  
  
Cette rubrique fournit une liste de propriétés qui sont ajoutés au et promues pour tous les messages publiés par le désassembleur SWIFT à la base de données MessageBox.  
  
## <a name="routing-properties"></a>Propriétés de routage

Le désassembleur SWIFT promeut les propriétés de routage. Vous pouvez utiliser ces propriétés pour le routage basé sur le contenu (filtres de port d’envoi) et le filtrage dans les orchestrations de réception.  
  
|Nom de promotion| Description|Type de données|Plage de valeurs|Exemple d’utilisation|  
|-------------------|-----------------|---------------|-----------------|-------------------|  
|**A4SWIFT_BatchId**|Un identificateur global unique généré dynamiquement par le désassembleur SWIFT lors du traitée d’un lot entrant. Le désassembleur affecte cet identificateur de lot à tous les messages publiés dans la base de données MessageBox d’origine à partir du même lot.<br /><br /> La valeur **-1** pour les messages uniques (ne pas d’origine à partir d’un lot entrant).|Chaîne|« -1 » ou *identificateur global unique (GUID)*|Mettre en corrélation des messages avec le même **A4SWIFT_BatchId** valeur pour les regrouper dans le même lot de leur arrivée à l’origine.|  
|**A4SWIFT_BreValidationErrors**|Indique le nombre d’erreurs de validation rencontrés pendant la validation du moteur de règles d’entreprise (BRE).|Numérique|>= 0|Filtre pour les messages qui n’a pas échoué la validation BRE (**A4SWIFT_BREValidationErrors** est égal à zéro).|  
|**A4SWIFT_Failed**|Indique si les erreurs s’est produite au cours de traitement (analyse et validation) du message. La valeur **True** si **A4SWIFT_ParseErrors** + **A4SWIFT_XmlValidationErrors** + **A4SWIFT_BreValidationErrors**  > 0.|Booléen|True, False|Filtre pour les messages SWIFT valides uniquement (**A4SWIFT_Failed** est égal à **False**).|  
|**A4SWIFT_ParseErrors**|Indique le nombre d’erreurs d’analyse rencontré lors de l’analyse.|Numérique|>= 0|Filtre pour les messages qui n’a pas échoué à l’analyse (**A4SWIFT_ParseErrors** est égal à zéro).|  
|**A4SWIFT_PosInBatch**|Indique la position ordinale d’un message provenant d’un lot entrant. Pour un lot contenant  *n*  messages, **A4SWIFT_PosInBatch** prend une valeur comprise entre 1 et  *n* , correspondant à l’ordinal du message position dans le lot.<br /><br /> La valeur **0** si le message est un en-tête de lot.<br /><br /> La valeur **n + 1** si le message est un code de fin du lot.<br /><br /> La valeur **1** si le message lui-même est l’ensemble du lot (désactivé de la fragmentation du lot).<br /><br /> La valeur **-1** pour les messages uniques (ne pas d’origine à partir d’un lot entrant).|Numérique|>= -1|Trier les messages à partir du même lot entrant dans l’ordre d’origine dans lequel ils sont arrivés.|  
|**A4SWIFT_XmlValidationErrors**|Indique le nombre d’erreurs de validation rencontrés pendant la validation du XML.|Numérique|>= 0|Filtre pour les messages qui n’a pas échoué la validation XML (**A4SWIFT_XmlValidationErrors** est égal à zéro).|  
  
> [!NOTE]
>  En règle générale, toutes les expressions de filtre ou de routage doivent évaluer **A4SWIFT_Failed** avant d’évaluer d’autres propriétés de routage. Uniquement **A4SWIFT_Failed** est garanti d’être promues et disponibles. Les propriétés restantes ne sont pas disponibles pour les messages uniques valides (les messages non-batch) publiés dans la base de données MessageBox. Les autres propriétés sont promues uniquement pour *échec* unique des messages et pour le traitement des messages (valide ou non).  

## <a name="runtime-properties"></a>Propriétés d’exécution

Le désassembleur SWIFT promeut les propriétés d’exécution et les utilise pour les processus internes en cours d’exécution. Elles ne sont promues et disponibles pour le routage dans certaines conditions, en fonction du contexte. En règle générale, n’utilisez pas ces propriétés de routage ou de filtrage. Il ne sont pas garantis d’être promues et disponibles. Dans certains scénarios, vous pouvez inspecter ces propriétés après la récupération ou de filtrage en utilisant les propriétés de routage. Le tableau suivant répertorie les propriétés d’exécution.  
  
|Nom de promotion| Description|Type de données|Plage de valeurs|Exemple d’utilisation|  
|-------------------|-----------------|---------------|-----------------|-------------------|  
|**A4SWIFT_IsMessageHeaderValued**|Indique si les données existent dans la partie de l’en-tête du message à parties multiples. La valeur **True** si la partie en-tête contient des données (en-tête d’enveloppe de message pour un message provenant d’un lot). La valeur **False** si la partie de l’en-tête est vide.|Booléen|True, False|Décider s’il faut examiner la partie de l’en-tête d’un message récupéré (par exemple, dans une orchestration de réparation de message).|  
|**A4SWIFT_IsMessageTrailerValued**|Indique si les données existent dans la partie du code de fin du message à parties multiples. La valeur **True** si la partie du code de fin contient des données (enveloppe le code de fin d’un message provenant d’un lot). La valeur **False** si la partie du code de fin est vide.|Booléen|True, False|Décider s’il faut examiner la partie du code de fin d’un message récupéré (par exemple, dans une orchestration de réparation de message).|  
|**A4SWIFT_MessageType**|Type de message du nombre de trois chiffres dans l’en-tête SWIFT indiquant le SWIFT (**MT*xxx***).|Chaîne|*Trois chiffres*|Identifier le type de message SWIFT d’un message de façon dynamique.|  
|**A4SWIFT_MessageType2**|Type de message du nombre de trois chiffres dans l’en-tête SWIFT indiquant le SWIFT (**MT*xxx***). Utiliser uniquement si **A4SWIFT_MessageType** est introuvable dans l’en-tête SWIFT.|Chaîne|*Trois chiffres*|Identifier le type de message SWIFT d’un message de façon dynamique.|  
|**A4SWIFT_NumberOfParts**|Indique le nombre de parties dans le message à parties multiples.<br /><br /> La valeur **1** si seul le corps existe (contenant un message individuel SWIFT valide ne pas provenant d’un lot, ou un en-tête de lot ou un code de fin du lot à partir d’une enveloppe de lot).<br /><br /> La valeur **2** si les parties de corps et d’erreur existent (corps contenant le message ayant échoué ou le lot, la partie de l’erreur qui contient la collection d’erreurs XML).<br /><br /> La valeur **3** si le corps, l’en-tête et les parties de code de fin existent (corps contenant des messages SWIFT individuels valide provenant d’un lot, l’en-tête partie contenant enveloppe en-tête du message, si utilisé et le message contenant des parties de code de fin code de fin enveloppe, si utilisée : **A4SWIFT_IsMessageHeaderValued** et **A4SWIFT_IsMessageTrailerValued** indiquer s’il existe des données dans les parties de l’en-tête et le code de fin).|Numérique|1, 2, 3|Filtre pour les messages ayant un nombre donné de parties (par exemple, filtrer **A4SWIFT_NumberOfParts** forme de réception est égale à deux pour une orchestration de réparation de message).|  
|**A4SWIFT_SecondaryMessageType**|Valeur de chaîne dans l’en-tête SWIFT indiquant le SWIFT sous-type du message (**MT*xxx_XYZ***).|Chaîne|*N’importe quelle chaîne*|Identifier de façon dynamique le sous-type de messages SWIFT d’un message.|  
  
 
## <a name="see-also"></a>Voir aussi  
[A4SWIFT_ * propriétés promues](../../adapters-and-accelerators/accelerator-swift/a4swift-promoted-properties.md)   