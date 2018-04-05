---
title: Qu'est-ce que l'adaptateur WCF-NetTcp ? | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF-NetTcp adapters, about WCF-NetTcp adapters
ms.assetid: 94dc24df-19a1-4701-9012-59d05b0c8abd
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a741d3a4d7b7bcc80405d0fc25e37a31860523b9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-wcf-nettcp-adapter"></a>Qu'est-ce que l'adaptateur WCF-NetTcp ?
L'adaptateur WCF-NetTcp permet à des ordinateurs ou à des processus connectés de communiquer au sein d'un environnement dans lequel les services et clients sont de type WCF. Il fournit un accès total aux fonctionnalités de sécurité, de fiabilité et de transaction SOAP. Cet adaptateur utilise le transport TCP et les messages ont un codage binaire.  
  
 Le tableau suivant répertorie les caractéristiques de l'adaptateur WCF-NetTcp.  
  
| Description|Caractéristique|  
|-----------------|--------------------|  
|Niveau d'interopérabilité|Profil .NET|  
|Codage du message|Binaire|  
|Limite|Entre ordinateurs ou entre processus|  
|Protocole de transport|TCP|  
|Mode de sécurité|None, Message, Transport et TransportWithMessageCredential.|  
|Mécanisme d'authentification du client|Sécurité du transport et sécurité des messages|  
|Prise en charge de WS-ReliableMessaging|Non|  
|Prise en charge de WS-AtomicTransaction|Oui|  
|Prise en charge de la messagerie unidirectionnelle|Oui|  
|Prise en charge de la messagerie bidirectionnelle|Oui|  
|Type d'hôte pour l'adaptateur de réception|In-process|  
|Type d'hôte pour l'adaptateur d'envoi|In-process|  
  
 L'adaptateur WCF-NetTcp est constitué de deux adaptateurs : un adaptateur de réception et un adaptateur d'envoi.  
  
 **Adaptateur de réception WCF-NetTcp**  
  
 L'adaptateur de réception WCF-NetTcp permet de recevoir des demandes de service WCF via le protocole TCP. Un emplacement de réception qui utilise l'adaptateur de réception WCF-NetTcp peut être configuré comme emplacement de réception unidirectionnel ou de requête-réponse (bidirectionnel).  
  
 **Adaptateur d’envoi WCF-NetTcp**  
  
 L'adaptateur d'envoi WCF-NetTcp permet d'appeler un service WCF à l'aide du contrat sans type via le protocole TCP.  
  
 Pour plus d’informations sur WCF de réception et les adaptateurs d’envoi, consultez [quelles sont les adaptateurs WCF ?](../core/what-are-the-wcf-adapters.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de l’adaptateur WCF-NetTcp](../core/configuring-the-wcf-nettcp-adapter.md)   
 [Adaptateurs WCF](../core/wcf-adapters.md)