---
title: "Fonctionne de l’exemple de gestionnaire FRR NAK | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f11bd20-3a0e-4d96-8e0a-32fecc7eed7e
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 009cb0c3dffce5f88c72207866f6778e3deb7b28
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-the-frr-nak-handler-sample-works"></a>Fonctionne de l’exemple de gestionnaire FRR NAK
L’exemple de gestionnaire personnalisé de FRR NAK sert d’intermédiaire entre l’orchestration de rapprochement de réponse de FIN (FRR) et l’orchestration de réparation de message. L’orchestration FRR identifie l’erreur qui s’est produite lorsque le réseau SWIFT a tenté de recevoir le message. La sortie de l’orchestration FRR est un message d’une partie avec un objet d’erreur. Le gestionnaire personnalisé FRR NAK transforme ce message dans un message en deux parties, avec une partie de l’erreur qui indique l’erreur qui s’est produite, l’activation de message à être récupéré par l’orchestration de réparation de message. L’orchestration de réparation de message ouvre le message dans une [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] formulaire qui vous permet de savoir quel était l’erreur, réparez le message en conséquence et soumettre à nouveau afin que [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] peut renvoyer à SAA.  
  
 Les étapes suivantes se produisent lorsque le gestionnaire personnalisé FRR NAK traite un message réseau rapide n’a pas été correctement reçu :  
  
1.  Une fois que l’orchestration FRR a mis en corrélation le message ayant échoué pour le message MTS21_FIN_ACKNAK NAK, l’orchestration RepairSWIFTRejectedMessage (le gestionnaire personnalisé) récupère le message d’origine à partir de la MessageBox. Il donc en filtrant sur A4SWIFT_FRRFailed == True et A4SWIFT_SendingServiceType = « A4SWIFT_FrrService ».  
  
2.  Le gestionnaire personnalisé ne prennent pas en charge le message de MTS21_FIN_ACKNAK NAK FRR mis en corrélation avec le message d’origine. Au lieu de cela, il crée un objet de collection d’erreurs, il remplit avec une erreur de validation BRE qui indique que la propriété A4SWIFT_FRRFailedReason a été et l’ajoute au message d’origine. L’orchestration de réparation de message peut traiter ce message en deux parties.  
  
3.  Le gestionnaire personnalisé promeut les propriétés suivantes pour provoquer le message à être récupéré par l’orchestration de réparation de message : A4SWIFT_Failed == True, A4SWIFT_SwiftBound == True et BizTalk Server. Opération = « A4SWIFT_DASMMarkedAsFailed ». Il définit le nombre de parties propriété à 2 et définit les propriétés de l’erreur appropriée.  
  
4.  À la suite les propriétés promues, l’orchestration de réparation de messages récupère le message, et l’orchestration RepairSWIFTRejectedMessage s’arrête.