---
title: "Comment remplacer les schémas | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 104e60d3-1303-4e56-b13a-c10ab14ba383
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: df444b8169d75408fe6e412135029ae2b051a6d2
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-replace-schemas"></a>Remplacement de schémas
Il peut arriver que vous souhaitiez remplacer le schéma source ou le schéma de destination dans un mappage existant, par exemple lorsqu'un partenaire commercial vous envoie un schéma mis à jour.  
  
> [!NOTE]
>  Le Mappeur BizTalk tente de gérer tous les liens existant entre le schéma conservé et le schéma remplacé.  
  
## <a name="replace-a-source-or-destination-schema"></a>Remplacer un schéma source ou de destination  
  
1.  Avec le bouton droit de la source ou la destination arborescence du schéma, puis sélectionnez **remplacer le schéma**.  
  
    > [!NOTE]
    >  Vous pouvez également appuyer sur CTRL+M, CTRL+S. Pour obtenir une liste complète des raccourcis du mappeur, consultez [raccourcis clavier de Mappeur BizTalk](../core/biztalk-mapper-keyboard-shortcuts.md).  
  
2.  Dans le **sélecteur de Type BizTalk** boîte de dialogue, développez le **schémas** nœud dans l’arborescence, sélectionnez le schéma approprié, puis **OK**.  
  
     ![Sélectionnez le schéma](../core/media/biztalk-typepicker.gif "BizTalk_TypePicker")  

    > [!TIP] 
    > **En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]** , vous pouvez redimensionner la fenêtre du sélecteur de Type pour afficher le nom complet de votre schéma.
      
     Si seule une racine unique existe dans le schéma de remplacement, ou un nœud racine a été établi pour le schéma de remplacement à l’aide de la **référence de racine** propriété de la **schéma** ouvre de nœud, le schéma de remplacement dans le volet correspondant, et vous ne devrez pas effectuer l’étape 3.  
  
3.  Si plusieurs nœuds racine dans le schéma de destination, et aucun nœud racine n’a été établie pour le schéma de destination à l’aide du **référence de racine** propriété de la **schéma** nœud, dans le  **Nœud racine pour \<* Source/cible* \> schéma ** boîte de dialogue, sélectionnez le nœud racine approprié, puis **OK**.  
  
     Le schéma de remplacement s'ouvre dans le volet correspondant.  
  
    > [!NOTE]
    >  Des liens peuvent être perdus lors du remplacement du schéma si des enregistrements/champs appropriés sont introuvables. Le schéma est remplacé uniquement lorsque vous sélectionnez **Oui** sur la **Confirmation** boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de mappages dans des projets](../core/managing-maps-within-projects.md)