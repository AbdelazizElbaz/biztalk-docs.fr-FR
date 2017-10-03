---
title: "Phase de désassemblage (traitement des échanges récupérables) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 552b1e90-f75d-4713-8c7b-155a52819308
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f36dd7a9d8bb10180d4af0562ba1e869957415d8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="disassembly-stage-recoverable-interchange-processing"></a>phase de désassemblage (Traitement des échanges récupérables)
Les échanges sont traités dans la phase de désassemblage selon deux modes :  
  
-   **En mode standard.** lorsque le composant désassembleur d'un pipeline de réception est configuré pour effectuer le désassemblage standard, les messages que contient un échange sont extraits, traités par le pipeline de réception, mappés et publiés sous la forme d'une unité transactionnelle de travail. C'est-à-dire que soit l'ensemble de l'échange et les messages qu'il contient sont entièrement traités et publiés dans la base de données MessageBox, soit l'échange est placé dans la file d'attente des messages interrompus.  
  
-   **Mode récupérable.** Lorsque le composant désassembleur d’un pipeline de réception est configuré pour effectuer **le traitement des échanges récupérables**, les messages contenus dans un échange sont extraits indépendamment les uns des autres. Les messages dont l'extraction réussit sont propagés plus bas dans le pipeline de réception. Les messages identifiés dans un échange mais dont l'extraction ne s'est pas déroulée correctement sont placés dans la file d'attente des messages interrompus.  
  
## <a name="examples"></a>Exemples  
 Les exemples ci-dessous illustrent des scénarios de traitement des échanges.  
  
### <a name="example-1"></a>Exemple 1  
 Dans cet exemple, le pseudo-échange suivant est soumis sur un emplacement de réception d'échanges standard. C'est-à-dire que le composant désassembleur dans le pipeline de réception est configuré pour le traitement des échanges standard.  
  
```  
<Interchange>  
<Document1>...</Document1>  
<Document2 failure=”routing”>...</Document2>  
<Document3>...</Document3>  
<Document4 failure=”pipeline” recoverableError=”true”>...</Document4>  
<Document5>...</Document5>  
</Interchange>  
```  
  
 Cet échange contient cinq messages tous correctement extraits par le désassembleur à partir de l'échange. Ils sont traités comme suit :  
  
-   Le premier, le deuxième et le troisième messages se propagent à travers le pipeline et sont prêts à être publiés.  
  
-   Le traitement du quatrième message échoue lors de la phase de désassemblage dans le pipeline. Tous les messages qui ont déjà été traités sont alors annulés et le message d'échange d'origine est suspendu et peut être repris.  
  
 Le résultat de l'envoi est le suivant :  
  
-   Rien n'est publié. L'échange d'origine est suspendu car, dans le traitement des échanges standard, tout message extrait qui échoue à n'importe quel moment, pendant ou après le traitement des échanges, entraîne la suppression de tous les messages extraits et le placement de l'échange d'origine dans la file d'attente des messages interrompus pour être repris.  
  
### <a name="example-2"></a>Exemple 2  
 Cet exemple utilise le même scénario de traitement et de propagation des échanges que l'exemple précédent sauf que la phase de désassemblage est configurée pour effectuer le traitement des échanges récupérables.  
  
 Le résultat de l'envoi est que chacun des messages extraits est traité et que l'échange d'origine est supprimé. Les messages sont traités de la manière suivante :  
  
-   Le premier, le deuxième et le troisième messages se propagent à travers le pipeline et sont prêts à être publiés.  
  
-   Le quatrième message subit un échec lors du traitement de désassemblage (autrement dit, son extraction est suivie d'un problème) et est prêt à être suspendu.  
  
-   Le cinquième message se propage à travers le pipeline et est prêt à être publié.  
  
-   Une fois que tous les messages ont été extraits de l'échange, les messages 1, 2, 3 et 5 sont publiés dans la base de données MessageBox et le message 4 est placé dans la file d'attente des messages interrompus. Le message 2 est également redirigé vers la file d'attente des messages interrompus en raison d'un échec de routage dû à un abonné non correspondant.  
  
## <a name="configuring-recoverable-interchange-processing"></a>Configuration du traitement des échanges récupérables  
 Le traitement des échanges récupérables est une propriété du composant désassembleur d'un pipeline de réception. Tous les composants désassembleur ne permettent pas de spécifier le traitement des échanges récupérables. Ce n'est par exemple pas le cas du Désassembleur BizTalk Framework natif. Si un désassembleur prend en charge le traitement des échanges récupérables, vous spécifiez ce comportement dans le Concepteur de pipeline dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] lorsque vous ajoutez le composant désassembleur à la phase de désassemblage du pipeline en cours de conception. Après avoir fait glisser le désassembleur sélectionné sur la phase de désassemblage du pipeline, vous définissez la propriété de traitement des échanges récupérables de ce composant désassembleur sur `true`.  
  
### <a name="party-resolution"></a>Résolution du tiers  
 Le tiers d'envoi des messages dont l'extraction a réussi dans le traitement des échanges récupérables est identifié en fonction du tiers configuré pour le port de réception sur lequel l'échange parent est arrivé. Si la résolution du tiers échoue pour tout message extrait d'un échange donné, elle est considérée comme ayant échoué pour l'ensemble de l'échange.  
  
### <a name="restrictions"></a>Restrictions  
  
-   Lorsqu'un échange échoue dans le désassembleur, il est suspendu et peut être repris. Toutefois, si l'échange reprend administrativement, il échouera à nouveau, car les types d'erreurs qui provoquent les échecs de désassemblage sont uniquement un résultat du contenu d'échange, qui reste le même quand l'échange est repris. Lorsqu'un échange a échoué de la sorte, il doit être modifié et réenvoyé via un emplacement de réception.  
  
-   Si un message ayant été extrait avec succès d'un échange subit un échec de propagation via la messagerie en raison d'un abonné sans correspondance, le message est suspendu et peut être repris. Ce message peut être repris administrativement si la cause de l'échec de routage est résolue.  
  
-   Le composant désassembleur continue d'extraire les messages d'un échange malgré l'apparition des erreurs suivantes dans les composants désassembleur :  
  
    -   Schéma introuvable  
  
    -   Ambiguïté de schéma non résolue (c'est-à-dire que plusieurs schémas existent pour le même type de message)  
  
    -   Échec de la validation XML  
  
    -   Échec de l'analyse de fichier plat  
  
-   Le composant désassembleur **pas** continuer à extraire des messages d’un échange si l’erreur suivante se produit dans les composants désassembleur :  
  
    -   Les données de document ne sont pas des données XML bien formées : n'importe quelles propriétés de document qui provoqueraient l'échec de System.Xml.XmlReader  
  
## <a name="see-also"></a>Voir aussi  
 [Comment configurer le composant de Pipeline désassembleur XML](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)   
 [Comment configurer le composant de Pipeline de désassembleur de fichier plat](../core/how-to-configure-the-flat-file-disassembler-pipeline-component.md)