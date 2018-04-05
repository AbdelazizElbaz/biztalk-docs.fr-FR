---
title: Qu'est-ce que l'adaptateur WCF-NetMsmq ? | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF-NetMsmq adapters, about WCF-NetMsmq adapters
ms.assetid: 506c5e2d-6cbe-4788-8e37-49d009dc559a
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1008cc7178c38532f1781890080eacf4b5dfb56c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-wcf-netmsmq-adapter"></a>Qu'est-ce que l'adaptateur WCF-NetMsmq ?
L'adaptateur WCF-NetMsmq permet à des ordinateurs déconnectés de communiquer à l'aide la technologie de mise en file d'attente au sein d'un environnement où les services et les clients sont de type WCF. Cet adaptateur utilise le transport MSMQ (Message Queuing) et les messages ont un codage binaire.  
  
 Le tableau suivant répertorie les caractéristiques de l'adaptateur WCF-NetMsmq.  
  
| Description|Caractéristique|  
|-----------------|--------------------|  
|Niveau d'interopérabilité|Profil .NET|  
|Codage du message|Binaire|  
|Limite|Entre ordinateurs|  
|Protocole de transport|MSMQ|  
|Mode de sécurité|None, Message, Transport et Both.|  
|Mécanisme d'authentification du client|Sécurité du transport et sécurité des messages|  
|Prise en charge de WS-ReliableMessaging|Non applicable|  
|Prise en charge de WS-AtomicTransaction|Oui|  
|Prise en charge de la messagerie unidirectionnelle|Oui|  
|Prise en charge de la messagerie bidirectionnelle|Non|  
|Type d'hôte pour l'adaptateur de réception|In-process|  
|Type d'hôte pour l'adaptateur d'envoi|In-process|  
  
> [!NOTE]
>  Les files d'attente à partir desquelles l'adaptateur de réception WCF-NetMsmq récupère les messages doivent être créées à l'avance. Les messages se trouvant dans les files d'attente doivent être du type WCF, sinon ils seront envoyés dans la file d'attente des messages non distribués.  
  
 L'adaptateur WCF-NetMsmq est constitué de deux adaptateurs : un adaptateur de réception et un adaptateur d'envoi.  
  
 **Adaptateur de réception WCF-NetMsmq**  
  
 L'adaptateur de réception WCF-NetMsmq permet de recevoir des demandes de service WCF via MSMQ. Un emplacement de réception qui utilise l'adaptateur de réception WCF-NetMsmq peut uniquement être configuré comme emplacement de réception unidirectionnel.  
  
 **Adaptateur d’envoi WCF-NetMsmq**  
  
 L'adaptateur d'envoi WCF-NetMsmq permet d'appeler un service WCF à l'aide du contrat sans type via MSMQ.  
  
 Pour plus d’informations sur WCF de réception et les adaptateurs d’envoi, consultez [quelles sont les adaptateurs WCF ?](../core/what-are-the-wcf-adapters.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de l’adaptateur WCF-NetMsmq](../core/configuring-the-wcf-netmsmq-adapter.md)   
 [Adaptateurs WCF](../core/wcf-adapters.md)