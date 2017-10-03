---
title: "Rapports d’erreurs à partir des composants de Pipeline | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IErrorInfo object
- pipeline components [custom], errors
- SetErrorInfo method
- Exception object
ms.assetid: ad7c519e-829a-4a92-a42f-3e367d5dbaa8
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d181f557d64152ff79f70b09986c05727076121
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="reporting-errors-from-pipeline-components"></a>Rapports d’erreurs à partir des composants de Pipeline
Les composants de pipeline signalent les erreurs de deux manières :  
  
-   Pour les composants .NET, en levant une exception.  
  
-   Pour les composants COM, en définissant le **ErrorInfo** objet et en retournant un HRESULT d’échec.  
  
## <a name="reporting-errors-from-net-pipeline-components"></a>Signalement des erreurs par les composants de pipeline .NET  
 Pour signaler une erreur, un composant de pipeline .NET doit lever une exception à l'emplacement où il signale la description de l'erreur. Pour signaler le nom du composant qui génère une erreur, définissez la **Source** propriété de la **Exception** objet.  
  
 Le moteur de messagerie utilise le **Message** et **Source** propriétés de la **Exception** objet pour signaler une erreur. Le message suivant est écrit dans le journal des événements :  
  
 « Échec de l’exécution de la [de réception &#124; envoi] pipeline : \<nom du pipeline > Source : \<Source > [emplacement de réception &#124; Port d’envoi :] \<emplacement &#124; nom de port > raison : \<Message >. »  
  
## <a name="reporting-errors-from-com-pipeline-components"></a>Signalement d'erreurs par les composants de pipeline COM  
 Pou signaler une erreur, les composants de pipeline COM effectuent les actions suivantes :  
  
1.  Le composant de pipeline définit la **IErrorInfo** objet en appelant le **SetErrorInfo** (méthode).  
  
2.  Il retourne une valeur HRESULT d'échec au moteur de messagerie.  
  
 Le moteur de messagerie utilise le **GetSource** et **GetDescription** propriétés de la **IErrorInfo** objet pour signaler une erreur. Si la source n'est pas définie, le nom du composant est utilisé. Si la description n’est pas définie ou la totalité de **ErrorInfo** objet n’est pas défini, le HRESULT retourné est signalé au lieu de la description. Le message suivant est écrit dans le journal des événements :  
  
 « Échec de l’exécution de la [de réception &#124; envoi] pipeline : \<nom du pipeline > Source : \<GetSource > [emplacement de réception &#124; Port d’envoi :] \<emplacement &#124; nom de port > raison : \<GetDescription ou HRESULT >. »  
  
## <a name="see-also"></a>Voir aussi  
 [Développement de composants de Pipeline personnalisé](../core/developing-custom-pipeline-components.md)