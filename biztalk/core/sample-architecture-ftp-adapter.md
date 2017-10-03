---
title: "Exemple d’Architecture : L’adaptateur FTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, security
- architecture, examples
- independent software vendor (ISV)
- security, examples
- security, architecture
- examples, architecture
- architecture, security
- FTP adapters, security
- FTP adapters, architecture examples
ms.assetid: 13fc1086-6acc-483c-be83-4ff6a60cd2bc
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bed15e06027bec5e73c19cf73548674bc51ce68a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sample-architecture-ftp-adapter"></a>Exemple d’Architecture : L’adaptateur FTP
Cette rubrique décrit l'exemple d'architecture associé à l'utilisation de l'adaptateur FTP pour échanger des messages.  
  
 La figure suivante illustre les composants de l'exemple d'architecture BizTalk Server associé à l'utilisation de l'adaptateur FTP.  
  
 **Figure 1 exemple d’architecture illustrant l’adaptateur FTP**  
  
 ![Exemple d’architecture pour l’adaptateur FTP](../core/media/tdi-sec-refarch-ftp.gif "TDI_Sec_RefArch_FTP")  
  
 Cet exemple d'architecture contient les composants décrits dans les sections suivantes.  
  
## <a name="perimeter-networkinternet"></a>Réseau de périmètre ― Internet  
 Lorsque vous utilisez l'adaptateur FTP, un serveur FTP est présent dans le réseau de périmètre Internet.  
  
> [!NOTE]
>  Le serveur FTP peut également être situé en dehors de votre environnement (dans le réseau d'un partenaire ou hébergé par un éditeur de logiciels indépendant tiers).  
  
## <a name="perimeter-networkintranet"></a>Réseau de périmètre ― intranet  
 Les entreprises utilisent généralement le protocole FTP pour les communications basées sur Internet, de sorte que vous n'avez pas besoin de serveurs dans le réseau de périmètre intranet pour prendre en charge ce scénario.  
  
## <a name="e-business-domain"></a>Domaine E-Business  
 Les serveurs de ce domaine sont les suivants :  
  
-   **BizTalk Server (traitement, l’adaptateur FTP et les hôtes de suivi).** Le moteur d'exécution BizTalk Server est installé sur ce serveur, ainsi que les instances des hôtes qui contiennent les orchestrations, les pipelines, le Moteur de règles d'entreprise et les autres processus d'entreprise de BizTalk Server. C'est là que les ports, emplacements de réception, pipelines, mappages, schémas et assemblys de BizTalk Server se trouvent pour recevoir, router, traiter et envoyer des messages. Ce serveur dispose également d'une instance d'hôte qui prend en charge le suivi des données d'analyse du fonctionnement et de l'entreprise. En outre, cet hôte contient les instances de l'hôte qui exécute les adaptateurs d'envoi et de réception FTP.  
  
    > [!NOTE]
    >  Plus ces besoins augmentent, plus vous pouvez ajouter de serveurs BizTalk Server à votre environnement pour les instances de vos hôtes de traitement. Pour plus d’informations sur la configuration de BizTalk Server pour la haute disponibilité, consultez [planification pour une haute disponibilité](../core/planning-for-high-availability3.md).  
  
-   **Serveur de secret principal.** Identique à la [exemple d’Architecture : BizTalk Server de Base](../core/sample-architecture-base-biztalk-server.md).  
  
-   **SQL Server.** Identique à la [exemple d’Architecture : BizTalk Server de Base](../core/sample-architecture-base-biztalk-server.md).  
  
-   **Contrôleur de domaine.** Identique à celui inclus dans le [exemple d’Architecture : BizTalk Server de Base](../core/sample-architecture-base-biztalk-server.md).  
  
-   **Outils d’administration.** Identique à la [exemple d’Architecture : BizTalk Server de Base](../core/sample-architecture-base-biztalk-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples d’architecture pour les petites et moyennes entreprises](../core/sample-architectures-for-small-medium-sized-companies.md)   
 [Exemples de scénarios d’analyse du modèle](../core/sample-scenarios-for-threat-model-analysis.md)