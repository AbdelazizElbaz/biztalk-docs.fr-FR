---
title: "Extension des énumérations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- enumeration values
- 2.X schemas, enumeration values
ms.assetid: 043def35-b644-4502-a2e2-cc1a5fc0328a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2abb040d79f0c9312a8761289c0bf6252fef2f3a
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="extending-enumerations"></a>Extension des énumérations
Vous pouvez ajouter des valeurs pour les énumérations qui définissent les valeurs acceptées pour de nombreux types de champs, des segments et des données dans le corps du message HL7, accusé de réception et les schémas de corps du message. Cela implique la modification de l’ensemble de valeurs dans une table spécifique dans le fichier de schéma valeurs de table commune pour la version HL7 dans lequel vous travaillez (le **Tablevalues_\<***version*  **\>.xsd** fichier de schéma).  
  
 Vous ajoutez à l’énumération d’une manière différente pour le schéma d’en-tête de message que vous effectuez dans d’autres schémas, tels que le schéma de corps de message. Pour le schéma d’en-tête de message, vous devez modifier la table dans le fichier MSH_25_GLO_DEF.xsd. Pour les autres schémas, vous modifiez la table dans le fichier de schéma de valeurs de table (tablevalues_\<version\>.xsd).  
  
### <a name="to-add-an-enumeration-value-to-the-table-values-common-schema-file"></a>Pour ajouter une valeur d’énumération vers la table de valeurs courantes schéma  
  
1.  Vous devez tout d’abord déterminer la table qui contient l’énumération que vous souhaitez ajouter à. Dans l’Explorateur de solutions de Visual Studio, ouvrez le fichier de schéma qui contient l’élément que vous souhaitez modifier. Dans l’Explorateur BizTalk, cliquez sur l’élément de champ que vous souhaitez ajouter une valeur à utiliser.  
  
    > [!NOTE]
    >  Lorsque vous modifiez une énumération dans le fichier de schéma table valeurs courantes, tous les objets qui font référence à cette énumération sont affectées.  
  
2.  Dans le **propriétés** volet, notez le nom de la table dans le **Base Data Type** champ.  
  
    > [!NOTE]
    >  S’il existe aucune table ne répertoriés dans **Base Data Type** champ et le **Derived By** propriété n’est pas définie sur **Restricted**, puis le champ n’est pas une énumération associée .  
  
3.  Dans l’Explorateur de solutions, ouvrez le **Tablevalues_\<***version***\>.xsd**, puis cliquez sur **ouvrir**.  
  
    > [!NOTE]
    >  Vous devez effectuer cette procédure séparément pour chaque version du schéma HL7 que vous souhaitez modifier.  
  
4.  Dans l’Éditeur BizTalk, accédez à la table que vous souhaitez modifier, puis cliquez sur ce nœud de la table.  
  
5.  Dans la fenêtre Propriétés, dans le **Restriction** , cliquez sur **énumération**, puis cliquez sur le bouton de sélection (...) pour ouvrir l’éditeur d’énumération.  
  
6.  Dans l’éditeur d’énumération, ajouter la nouvelle valeur à la liste des valeurs existantes, puis cliquez sur **OK**.  
  
### <a name="to-add-an-enumeration-value-to-a-message-header-schema"></a>Pour ajouter une valeur d’énumération à un schéma d’en-tête de message  
  
1.  Dans l’Explorateur de solutions, ouvrez le schéma MSH_25_GLO_DEF, puis cliquez sur **ouvrir**.  
  
2.  Cliquez sur le **MSH** nœud, pointez sur **insérer un nœud de schéma**, puis cliquez sur **élément de champ enfant**. [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]Ajoute un nœud de champ à MSH, appelé **champ**. Cliquez sur **entrée**.  
  
3.  Dans le **propriétés** fenêtre, cliquez sur le **Type de données** nœud, puis dans la liste déroulante, sélectionnez la table à laquelle vous souhaitez ajouter la valeur d’énumération.  
  
4.  Dans le **propriétés** fenêtre, dans le **Restriction** , cliquez sur **énumération**, puis cliquez sur le bouton de sélection (...) pour ouvrir l’éditeur d’énumération.  
  
5.  Dans l’éditeur d’énumération, ajouter la nouvelle valeur à la liste des valeurs existantes, puis cliquez sur **OK**.  
  
     Lorsque vous ajoutez une valeur à l’énumération de tous les nœuds, tels que les **champ** nœud, vous ajoutez cette valeur globalement pour tous les objets qui utilisent cette table. Par conséquent, vous pouvez à présent supprimer la **champ** nœud et la valeur toujours sera présent pour la table. Vous pouvez le vérifier en le défilement dans le volet droit de l’Éditeur BizTalk pour la table et en vérifiant que la valeur que vous avez ajouté est présente.  
  
6.  Cliquez sur le **champ** dans l’Éditeur BizTalk, cliquez sur **supprimer**, puis cliquez sur **Oui**.  
  
## <a name="see-also"></a>Voir aussi  
 [Table les valeurs des schémas courants](../../adapters-and-accelerators/accelerator-hl7/table-values-common-schemas.md)   
 [Extension des schémas 2.X HL7 avec des objets Z](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md)   
 [Création de Segments de Z déclaré](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md)   
 [Création de Types de données personnalisés dans les schémas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-data-types-in-schemas.md)   
 [Création de Tables personnalisées dans les schémas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-tables-in-schemas.md)   
 [Gestion des segments Z non déclarés](../../adapters-and-accelerators/accelerator-hl7/handling-undeclared-z-segments.md)