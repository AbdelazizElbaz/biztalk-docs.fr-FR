---
title: Qu'est-ce que l'adaptateur WCF-WSHttp ? | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF-WSHttp adapters, about WCF-WSHttp adapters
ms.assetid: 183a19e3-10b1-403f-b274-34a441e774d1
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb5d244dcfe26cf10bc4ae10c63374eef0824444
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-wcf-wshttp-adapter"></a>Qu'est-ce que l'adaptateur WCF-WSHttp ?
L'adaptateur WCF-WSHttp permet d'établir une communication entre ordinateurs avec les services et clients qui peuvent comprendre les normes de service Web de nouvelle génération, via le transport HTTP ou HTTPS avec le codage Texte ou MTOM (Message Transmission Optimization Mechanism). Il fournit un accès complet aux fonctionnalités de sécurité, de fiabilité et de transaction SOAP.  
  
 Le tableau suivant répertorie les caractéristiques de l'adaptateur WCF-WSHttp.  
  
| Description|Caractéristique|  
|-----------------|--------------------|  
|Niveau d'interopérabilité|WS-Profile|  
|Codage du message|Texte ou MTOM|  
|Limite|Entre ordinateurs|  
|Protocole de transport|HTTP ou HTTPS|  
|Mode de sécurité|None, Message, Transport et TransportWithMessageCredential.|  
|Mécanisme d'authentification du client|Sécurité du transport et sécurité des messages|  
|Prise en charge de WS-ReliableMessaging|Non|  
|Prise en charge de WS-AtomicTransaction|Oui|  
|Prise en charge de la messagerie unidirectionnelle|Oui|  
|Prise en charge de la messagerie bidirectionnelle|Oui|  
|Type d'hôte pour l'adaptateur de réception|Isolé|  
|Type d'hôte pour l'adaptateur d'envoi|In-process|  
  
 L'adaptateur WCF-WSHttp est constitué de deux adaptateurs : un adaptateur de réception et un adaptateur d'envoi.  
  
 **Adaptateur de réception WCF-WSHttp**  
  
 L'adaptateur de réception WCF-WSHttp permet de recevoir des demandes de service WCF via le protocole HTTP ou HTTPS. Un emplacement de réception qui utilise l'adaptateur de réception WCF-WSHttp peut être configuré comme emplacement de réception unidirectionnel ou de requête-réponse (bidirectionnel).  
  
 **Adaptateur d’envoi WCF-WSHttp**  
  
 L'adaptateur d'envoi WCF-WSHttp permet d'appeler un service WCF à l'aide du contrat sans type via le protocole HTTP ou HTTPS.  
  
 Pour plus d’informations sur WCF de réception et les adaptateurs d’envoi, consultez [quelles sont les adaptateurs WCF ?](../core/what-are-the-wcf-adapters.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de l’adaptateur WCF-WSHttp](../core/configuring-the-wcf-wshttp-adapter.md)   
 [Adaptateurs WCF](../core/wcf-adapters.md)