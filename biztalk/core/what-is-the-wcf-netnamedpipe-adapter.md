---
title: "Qu'est-ce que l'adaptateur WCF-NetNamedPipe ? | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF-NetNamedPipe adapters, about WCF-NetNamedPipe adapters
ms.assetid: b9f84256-e49d-4ee2-b0fa-d3f692ade1d4
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43c73a670139690c4a27d4784c6ad23225492f17
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-wcf-netnamedpipe-adapter"></a>Qu'est-ce que l'adaptateur WCF-NetNamedPipe ?
L'adaptateur WCF-NetNamedPipe permet une communication entre processus sur un ordinateur au sein d'un environnement où les services et les clients sont de type WCF. Il fournit un accès total aux fonctionnalités de fiabilité et de transaction SOAP. Il utilise le transport de canal nommé et les messages relèvent d'un codage binaire. Vous ne devez pas utiliser cet adaptateur dans une communication entre ordinateurs.  
  
 Le tableau suivant répertorie les caractéristiques de l'adaptateur WCF-NetNamedPipe.  
  
| Description|Caractéristique|  
|-----------------|--------------------|  
|Niveau d'interopérabilité|Profil .NET|  
|Codage du message|Binaire|  
|Limite|Interprocessus|  
|Protocole de transport|Canal nommé|  
|Mode de sécurité|None et Transport|  
|Mécanisme d'authentification du client|Sécurité du transport et sécurité des messages|  
|Prise en charge de WS-ReliableMessaging|Non|  
|Prise en charge de WS-AtomicTransaction|Oui|  
|Prise en charge de la messagerie unidirectionnelle|Oui|  
|Prise en charge de la messagerie bidirectionnelle|Oui|  
|Type d'hôte pour l'adaptateur de réception|In-process|  
|Type d'hôte pour l'adaptateur d'envoi|In-process|  
  
 L'adaptateur WCF-NetNamedPipe est constitué de deux adaptateurs : un adaptateur de réception et un adaptateur d'envoi.  
  
 **Adaptateur de réception WCF-NetNamedPipe**  
  
 L'adaptateur de réception WCF-NetNamedPipe permet de recevoir des demandes de service WCF via le transport de canal nommé. Un emplacement de réception qui utilise l'adaptateur de réception NetNamedPipe peut être configuré comme emplacement de réception unidirectionnel ou de requête-réponse (bidirectionnel).  
  
 **Adaptateur d’envoi WCF-NetNamedPipe**  
  
 L'adaptateur d'envoi WCF-NetNamedPipe permet d'appeler un service WCF à l'aide du contrat sans type via le transport de canal nommé.  
  
 Pour plus d’informations sur WCF de réception et les adaptateurs d’envoi, consultez [quelles sont les adaptateurs WCF ?](../core/what-are-the-wcf-adapters.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de l’adaptateur WCF-NetNamedPipe](../core/configuring-the-wcf-netnamedpipe-adapter.md)   
 [Adaptateurs WCF](../core/wcf-adapters.md)