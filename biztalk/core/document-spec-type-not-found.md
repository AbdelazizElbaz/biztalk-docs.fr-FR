---
title: "Ne pas trouvé de type de spécification de document | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2cb2a458-d0f4-420d-8d35-0e739167464f
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 886f4ac81ab7fb2c4a844f50348d84bead65a892
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="document-spec-type-not-found"></a>Type de spécification de document non trouvé
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|-|  
|Texte du message|Type de spécification de document {0} non trouvé|  
  
## <a name="explanation"></a>Explication  
 Cette erreur indique que le schéma est introuvable.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, déployez le schéma de document :  
  
1.  Démarrer **Microsoft Visual Studio**.  
  
2.  Créez un projet ou ouvrez-en un qui existe déjà.  
  
3.  Ajoutez le schéma au projet.  
  
4.  Déployez le projet dans Visual Studio.