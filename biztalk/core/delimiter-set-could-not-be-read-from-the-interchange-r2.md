---
title: "L’ensemble de délimiteurs n’a pas pu être lue dans l’échange (R2) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 17bdd32e-d43f-4f59-af27-5d3054fd5432
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d3836b218ac3596bef25edb29eaf72c38f65b6e9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="delimiter-set-could-not-be-read-from-the-interchange-r2"></a>Un ensemble de délimiteurs n'a pu être lu à partir de l'échange (R2).
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|-|  
|Texte du message|L’ensemble de délimiteurs n’a pas pu être lus à partir de l’échange. L'attribut DelimiterSetSerializedData est manquant dans le noeud racine.|  
  
## <a name="explanation"></a>Explication  
 Cette erreur indique que l'échange ne contient pas les valeurs de l'ensemble de délimiteurs.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, effectuez l’une des opérations suivantes :  
  
-   Ajoutez les valeurs de l'ensemble de délimiteurs à l'échange, de la façon suivante :  
  
    1.  Ouvrez le message.  
  
    2.  Déterminez s'il existe un segment UNA dans l'échange. S'il n'existe pas de segment UNA, demandez au partenaire de l'ajouter à l'échange.  
  
-   Entrez les valeurs du délimiteur à la propriété de pipeline EfactDelimiters, de la façon suivante :  
  
    1.  Dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], cliquez avec le bouton droit sur l'emplacement de réception ou sur le port d'envoi qui utilise le pipeline pour lequel définir les propriétés. Cliquez sur **Propriétés**.  
  
    2.  Cliquez sur le bouton représentant des points de suspension (…) en regard du pipeline pour lequel définir les propriétés.  
  
    3.  Entrez les valeurs des délimiteurs UNA sous la forme d'une liste délimitée par des virgules (pour UNA1, UNA2, UNA3, UNA4, UNA5 et UNA6), en modifiant les paramètres par défaut si nécessaire. Les valeurs par défaut sont les suivantes : 0x3A, 0x2B, 0x2C, 0x3F, 0 x 20, 0 x 27.  
  
    4.  Cliquez sur **OK**.