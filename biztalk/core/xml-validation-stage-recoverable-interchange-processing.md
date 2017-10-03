---
title: "Étape de Validation XML (traitement des échanges récupérables) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1ed00971-d85b-4adb-86c4-c56de7ba7c67
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de8f0225e100053fe6dced8165b7fc800c5e4804
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="xml-validation-stage-recoverable-interchange-processing"></a>Étape de validation XML (Traitement des échanges récupérables)
Le **valideur XML** composant de pipeline traite un échange dans deux modes :  
  
-   **Mode standard**. Lorsque le **valideur XML** composant est configuré pour effectuer une validation standard, les messages contenus dans un échange sont validés dans une unité transactionnelle de travail. Plus précisément, si la validation d'un message de l'échange échoue, l'ensemble de l'échange (contenant tous les messages) est placé dans la file d'attente des messages interrompus.  
  
-   **Mode récupérable**. Lorsque le **valideur XML** composant est configuré pour effectuer le traitement des échanges récupérables, si la validation d’un message échoue, le message est placé dans la file d’attente suspendue et le **valideur XML** le composant continue à valider les messages restants dans l’échange.  
  
### <a name="to-configure-recoverable-interchange-processing"></a>Pour configurer le traitement des échanges récupérables  
  
1.  Ouvrez un pipeline de réception à l'aide du concepteur de pipeline dans Visual Studio.  
  
2.  Faites glisser **valideur XML** composant à partir de la **boîte à outils** à la **Validate** étape du pipeline de réception.  
  
3.  Dans la fenêtre Propriétés, définissez la valeur de la **traitement des échanges récupérables** propriété **True** si vous souhaitez que le **valideur XML** composant aux échanges de processus mode récupérable, ou affectez à la propriété **False** si vous souhaitez que le composant de traiter les échanges en mode standard. La valeur par défaut de cette propriété est `False`.  
  
 Le **valideur XML** classe dans le modèle objet, qui correspond à la **valideur XML** pipeline composant, a une propriété publique nommée **RecoverableInterchangeProcessing**que vous pouvez utiliser pour obtenir/définir le mode par programme. Consultez la documentation de [Microsoft.BizTalk.Component.XmlValidator](http://msdn.microsoft.com/library/microsoft.biztalk.component.xmlvalidator.aspx) classe pour plus d’informations.  
  
 Le tiers d'envoi des messages dont la validation a réussi est identifié en fonction du tiers configuré pour le port de réception sur lequel l'échange parent est arrivé. Si la résolution du tiers pour tout message extrait de l'échange échoue, elle est considérée comme ayant échoué pour l'ensemble de l'échange.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment configurer le composant de Pipeline valideur XML](../core/how-to-configure-the-xml-validator-pipeline-component.md)