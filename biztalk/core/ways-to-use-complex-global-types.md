---
title: "Modes d’utilisation des Types globaux complexes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ddea1c7b-eb0e-4521-8576-0ea6f9460847
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5f84b8b872d047a62a913514a695b4bba2d482c0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="ways-to-use-complex-global-types"></a>Utilisations des types globaux complexes
Une fois que vous avez converti un type complexe en un type complexe global, il devient disponible pour une éventuelle réutilisation dans d'autres emplacements de votre schéma. Pour plus d’informations sur la définition d’un type complex et sur sa conversion en un type complex global, consultez [définition de Type Global complexe et attribution de nom](../core/complex-global-type-definition-and-naming.md).  
  
 Tout d’abord, vous insérez une nouvelle **enregistrement** nœud. Ensuite, vous devez sélectionner le nœud inséré et définir l'une des deux propriétés de nœud suivantes dans la fenêtre Propriétés. Chacune a un effet différent :  
  
-   **Propriété Data Structure Type**. si vous voulez utiliser le type global complexe sans le modifier de quelque façon, définissez cette propriété sur le nom de type que vous avez donné au type global complexe en le sélectionnant dans la liste déroulante. Dans l'arborescence de schéma, la structure de nœuds globale choisie sera dupliquée graphiquement au nouvel emplacement et toute modification apportée ultérieurement à la structure dans n'importe lequel de ses emplacements dans l'arborescence de schéma sera automatiquement appliquée à tous les emplacements qui utilisent ce type global complexe.  
  
-   **Propriété de Type de données de base**. si vous voulez utiliser une variation du type global complexe, soit en l'étendant soit le restreignant de quelque façon, définissez cette propriété sur le nom de type que vous avez donné au type global complexe, sélectionnable dans la liste déroulante. Lorsque vous définissez cette propriété, le **Derived By** modifications apportées aux propriétés de nœud **Extension** (et **le Type de contenu** modifications apportées aux propriétés **ComplexContent**), qui indique que l’extension du type global complexe est le type de dérivation par défaut. Vous pouvez le remplacer par **Restriction** si vos modifications sont de cette nature. Les modifications apportées au type global de base complexe à partir duquel vous effectuez la dérivation sont automatiquement reflétées dans le type dérivé, mais les modifications apportées au type dérivé ne sont jamais reflétées dans le type de base.  
  
> [!NOTE]
>  Si vous définissez l'une de ces propriétés, tout paramétrage de l'autre propriété sera automatiquement supprimé. En outre, vous remarquerez les autres interactions automatiques entre les propriétés associées, telles que la définition du **Derived By** propriété **(par défaut)** supprime tout paramétrage existant à partir de la **Base Type de données** propriété.  
  
> [!NOTE]
>  Vous pouvez créer un schéma de test et utiliser des valeurs différentes pour ces propriétés, en observant les modifications dans l'affichage XSD.  
  
 Cette section décrit l'utilisation de types globaux complexes tels quels, mais aussi en les étendant ou les restreignant, comme s'ils étaient contrôlés par les paramètres des propriétés décrites dans cette rubrique.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Réutilisation de types globaux complexes](../core/complex-global-type-re-use.md)  
  
-   [Dérivation de Type Global complexe](../core/complex-global-type-derivation.md)