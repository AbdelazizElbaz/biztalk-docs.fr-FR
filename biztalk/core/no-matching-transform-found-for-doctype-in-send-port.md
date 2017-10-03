---
title: "Aucune transformation correspondante trouvée pour le type de document dans le Port d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 23f62ac7-3849-49fe-a765-2be72880a4c9
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8bc45ac0edf425bc19ab526fac6b2690f3a6b6d0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="no-matching-transform-found-for-doctype-in-send-port"></a>Aucune transformation correspondante trouvée pour le type de document dans le port d'envoi.
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|NoMatchingTransformFoundForSendPortAndDocType|  
|Texte du message|Aucune transformation correspondante trouvée pour {0} DocType dans {{1} du Port d’envoi. Incompatible avec les informations ExplorerOM|  
  
## <a name="explanation"></a>Explication  
 Cette erreur indique qu'aucune transformation correspondante n'a été trouvée pour un type de document ou un port d'envoi donnés.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, procédez comme suit :  
  
1.  Ouvrez la console Administration de BizTalk, repérez le transport et cliquez avec le bouton droit de la souris sur son nom.  
  
2.  Cliquez sur **Propriétés**.  
  
3.  Dans la liste des types de port, sélectionnez celui qui convient. Cliquez sur **configurer**.  
  
4.  Dans la boîte de dialogue Propriétés de Port d’envoi [nom du port], cliquez sur **mappages sortants** dans le volet gauche.  
  
5.  Vérifiez que le mappage est répertorié à cet endroit et qu'il correspond au type de document adéquat.