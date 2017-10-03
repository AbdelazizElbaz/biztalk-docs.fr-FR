---
title: "Concepts d’analyse BAM pour les développeurs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c26d0aed-821c-4e1f-9cc9-9375a2ba28de
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9e407121e9f71707b45f95e77a8520ed30df3b33
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="bam-concepts-for-the-developer"></a>Concepts de l'analyse BAM à l'attention du développeur
En tant que développeur BAM, vous devez être familiarisé avec les importants concepts de l'analyse BAM que sont par exemple les activités, les continuations et les références. Vous devez également connaître les différences existant entre le suivi et le traitement transactionnel.  
  
## <a name="what-is-a-bam-activity"></a>Qu'est-ce qu'une activité BAM ?  
 Une activité BAM est ce qui définit quelles données sont intéressantes pour un élément dans le processus d'entreprise (un bon de commande unique par exemple). Elle détermine quelles colonnes figurent dans la base de données BAM.  
  
 L'instance d'une activité représente une unité de travail dans une activité commerciale : un bon de commande ou une application d'emprunt par exemple. Une activité spécifie une liste d'étapes majeures (l'historique de l'activité) et des données d'intérêt. L'instance d'une activité est représentée par une ligne unique dans la base de données d'importation principale BAM. Une seule et unique valeur est associée à tout élément de données de cette instance de l'activité.  
  
 Une activité sert à montrer les étapes majeures et les données ayant trait à cette unité de travail à l'utilisateur final du processus d'entreprise ou au travailleur de l'information. Par exemple, l'activité définie dans l'exemple du kit de développement logiciel BAM contient des étapes majeures telles que des informations portant sur ce qui a été payé et envoyé, ainsi que des données d'intérêt se rapportant par exemple au montant total.  
  
 Les activités BAM sont souvent directement mappées vers un processus d'entreprise même si, en tant qu'abstractions de haut niveau, les activités sont indépendantes de l'implémentation de votre infrastructure informatique.  
  
 En tant que développeur, votre rôle consiste à conserver cette abstraction en n'exposant que les données et les étapes majeures pertinentes de l'implémentation dans le contexte d'une activité spécifique.  
  
## <a name="what-is-a-continuation"></a>Qu'est-ce qu'une continuation ?  
 Les continuations assistent l'infrastructure BAM quant aux informations suivantes :  
  
-   L'ordre dans lequel les événements sont censés se produire  
  
-   Une manière de traiter toute modification de l'ID unique avec lequel les éléments d'événement sont corrélés  
  
 Pour plus d’informations sur les Continuations et comment elles sont utilisées, consultez [nœuds Continuation et ContinuationID](../core/continuation-and-continuationid-nodes.md).  
  
## <a name="what-is-a-reference"></a>Qu'est-ce qu'une référence ?  
 Une référence (ou activité associée) spécifie une relation entre une activité et un autre élément quelconque. Les éléments associés peuvent être par exemple une autre activité ou un emplacement de document.  
  
> [!NOTE]
>  Lorsque vous spécifiez une activité en tant qu'activité associée, l'activité actuelle peut, à la différence d'une activité de continuation, se terminer même si l'activité associée n'est pas terminée.  
  
## <a name="tracking-and-transactional-processing"></a>Suivi et traitement transactionnel  
 L'écriture de code pour l'analyse BAM vous permet de décider qui, du suivi ou du traitement transactionnel, effectuera le suivi des données. Par défaut, l'analyse donne la même importance au suivi et au traitement. Cela signifie que si la fonction de suivi ou le processus transactionnel échoue, aucun des deux n'est autorisé à continuer. Rien n'est enregistré dans la base de données des suivis et la transaction est annulée. Il se peut que ce ne soit pas la meilleure méthode de suivi pour votre solution. En développant pour l'analyse BAM, vous pouvez déterminer qui, du suivi ou du traitement transactionnel, doit avoir la priorité.  
  
 Le tableau suivant répertorie les modes de suivi des données dans l'analyse BAM.  
  
|Scénario|Descriptions|  
|--------------|------------------|  
|Le suivi est prioritaire sur le traitement|Si le processus réussit, écrire les informations de suivi.<br /><br /> Si le processus échoue, écrire les informations relatives à l'échec.|  
|Le traitement a la même importance que le suivi|Si le suivi ou le traitement échoue, tout annuler.|  
|Le traitement est prioritaire sur le suivi|Si le processus réussit et que la fonction de suivi échoue, poursuivre le traitement.|