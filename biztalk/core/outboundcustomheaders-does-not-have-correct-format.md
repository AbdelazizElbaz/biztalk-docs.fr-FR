---
title: "OutboundCustomHeaders n’a pas le format correct | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6097762b-01c9-48b8-8cee-ccd6b11d28d4
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3b81a8c9c605f646a8ac0b6df2045af05eb58e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="outboundcustomheaders-does-not-have-correct-format"></a>OutboundCustomHeaders n’a pas le format correct
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|OutboundCustomHeaders n'a pas le format correct|  
  
## <a name="explanation"></a>Explication  
 La valeur de WCF. InboundHeaders ou WCF. OutboundCustomHeaders n’est pas dans le format suivant : \<en-têtes >...\</headers >.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Retour à la ligne avec les valeurs de propriété \<en-têtes > élément.  
  
 Pour plus d'informations, consultez la ressource suivante dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Utilisation des en-têtes SOAP des Messages WCF avec les composants de Pipeline](../core/using-soap-headers-in-wcf-messages-with-pipeline-components.md)