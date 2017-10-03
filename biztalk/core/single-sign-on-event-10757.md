---
title: "Single Sign-On : Événement 10757 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24765a25-560b-4391-9839-a325894c679f
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5887694e8fd307c0738fc7596c52354925bfbc7c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10757"></a>Single Sign-On : Événement 10757
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10757|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|ENTSSO_E_NO_MAPPING|  
|Texte du message|Le mappage n'existe pas. Les informations de configuration n'ont pas été définies pour les applications de la banque de configuration.|  
  
## <a name="explanation"></a>Explication  
 S'il s'agit d'une application de type Individuel ou Groupe, le mappage n'existe pas.  
  
 S'il s'agit d'une application de la banque de configuration, les données de configuration n'ont pas été définies. Ceci peut se produire lorsque la base de données SSO a été réinitialisée, contrairement à la base de gestion BizTalk, et inversement.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 S'il s'agit d'une application de type Individuel ou Groupe, créez le mappage souhaité. Pour plus d’informations, consultez [comment créer des mappages utilisateur](../core/how-to-create-user-mappings.md).