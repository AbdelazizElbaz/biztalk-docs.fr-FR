---
title: "Fonctionnement du Service de la Solution orientée services | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service solution tutorial, background information
- service solutions, about service solutions
- service solution tutorial, about service solution tutorial
- Service Oriented Architecture (SOA)
ms.assetid: 56a2ad90-74bb-489a-ab1d-900f3bea3d64
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a8be3a1e7a05c2c60f1ab16c6da4df74dddf7adb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="understanding-the-service-oriented-solution"></a>Fonctionnement du Service de la Solution orientée services
La solution orientée services présente une application de création de rapports de solde créditeur conçue comme un service. Cette application, à son tour, utilise trois applications principales, exposées elles-mêmes en tant que services, pour obtenir les informations nécessaires au solde créditeur.  
  
 Une architecture orientée services est une approche qui chevauche partiellement la création de systèmes distribués. Une approche orientée services présente plusieurs caractéristiques :  
  
-   Faiblement couplée. La logique d'entreprise de l'application est séparée de la logique de gestion du service.  
  
-   Détectable. Il doit exister un mécanisme pour que les applications trouvent le service.  
  
-   Contractuelle. L'interface pour le service implémente le contrat entre les utilisateurs et le service.  
  
 Bien que la documentation traite souvent les approches orientées services comme des synonymes de services Web, ce n'est pas nécessairement le cas. Les services Web ont une manière intéressante d'implémenter les solutions orientées services mais vous pouvez utiliser d'autres technologies, telles que l'accès à distance .NET, pour créer des services.  
  
 Pour plus d’informations sur les architectures orientées service, consultez « Service Interface » à [http://go.microsoft.com/fwlink/?LinkId=46185](http://go.microsoft.com/fwlink/?LinkId=46185) et « Service-Oriented Integration » à [http://go.microsoft.com/fwlink/?LinkId=46186](http://go.microsoft.com/fwlink/?LinkId=46186).  
  
## <a name="reader-guidance"></a>Conseils à destination du lecteur  
 La documentation de cette solution part du principe que vous êtes familiarisé avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Il suppose également que vous comprenez les concepts élémentaires relatifs à l'intégration des applications de l'entreprise et aux services Web.  
  
 En outre, pour lire et suivre la documentation du développeur, vous devez être familiarisé avec la création d’applications à l’aide de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] et effectuer les tâches suivantes : création de projets, références et le débogage et test BizTalk solutions.  
  
## <a name="credit-card-reporting-at-woodgrove-bank"></a>Création de rapports de carte de crédit chez Woodgrove Bank  
 La solution d'architecture orientée services est un service de création de rapports de solde de carte de crédit pour Woodgrove Bank. Bien que la banque soit fictive, le scénario est basé sur une application client réellement déployée.  
  
 Dans le scénario, les demandes de soldes de carte de crédit proviennent de deux sources :  
  
-   Une application de réponse vocale interactive (IVR).  
  
-   Un client interactif, tel qu'une page Web ou une application cliente personnalisée.  
  
 La solution reçoit des demandes de l'application de réponse vocale interactive (IVR) par l'intermédiaire de MQSeries. Elle gère les demandes du client interactif par l'intermédiaire d'un service Web utilisant HTTP et SOAP.  
  
 Les nouvelles applications d'architecture orientée services doivent souvent travailler avec des applications héritées qui utilisent des technologies plus anciennes et fonctionner avec des applications modernes, telles que des sites Web qui utilisent des services Web. Le scénario reflète cette exigence du monde réel : l'application de réponse vocale interactive (IVR) représente une application héritée tandis que l'application cliente de service client est une application moderne.  
  
 L'application Woodgrove Bank utilise les données de trois systèmes principaux hérités pour répondre aux demandes :  
  
-   Une application qui fournit la limite de crédit générale. Il s'agit d'un système SAP sur un macroordinateur.  
  
-   Un système de transactions en attente qui signale le nombre total des transactions en attente dans le compte. Ce système est un macroordinateur ou un système AS/400. La solution utilise un service Web et un Microsoft Host Integration Server (HIS) pour communiquer avec le macroordinateur ou le système AS/400.  
  
-   Un système de suivi des paiements qui indique le dernier paiement effectué dans le système. Le système de suivi des paiements peut être atteint à l'aide de MQSeries.  
  
 Après avoir collecté et compilé les informations des systèmes hérités, la solution renvoie la réponse à l'application d'origine, puis au client.  
  
## <a name="business-requirements"></a>Impératifs de l'entreprise  
 Comme l'application de création de rapports de crédit répond en temps réel aux demandes des clients, elle doit présenter une faible latence pour gérer les demandes rapidement. En outre, elle doit également être en mesure de gérer un nombre élevé de demandes simultanées. La solution utilise des informations sensibles et une interface publique, de sorte que la sécurité est une préoccupation majeure. Enfin, le service doit être fiable.  
  
 Pour plus d’informations sur la façon dont la solution répond à ces exigences, consultez [développement d’une Solution orientée services](../core/developing-a-service-oriented-solution.md).  
  
## <a name="performance-characteristics"></a>Caractéristiques de performances  
 Pour répondre aux impératifs de l'entreprise, le scénario présente les caractéristiques de performances suivantes :  
  
-   Débit soutenu de 40 demandes entrantes par seconde.  
  
-   Débit de pointe de 100 demandes entrantes par seconde.  
  
-   90 % des demandes à traiter (allant vers ou sortant de BizTalk Server) en moins de 1000 millisecondes.  
  
-   95 % des demandes à traiter (allant vers ou sortant de BizTalk Server) en moins de 2000 millisecondes.  
  
-   100 % des demandes à traiter (allant vers ou sortant de BizTalk Server) en moins de 5000 millisecondes.  
  
> [!NOTE]
>  Ces temps n'incluent pas les temps de latence des systèmes principaux.  
  
## <a name="three-versions-of-the-solution"></a>Trois versions de la solution  
 Il existe trois versions de la solution :  
  
-   La version stub remplace tous les systèmes principaux par des stubs logiciels. Les stubs simulent les systèmes principaux. Cette version offre un moyen rapide de déployer et d'exécuter la solution sur un seul ordinateur.  
  
-   La version d'adaptateur utilise des adaptateurs BizTalk pour se connecter aux systèmes principaux. Cette version est celle qui vient la première à l'esprit pour implémenter la solution. Cependant, l'envoi des messages aux systèmes principaux à l'aide des adaptateurs entraîne une latence importante dans l'obtention des réponses. Alors que les adaptateurs eux-mêmes peuvent présenter une très faible latence, l'architecture distribuée de BizTalk Server les oblige à communiquer avec les instances d'hôte de l'orchestration via la base de données MessageBox. Cela entraîne des allers-retours vers la base de données et affecte les délais de latence.  
  
-   La version Inline remplace les adaptateurs par le code Inline qui communique directement avec les systèmes principaux. La version Inline de la solution a la latence la plus faible et le débit le plus élevé.  
  
 Le guide de déploiement fournit des consignes de création et de déploiement des trois versions de la solution et offre un moyen, dans chaque solution, de simuler la connexion via HIS au système de transactions en attente. Pour plus d’informations sur la création et déploiement de la solution, consultez [déployer la Solution orientée services](../core/deploying-the-service-oriented-solution.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Solution orientée services](../core/service-oriented-solution.md)