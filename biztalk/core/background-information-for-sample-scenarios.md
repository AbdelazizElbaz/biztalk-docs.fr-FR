---
title: "Informations pour les exemples de scénarios d’arrière-plan | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security examples [TMA], background information
- DFD
- TMA, examples
ms.assetid: f9518fe7-9892-44f5-8e05-fe48bdb5161a
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 13dbb247e42116d5b308170d5ef365ed9f20d793
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="background-information-for-sample-scenarios"></a>Informations générales sur les exemples de scénarios
Cette rubrique contient des informations générales relatives aux scénarios de cette section.  
  
## <a name="background-for-all-scenarios"></a>Informations générales pour tous les scénarios  
 Avant la principale réunion sur le modèle des menaces, nous avons recueilli les informations générales suivantes. Ces informations s'appliquent à tous les scénarios d'utilisation que nous avons identifiés pour l'exemple d'architecture :  
  
-   Limites et étendue de l'architecture  
  
-   Limites entre les composants approuvés et non approuvés  
  
-   Modèle de configuration et d'administration pour chaque composant  
  
-   Hypothèses sur les autres composants et applications  
  
### <a name="boundaries-and-scope-of-the-architecture"></a>Limites et étendue de l'architecture  
  
-   Le pare-feu 2 aide à protéger les serveurs et les applications dans le domaine E-Business du réseau de périmètre et d'autres domaines de votre environnement (par exemple, un domaine d'entreprise ou des domaines pour d'autres applications).  
  
-   Le pare-feu 2 achemine tout le trafic entrant et sortant vers le domaine E-Business.  
  
-   Tous les groupes et comptes d'utilisateur qui accèdent à l'environnement BizTalk Server doivent être des groupes globaux dans le domaine E-Business.  
  
-   L'accès est limité au compte de service pour l'instance de l'hôte, à toute application qui dépose des messages dans le serveur de réception pour FILE, SQL ou Message Queuing, et aux administrateurs pour BizTalk Server, l'authentification unique de l'entreprise et Windows.  
  
### <a name="boundaries-between-trusted-and-untrusted-companies"></a>Limites entre les composants approuvés et non approuvés  
  
-   Le pare-feu 2 achemine tout le trafic entrant et sortant vers le domaine E-Business.  
  
-   Utilisez différents hôtes BizTalk comme limite de sécurité entre les applications au sein de BizTalk Server.  
  
-   Utilisez des hôtes approuvés uniquement lorsque vous faites confiance au code au sein de l'application (par exemple, n'exécutez pas de composants tiers dans un hôte approuvé).  
  
### <a name="configuration-and-administration-model-for-each-component"></a>Modèle de configuration et d'administration pour chaque composant  
 **Modèle de configuration :**  
  
-   Les composants d'exécution BizTalk Server sont installés uniquement sur les serveurs BizTalk Server.  
  
-   Le serveur de secret principal ne possède aucun composant supplémentaire.  
  
-   SQL Server contient toutes les bases de données BizTalk Server.  
  
-   Les serveurs dans les réseaux de périmètre ne disposent pas de composants BizTalk Server.  
  
-   Le client d'administration est utilisé pour administrer tous les serveurs du domaine E-Business.  
  
 **Modèle d’administration :**  
  
-   À partir d'un ordinateur (ou d'un ordinateur portable), un administrateur se connecte à l'ordinateur qui a les outils d'administration (à l'aide des services Terminal Server ou de la connexion Bureau à distance). Une fois que l'administrateur s'est connecté à l'ordinateur qui a les outils d'administration, l'administrateur peut utiliser les outils d'administration de BizTalk pour gérer tous les serveurs et applications au sein du domaine.  
  
### <a name="assumptions-about-other-components-and-applications"></a>Hypothèses sur les autres composants et applications  
 Tous les autres applications et composants qui interagissent avec l'environnement BizTalk Server sont dans un domaine autre que le domaine E-Business (par exemple, dans un réseau de périmètre). Le trafic à partir de ces applications et composants vers et depuis l'environnement BizTalk Server passe par le pare-feu 2.  
  
 Toutes les applications tierces pour BizTalk Server proviennent d'un fournisseur approuvé.  
  
### <a name="data-flow-diagrams"></a>Diagrammes de flux de données  
 L'élément final des informations générales pour chaque scénario d'utilisation est un diagramme de flux de données (DFD). Un diagramme de flux de données illustre le flux des données à travers l'architecture. Chaque scénario possède un diagramme de flux de données différent. Dans ce document, des diagrammes de flux de données contiennent les éléments indiqués dans la figure suivante.  
  
 **Figure 1 éléments de du diagramme**  
  
 ![Éléments du diagramme](../core/media/tdi-sec-dfd-legend.gif "TDI_Sec_DFD_Legend")  
  
## <a name="background-for-adapter-scenarios"></a>Informations générales pour les scénarios des adaptateurs  
 Dans notre exemple d'architecture, nous avons identifié les scénarios d'utilisation suivants en fonction de certains adaptateurs prêts à l'emploi que vous pouvez utiliser :  
  
-   Scénarios des adaptateurs HTTP et SOAP (services Web)  
  
-   Scénario de l'adaptateur de Message Queuing BizTalk  
  
-   Scénario de l'adaptateur FILE  
  
-   Scénario de l'adaptateur FTP  
  
 Pour chaque scénario, nous avons suivi ces étapes pour compléter l'analyse du modèle des menaces :  
  
-   Collecter les informations générales  
  
-   Créer et analyser le modèle des menaces  
  
-   Passer en revue les menaces  
  
-   Identifier les techniques et technologies de prévention  
  
 Pour chaque scénario, nous avons tenté de mettre au point des degrés génériques de niveau de menace que les diverses attaques peuvent représenter. Cependant, votre environnement ou expérience peut suggérer qu'une menace particulière mérite un degré différent de celui attribué. Comme dans tous les scénarios de sécurité, vos propres données sont les plus sûres pour déterminer les niveaux de menace et nous vous recommandons d'effectuer votre propre analyse, en vous servant de nos analyse et résultats.  
  
 Les informations générales, à l'exception du diagramme de flux de données, sont les mêmes pour tous nos scénarios d'utilisation. Dans les sections suivantes, nous présentons le diagramme de flux de données pour chaque scénario.  
  
## <a name="see-also"></a>Voir aussi  
 [Analyse du modèle](../core/threat-model-analysis.md)   
 [Exemples de scénarios d’analyse du modèle](../core/sample-scenarios-for-threat-model-analysis.md)   
 [Planification de la sécurité](../core/planning-for-security.md)   
 [Exemples d’architecture pour les petites et moyennes entreprises](../core/sample-architectures-for-small-medium-sized-companies.md)