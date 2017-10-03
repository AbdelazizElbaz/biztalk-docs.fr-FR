---
title: "Comment définir des alertes de Dimension numérique de Out-of-Range dans les Installations Non anglaises | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f1e0373-eadf-4c6d-9a38-a34d847f310f
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea63008680c026eded843e32a7b2c6ff26dc0bf0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-define-out-of-range-numeric-dimension-alerts-in-non-english-installations"></a>Définition d'alertes de dimension numérique hors limite dans les installations non anglaises
Lorsque vous définissez des alertes qui incluent une condition pour une valeur qui se trouve en dehors de la dimension de plage numérique définie sur les installations non anglaises, vous devez modifier manuellement la définition BAM avec la version localisée de la chaîne **hors limites**.  
  
 Le tableau suivant répertorie des exemples de valeurs hors limites traduites.  
  
|Code langue|Chaîne traduite|  
|-------------------|----------------------|  
|CN|超出范围|  
|DE|Außerhalb des gültigen Bereichs|  
|ES|Fuera de rango|  
|FR|hors limites|  
|IT|Fuori intervallo|  
|JA|範囲外|  
|KO|범위를 벗어남|  
|TW|超過範圍|  
  
### <a name="to-define-out-of-range-alerts-in-non-english-installations"></a>Pour définir des alertes de dimension numérique hors limites dans les installations non anglaises  
  
1.  Accédez au dossier contenant le fichier .xml de définition d'analyse BAM.  
  
2.  À l'aide d'un éditeur de texte ou d'un éditeur XML, ouvrez le fichier de définition d'analyse BAM.  
  
3.  Repérez la dimension de découpage pour la dimension numérique. Par exemple, si votre dimension de découpage est nommée **Alerts_NumDim**, recherchez le nœud suivant :  
  
    ```  
    <SlicerDimension Name="Alerts_NumDim">  
    <Level Name="(Out of Range)" />  
    </SlicerDimension>  
    ```  
  
4.  Modifier la **hors plage** chaîne localisée de valeur de chaîne approprié.  
  
5.  Enregistrez le fichier et déployez la définition.  
  
## <a name="see-also"></a>Voir aussi  
 [Qu’est un schéma de définition BAM ?](../core/what-is-a-bam-definition-schema.md)   
 [Comment déployer des définitions BAM](../core/how-to-deploy-bam-definitions.md)