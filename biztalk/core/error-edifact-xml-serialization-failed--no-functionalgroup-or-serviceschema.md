---
title: "Échec de la sérialisation Xml de l’échange EDIFACT en raison d’une structure non valide, aucun FunctionalGroup ou ServiceSchema | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 530faadd-e301-4743-b4b3-b04ba7578f1d
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f79d64a9ec19e62f13220be056335bf2d249519a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edifact-interchange-xml-serialization-failed-due-to-invalid-structure-no-functionalgroup-or-serviceschema"></a>Échec de la sérialisation XML de l'échange EDIFACT dû à une structure non valide, absence de FunctionalGroup ou ServiceSchema.
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|-|  
|Texte du message|Échec de la sérialisation XML de l'échange EDIFACT dû à une structure non valide. Recherche de FunctionalGroup ou de ServiceSchema pour UNZ, mais aucun n'a été trouvé.|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que le pipeline d'envoi n'a pas pu traiter un échange reçu par lot EDIFACT qui a été préservé, car les balises TransactionSetGroup ou FunctionalGroup n'étaient pas incluses dans le fichier d'échange XML.  
  
 Lorsque BizTalk traite un échange reçu par lot qui est préservé, une balise XML est attribuée à un groupe de documents informatisés ou à un groupe de groupes dans le fichier XML de l'échange. Une balise FunctionalGroup est attribuée au groupe de groupes. La balise ServiceSchema indique le schéma de contrôle utilisé pour l'échange reçu par lot préservé. Cette condition d'erreur se produit si vous configurez un lot préservé via un pipeline de réception et un pipeline d'envoi de transmission de transfert. Les balises sont définies par le pipeline de réception et sont supprimées par le pipeline d'envoi.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour remédier à cette erreur, vérifiez que la structure XML du fichier XML généré pour le lot préservé est bien formée, avec la balise FunctionalGroup (pour plusieurs groupes) et/ou la balise ServiceSchema (pour le schéma de contrôle utilisé pour l'échange reçu par lot préservé).