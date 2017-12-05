---
title: "Schémas XML | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1ec364e7-866d-4164-be91-be75a40ce878
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86760d50b729419f31ba8186033181e0d03ad14c
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="xml-schemas"></a>Schémas XML
Un schéma XML décrit un document professionnel représenté au format XML. Étant donné que Microsoft BizTalk Server utilise XML comme représentation canonique des documents d’entreprise, les documents entrants et sortants ne nécessitent pas de traduction. Les schémas XML peuvent être créés dans l’Éditeur BizTalk uniquement à partir de l’ensemble de propriétés de base disponible dans tous les schémas et ne nécessitent l’activation d’aucune extension d'éditeur de schéma.  
  
 Il existe plusieurs façons dans laquelle vous pouvez créer des schémas XML dans BizTalk Server. notamment :  
  
-   **Création d’un schéma**. cette méthode de création de schéma implique l'ajout d'un nouveau schéma à un projet BizTalk. Dans **l’Explorateur de solutions**, cliquez sur le projet BizTalk, cliquez sur **ajouter**, cliquez sur **un nouvel élément**, puis cliquez sur **schéma**. Élaborez la structure du schéma en ajoutant différents nœuds dans l'arborescence de schéma.  
  
-   **Création d’un schéma, conjointement avec d’autres schémas**. dans le cas de schémas complexes concrets, vous préférerez certainement créer les schémas de vos messages à partir des types proposés dans les autres schémas existants. Les concepts d’importation, d’intégration et de redéfinition de schémas du langage XSD (XML Schema definition) vous permettent de bénéficier des types déjà définis dans d'autres schémas. Pour plus d’informations sur l’utilisation conjointe de plusieurs schémas, consultez [schémas utilisant d’autres schémas](../core/schemas-that-use-other-schemas.md).  
  
-   **Génération d’un schéma à partir d’un message d’instance**. vous pouvez générer un schéma XML correspondant à un message d'instance particulier tant que le format XML de ce message d'instance est correct. Utilisez le **ajouter les éléments générés -  *\<nom du projet BizTalk\>***  boîte de dialogue, accédé en cliquant sur **ajouter les éléments générés** sur la **Projet** menu pour effectuer ce type d’opération de génération de schéma.  
  
    > [!NOTE]
    >  Ce type d'opération ne peut être utilisé que pour générer des schémas XML, et non pour des schémas de propriété ou des schémas de fichier plat.  
  
-   **Migration d’un schéma en langage XSD à partir d’un langage de spécification de schéma plus anciens**. Vous pouvez générer un schéma XML pour BizTalk Server à partir d’un schéma qui a été développé à l’aide d’une version précédente de BizTalk Server, qui a stocké des schémas dans le format du XML-Data Reduced (XDR). Pour plus d’informations sur la migration d’anciens schémas XDR vers le format XSD utilisé par BizTalk Server, consultez [Migration de schéma à partir de Versions précédentes de BizTalk Server](../core/schema-migration-from-previous-versions-of-biztalk-server.md).  
  
     Vous pouvez également générer un schéma XML basé sur XSD à partir d'un schéma de document exprimé à l’aide de la syntaxe de définition de type de document (DTD).  
  
     Utilisez le **ajouter les éléments générés -  *\<nom du projet BizTalk\>***  boîte de dialogue, accédé en cliquant sur **ajouter les éléments générés** sur la **Projet** menu pour effectuer ce type d’opération de génération de schéma.  
  
    > [!NOTE]
    >  Ces types d'opération de génération ne peuvent être utilisés que pour générer des schémas XML, et non pour générer des schémas de propriété ou des schémas de fichier plat.  
  
 Quelle que soit la technique que vous utilisez pour créer des schémas, poursuivez leur modification de sorte qu'ils décrivent le mieux possible les messages d'instance correspondants. Pour commencer à utiliser ces tâches, consultez [la gestion des nœuds dans un schéma](../core/managing-the-nodes-within-a-schema.md), [définition des propriétés de nœud](../core/how-to-set-node-properties.md), et [utilisation des nœuds existants](../core/working-with-existing-nodes.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Différents types de schémas BizTalk](../core/different-types-of-biztalk-schemas.md)