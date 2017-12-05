---
title: Index fonctoid | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Max Occurs property
- Index functoids, about Index functoids
- Index functoids
ms.assetid: 0c8ba427-881c-4b1f-92b9-61992d2a29df
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a22881e7694fee872b7820b8b99157ef2cf20170
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="index-functoid"></a>Fonctoid Index
Le **Index** fonctoid vous permet de sélectionner des informations à partir d’un enregistrement spécifique dans une série d’enregistrements. Chaque **Index** fonctoid collecte des informations à partir d’un champ unique.  
  
 Certains enregistrements apparaissent généralement plusieurs fois dans un fichier d'entrée. Par exemple, dans un bulletin météorologique, le **DailySummary** élément peut se produire plusieurs fois. Le **DailySummary** élément peut contenir des attributs pour la température, la pression atmosphérique et la vitesse du vent. Le code suivant correspond à un exemple de bulletin météorologique :  
  
```  
<ns0:WeatherReport xmlns:ns0="http://IndexFunctoid.WeatherReport">  
    <DailySummary Pressure="80" Windspeed="10" Temperature="20" />  
    <DailySummary Pressure="78" Windspeed="20" Temperature="23" />  
    <DailySummary Pressure="77" Windspeed="16" Temperature="24" />  
</ns0:WeatherReport>  
```  
  
 Dans le schéma sous-jacent, le **Max Occurs** propriété pour le **DailySummary** enregistrement est défini sur non lié pour indiquer l’enregistrement de boucle ou d’un abonnement. Le Mappeur BizTalk compile cet enregistrement en tant que boucle.  
  
 Supposons que vous souhaitez collecter des informations météorologiques pour les deux premières **DailySummary** enregistrements du bulletin météorologique. Dans le Mappeur BizTalk, chaque attribut de la **DailySummary** enregistrement du schéma source entrant peut être connecté à un **Index** fonctoid. Ensuite, chaque **Index** fonctoid peut spécifier le **DailySummary** enregistrement à partir de laquelle les informations : la première ou deuxième. Le **Index** fonctoids peuvent être liés aux champs appropriés du schéma de destination.  
  
 L’illustration suivante montre **Index** fonctoids utilisés de cette manière.  
  
 ![](../core/media/ebiz-prog-map-index.gif "ebiz_prog_map_index")  
Exemple de fonctoid Index  
  
 Pour obtenir un résumé quotidien des informations pour le premier jour, la limite supérieure définie de trois **Index** fonctoids ont leurs valeurs d’index définis sur 1. Pour obtenir les informations de résumé quotidiennes pour le deuxième jour, la limite inférieure définie de trois **Index** fonctoids ont leurs valeurs d’index définis sur 2.  
  
 **Index** fonctoids utilisent la **configurer \<fonctoid\> fonctoid** boîte de dialogue pour définir les paramètres d’entrée. Le premier paramètre d'entrée indique un champ au sein d'un enregistrement de boucle dans le schéma source. Le deuxième paramètre ainsi que les suivants précisent l'enregistrement particulier. Vous pouvez spécifier plusieurs valeurs d’index pour sélectionner un enregistrement au sein de structures répétées imbriquées. La valeur d’index pour la structure la plus profonde correspond au deuxième paramètre. La valeur d’index de la structure la plus externe correspond au troisième paramètre, et ainsi de suite. Par exemple, supposons que l’exemple précédent **DailySummary** d’enregistrements qui étaient à l’intérieur de **WeeklyData** enregistrements. Pour récupérer le **pression** à partir de la première **DailySummary** dans la seconde **WeeklyData**, le deuxième paramètre est 1, et le troisième paramètre serait 2.  
  
 Notez que cet exemple suppose la **pression** champ ne se répète pas. Si le champ se répétait, les index seraient désactivés : le compte démarrerait avec le **pression** champ, plutôt que la **résumé quotidien**.  
  
> [!NOTE]
>  Même si un paramètre d’entrée de séquence d’index est généralement constant, il est possible d’utiliser un lien provenant d’un nœud dans le schéma source. Si le lien vient d’un enregistrement de boucle qui n’est pas un parent du premier paramètre d’entrée, la valeur d’entrée de la séquence d’index vient de la première instance du nœud dans le message d'instance d'entrée.  
  
> [!NOTE]
>  La valeur de l’entrée de séquence d’index est toujours en rapport avec le contexte actuel du document source.  
  
> [!IMPORTANT]
>  Un **Index** fonctoid doivent être aussi grand nombre de valeurs d’index qu’il existe des nœuds parents du niveau du champ jusqu’au premier niveau sous le nœud racine. Par exemple, dans le message d’instance du bulletin météorologique multiple, deux valeurs d'index sont nécessaires. Dans le message d’instance du bulletin météorologique unique, une seule valeur d'index est nécessaire. Impossible de définir le nombre requis de valeurs d’index d’un **Index** fonctoid crée une sortie basée sur le premier nœud dans le message d’instance source qui correspond au premier paramètre d’entrée de la **Index** fonctoid.  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout de fonctoids Index à une carte](../core/how-to-add-index-functoids-to-a-map.md)   
 [Fonctoids avancés](../core/advanced-functoids.md)   
 [Fonctoid Itération](../core/iteration-functoid.md)   
 [Fonctoid Nombre d’enregistrements](../core/record-count-functoid.md)