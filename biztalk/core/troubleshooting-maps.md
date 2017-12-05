---
title: "Résolution des problèmes de mappages | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 32e2eb52-6740-4cf5-82ec-3b6d0b784276
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7bb7b3dc8356172989c215dc13e5fd82e46f4689
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="troubleshooting-maps"></a>Dépannage de problèmes liés aux cartes
Cette rubrique présente des stratégies de dépannage et des informations permettant de résoudre les problèmes liés aux mappages.  
  
## <a name="troubleshooting-strategies"></a>Stratégies de résolution de problèmes  
  
### <a name="validate-your-map"></a>Validation du mappage  
 Cela peut paraître évident, mais vous devez toujours valider votre mappage à différents stades de son développement. Cette opération vous aide ainsi à identifier dès le début du cycle de développement tout problème de schéma, logique ou conception, vous permettant ainsi de le résoudre rapidement.  
  
##### <a name="to-validate-a-biztalk-map"></a>Pour valider un mappage BizTalk  
  
1.  Dans l'Explorateur de solutions, ouvrez le mappage que vous souhaitez valider.  
  
2.  Dans l’Explorateur de solutions, cliquez sur la carte, puis cliquez sur **valider le mappage**.  
  
3.  Vérifiez les résultats dans la fenêtre Sortie.  
  
> [!NOTE]
>  Quand vous validez un mappage, le système ne vérifie pas si les données d'instance du test violent des types de données définis dans les schémas. Cette vérification a lieu quand vous testez le mappage ou que vous validez les données d'instance dans l'Éditeur BizTalk.  
  
### <a name="review-the-xslt-generated-for-your-map"></a>Révision du fichier XSLT généré pour le mappage  
 Il est souvent utile de contrôler le fichier XSLT généré par le compilateur de mappage. L'inspection du fichier XSLT présente notamment les avantages suivants :  
  
-   Si vous utilisez le bouclage ou des fonctoids personnalisés, vous comprendrez mieux la manière dont le bouclage est exécuté ou dont le fonctoid personnalisé est appelé.  
  
-   Si vous avez un mappage complexe, examen du fichier XSLT vous permettra de voir comment le mappage est traduit en une transformation et peut-être vous donner une sur la façon de mieux structurer, remplacer ou rationaliser une ou plusieurs parties.  
  
-   Si vous utilisez des scripts personnalisés ou tout autre artefact, l'examen du fichier XSLT vous permettra de mieux comprendre l'interaction entre les scripts, les artefacts et les autres parties du mappage.  
  
 Par ailleurs, la révision du fichier XSLT d'un mappage est une opération facile.  
  
##### <a name="to-view-the-xslt-generated-by-the-map-compiler"></a>Pour afficher le fichier XSLT généré par le compilateur de mappage  
  
1.  À partir d’un [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projet BizTalk, cliquez sur le **l’Explorateur de solutions** onglet, cliquez sur une carte, puis cliquez sur **valider le mappage**.  
  
2.  Faites défiler la fenêtre Sortie pour rechercher l'URL du fichier XSL. Appuyez sur CTRL et cliquez sur l'URL pour afficher le fichier.  
  
 Si vous décidez de personnaliser manuellement votre mappage, vous pouvez modifier la version générée par le compilateur de mappage. Les modifications ne seront pas répercutées par le mappeur et seront perdues la prochaine fois que vous construirez votre solution.  
  
### <a name="tune-your-map-for-specific-scenarios-using-mapsource"></a>Paramétrage du mappage pour des scénarios spécifiques à l’aide de \<mapsource\>  
 Vous pouvez modifier certains comportements par défaut du Mappeur en modifiant les attributs de la **mapsource** élément directement dans un fichier source (.btm) de mappage. Vous pouvez ainsi modifier trois comportements :  
  
-   **Optimiser la génération du code de fonctoid Mappage des valeurs**. vous pouvez modifier le comportement qui gère l'utilisation d'une variable avec les instructions `if`.  
  
-   **Prendre en charge les schémas de grande taille**. vous pouvez modifier la façon dont sont utilisés les nœuds internes du compilateur dans les grands mappages.  
  
-   **Gérer la syntaxe for-each avec les fonctoids bouclage, conditionnel et mappage des valeurs**. vous pouvez contrôler l'utilisation de l'instruction `xsl:for-each` dans le schéma de destination.  
  
 Pour plus d’informations sur la modification **mapsource**, consultez [la gestion par défaut du Mappeur comportement à l’aide de \<mapsource\>](../core/managing-default-mapper-behavior-using-mapsource.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Résolution des problèmes de Questions et réponses de général](../core/general-troubleshooting-questions-and-answers.md)   
 [Erreurs fréquentes](../core/common-errors.md)