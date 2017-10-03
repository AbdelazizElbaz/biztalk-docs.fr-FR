---
title: "Comment créer un mappage sans mappages | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 520ec44f-5aca-4271-8835-b8e784214061
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 81be2591c1d8f20f5b8dd01cf01c03e8daed9c9e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-map-without-maps"></a>Création d'un mappage sans mappages
Si vous disposez du code XSLT que vous avez utilisé pour convertir les messages d'instance, vous pouvez vous en servir directement au lieu de créer un mappage.  
  
 À l’aide de votre code XSLT implique la création d’un mappage vide et en définissant son **chemin du XSLT personnalisé** propriété de grille. Si votre code XSLT utilise des assemblys .NET externes, vous devez également créer un fichier XML avec extensions personnalisées. Pour plus d’informations sur la structure d’un fichier XML avec extensions personnalisées, consultez la **XML avec extensions personnalisées (propriété de grille)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## <a name="use-custom-xslt-code-in-place-of-a-map"></a>Utiliser du code XSLT personnalisé à la place d’une carte  
  
1.  Créez un mappage BizTalk vide dans votre projet et configurez les schémas source et de destination.  
  
     Pour plus d’informations sur la création de la carte et de configuration de schémas, consultez [création de mappages](../core/creating-maps.md).  
  
2.  Dans la vue Grille, cliquez sur la grille du Mappeur.  
  
     La fenêtre Propriétés affiche les **grille** propriétés.  
  
3.  Dans la fenêtre Propriétés, sélectionnez **chemin du XSLT personnalisé** et cliquez sur le bouton de sélection (**...** ) bouton.  
  
4.  Dans le **ouvrir** boîte de dialogue zone, accédez au fichier, puis cliquez sur **ouvrir**.  
  
     Le **chemin du XSLT personnalisé** est définie.  
  
> [!NOTE]
>  Le Mappeur BizTalk ne prend en charge que XSLT 1.0. Il ne prend pas en charge XSLT 2.0.  
  
## <a name="see-also"></a>Voir aussi  
 [À propos des mappages](../core/about-maps.md)   
 [Écriture de scripts utilisant Inline XSLT et modèles d’appel XSLT](../core/scripting-using-inline-xslt-and-xslt-call-templates.md)   
 [XSLT personnalisé](../core/custom-xslt.md)   