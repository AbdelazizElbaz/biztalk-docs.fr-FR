---
title: "Le traitement des messages d’instance à l’aide des champs distinctifs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b8f3f77-5385-4294-b441-bcb28bdc51b4
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f4dca22ff1b09a0d1cfb261a9d5726da8b1b17b1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="instance-message-processing-using-distinguished-fields"></a>Traitement des messages d'instance à l'aide de champs distinctifs
Promotion des propriétés à l’aide de la **champ distinctif** mécanisme ne nécessite pas la création d’un schéma de propriété. Comme avec toutes les promotions de propriété, vous utilisez la **promouvoir les propriétés** boîte de dialogue, qui est accessible à l’aide de la **promouvoir les propriétés** propriété de la **schéma** nœud schémas de message ou à l’aide de la **promouvoir &#124; Afficher les Promotions** commande sur le **BizTalk** ou les menus contextuels.  
  
 Dans le **promouvoir les propriétés** boîte de dialogue zone, vérifiez que le **champs distinctifs** onglet est sélectionné dans la partie droite de la boîte de dialogue. Ensuite développez les nœuds dans l’arborescence de schéma sur le côté gauche de la boîte de dialogue pour rechercher et sélectionner les **élément de champ** nœud ou **attribut de champ** nœud que vous souhaitez promouvoir en tant que champ distinctif, puis Cliquez sur **ajouter**. Pour obtenir des instructions sur la promotion des propriétés à **champs distinctifs** à l’aide de la **promouvoir les propriétés** boîte de dialogue, consultez [copie de données dans le contexte du Message en tant qu’unique Champs](../core/how-to-copy-data-to-the-message-context-as-distinguished-fields.md).  
  
> [!NOTE]
>  Vous pouvez également promouvoir un **enregistrement** nœud à un nœud d’élément de champ dans le schéma de propriété, mais uniquement si le **le Type de contenu** propriété de la **enregistrement** nœud a la valeur  **SimpleContent**.  
  
 Pour supprimer un nœud de l’ensemble des propriétés promues en tant que champs distinctifs, sélectionnez la propriété promue dans le **champs distinctifs** onglet, puis cliquez sur **supprimer**.  
  
 Lorsque vous assurez la promotion de propriétés à l'aide du mécanisme des champs distinctifs, un fragment de langage XSD (XML Schema Definition) est ajouté dans le sous-élément d'annotation de l'élément racine. Dans l'exemple ci-dessous, le fragment montre deux propriétés promues à l'aide du mécanisme des champs distinctifs.  
  
```  
<b:properties>  
    <b:property distinguished="true"  
        xpath="/*[local-name()='Record' and namespace-  
         uri()='http://BizTalk_Server_Project1.Schema11']/*[local-  
         name()='test']/*[local-name()='Field1']" />  
    <b:property distinguished="true"  
        xpath="/*[local-name()='Record' and namespace-  
         uri()='http://BizTalk_Server_Project1.Schema11']/*[local-  
         name()='test']/*[local-name()='Field5' and position()='1']" />  
</b:properties>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Façons d’utiliser le contenu de Message pour le traitement des messages de contrôle](../core/ways-to-use-message-content-to-control-message-processing.md)   
 [Comment copier des données dans le contexte du Message en tant que champs distinctifs](../core/how-to-copy-data-to-the-message-context-as-distinguished-fields.md)