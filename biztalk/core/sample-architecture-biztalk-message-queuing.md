---
title: "Exemple d’Architecture : Message Queuing de BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, security
- Message Queuing binary protocol
- architecture, examples
- security, examples
- security, architecture
- examples, architecture
- MSMQ adapters, security
- architecture, security
- MSMQ adapters, architecture examples
- servers, Windows Message Queuing
- Windows Message Queuing
- message queuing adapters
ms.assetid: a660c798-1c45-4759-a6c8-f11550683a31
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f38d373680fd1b47722fc1ac52c56b113ef59cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sample-architecture-biztalk-message-queuing"></a>Exemple d’Architecture : Message Queuing de BizTalk
Cette rubrique décrit l'exemple d'architecture associé à l'utilisation de l'adaptateur Message Queuing BizTalk pour échanger des messages.  
  
 La figure suivante illustre les composants de l'exemple d'architecture BizTalk Server associé à l'utilisation de l'adaptateur Message Queuing BizTalk.  
  
 **Figure 1 exemple d’architecture qui affiche l’adaptateur Message Queuing BizTalk**  
  
 ![Exemple d’architecture pour Message Queuing BizTalk](../core/media/tdi-sec-refarch-msmq.gif "TDI_Sec_RefArch_MSMQ")  
  
 Cet exemple d'architecture contient les composants présentés dans les sections suivantes.  
  
## <a name="perimeter-networkinternet"></a>Réseau de périmètre ― Internet  
 Il est déconseillé d'utiliser le protocole binaire Message Queuing sur Internet. Vous ne devez pas laisser tout le trafic Message Queuing via le pare-feu 1. Si vous souhaitez utiliser l’adaptateur BizTalk Message Queuing pour recevoir des messages via Internet, procédez comme suit :  
  
-   Utilisez un serveur Message Queuing dans le réseau de périmètre.  
  
-   Utilisez le protocole HTTP Message Queuing sur Internet.  
  
-   Assurez-vous de disposer d'une application de transfert dans le réseau de périmètre, qui prélève les messages du serveur Message Queuing et les transfère à l'adaptateur BizTalk Message Queuing à l'aide d'un protocole binaire.  
  
    > [!IMPORTANT]
    >  Même si vous utilisez BizTalk Message Queuing pour recevoir des messages d'Internet, les ports que BizTalk Message Queuing utilise doivent rester fermés dans le pare-feu 1.  
  
## <a name="perimeter-networkintranet"></a>Réseau de périmètre ― intranet  
 Lorsque vous utilisez l'adaptateur BizTalk Message Queuing pour recevoir des messages de l'intranet, un serveur Windows Message Queuing transfère le trafic de Message Queuing au serveur BizTalk exécutant une instance de l'hôte de l'adaptateur BizTalk Message Queuing.  
  
 Si l'intranet et le domaine E-Business partagent un Active Directory commun, un message transite par une série de routeurs Message Queuing jusqu'à atteindre la destination appropriée (le serveur BizTalk exécutant une instance de l'hôte de l'adaptateur de réception BizTalk Message Queuing). Cette option n'est pas représentée dans la diagramme parce qu'elle est moins sûre que la première.  
  
## <a name="e-business-domain"></a>Domaine E-Business  
 Les serveurs de ce domaine sont les suivants :  
  
-   **BizTalk Server (traitement, adaptateur BizTalk Message Queuing et hôtes de suivi).** Le moteur d'exécution BizTalk Server est installé sur ce serveur, ainsi que les instances des hôtes qui contiennent les orchestrations, les pipelines, le Moteur de règles d'entreprise et les autres processus d'entreprise de BizTalk Server. C'est là que les ports, emplacements de réception, pipelines, mappages, schémas et assemblys de BizTalk Server se trouvent pour recevoir, router, traiter et envoyer des messages. Ce serveur dispose également d'une instance d'hôte qui prend en charge le suivi des données d'analyse du fonctionnement et de l'entreprise. En outre, cet hôte contient les instances de l'hôte qui exécute les adaptateurs d'envoi et de réception BizTalk Message Queuing.  
  
    > [!NOTE]
    >  Plus ces besoins augmentent, plus vous pouvez ajouter de serveurs BizTalk Server à votre environnement pour les instances de vos hôtes de traitement.  
  
-   **Serveur de secret principal.** Identique à la [exemple d’Architecture : BizTalk Server de Base](../core/sample-architecture-base-biztalk-server.md).  
  
-   **SQL Server.** Identique à la [exemple d’Architecture : BizTalk Server de Base](../core/sample-architecture-base-biztalk-server.md).  
  
-   **Contrôleur de domaine.** Identique à la [exemple d’Architecture : BizTalk Server de Base](../core/sample-architecture-base-biztalk-server.md).  
  
-   **Outils d’administration.** Identique à la [exemple d’Architecture : BizTalk Server de Base](../core/sample-architecture-base-biztalk-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples d’architecture pour les petites et moyennes entreprises](../core/sample-architectures-for-small-medium-sized-companies.md)   
 [Exemples de scénarios d’analyse du modèle](../core/sample-scenarios-for-threat-model-analysis.md)