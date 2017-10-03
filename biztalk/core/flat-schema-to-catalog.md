---
title: "Plats schéma au catalogue | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0e37afa-2329-4691-9fa1-82b8c7bcd59a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f3a45ad66ca10ab829a4cc7279891487124c3cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="flat-schema-to-catalog"></a>Conversion d'un schéma plat vers un catalogue

## <a name="overview"></a>Vue d'ensemble
Vous pouvez utiliser la **bouclage** fonctoid pour convertir un schéma plat en schéma hiérarchique en mappant un enregistrement unique vers plusieurs enregistrements. Il s'agit d'une opération courante lors de la conversion de schémas plats vers des catalogues Microsoft Commerce Server.  
  
 Le code suivant représente une partie d'un catalogue listant des variantes d'un produit dont chacune constitue un enregistrement.  
  
```  
<ns0:Root xmlns:ns0="http://ValueMappingFlattening.FlatCatalog">  
    <ProductVariant ListPrice="99.99" ID="45-01" Material="Leather" Color="Black" />  
    <ProductVariant ListPrice="69.99" ID="45-02" Material="Vinyl" Color="Brown" />  
</ns0:Root>  
```  
  
 Développement de cette portion du catalogue convertirait tout ou partie de la **ProductVariant** attributs dans des enregistrements.  
  
```  
<ns0:Root xmlns:ns0="http://ValueMappingFlattening.Catalog">  
    <ProductVariant ListPrice="99.99" ID="45-01">  
        <Feature Name="Material" Value="Leather"/>  
        <Feature Name="Color" Value="Black"/>  
    </ProductVariant>  
    <ProductVariant ListPrice="69.99" ID="45-02">  
        <Feature Name="Material" Value="Vinyl"/>  
        <Feature Name="Color" Value="Brown"/>  
    </ProductVariant>  
</ns0:Root>  
```  
  
 La figure suivante présente un mappage qui réalise cette conversion.  
  
 ![Mappage illustrant l’utilisation du fonctoid Bouclage. ] (../core/media/loopingflattenfunctoid.gif "loopingflattenfunctoid")  
Fonctoid Bouclage, mappage d'un schéma plat  

## <a name="set-the-schema"></a>Définissez le schéma  
 Pour que ce type de mappage fonctionne correctement, vous devez effectuer les opérations suivantes :  
  
-   Pour chaque lien de connexion à la **nom** champ du schéma de destination, définissez des propriétés des liaisons pour copier le nom du schéma source. Pour plus d’informations, consultez [configuration des liens](../core/configuring-links.md). Consultez également **propriétés des liaisons** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
-   Pour chaque lien de connexion à la **valeur** champ du schéma de destination, définissez le schéma de la source des propriétés de liaison pour copier la valeur (valeur par défaut).  
  
-   Pour la liaison connectant le **bouclage** fonctoid à l’enregistrement **fonctionnalité** dans le schéma de destination, définissez le schéma de destination propriétés des liaisons pour faire correspondre les liaisons de haut en bas.  
  
 Pour l’inverse de ce mappage, la conversion d’un schéma de catalogue à un schéma plat, consultez [Value Mapping (Flattening) Functoid](../core/value-mapping-flattening-functoid.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment ajouter des fonctoids à une carte de bouclage](../core/how-to-add-looping-functoids-to-a-map.md)   
 [Fonctoid Bouclage](../core/looping-functoid.md)   
 [(Mise à plat) fonctoid Mappage](../core/value-mapping-flattening-functoid.md)