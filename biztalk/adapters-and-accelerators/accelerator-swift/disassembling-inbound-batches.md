---
title: "Désassembler des lots entrants avec SWIFT | Documents Microsoft"
description: "Debatch message entrant et personnaliser des schémas pour le traitement par lot à l’aide de l’accélérateur SWIFT dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11cb5672-1155-4648-b1fd-c9a3bc30e351
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4f14a199e3422a45235727d2d16fc1464e2e4927
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="disassemble-inbound-batches"></a>Désassembler des lots entrants

## <a name="debatch-inbound-message"></a>Debatch message entrant
Le désassembleur rapide est en mesure de trafic entrant debatching dans lequel il traite ou Désassemble les lots entrants (fichiers ou des messages contenant plusieurs messages SWIFT). Vous activez debatching entrant à l’aide de la propriété de configuration désassembleur SWIFT du même nom. Après avoir activé debatching entrant, le désassembleur SWIFT attend que tous les messages qu’il reçoit à des lots qui incluent plusieurs messages SWIFT. Un lot peut ou ne peut pas contenir une enveloppe de lot (un en-tête de lot et un code de fin du lot), et chaque message SWIFT dans un lot peut ou ne peut pas contenir une enveloppe de message (un en-tête de message et un code de fin de message). Vous pouvez configurer ces attributs de lot (formats) utilisant les propriétés de configuration désassembleur SWIFT suivantes :  
  
-   Schéma d’en-tête de lot  
  
-   Schéma de code de fin du lot  
  
-   Schéma d’en-tête de message  
  
-   Schéma de code de fin de message  
  
    > [!NOTE]
    >  Définition d’une de ces propriétés sur « Aucun » indique que le traitement par lots entrant n’inclut pas cette partie.  
  
 Le désassembleur SWIFT attend tous les lots entrants d’avoir la structure suivante :  
  
 **En-tête de lot**  
  
 **En-tête de message**  
  
 **Échange/de messages SWIFT (SWIFT blocs de 1 à 5)**  
  
 **Code de fin**  
  
 **Code de fin du lot**  
  
 Dans cette structure, vous pouvez envisager un « bloc de message » à la **en-tête du Message : échange SWIFT : le code de fin** parties. Une série de plusieurs « blocs de messages » constitue les plusieurs messages SWIFT dans un lot. L’en-tête de lot, l’en-tête de Message, le code de fin et code de fin de traitement par lots sont facultatifs, mais doivent être cohérentes entre les répétitions.  
  
> [!NOTE]
>  Ne confondez pas l’enveloppe du message (en-tête de Message et le code de fin) avec les blocs d’en-tête et le code SWIFT. Dans le contexte de lots, il convient de consulter les messages SWIFT (échange), y compris les blocs d’en-tête et le code SWIFT, comme une unité (atomique) globale. Dans ce contexte, l’en-tête de Message et le code de fin de Message font référence à l’enveloppe qui encapsule chaque message SWIFT dans un lot.  
  
 Pour exprimer cette structure, ses options et ses répétabilité plus formellement, pensez comment [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] définit un lot :  
  
-   **En-tête de lot** est représenté par **BH**  
  
-   **L’en-tête du message** est représenté par **EP**  
  
-   **L’échange SWIFT** est représenté par **SI**  
  
-   **Code de fin de message** est représenté par **MT**  
  
-   **Code de fin du lot** est représenté par **BT**.  
  
 L’expression qui représente la structure de lot attendu est le suivant :  
  
 `[BH] ([MH] SI [MT])* [BT]  `
  
 Les crochets ( `[ ] ` ) indiquent que la partie est facultative. L’astérisque (**\***) indique que le bloc est renouvelable. La personne qui crée le lot de messages doit utiliser l’en-tête de message (**LP**) et le code de fin (**MT**) cohérente dans chaque répétition de (`[MH] SI [MT]`).  
  
 Le désassembleur rapide est en mesure de traiter un lot entrant qui obéit à la structure ci-dessus, étant donné que chaque partie de la structure est conforme à un schéma de fichier plat. Toutefois, si vous n’utilisez pas l’en-tête facultatif lot/code de fin et l’en-tête/le code de fin, le message ne soit pas conforme à ces schémas. Par conséquent, un lot contenant uniquement les messages SWIFT consécutifs aura le schéma d’en-tête de lot, schéma de code de fin du lot, schéma d’en-tête de Message et les propriétés de schéma de code de fin de Message définie sur « None ».  

## <a name="customize-schemas-for-batching"></a>Personnaliser les schémas pour le traitement par lot  
 Vous pouvez personnaliser les schémas pour l’en-tête/fin du lot et l’en-tête/le code de fin. Un exemple est le traitement suivant :  
  
```  
4  
SWIFT Message # 1  
$  
SWIFT Message # 2  
$  
SWIFT Message # 3  
$  
SWIFT Message # 4  
$  
```  
  
 Pour gérer ce type de lot, vous définiriez les propriétés de schéma pour le lot comme suit :  
  
-   Vous définissez la propriété de schéma d’en-tête de lot à un schéma de fichier plat qui analyse un seul nombre (nombre de messages) délimité par un retour chariot.  
  
-   Vous définissez le schéma de code de fin de Message sur un schéma de fichier plat qui analyse un seul symbole $ et un retour chariot.  
  
-   Vous définissez les autres schémas d’enveloppe (schéma de code de fin du lot et schéma d’en-tête de Message) sur aucun.  
  
 Vous pouvez configurer le désassembleur SWIFT tel qu’il traite pratiquement n’importe quel lot de messages SWIFT en créant et en spécifiant la combinaison appropriée de schémas d’enveloppe de fichier plat. Cette fonctionnalité est très flexible.  
  
 Le désassembleur SWIFT tente toujours de la fin du traitement d’un lot entier, même lorsqu’il rencontre des erreurs en cours de route. Cela lui permet de collecter et consigner les erreurs autant que possible tous en même temps. Pour effectuer cet « meilleur effort » heuristique, le désassembleur SWIFT doit rendre certaines décisions et les hypothèses lorsque vous sélectionnez le schéma à utiliser lorsqu’il rencontre une nouvelle partie, ou si une erreur d’analyse se produit. En sélectionnant le schéma correct n’est pas toujours possible en fonction de la nature et l’emplacement d’une erreur d’analyse et de l’ambiguïté/la similarité entre les schémas d’enveloppe et les schémas d’échange SWIFT. Dans certains cas, vous pouvez minimiser la possibilité de sélectionner un schéma à l’aide de schémas d’enveloppe bien conçue. Si le désassembleur rencontre une erreur d’analyse irrécupérable ou le désassembleur ne peut pas déterminer le schéma correct, le désassembleur échoue le lot sans traiter les données restantes.  
  
 Lorsque **entrant Debatching** est **activé** (la valeur **True**), le désassembleur SWIFT analyse le lot à l’aide de schémas spécifiés pour l’enveloppe de lot (schéma d’en-tête de lot et le schéma de code de fin du lot) et enveloppe de message (schéma d’en-tête de Message et le schéma de code de fin de Message), ainsi que le schéma spécifié pour l’analyse des messages SWIFT (échanges) dans le lot. Pour les messages SWIFT dans le lot, le type de message et le schéma peuvent être dynamiquement détectés et chargées dans la même façon que les messages non-batch uniques (en spécifiant un schéma d’en-tête SWIFT). Pour plus d’informations sur la façon dont le désassembleur SWIFT exécute résolution de schéma, consultez [dynamique découverte de Type de Message et la résolution de schéma](../../adapters-and-accelerators/accelerator-swift/dynamic-message-type-discovery-and-schema-resolution.md).  
  
 Le désassembleur SWIFT analyse et valide chaque message SWIFT dans un lot entrant individuellement. Il exécute la séquence de traitement par lots suivants :  
  
1.  Analyse de l’en-tête du lot si vous avez spécifié le schéma d’en-tête de lot.  
  
2.  Analyse de l’en-tête d’enveloppe de message si vous avez spécifié le schéma d’en-tête de Message.  
  
3.  Analyse de l’échange rapide (message).  
  
4.  Valide le message SWIFT par rapport aux contraintes XML si vous avez activé la validation XML.  
  
5.  Valide le message SWIFT par rapport aux stratégies BRE (règles de réseau et l’utilisation SWIFT) si vous avez activé la validation BRE.  
  
6.  Analyse du code de fin d’enveloppe de message si le schéma de code de fin du Message n’est spécifié.  
  
7.  Répète les étapes 2 à 6 jusqu'à ce que le désassembleur ne trouve pas plus de messages dans le lot.  
  
8.  Analyse du code de fin du lot si vous avez spécifié le schéma de code de fin du lot.  
  
 Vous pouvez configurer le désassembleur SWIFT pour effectuer différentes opérations avec les données du lot qu’il analyse et valide utilisant les propriétés de configuration désassembleur SWIFT suivantes :  
  
-   Le **Fragmentation** propriété détermine si le désassembleur SWIFT doit publier les chaque message du lot à la base de données MessageBox individuellement (autrement dit, pour chaque message, après chaque occurrence de l’étape 6 ci-dessus), ou s’il doit effectuez les étapes 1 à 8, puis publiez le lot entier, sous la forme native (copie exacte de l’entrée), un seul message à la base de données MessageBox. Vous définissez **Fragmentation** à **True** pour activer la fragmentation et de publier des messages à partir d’un lot individuellement. Vous définissez **Fragmentation** à **False** pour désactiver la fragmentation et de publier l’ensemble du lot, format natif, sous la forme d’un seul message uniquement après le traitement de l’ensemble du lot. En général, définissez **Fragmentation** à **désactivé**pour les scénarios lorsque vous devez seulement BizTalk Accelerator pour SWIFT ([!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]) pour analyser et valider des lots entrants et a échoué ou transférés, dans le même formulaire [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] reçus. Vous définissez généralement **Fragmentation** à **activé** pour les scénarios dans lesquels vous [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] pour transformer ou modifier les messages dans un lot après l’analyse et de validation, ou lorsque vous souhaitez [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]trier à nouveau les messages dans un lot à un ordre différent de celui que [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] initialement reçu dans. Vous définissez également **Fragmentation** à **activé** pour les scénarios dans lesquels un lot entrant contient des messages qui ont différentes destinations finales.  
  
-   Le **préserver l’en-tête de lot / conserver le code de fin du lot** propriété détermine si le désassembleur SWIFT doit ignorer ou conserver les données de (en-tête et code de fin) d’enveloppe lot après l’analyser. Si vous définissez **conserver un en-tête de lot ou conserver le code de fin lot** à **True**, le désassembleur publie la partie de lot (code XML analysé) correspondant à la base de données MessageBox en tant que messages individuels. Le désassembleur publie les données dans le corps du message à parties multiples. Le désassembleur promeut les propriétés de contexte spéciale afin que [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] peut corréler ces messages pour le lot dont elles proviennent et la position ordinale, ils se trouvaient dans le lot (première position de l’en-tête de lot, dernière position de fin du lot). Si vous définissez **conserver un en-tête de lot ou conserver le code de fin lot** à **False**, le désassembleur ignore la partie de lot correspondant (données analysées) après l’analyse.  
  
    > [!NOTE]
    >  Ces propriétés de configuration sont valides uniquement lorsque la fragmentation est activée (**Fragmentation** la valeur **True**). Lorsque la fragmentation est désactivée, le désassembleur publie une copie exacte de l’ensemble du lot, format natif, la base de données MessageBox, donc les paramètres de conservation sont sans importance (*tout* est conservé).  
  
-   Le **conserver un en-tête de Message** / **conserver le code de fin** propriété détermine si le désassembleur SWIFT doit ignorer ou conserver les enveloppes de message (en-têtes de message et codes de fin) Après avoir analysé les. Si vous définissez **conserver un en-tête de Message ou conserver le code de fin** à **True**, le désassembleur publie la partie de lot (code XML analysé) correspondant à la base de données MessageBox *avec le les messages SWIFT individuels qu’il encapsule*. Le désassembleur publie des en-têtes d’enveloppe de message dans le **en-tête** dans le cadre du message à parties multiples. Le désassembleur publie des codes d’enveloppe de message dans le **remorque** dans le cadre du message à parties multiples. Le désassembleur publie le message SWIFT contenu dans l’enveloppe du message dans le **corps** dans le cadre de la même message à parties multiples. Le désassembleur promeut les propriétés de contexte spéciale afin que [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] peut corréler ces messages pour le lot dont elles proviennent et la position ordinale qu’ils avaient dans le lot. Si vous définissez **conserver un en-tête de Message ou conserver le code de fin** à **False**, le désassembleur ignore la partie de lot correspondant (données analysées) après l’analyse.  
  
    > [!NOTE]
    >  Ces propriétés de configuration sont valides uniquement lorsque la fragmentation est activée (**Fragmentation** la valeur **True**). Lorsque la fragmentation est désactivée, le désassembleur publie une copie exacte de l’ensemble du lot, format natif, la base de données MessageBox, donc les paramètres de conservation sont sans importance (*tout* est conservé).  
  
 Pour plus d’informations sur chaque propriété de configuration, ainsi que d’autres informations de configuration et de l’utilisation, consultez [propriétés de Configuration du désassembleur SWIFT](../../adapters-and-accelerators/accelerator-swift/swift-disassembler-configuration-properties.md). Pour plus d’informations sur la publication de base de données MessageBox et de messages à parties multiples, consultez l’aide de BizTalk Server.  
  
## <a name="next-step"></a>Étape suivante
  
[Propriétés promues relatives aux lots](batch-related-promoted-properties.md)
