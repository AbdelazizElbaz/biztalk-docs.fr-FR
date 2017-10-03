---
title: "Exemple d’Architecture : Adaptateurs HTTP et SOAP | Documents Microsoft"
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
- SOAP adapters, security
- Web Publishing
- security, examples
- security, architecture
- SOAP adapters, architecture examples
- examples, architecture
- architecture, security
- HTTP adapters, architecture examples
- reverse proxy rules
- ISA Server implementation
- HTTP adapters, security
ms.assetid: 935197d0-5108-4970-b237-3c6d5b40c5e9
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dae8be185084a9a838876e3d50b605a63c161b66
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sample-architecture-http-and-soap-adapters"></a>Exemple d’Architecture : Adaptateurs HTTP et SOAP
Cette rubrique décrit l'exemple d'architecture associé à l'utilisation des adaptateurs HTTP et SOAP pour échanger des messages.  
  
 La figure suivante illustre les composants de l'exemple d'architecture BizTalk Server associé à l'utilisation des adaptateurs HTTP et SOAP.  
  
 **Figure 1 exemple d’architecture qui affiche les adaptateurs HTTP ou SOAP**  
  
 ![Exemple d’architecture pour l’adaptateur HTTP ou SOAP](../core/media/tdi-sec-refarch-http.gif "TDI_Sec_RefArch_HTTP")  
  
 Cet exemple d'architecture contient les composants présentés dans les sections suivantes.  
  
## <a name="perimeter-networkinternet"></a>Réseau de périmètre ― Internet  
 Si vous utilisez les adaptateurs SOAP et HTTP, il est recommandé d'utiliser les règles de proxy inverse (l'implémentation du serveur TMG est appelée Publication sur le Web) pour relayer le message en provenance du pare-feu connecté à Internet (Pare-feu 1) vers le pare-feu protégeant le domaine E-Business (Pare-feu 2), et de ce pare-feu vers le serveur BizTalk Server qui exécute l'hôte isolé. Pour plus d’informations sur les règles de publication Web, consultez le site Web de Microsoft à [http://go.microsoft.com/fwlink/?LinkID=205340](http://go.microsoft.com/fwlink/?LinkID=205340) (http://go.microsoft.com/fwlink/?LinkID=205340).  
  
> [!NOTE]
>  Si vous utilisez le proxy inverse, vous n'avez pas besoin de serveurs Web dans le réseau de périmètre.  
  
## <a name="perimeter-networkintranet"></a>Réseau de périmètre ― intranet  
 Les entreprises utilisent généralement les protocoles HTTP et SOAP pour les communications basées sur Internet, de sorte que vous n'avez pas besoin de serveurs dans le réseau de périmètre intranet pour prendre en charge ce scénario. Si vous avez une application interne dans l'intranet intégrée à BizTalk Server via les protocoles HTTP et SOAP, vous devez suivre les recommandations relatives au réseau de périmètre Internet.  
  
## <a name="e-business-domain"></a>Domaine E-Business  
 Ce domaine contient toutes les infrastructures et applications utilisées par votre implémentation BizTalk Server. Les serveurs de ce domaine sont les suivants :  
  
-   **BizTalk Server (traitement et de suivi des hôtes).** Le moteur d'exécution BizTalk Server est installé sur ce serveur, ainsi que les instances des hôtes qui contiennent les orchestrations, les pipelines, le Moteur de règles d'entreprise et les autres processus d'entreprise de BizTalk Server. Ce serveur dispose également d'une instance d'hôte qui prend en charge le suivi des données d'analyse du fonctionnement et de l'entreprise.  
  
    > [!NOTE]
    >  Plus ces besoins augmentent, plus vous pouvez ajouter de serveurs BizTalk Server à votre environnement pour les instances de vos hôtes de traitement.  
  
-   **BizTalk Server (hôtes isolés pour les adaptateurs SOAP et HTTP).** Le moteur d'exécution BizTalk Server est installé sur ce serveur, ainsi que les instances des hôtes qui contiennent les adaptateurs HTTP et SOAP. Ces hôtes sont exécutés sur un serveur distinct car ces adaptateurs nécessitent d'installer IIS (Internet Information Services) sur l'ordinateur sur lequel ils sont exécutés.  
  
    > [!NOTE]
    >  Plus ces besoins augmentent, plus vous pouvez ajouter de serveurs BizTalk Server à votre environnement pour les instances de vos hôtes d'adaptateur HTTP et SOAP. Dans ce cas, vous devez également configurer l'équilibrage de la charge réseau. Pour plus d’informations sur la configuration de BizTalk Server pour la haute disponibilité, consultez [planification pour une haute disponibilité](../core/planning-for-high-availability3.md).  
  
-   **Serveur de secret principal.** Identique à la [exemple d’Architecture : BizTalk Server de Base](../core/sample-architecture-base-biztalk-server.md).  
  
-   **SQL Server.** Identique à la [exemple d’Architecture : BizTalk Server de Base](../core/sample-architecture-base-biztalk-server.md).  
  
-   **Contrôleur de domaine.** Identique à la [exemple d’Architecture : BizTalk Server de Base](../core/sample-architecture-base-biztalk-server.md).  
  
-   **Outils d’administration.** Identique à la [exemple d’Architecture : BizTalk Server de Base](../core/sample-architecture-base-biztalk-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples d’architecture pour les petites et moyennes entreprises](../core/sample-architectures-for-small-medium-sized-companies.md)   
 [Exemples de scénarios d’analyse du modèle](../core/sample-scenarios-for-threat-model-analysis.md)