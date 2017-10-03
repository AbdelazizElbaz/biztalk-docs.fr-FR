---
title: "Impossible d’obtenir le type de liaison pour l’extension de liaison | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a7cfc81-7439-48f9-8cac-42b2419ecd9d
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 453a579daae80a202df1ed4d3c72ae9c13f47d9b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unable-to-get-binding-type-for-binding-extension"></a>Impossible d'obtenir le type de liaison pour l'extension de liaison
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Impossible d'obtenir le type de liaison pour l'extension de liaison « {0} ». Si machine.config a été mis à jour alors que votre application était ouverte, redémarrez votre application pour prendre les modifications en compte. Vérifiez que l'extension de liaison est enregistrée dans machine.config|  
  
## <a name="explanation"></a>Explication  
 Une extension de liaison personnalisée pour un transport WCF-Custom ou WCF-CustomIsolated n'a pas été correctement configurée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, effectuez l'une des opérations suivantes :  
  
-   Vérifiez le **fichier machine.config** dans **%WinDir%\Microsoft.NET\Framework\v4.0.30319\Config** a le \< **bindingExtensions**> élément configuré correctement.  
  
-   Dans l’Explorateur Windows, accédez à **%WinDir%\Assembly**et assurez-vous que l’implémentation de l’extension de liaison personnalisée sont correctement installés.  
  
-   Pour l'adaptateur WCF-Custom, dans la console Administration de BizTalk, redémarrez l'instance d'hôte exécutant le transport WCF.  
  
-   Pour l'adaptateur WCF-CustomIsolated, dans la console de gestion IIS, redémarrez le pool d'applications hébergeant le transport WCF.  
  
-   Ouvrez puis fermez la console Administration de BizTalk.  
  
 Pour plus d'informations, consultez la ressource suivante :  
  
-   [Comment activer les Points d’extensibilité WCF avec les adaptateurs WCF](../core/how-to-enable-the-wcf-extensibility-points-with-the-wcf-adapters.md)