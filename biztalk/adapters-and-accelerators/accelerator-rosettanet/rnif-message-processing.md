---
title: Le traitement des messages RNIF | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RosettaNet Implementation Framework (RNIF)
- RosettaNet, about RosettaNet
- RNIF
- RNIF, non-repudiation
- RNIF, BizTalk Accelerator for RosettaNet
- non-repudiation
- RNIF, about RNIF
- BizTalk Accelerator for RosettaNet, RNIF
- RosettaNet
ms.assetid: 994f15bc-765c-4220-8ab1-176919e9e821
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 34ff8794c6dcc94571607207b4c13e9dd2bf54cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="rnif-message-processing"></a>Traitement des messages RNIF
L’organisation RosettaNet définit un échange de messages dans les spécifications de Framework RNIF (RosettaNet Implementation). RNIF définit la façon dont les systèmes d’intégration transport des messages. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]entièrement implémente les spécifications de RNIF, à ce que l’ajout de cette fonctionnalité [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] en mode natif offre d’emploi.  
  
 RNIF communications sont complexes. Les processus publics qui effectuent le traitement de RNIF incluent une variété de contrôles de validation et la logique de flux de travail complexe. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]fournit cette fonctionnalité en mode natif. Cela vous permet d’utiliser un système compatible avec RosettaNet sans développement ou de la gestion de logique RNIF à partir de zéro.  
  
## <a name="btarn-support-for-rnif"></a>Prise en charge BTARN de RNIF  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]prend en charge les deux versions de la norme RNIF : RNIF 1.1 et RNIF 2.0 (V02.00.01). RNIF 2.0 ajouté des fonctionnalités significatives au-delà de la prise en charge par RNIF 1.1, notamment le chiffrement, les pièces jointes et les transactions synchrones. RNIF 2.0 n'est pas à compatibilité descendante avec RNIF 1.1.  
  
> [!NOTE]
>  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]RosettaNet prêt RNIF 2.0 n’est conforme.  
  
 Les deux versions définissent le message RosettaNet différemment. Pour plus d’informations sur les conteneurs de messages différents, consultez [RNIF Standard](../../adapters-and-accelerators/accelerator-rosettanet/rnif-standard.md).  
  
 Systèmes d’intégration effectuer de transfert RNIF via HTTP/HTTPS et SMTP ; Toutefois, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] implémente uniquement HTTP/HTTPS. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]ne prend pas en charge les transactions synchrones et des pièces jointes dans RNIF 1.1.  
  
### <a name="non-repudiation"></a>Non répudiation  
 La norme RNIF inclut une spécification de non répudiation. Cela implique le stockage de tous les messages reçus ou envoyés par le format de transmission [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] dans une base de données de non-répudiation, afin que vous pouvez légalement prouver que vous avez reçu ou envoyé. Pour cela, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] utilise la table MessageStorageIn le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]archiver la base de données pour les messages entrants et la table MessageStorageOut de la même base de données pour les messages sortants.  
  
 Vous définissez les exigences de non-répudiation pour le contenu de service et des accusés de réception séparément dans le profil de configuration de processus. Si vous définissez une ou les deux le **non-répudiation de l’origine et du contenu** et **non-répudiation requis** options `True`, puis [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] stockera les données suivantes :  
  
|data|Sommaire|  
|----------|--------------|  
|RecordID|Propriétaire ID unique du message stocké|  
|MessageCategory|Demande (0), de réponse (1) ou de Signal (2)|  
|DestinationParty|Nom du tiers de destination|  
|SourceParty|Nom du tiers source|  
|PIPCode|Par exemple, PIP3A4|  
|PIPVersion|Par exemple, V02.00|  
|MessageContent|Message au format binaire|  
|MessageTrackingID|ID du message de suivi des messages|  
|PIPInstanceID|ID de l’instance du processus PIP|  
  
## <a name="see-also"></a>Voir aussi  
 [BizTalk Accelerator for RosettaNet ajoutée à BizTalk Server](../../adapters-and-accelerators/accelerator-rosettanet/what-biztalk-accelerator-for-rosettanet-adds-to-biztalk-server.md)   
 [Implémentation d’un PIP](../../adapters-and-accelerators/accelerator-rosettanet/pip-implementation.md)