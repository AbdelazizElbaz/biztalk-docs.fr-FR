---
title: "Comment configurer la Validation de la carte et les paramètres de Test | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1768918c-e94f-476f-b288-9e030c691177
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f691a58ece178ee00ce983e400e5420ef54fafdf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-map-validation-and-test-parameters"></a>Comment configurer la Validation de la carte et les paramètres de Test
Avant de valider et tester un mappage, vous devez définir les paramètres de validation et de test le **propriétés** fenêtre de la carte.  
  
## <a name="configure-the-map-validation-and-test-parameters"></a>Configurer les paramètres de validation et de test du mappage  
  
1.  Dans l’Explorateur de solutions, cliquez sur la carte dont vous souhaitez configurer, puis cliquez sur les pages de propriété **propriétés**.  
  
2.  Dans la fenêtre Propriétés, procédez comme suit.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Valider l’entrée TestMap**|Déterminer s'il faut valider le message d’instance par rapport au schéma source avant de tester le mappage.|  
    |**Valider la sortie TestMap**|Déterminer s'il faut valider le message d’instance par rapport au schéma de destination après le test du mappage.|  
    |**Instance d’entrée TestMap**|Configurer l'emplacement des données du message d'instance à utiliser lors du test du mappage.<br /><br /> Si vous configurez cette propriété, vous devez également configurer le **entrée TestMap** propriété.|  
    |**Instance de sortie TestMap**|Configurez l'emplacement du fichier où vous souhaitez enregistrer le résultat de l'opération Test Map.<br /><br /> Si vous configurez cette propriété, vous devez également configurer le **sortie TestMap** propriété.|  
    |**Entrée TestMap**|Configurer le format de données de l'instance d'entrée.|  
    |**Sortie TestMap**|Configurer le type de données de sortie à utiliser lors du test du mappage.|  
  
    > [!IMPORTANT]
    >  Pour tester votre mappage, vous devez d'abord configurer les pages de propriétés du mappage.  

L'une des étapes qui suit le développement d'un mappage est celle de la validation. Cette rubrique contient des instructions détaillées concernant la validation des mappages.  
  
## <a name="validate-a-biztalk-map"></a>Valider un mappage BizTalk  
  
1.  Dans l'Explorateur de solutions, ouvrez le mappage que vous souhaitez valider.  
  
2.  Dans l’Explorateur de solutions, cliquez sur la carte, puis **valider le mappage**.  
  
3.  Dans le **sortie** fenêtre, vérifier les résultats.  
  
> [!IMPORTANT]
>  Si vous utilisez des données personnalisées ou des constantes dans votre sortie, vous devez vérifier que les types de vos données de test sources et les valeurs des constantes cibles sont valides. Lorsque vous validez un mappage, le Mappeur BizTalk ne vérifie pas si les données d'instance violent des types de données définis dans les schémas. Cela lorsque vous testez le mappage ou validez les données d’instance avec l’Éditeur BizTalk. 

## <a name="test-a-biztalk-map"></a>Tester un mappage BizTalk

L'étape qui suit le développement d'un mappage est celle du test. Cette rubrique contient des instructions détaillées relatives au test des mappages, notamment la procédure à effectuer pour afficher le fichier XSLT généré par le compilateur de mappage.  
  
1.  Dans l’Explorateur de solutions, cliquez sur la carte que vous souhaitez tester, puis sélectionnez **tester le mappage**.  
  
2.  Vérifier les résultats dans le **sortie** fenêtre.  
  
    > [!IMPORTANT]
    >  Avant de tester un mappage, il est recommandé de configurer les propriétés d'instance d'entrée et de sortie dans la fenêtre Propriétés.  
  
## <a name="review-the-xslt"></a>Passez en revue le fichier XSLT  
 Il est souvent utile de contrôler le fichier XSLT généré par le compilateur de mappage. L'inspection du fichier XSLT présente notamment les avantages suivants :  
  
-   Si vous utilisez le bouclage ou des fonctoids personnalisés, vous comprendrez mieux la manière dont le bouclage est exécuté ou dont le fonctoid personnalisé est appelé.  
  
-   Si vous avez un mappage complexe, examen du fichier XSLT vous permettra de voir comment le mappage est traduit en une transformation et peut-être vous donner une comment mieux structurer, remplacer ou rationaliser une ou plusieurs parties.  
  
-   Si vous utilisez des scripts personnalisés ou tout autre artefact, l'examen du fichier XSLT vous permettra de mieux comprendre l'interaction entre les scripts, les artefacts et les autres parties du mappage.  
  
 En d'autres termes, l'examen du fichier XSLT constitue un moyen remarquable pour déboguer un mappage.  
  
#### <a name="view-the-xslt-generated-by-the-map-compiler"></a>Afficher le XSLT généré par le compilateur de mappage  
  
1.  À partir d’un projet BizTalk Visual Studio, sélectionnez le **l’Explorateur de solutions** onglet, cliquez sur une carte, puis sélectionnez **valider le mappage**.  
  
2.  Faites défiler la fenêtre Sortie pour rechercher l'URL du fichier XSL. Appuyez sur **CTRL**, puis sélectionnez l’URL pour afficher le fichier.  
  
> [!NOTE]
>  Les modifications apportées au fichier XSL ne sont pas répercutées dans le mappage et sont écrasées lors de la génération suivante.  
  
## <a name="see-also"></a>Voir aussi  

[Comment déboguer des mappages](../core/how-to-debug-maps.md)  
[Résolution des problèmes de mappages](../core/troubleshooting-maps.md)  