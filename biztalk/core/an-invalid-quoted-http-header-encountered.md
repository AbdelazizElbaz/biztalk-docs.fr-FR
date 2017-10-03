---
title: "Non valide entre guillemets en-tête HTTP détecté | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb530ee6-ec6a-4791-ae99-b9db426c0896
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e154e3bacf34025edd837516a15dca6f2caa174
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="an-invalid-quoted-http-header-encountered"></a>En-tête HTTP entre guillemets non valide rencontré
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur AS2|  
|Nom symbolique|-|  
|Texte du message|En-tête HTTP entre guillemets non valide rencontré.  Détails sont les suivants : nom d’en-tête : valeur d’en-tête « {0} » : « {{1} »|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception AS2 ou le pipeline d'envoi AS2 n'a pas pu traiter le message AS2 car le nom de l'en-tête AS2-From ou AS2-To du message est placé entre guillemets de manière incorrecte. Le nom de l'en-tête est placé entre guillemets pour prendre en compte un espace, une barre oblique ou des guillemets doubles dans le nom.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, placez le nom d'en-tête du message AS2 entre guillemets de manière à ce qu'il soit conforme aux spécifications de la section 6.2 (« Identificateurs de système AS2 ») de la norme (« Échange de données d'entreprise MIME pair à pair sécurisé via HTTP, AS2 (Applicability Statement 2) »).