---
title: Comment lier automatiquement des enregistrements | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc2926c7-07c2-45d1-afde-d3f894f6b88d
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc5ab4e18a291321247655101d32d2bf7e35ff92
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-link-records-automatically"></a>Création automatique de liens d’enregistrements
Le Mappeur BizTalk vous offre une assistance juste-à-temps, via un menu contextuel, lorsque vous créez des liens entre deux éléments d'enregistrement des schémas source et de destination. Cette rubrique fournit des informations sur l'utilisation du menu contextuel pour effectuer les opérations de liaison.  
  
 Vous pouvez créer des liens enregistrement à enregistrement automatiquement de l'une des manières suivantes :  
  
-   **Lien direct.** À l'aide de cette technique, le Mappeur BizTalk lie l'enregistrement du schéma source à l'enregistrement sélectionné dans le schéma de destination.  
  
-   **Lien par Structure.** À l’aide de cette technique, le Mappeur BizTalk tente de faire correspondre le **enregistrement** et **champ** nœuds au sein de la **enregistrement** nœuds liés en fonction de la structure de ces **Enregistrement** nœuds, quels que soient les noms des nœuds correspondants au sein de ces structures.  
  
-   **Lien par nom.** À l’aide de cette technique, le Mappeur BizTalk tente de faire correspondre le **enregistrement** et **champ** nœuds au sein de la **enregistrement** nœuds liés en fonction des noms de la correspondant au sein des nœuds, quelle que soit leur structure, le **enregistrement** nœuds liés.  
  
-   **Copie de masse.** Le **copie de masse** fonctoid permet d’utiliser les schémas incluant vos mappages **tout** et **anyAttribute** éléments. Pour plus d’informations sur les fonctoids du Mappeur BizTalk, voir [à l’aide des fonctoids pour créer des mappages plus complexes](../core/using-functoids-to-create-more-complex-mappings.md).  
  
 Pour utiliser le menu contextuel, un lien doit provenir d'un nœud parent de la sous-hiérarchie et rejoindre un autre nœud parent de la sous-hiérarchie. Le menu contextuel aide à choisir le type de lien à créer entre les deux nœuds de schéma. Voici une liste des options disponibles dans le menu contextuel.  
  
|Mapper à partir de|Mapper à|Comportement de lien|  
|--------------|------------|-------------------|  
|Champ|Champ|Lien direct|  
|Record|Champ|Lien direct|  
|Champ|Record|Lien direct|  
|Record|Record|Le menu contextuel s'affiche.|  
  
## <a name="prerequisites"></a>Conditions préalables  
 Ces opérations requièrent l'exécution du Mappeur BizTalk.  
  
### <a name="to-link-the-record-elements-directly"></a>Pour lier directement les éléments d'enregistrement  
  
1.  Faites glisser la souris d'un nœud parent de la sous-hiérarchie dans le schéma source vers le nœud parent de la sous-hiérarchie dans le schéma de destination.  
  
2.  Dans le menu contextuel, cliquez sur **lien Direct**. La figure suivante illustre un lien direct entre le nœud source sélectionné et le nœud cible.  
  
     ![Lien direct à partir du nœud source vers le nœud cible](../core/media/linkrecordelements-directly.gif "Linkrecordelements_directly")  
  
    > [!IMPORTANT]
    >  Vous pouvez lier directement un nœud parent de la sous-hiérarchie dans le schéma source à un nœud parent n'appartenant pas à la sous-hiérarchie dans le schéma de destination. La figure suivante montre un lien direct entre « Root » qui est un nœud parent dans le schéma source et « Record1 », enfant de « Root » dans le schéma de destination.  
  
     ![Liaison d’éléments d’enregistrement directement](../core/media/linkrecordelements-directly2.gif "Linkrecordelements_directly2")  
  
### <a name="to-link-the-record-elements-by-structure"></a>Pour lier les éléments d'enregistrement par structure  
  
1.  Faites glisser la souris d'un nœud parent de la sous-hiérarchie dans le schéma source vers le nœud parent de la sous-hiérarchie dans le schéma de destination.  
  
2.  Dans le menu contextuel, cliquez sur **lien par Structure**. Le Mappeur BizTalk fait correspondre le **enregistrement** et **champ** nœuds au sein de la **enregistrement** les nœuds liés en fonction de la structure de ces **enregistrement** nœuds, quels que soient les noms des nœuds correspondants au sein de ces structures.  
  
     ![Lier des éléments d’enregistrement &#95; par structure](../core/media/linkrecordelements-bystructure.gif "Linkrecordelements_bystructure")  
  
    > [!IMPORTANT]
    >  Lorsque vous tentez de lier par structure un nœud parent de la sous-hiérarchie dans le schéma source à un nœud parent n'appartenant pas à la sous-hiérarchie dans le schéma de destination, le Mappeur BizTalk mappe les enfants du nœud parent source aux enfants du nœud parent cible, respectivement. La figure suivante illustre la liaison par structure.  
  
     ![Liaison d’éléments d’enregistrement par structure](../core/media/linkrecordelements-bystructure2.gif "Linkrecordelements_bystructure2")  
  
### <a name="to-link-the-record-elements-by-name"></a>Pour lier les éléments d'enregistrement par nom  
  
1.  Faites glisser la souris d'un nœud parent de la sous-hiérarchie dans le schéma source vers le nœud parent de la sous-hiérarchie dans le schéma de destination.  
  
2.  Dans le menu contextuel, cliquez sur **lien par nom**. Le Mappeur BizTalk tente de faire correspondre le **enregistrement** et **champ** nœuds au sein de la **enregistrement** nœuds liés en fonction des noms de nœuds correspondants, quelle que soit de leur structure, à l’intérieur du **enregistrement** auquel vous liez des nœuds.  
  
     ![Liaison d’éléments d’enregistrement par nom](../core/media/linkrecordelements-byname.gif "Linkrecordelements_byname")  
  
    > [!IMPORTANT]
    >  Vous pouvez lier par nom un nœud parent de la sous-hiérarchie dans le schéma source à un nœud parent n'appartenant pas à la sous-hiérarchie dans le schéma de destination. Le Mappeur BizTalk fait correspondre les noms des enfants du nœud source aux enfants du nœud cible. S'il trouve des enfants identiques, un lien est établi entre les enfants respectifs. La figure suivante explique ce concept.  
  
## <a name="to-link-using-a-mass-copy-functoid"></a>Pour effectuer une liaison à l'aide d'un fonctoid Copie de masse  
 Le **copie de masse** fonctoid permet d’utiliser les schémas incluant vos mappages **tout** et **anyAttribute** éléments. Ces éléments sont, par essence, des caractères génériques fournis par le langage de définition du schéma XML pour remplacer des structures ou des attributs non connus.  
  
 En plus de gérer les données dont la structure est inconnue, le **copie de masse** fonctoid vous permet de simplifier le développement du schéma : seules les parties d’un schéma qui seront traités doivent être spécifiées en détail.  
  
 ![Liaison d’éléments d’enregistrement par le fonctoid copie de masse](../core/media/linkrecordelements-masscopyfunctoid.gif "Linkrecordelements_MassCopyfunctoid")  
  
 Pour plus d’informations sur la **copie de masse** fonctoid, consultez [fonctoid copie de masse](../core/mass-copy-functoid.md).  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de liens pour spécifier l’enregistrement et les mappages de champs](../core/using-links-to-specify-record-and-field-mappings.md)   
 [Ajout de fonctoids copie de masse à une carte](../core/how-to-add-mass-copy-functoids-to-a-map.md)