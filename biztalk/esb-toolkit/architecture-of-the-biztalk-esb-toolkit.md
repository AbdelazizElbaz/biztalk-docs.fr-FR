---
title: Architecture de BizTalk ESB Toolkit | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a41674f5-5ea4-4a8f-a270-b67fd6854028
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 068eddfdd2138fbc92ad4821b2eaf9491ad39000
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="architecture-of-the-biztalk-esb-toolkit"></a>Architecture de BizTalk ESB Toolkit
Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] se compose d’une série de l’interaction des composants qui prennent en charge et implémentent un environnement de messagerie faiblement couplé qui facilite la génération d’applications d’entreprise basée sur le message. Les services et les composants se répartissent naturellement sept catégories suivantes :  
  
-   **Services Web.** Celles-ci exposent les services internes telles que le traitement d’itinéraire, gestion des exceptions, la résolution de points de terminaison et des mappages, [!INCLUDE[prague](../includes/prague-md.md)] opérations, interopérabilité Universal Description, Discovery and Integration (UDDI) et la transformation du message contenu.  
  
-   **Services d’itinéraire.** Notamment les services basés sur la messagerie et d’orchestration pour effectuer des transformations et le routage des messages. Vous pouvez créer des services personnalisés qui participent à dans le traitement de l’itinéraire. Notamment les services basés sur la messagerie et d’orchestration pour effectuer des transformations et le routage des messages. Vous pouvez créer des services personnalisés qui participent à dans le traitement de l’itinéraire.  
  
-   **Itinéraire sur écarts.** Ces recevoir des messages externes, attachement l’itinéraire approprié pour chaque message et traiter les données d’itinéraire ; ils utilisent la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] programme de résolution et de l’infrastructure de fournisseur de carte pour la résolution dynamique des points de terminaison et des métadonnées.  
  
-   **Écarts.** À la différence d’itinéraire sur écarts, ces messages d’externe dans une gamme de formats et transports, tels que HTTP, Service JMS (Java Message), IBM WebSphere MQ (WMQ), protocole de transfert de fichier (FTP), fichier plat et XML. Ils sont par défaut de BizTalk Server emplacements de réception qui utilisent éventuellement le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] composants de pipeline interopérabilité et le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] programme de résolution et de l’infrastructure de fournisseur de carte pour la résolution dynamique des points de terminaison et des métadonnées.  
  
-   **Écarter.** Implémente ports d’envoi pour la remise des messages à l’aide de formats et transports, tels que WCF, JMS, WMQ, FTP, HTTP, fichier plat, XML ou tous les autres formats personnalisés. Ils sont classique BizTalk Server, les ports d’envoi dynamiques qui sont directement liées à la boîte de Message et éventuellement utilisent le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] composants de pipeline interopérabilité et le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] programme de résolution et de l’infrastructure de fournisseur de carte pour la résolution dynamique des points de terminaison et métadonnées.  
  
-   **Infrastructure de gestion des exceptions.** Cela inclut le service Web (exception), l’API de gestion des exceptions et composants d’enrichissement, traitent et passer les détails de l’exception au portail de gestion ESB.  
  
-   **Portail de gestion ESB.** Cet exemple d’application fournit la configuration du Registre médiation d’exception, notification d’alerte et analytique.  
  
 La plupart de ces composants et services s’appuient sur les fonctionnalités implémentées par [!INCLUDE[prague](../includes/prague-md.md)], tels que les moteurs d’Orchestration, de Transformation et de règles d’entreprise et de la base de données de la boîte de Message. La figure 1 montre une vue schématique de catégories, les composants et les services qui se produisent généralement dans chaque catégorie, et les composants centraux du système BizTalk Server utilisé par le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].  
  
 ![Architecture ESB](../esb-toolkit/media/esbarchitecture.gif "ESBArchitecture")  
  
 **Figure 1**  
  
 **L’architecture et les composants de la[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]**  
  
## <a name="how-the-biztalk-esb-toolkit-works"></a>Fonctionnement de BizTalk ESB Toolkit  
 Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] accepte les messages entrants et agit sur eux, éventuellement (mais pas toujours) en effectuant des processus tels que la transformation, routage ou de tout autre personnalisées processus. Pour spécifier les opérations requises, les composants de traitement principaux requièrent chaque message à un bordereau de routage qui contient des instructions associées et les métadonnées qui définissent les processus à appliquer et les tâches à exécuter avec le contenu du message. Ces bordereaux de routage sont désignés comme des itinéraires et peuvent être automatiquement résolues, récupérées à partir d’un référentiel central et joint à un message lorsqu’il est reçu par une rampe d’entrée.  
  
 Cette approche de bordereau de routage fournit un couplage faible entre les services, ce qui signifie que l’architecture ESB ne requiert pas de la connaissance préalable du traitement spécifique pour chaque message. Elle doit simplement savoir quelle est la plage possible de processus et s’appliquent à chaque processus. Les diverses options de spécification des processus disponibles et du mappage entre les processus, de même que les instructions au sein des messages, fournissent un mécanisme flexible pour configurer et ajuster le comportement, sans modification du code ni redéploiement des composants.  
  
## <a name="design-patterns"></a>Modèles de conception  
 L’architecture ESB utilise, où les processus déposer des messages dans la base de données de la boîte de Message et les abonnés les récupèrent basé sur une instruction de traitement dans le message, met en œuvre efficacement le modèle de conception de l’ordinateur d’état. En outre, l’architecture ESB implémente et expose ses fonctionnalités principales d’une manière orientée services, y compris pour des applications externes via un ensemble de services Web principaux.  
  
 Cette approche à couplage lâche conception de BizTalk Server et [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]-applications basées sur des solutions très flexibles et elle est devenue une secteur meilleure pratique.