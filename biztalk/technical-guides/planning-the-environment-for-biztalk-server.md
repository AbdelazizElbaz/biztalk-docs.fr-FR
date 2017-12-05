---
title: "Planification de l’environnement pour BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e9ef0b4-eccb-47e2-bbb5-e859ffa0468c
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 66cd358f3d8a4fbda2c4ed43432f1ad8b2f6979e
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="planning-the-environment-for-biztalk-server"></a>Planification de l’environnement pour BizTalk Server
La section du guide des opérations de planification décrit les rôles et responsabilités associées à un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement. Elle inclut la planification des recommandations pour les couches application et données d’un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement et il fournit des recommandations de planification pour la mise à jour des étapes de gestion d’une solution BizTalk.  
  
 Comme on accède, « Si vous ne parvenez pas à planifier, vous envisagez d’échouer. » Lorsqu’il y a certainement des exceptions à ce Conseil sécurisée, réussite de l’implémentation d’une solution BizTalk de production n’est pas un d’eux. Cette rubrique d’introduction à la section Planification fournit une vue d’ensemble des décisions que vous devez effectuer lors de la planification de votre solution BizTalk.  
  
## <a name="deciding-whether-biztalk-server-is-the-right-tool-for-the-job"></a>Décider si BizTalk Server est l’outil adapté à la tâche  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]peut être considéré comme un « moteur d’intégration business ». Fondamentalement, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet d’intégrer des systèmes d’entreprise hétérogènes, les processus et les messages. Par exemple, un système d’entreprise qui échange des messages conformes à la norme EDI devrez intégrer à un système d’entreprise qui échange des messages conformes à la norme RosettaNet. Ou un système métier internes qui utilise SAP peut communiquer avec un autre système métier internes qui stocke les données dans une base de données Microsoft SQL Server. Ou peut-être a besoin d’un système métier qui peut uniquement envoyer ou recevoir des messages à l’aide du protocole FTP pour échanger des messages avec un système métier qui peut uniquement utiliser le protocole HTTP.  
  
 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]prend en charge l’intégration de ces systèmes disparates en jouant le rôle d’intermédiaire pour la remise de messages entre les systèmes. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]prend en charge un large éventail de protocoles de transport de la norme, formats d’échange de documents et des applications métier.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]fournit également des capacités d’automatisation de processus d’entreprise puissant dans le moteur d’Orchestration de BizTalk. Le Concepteur d’Orchestration BizTalk vous permet de créer des représentations visuelles des processus d’entreprise qui peuvent être intégrées dans le code exécutable qui est exécuté dans le moteur d’Orchestration de BizTalk.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]inclut également plusieurs autres fonctionnalités qui facilitent l’intégration d’entreprise, y compris un moteur de flux de travail de message, un moteur de règles d’entreprise (BRE) et les technologies pour les travailleurs tels qu’analyse BAM (Business Activity).  
  
 Pour plus d’informations sur l’utilisation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fonctionnalités de gestion de processus métier, consultez [livre blanc : Microsoft et BPM : vue d’ensemble technique](http://go.microsoft.com/fwlink/?LinkId=106015) (http://go.microsoft.com/fwlink/?LinkId=106015). Pour en savoir plus sur les technologies d’intégration différents proposés par Microsoft et les avantages d’un a via les autres, consultez [comprendre les Technologies de l’intégration de Microsoft](http://go.microsoft.com/fwlink/?LinkId=158452) (http://go.microsoft.com/fwlink/?LinkId=158452).  
  
 Certains scénarios d’intégration sont mieux adaptées aux autres produits Microsoft. Si votre objectif principal est à un des scénarios suivants, envisagez d’utiliser ces produits de Microsoft à la place de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]:  
  
|**Scénario**|**Produit à utiliser**|  
|------------------|------------------------|  
|Configuration de l’utilisateur|**Microsoft Identity Lifecycle Manager 2010**<br /><br /> Pour plus d’informations sur Microsoft Identity Lifecycle Manager 2010, consultez [Microsoft Identity Lifecycle Manager 2010 FP1](http://go.microsoft.com/fwlink/?LinkId=204577) (http://go.microsoft.com/fwlink/?LinkId=204577).|  
|Réplication des données entre les systèmes|**Réplication SQL Server**<br /><br /> Pour plus d’informations sur la réplication SQL Server, consultez [la réplication SQL Server 2008 R2](http://go.microsoft.com/fwlink/?LinkID=69978) (http://go.microsoft.com/fwlink/?LinkID=69978).|  
|Extraction de données, de transformation et chargement (ETL)|**SQL Server Integration Services (SSIS)**<br /><br /> Pour plus d’informations sur SQL Server Integration Services, consultez [SQL Server 2008 R2 Integration Services](http://go.microsoft.com/fwlink/?LinkId=152044) (http://go.microsoft.com/fwlink/?LinkId=152044).|  
  
## <a name="deciding-which-edition-of-biztalk-server-is-right-for-the-job"></a>Décider quelle édition de BizTalk Server est à droite de la tâche  
 Il existe quatre différentes éditions de BizTalk Server, chacune d’elles est destiné à des scénarios spécifiques. Les quatre éditions de BizTalk Server sont les suivantes :  
  
-   **Enterprise** - conçue pour les clients avec les exigences de niveau entreprise pour un volume élevé, la fiabilité et la disponibilité.  
  
-   **Standard** - conçue pour les entreprises avec volume modéré en matière de déploiement en puissance.  
  
-   **Branche** -version spécialisée de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] conçu pour le hub et spoke des scénarios de déploiement, y compris de RFID.  
  
-   **Développeur** : fournit toutes les fonctionnalités de l’édition entreprise pour le développement et à des fins de tests et est disponible en tant que BizTalk Server d’évaluation édition sans frais à des fins d’évaluation. Lors de l’installation en tant que l’édition d’évaluation, BizTalk Server fonctionnera pendant 120 jours.  
  
-   **RFID Enterprise** - conçue pour fournir une plateforme évolutive et extensible de développement, de déploiement et de gestion des solutions RFID et capteurs, comprend BizTalk RFID Server et BizTalk RFID Mobile.  
  
 Pour plus d’informations sur les différentes éditions de BizTalk Server, consultez [éditions de Microsoft BizTalk Server](http://go.microsoft.com/fwlink/?LinkId=108051) (http://go.microsoft.com/fwlink/?LinkId=108051).  
  
## <a name="planning-for-message-load"></a>Planification de la charge de Message  
 Une fois que vous avez déterminé que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] répond à l’intégration de votre entreprise a besoin, la prochaine chose que vous devez déterminer la charge de message à la solution BizTalk doit traiter. Ceci est une décision importante car différentes éditions de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ont des fonctions différentes de montée en puissance parallèle et de montée en puissance parallèle.  
  
 La clé pour déterminer la charge de message est de réaliser des tests de charge afin de déterminer le débit durable maximal (MST) et le Maximum acceptable de suivi débit (MSTT) de la solution BizTalk. Pour plus d’informations sur la mesure du débit maximal et les performances les meilleures pratiques en général, consultez le [Guide des performances BizTalk Server 2009](http://go.microsoft.com/fwlink/?LinkID=150492) (http://go.microsoft.com/fwlink/?LinkID=150492).  
  
## <a name="planning-for-expansion"></a>Planification d’Expansion  
 Envisagez d’implémenter une solution BizTalk à l’aide de l’édition Enterprise de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] si vous allez ajouter un nombre important de partenaires commerciaux, peut-être le point d’utiliser le cluster hôte, ou devez montée en puissance parallèle sur plusieurs ordinateurs en cours d’exécution [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans le Groupe BizTalk. Les éditions Standard et de branche de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne contiennent pas de plusieurs ordinateurs exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans un groupe ou un cluster hôte.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Rôles et responsabilités de BizTalk Server](../technical-guides/biztalk-server-roles-and-responsibilities.md)  
  
-   [Planification du niveau BizTalk Server](../technical-guides/planning-the-biztalk-server-tier.md)  
  
-   [Planification de la couche base de données](../technical-guides/planning-the-database-tier.md)  
  
-   [Planification des environnements de test, de préproduction et de production](../technical-guides/planning-the-development-testing-staging-and-production-environments.md)