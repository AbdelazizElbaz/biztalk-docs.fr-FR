---
title: CIDX normes de messagerie | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CIDX, RosettaNet
- RosettaNet, CIDX
ms.assetid: 6f70fa56-1fc3-4016-ac9e-6af18026292a
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4d37cd02f92a8a13857071d0b3d84ab40c480787
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="cidx-messaging-standards"></a>Normes de messagerie CIDX
CIDX (Chemical Industry Data Exchange) fonctionne comme une organisation de normes qui prend en charge et gère les normes chem pour l’échange de messages standard. Les entreprises dans l’industrie chimique utilisent ces normes pour leurs besoins de messagerie spécifiques.  
  
 CIDX a arrêté le Framework RNIF (RosettaNet Implementation) au niveau de la couche de messagerie pour permettre l’échange de documents XML. CIDX n’a pas adopté la couche de processus publics des normes RNIF.  
  
 Normes chem définissent des définitions de type document (DTD) XML décrivent le contenu du service d’un message qui échangent des systèmes. Le message est identique à un objet de RNIF 1.1 RosettaNet dans la structure, avec les différences dans le contenu de service et de certaines valeurs d’en-tête. Lorsqu’il existe une correspondance entre les normes CIDX et messages RosettaNet, la norme CIDX adopte RosettaNet les noms d’éléments et les structures de données.  
  
 CIDX a utilisé traditionnellement d’échange de document informatisé (EDI) pour l’échange de messages, mais il a créé un nouveau jeu de documents basés sur les technologies XML. Normes chem fournit des réplicas XML des messages EDI.  
  
 Normes chem créer des messages individuels pour chaque transaction commerciale. Normes chem utilisent deux types de réponses : réponses techniques et les réponses de la transaction. Pour la messagerie sécurisée et fiable, les normes chem utilisez uniquement des processus de type de Notification de RNIF 1.1. Normes chem n’utilisez pas de 0 a 1 processus PIP (Partner Interface).  
  
## <a name="cidx-and-rosettanet-differences"></a>CIDX et les différences de RosettaNet  
 Le tableau suivant répertorie certaines des différences entre RosettaNet et CIDX.  
  
|Implémentation de RosettaNet|Implémentation de CIDX|  
|-------------------------------|-------------------------|  
|RosettaNet utilise le « Application/x-RosettaNet » comme type MIME Multipurpose Internet Mail Extensions ().|CIDX utilise « Application/x-ChemXML » comme type MIME.|  
|Pour les en-têtes de RosettaNet, RosettaNet utilise GlobalAdministeringAuthorityCode = RosettaNet|CIDX utilise GlobalAdministeringAuthorityCode = CIDX|  
|RosettaNet prend en charge les messages d’action unique et double action.|CIDX prend en charge uniquement les messages d’action unique.|  
|Prend en charge de RosettaNet PIP 0 a 1 (Notification d’échec).|CIDX ne prend pas en charge le PIP 0 a 1.|  
|Messages RosettaNet peuvent être de la Transaction ou de Notification de type.|Tous les messages CIDX sont du type de Notification.|  
|Dans RosettaNet, vous devez dériver les paramètres de Configuration PIP les spécifications PIP.|Dans CIDX, vous devez dériver les paramètres de Configuration PIP CIDX normes chem spécifications.|  
  
## <a name="see-also"></a>Voir aussi  
 [RosettaNet et CIDX normes de messagerie](../../adapters-and-accelerators/accelerator-rosettanet/rosettanet-and-cidx-messaging-standards.md)   
 [Norme RNIF](../../adapters-and-accelerators/accelerator-rosettanet/rnif-standard.md)   
 [PIP de RosettaNet](../../adapters-and-accelerators/accelerator-rosettanet/rosettanet-pips.md)   
 [Prise en charge CIDX](../../adapters-and-accelerators/accelerator-rosettanet/cidx-support.md)