---
title: "Haute disponibilité pour les hôtes BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3153f7f7-7e82-4b0c-9b48-e9f871de285d
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 29636a63f7847017b233275ee3dd7c2c389c43be
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="high-availability-for-biztalk-hosts"></a>Haute disponibilité pour les hôtes BizTalk
BizTalk Server offre une grande souplesse en matière de haute disponibilité, car vous pouvez stratégiquement dédier des hôtes logiques pour exécuter des zones spécifiques de fonctionnalités, telles que recevoir et envoyer des messages ou le traitement des orchestrations, qui peuvent être physiquement déployé sur plusieurs serveurs.  
  
 Un hôte BizTalk est un conteneur logique dans un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe peut héberger [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] éléments tels que l’adaptateur (y compris des pipelines) des gestionnaires d’envoi, emplacements de réception et orchestrations. En général, il faut regrouper dans un hôte particulier des éléments aux propriétés de mise à l'échelle similaires.  
  
 Après avoir créé un ordinateur hôte, vous pouvez la déployer sur une physique [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateur en tant qu’une instance d’hôte. Une instance d’hôte s’exécute comme un service Windows, BTSNTSvc.exe (ou BTSNTSvc64.exe pour l’instance d’hôte 64 bits), sur le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateur. Pour chaque hôte, vous pouvez avoir qu’une seule instance sur un particulier [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateur. Toutefois, vous pouvez avoir des instances d’un hôte particulier sur un ou plusieurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateurs et vous pouvez avoir des instances d’hôtes différents sur un particulier [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateur.  
  
 Les éléments qui figurent dans les hôtes BizTalk peuvent effectuer les fonctions suivantes :  
  
-   **Réception**. ces éléments effectuent le traitement initial des messages après leur récupération dans un emplacement de réception. Lorsqu’un ordinateur hôte contient un élément de réception, tel qu’un emplacement de réception (avec un pipeline), le message, le décodage et le déchiffrement se produit dans un pipeline au sein de l’hôte.  
  
-   **Envoi de**. ces éléments effectuent le traitement final des messages avant leur transmission au port d'envoi. Lorsqu’un ordinateur hôte contient un élément de réception, par exemple un port d’envoi, la signature des messages et le chiffrement se produit dans un pipeline au sein de l’hôte.  
  
-   **Traitement**. Ces éléments traitent les messages selon les instructions contenues dans les orchestrations.  
  
 Un hôte BizTalk peut contenir des éléments qui reçoivent, envoient et traitent des messages. Pour la gestion plus facile et d’évolutivité, nous vous recommandons de créer des hôtes différents désignés pour chaque fonction. En particulier, nous vous recommandons d’utiliser des hôtes différents pour le traitement et pour les opérations d’envoi/réception.  
  
 Par exemple, si vous recevez un message, exécutez une orchestration et recevez dix messages, vous devez séparer les fonctions d'envoi et de réception et les répartir sur deux hôtes distincts. En effet, le trafic correspondant aux éléments d'envoi sera dix fois plus important que celui des éléments de réception. Si vous recevez un message, exécutez une orchestration et envoyez un seul message, vous pouvez considérer ces éléments comme des unités de travail et les regrouper dans un seul et même hôte. Une autre possibilité consiste à les répartir entre trois hôtes différents afin d'améliorer les performances et la flexibilité. En revanche, les coûts de gestion s'en trouvent accrus.  
  
 Hôtes BizTalk sont un des deux types, *In-process* ou *isolé*. Hôtes in-process s’exécuter à l’intérieur de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processus d’exécution (BTSNTSvc.exe ou BTSNTSvc64.exe) et les hôtes isolés ne s’exécutent pas dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processus d’exécution. Hôtes isolés sont utilisés uniquement à la réception pour les adaptateurs de réception isolées. Le tableau suivant répertorie les éléments que chaque type d'hôte est susceptible de contenir.  
  
|Type d’hôte|Éléments contenus|  
|---------------|---------------------------|  
|In-process|-Orchestrations<br />-Gestionnaires d’envoi de l’adaptateur<br />-Gestionnaires de réception adaptateur in-process|  
|Isolé|-Gestionnaires de réception HTTP, SOAP<br />-Gestionnaires de réception n’importe quel autre adaptateur isolé|  
  
 Pour plus d’informations sur la gestion des hôtes BizTalk et les instances d’hôte, consultez [gestion d’hôtes BizTalk et les Instances d’hôte](http://go.microsoft.com/fwlink/?LinkID=154191) (http://go.microsoft.com/fwlink/?LinkID=154191) dans l’aide de BizTalk Server.  
  
 Pour fournir une haute disponibilité pour les hôtes BizTalk, vous devez disposer des deux ou plusieurs instances d’hôte pour chaque ordinateur hôte (sur deux ordinateurs ou plus) dans votre environnement. En ayant plus d’une instance d’hôte pour chaque ordinateur hôte pour vous assurer que si une instance d’hôte devenue indisponible, les instances d’hôtes sur d’autres ordinateurs qui exécutent des instances du même hôte peut reprendre les fonctions de l’instance d’hôte problématique ou ayant échoué, et que l’ensemble du système continue de fonctionner avec une perturbation minimale.  
  
## <a name="disadvantages-of-additional-hosts"></a>Inconvénients des hôtes supplémentaires  
 Bien qu’il existe des avantages de la création des instances d’hôte supplémentaires, il existe également des inconvénients potentiels si trop d’instances d’hôte sont créées. Chaque instance d’hôte est un service Windows (BTSNTSvc.exe ou BTSNTSvc64.exe), qui génère une charge supplémentaire par rapport à la base de données MessageBox et consomme des ressources informatiques, telles que le processeur, mémoire et les threads. Vous avez les raisons suivantes n’est ne pas configuré trop d’instances d’hôte supplémentaires :  
  
-   Plusieurs compteurs de performances sont signalés par l’hôte avec une granularité de trop. Cela affecte la facilité d’utilisation pour l’administrateur qui devra parcourir une grande quantité de données. Cela a un impact négatif sur la vue globale de que l’administrateur a.  
  
-   Chaque hôte consomme beaucoup de mémoire qui peut entraîner une situation de limitation et une diminution des performances.  
  
-   Si les ordinateurs hôtes ont des adaptateurs qui assure en continu d’interrogation de réception, chaque hôte interroge la base de données à intervalles courts, ce qui entraînerait la diminution des performances.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Montée en charge des hôtes de réception](../technical-guides/scaling-out-receiving-hosts.md)  
  
-   [Mise en cluster des hôtes de réception](../technical-guides/clustering-receiving-hosts.md)  
  
-   [Montée en charge des hôtes de traitement](../technical-guides/scaling-out-processing-hosts.md)  
  
-   [Montée en charge des hôtes d’envoi](../technical-guides/scaling-out-sending-hosts.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des ordinateurs hôtes et les Instances d’hôte](../technical-guides/configuring-hosts-and-host-instances.md)   
 [Configuration d’un hôte de suivi dédié](../technical-guides/configuring-a-dedicated-tracking-host.md)   
 [Planification pour une haute disponibilité2](../technical-guides/planning-for-high-availability2.md)   
 [Haute disponibilité pour les bases de données](../technical-guides/high-availability-for-databases.md)   
 [Haute disponibilité pour le serveur de secret principal](../technical-guides/high-availability-for-the-master-secret-server.md)