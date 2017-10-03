---
title: "Schémas utilisant d’autres schémas | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02954d46-48ce-4cdf-a012-74c212ce8b6d
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 563260031e545b5223697d49992c1ae85bae3891
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="schemas-that-use-other-schemas"></a>Schémas utilisant d'autres schémas 

## <a name="overview"></a>Vue d'ensemble
Lorsque vos schémas gagnent en taille et en complexité, ou lorsque les schémas représentant vos différents types de messages d’instance comportent plusieurs portions en commun, il peut être utile de combiner des schémas plus petits en des schémas qui définiront la structure finale des messages d'instance que vous prévoyez d'échanger avec des partenaires commerciaux. Par exemple, plusieurs types de messages peuvent nécessiter de comporter une adresse de livraison. Vous pouvez définir la structure d’une adresse de livraison dans un seul schéma, puis utiliser ce schéma au sein d’autres schémas qui définissent par exemple les schémas de message Commande, Facture et Avis d’expédition.  

## <a name="import-include-and-redefine"></a>Importer, inclure et redéfinir.  
 Le langage XSD (XML Schema definition)  propose trois mécanismes associés pour l’utilisation conjointe de plusieurs schémas pris en charge par l’Éditeur BizTalk. Le tableau suivant répertorie les caractéristiques de ces mécanismes, tels qu’ils sont définis par XSD.  
  
|Mécanisme multischéma|Scénario d'utilisation|  
|---------------------------|--------------------|  
|Importer|-Accède et utilise des types définis dans le schéma importé.<br />-Doit utiliser des types dans le schéma importé en l’état, ou déduire de nouveaux types à partir de celles-ci ; aucune modification de type autorisée.<br />: Fournit un mécanisme pour l’utilisation de types définis dans d’autres espaces de noms. En effet, un schéma importé doit être associé à un espace de noms cible différent du schéma importateur.<br />-Utilise le **importer** élément et ses **espace de noms** et **schemaLocation** attributs pour référencer l’autre schéma.|  
|Inclure|-Accède et utilise des types définis dans le schéma inclus.<br />-Doit utiliser des types dans le schéma inclus comme il est, ou déduire de nouveaux types à partir de celles-ci ; aucune modification de type autorisée.<br />-Le schéma inclus doit être dans le même espace de noms cible que le schéma, y compris, ou l’espace de noms cible du schéma inclus doit être vide.<br />-Utilise le **incluent** élément et ses **schemaLocation** attribut pour faire référence à l’autre schéma.|  
|Redéfinir|-Accède et utilise des types définis dans le schéma redéfini.<br />-Peuvent utiliser des types dans le schéma redéfini en l’état, déduire de nouveaux types à partir de celles-ci, ou spécifier les modifications.<br />-Le schéma redéfini doit se trouver dans le même espace de noms cible que le schéma redéfini, ou l’espace de noms cible du schéma redéfini doit être vide.<br />-Utilise le **redéfinir** élément et ses **schemaLocation** attribut pour faire référence à l’autre schéma. Toutes les redéfinitions sont spécifiées avec la **redéfinir** élément. **Remarque :** à l’aide du mécanisme de redéfinition est un concept XSD avancé et doit être utilisée uniquement après avoir suffisamment comprendre comment et quand il doit être utilisé.|  
  
> [!NOTE]
>  Pour plus d’informations sur les différences et les ressemblances entre l’importation, inclure et redéfinir les mécanismes, consultez les références listées dans [ressources XSD sur le Web](../core/xsd-resources-on-the-web.md).  

## <a name="important-details"></a>Obtenir des informations importantes  
 Pour utiliser un type défini dans un schéma (Schema1) à l'intérieur d'un autre schéma (Schema2), vous devez fournir une référence à Schema1 dans Schema2. Pour ce faire, utilisez le **importations** propriété de la **schéma** nœud dans Schema2. Lorsque vous cliquez sur le bouton de sélection (**...** ) situé dans le **importations** champ de propriété, le **importations** boîte de dialogue s’ouvre. Dans le **importer le nouveau schéma en tant que** la liste déroulante, sélectionnez **XSD : importer**, **XSD : inclure**, ou **XSD : redéfinir**. Puis cliquez sur **ajouter** pour ouvrir le **sélecteur de Type BizTalk** boîte de dialogue et parcourez votre projet BizTalk pour sélectionner **Schema1**.  
  
 Pour obtenir des instructions détaillées sur ces étapes, consultez [création de schémas utilisant d’autres schémas](../core/how-to-create-schemas-that-use-other-schemas.md).  
  
 Lorsque vous utilisez la **importations** boîte de dialogue pour importer, inclure ou redéfinir un autre schéma, une ou plusieurs des éléments XSD **importer**, **incluent**, et **redéfinir**  est ajouté à la représentation XSD de votre schéma, y compris les attributs appropriés et les valeurs d’attribut. En outre, dans le cas de la **importer** , une déclaration de préfixe pour l’espace de noms de l’autre schéma est ajoutée à la **schéma** élément.  
  
 Tous les types globaux (tels que **ComplexTypes**, **SimpleTypes**, groupes d’éléments, des groupes d’attributs) dans un schéma importé/inclus/redéfini sont automatiquement disponibles pour une utilisation dans le schéma dans lequel la ancien schéma est importé, inclus ou redéfini. Par exemple, global **ComplexTypes** définie dans un schéma importé/inclus/redéfini sont ajoutés à la liste déroulante de la **Data Structure Type** propriété pour tous le **enregistrement** nœuds dans le schéma d’importation, inclut ou redéfinit. Plus de détails sur cette propriété [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## <a name="see-also"></a>Voir aussi  
 [À propos des schémas](../core/about-schemas.md)   
 [Création de schémas utilisant d’autres schémas](../core/how-to-create-schemas-that-use-other-schemas.md)   
 [Créer des références à un autre nœud ou Type](../core/how-to-create-references-to-another-node-or-type.md)