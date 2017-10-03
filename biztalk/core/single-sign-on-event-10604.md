---
title: "Single Sign-On : Événement 10604 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eea14ab1-5a89-4a62-b414-1bcb36ea339e
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d9d6858fb13542ca642c9c48a8a187b66ba6526
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10604"></a>Single Sign-On : Événement 10604
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10604|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_ERROR_SSOCSTX_OUT_OF_PROC|  
|Texte du message|L'application COM+ du « serveur ENTSSO » n'est pas configurée correctement. Il doit s'agir d'une application de bibliothèque COM+.|  
  
## <a name="explanation"></a>Explication  
 L'application COM+ doit être configurée en tant qu'application de bibliothèque COM+.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Dans le composant logiciel enfichable ENTSSO, développez le dossier COM+ et localisez votre serveur ENTSSO. Cliquez avec le bouton droit sur le serveur, puis cliquez sur Propriétés. Sélectionnez l'option d'application de bibliothèque plutôt que d'application serveur, puis cliquez sur OK.