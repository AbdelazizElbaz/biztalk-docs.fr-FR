---
title: Adresse non valide (uri absolu) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5db292ad-9105-492d-a6c5-a7108159901a
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af2cb19c793bdcd7ab4a1dc18eb0ea1c98a991ed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-address-absolute-uri"></a>Adresse non valide (Uri absolu)
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Adresse non valide ; « {0} » n'est pas un URI absolu correctement constitué|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur indique que l'adresse absolue fournie pour le transport WCF de type In-process n'est pas bien formée. Par exemple, vous ne pouvez pas définir la propriété Adresse d'un transport WCF de type In-process sur une adresse relative, telle que /path/service.svc.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Remplacez l'adresse du transport WCF de type In-process par une adresse absolue bien formée.  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]** , puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans la racine de la Console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**.  
  
3.  Recherchez votre application, puis recherchez votre transport.  
  
4.  Cliquez avec le bouton droit sur le nom du transport.  
  
5.  Cliquez sur **Propriétés**.  
  
6.  Dans le port **Type** , sélectionnez le port approprié.  
  
7.  Cliquez sur **configurer**.  
  
8.  Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **général** onglet.  
  
9. Dans le **adresse (URI)** zone de texte. modifier l’adresse. http://localhost/path/service.svc est un exemple d'adresse absolue bien formée