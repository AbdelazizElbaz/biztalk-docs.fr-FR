---
title: Comment copier XPath | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 404599d4-0fb3-4c7c-91e6-1295d9d0965e
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb282c5c32d8da62a9da6d7a9c900c798e44eee7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-copy-xpath"></a>Comment copier XPath
Le langage XSD (XML Schema definition) fournit la syntaxe sous-jacente des schémas de message définis dans BizTalk Server. Bien que les arborescences du Mappeur BizTalk utilisent une hiérarchie graphique propre à BizTalk pour les nœuds d'enregistrement et de champ (entre autres types de nœuds), chacune associée à son propre ensemble de propriétés, de telles hiérarchies sont élaborées et conservées au format XSD.  
  
 Dans les scénarios incluant des mappages complexes et étendus sur plusieurs pages de grille, la localisation du parent d'un nœud de schéma peut être difficile. Le chemin d'accès XSD est utile dans ce cas. Vous pouvez utiliser le chemin d'accès XSD pour obtenir des informations sur la profondeur des nœuds de schéma. Vous pouvez également réutiliser ce chemin d'accès dans une autre page de grille pour identifier la relation.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Les instructions suivantes requièrent que le Mappeur BizTalk est en cours d’exécution.  
  
### <a name="to-copy-the-xsd-path-xpath"></a>Pour copier le chemin XSD (XPath)  
  
1.  Cliquez sur le nœud de schéma pour lequel vous souhaitez que le chemin d’accès XSD, puis cliquez sur **Copier XPath**.  
  
2.  Ouvrez un éditeur de texte. Dans le menu **Edition** , cliquez sur **Coller**. Le chemin d'accès XSD est à présent affiché.  
  
    > [!NOTE]
    >  Vous pouvez également appuyer sur CTRL+V pour coller le chemin d'accès dans un éditeur de texte.  
  
     Le code suivant affiche le chemin XSD du nœud de schéma sélectionné.  
  
    ```  
    /*[local-name()='<Schema>']/*[local-name()='Shipment']/*[local-name()='DataCollection']  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide des fonctionnalités améliorées dans le Mappeur BizTalk](../core/using-enhanced-features-in-biztalk-mapper.md)   
 [Procédure de remplacement des schémas](../core/how-to-replace-schemas.md)   
 [Comment développer et réduire les arborescences de schéma](https://msdn.microsoft.com/library/ee253802(v=bts.10).aspx)