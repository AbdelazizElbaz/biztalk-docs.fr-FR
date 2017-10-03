---
title: "Configuration des propriétés de Pipeline AS2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.edir2.AS2.pipeline.properties
ms.assetid: 7faf6b05-710a-4d00-8c77-590ce9d9f962
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4e41afd99e7af1441e2d3d8cc936c04cd9321779
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-as2-pipeline-properties"></a>Configuration des propriétés du pipeline AS2
Des propriétés de pipeline sont utilisées dans le traitement d'un message AS2 entrant ou sortant lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'a pas été en mesure de déterminer l'accord correspondant à l'échange envoyé ou reçu.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="as2-pipeline-properties"></a>Propriétés de pipeline AS2  
 La propriété suivante peut être définie dans les pipelines AS2 :  
  
|Propriété|Utiliser|Valeurs|Pipeline/Étape|  
|--------------|---------|------------|---------------------|  
|ContentTransferEncoding|Indique la méthode à utiliser pour représenter des données binaires au format texte ASCII.|8 bits (par défaut)<br /><br /> 7 bits<br /><br /> 8 bits|AS2EdiSend/Codage<br /><br /> AS2Send/Codage|  
  
### <a name="to-set-a-pipeline-property"></a>Pour définir une propriété de pipeline  
  
1.  Dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], cliquez avec le bouton droit sur l'emplacement de réception ou sur le port d'envoi qui utilise le pipeline pour lequel définir les propriétés. Cliquez sur **Propriétés**.  
  
2.  Cliquez sur le bouton représentant des points de suspension (…) en regard du pipeline pour lequel définir les propriétés.  
  
3.  Entrez la valeur de la propriété, puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement et la configuration des Solutions AS2 BizTalk Server](../core/developing-and-configuring-biztalk-server-as2-solutions.md)