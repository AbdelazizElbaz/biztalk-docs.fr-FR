---
title: "Montée en puissance parallèle de l’hôte de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e9f78710-93fa-4877-8273-a1634d768d88
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 843e20e76f7320555a0cfab5af5103ce3fd597d1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scaling-out-receiving-hosts"></a>Montée en puissance parallèle de l’hôte de réception
Pour que les hôtes de réception hautement disponible, vous devez disposer d’au moins deux [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateurs qui exécutent des instances de chaque hôte de réception. Par la mise à l’échelle des hôtes de réception, vous pouvez augmenter la disponibilité pour [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] déploiements qui sollicitent de messagerie. Bien que son traitement des orchestrations soit minimal, ce modèle de déploiement permet d'acheminer de nombreux messages de types différents de manière rapide et fiable.  
  
 Vous pouvez encore améliorer la sécurité et l'évolutivité au sein de votre environnement en séparant l'hôte de réception des hôtes chargés du traitement des orchestrations et de l'envoi des messages, car il est alors possible de sécuriser et de déployer chaque hôte indépendamment des autres. Par exemple, vous pouvez attribuer deux ordinateurs supplémentaires (instances de l'hôte) à l'hôte de réception sans pour autant en ajouter aux hôtes de traitement ou d'envoi.  
  
## <a name="understanding-in-process-and-isolated-receiving-hosts"></a>Présentation de In-Process et isolés hôtes de réception  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]intègre des applications pour fournir des services d’entreprise. L’intégration est généralement représentée par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] reçoit un document (à partir d’une application), traite le document et envoie le document à l’application ou une autre application. Le processus est appelé une transaction de document.  
  
 En règle générale, une transaction commence avec un analyse d’un canal de protocole spécifique et de la réception d’un document de l’adaptateur BizTalk. Le *carte* est appelé ainsi car il connecte d’autres applications [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. En fonction de sa fonction, il peut être un adaptateur d’envoi ou un adaptateur de réception. La plupart des adaptateurs par défaut est un composant .NET avec la fonction de réception et la fonction d’envoi intégrée à un assembly .NET. En fonction de l’espace de mémoire de processus dans lequel réside un adaptateur, il est soit un in-process (réception) adaptateur ou un hôte isolé (réception) l’adaptateur. Un adaptateur in-process peut uniquement être hébergé par le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processus (BTSNTSvc.exe) et un adaptateur isolé est conçu pour être hébergé par un autre processus. Par exemple, l’adaptateur HTTP et l’adaptateur SOAP sont hébergés par le processus Internet Information Services (IIS). Ils sont essentiellement des extensions ISAPI. En revanche, tous les adaptateurs d’envoi sont des adaptateurs in-process.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Configuration crée deux hôtes par défaut, l’hôte in-process est appelée BizTalkServerApplication, et l’hôte isolé est appelé BizTalkServerIsolatedHost. Un hôte remplit deux fonctions : un est un regroupement logique du [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] les éléments de ces éléments peuvent donc être affectées à différentes [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processus et l’autre est contrôle de la sécurité. Vous devez spécifier un groupe Windows pour un ordinateur hôte. Seuls les utilisateurs de ce groupe peuvent envoyer des documents pour les adaptateurs hébergés par le *instances d’hôte* attribués à cet hôte.  
  
 Chacun des ordinateurs hôtes par deux défaut possède une instance d’hôte. Une instance d’hôte n’a pas de nom, mais il est associée à un ordinateur hôte. L’instance de l’hôte BizTalkServerApplication est en fait le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] (BTSNTSvc.exe) de processus du service sur un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateur dans le groupe BizTalk. L’instance de l’hôte BizTalkServerIsolatedHost n’est pas directement lié à un processus. Il est associé au processus qui héberge l’adaptateur de réception.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Configuration crée également un *Gestionnaire de réception* pour chacune des cartes à l’exception de SMTP par défaut (SMTP est un adaptateur d’envoi). Une des propriétés du Gestionnaire de réception est le nom d’hôte. Qui est la façon dont il est lié à un hôte et les instances d’hôte de cet hôte.  
  
 En plus d’un adaptateur hôte, instance de l’hôte et Gestionnaire de réception, vous devez configurer un port de réception avant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] peut commencer à recevoir des documents. Un port de réception contient des emplacements de réception. Un emplacement de réception a une propriété de gestionnaire de réception. La logique, vous pouvez tracer à le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processus qui traite ce port de réception.  
  
 Dans la configuration de port de réception, vous spécifiez éventuellement maps. Dans la configuration d’emplacement de réception, vous devez spécifier un pipeline utilisé pour le prétraitement du document. Désigné [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processus gère tous les éléments à partir de la réception d’un document, le document, en le document de mappage de prétraitement. Ceci est le même pour les instances d’hôte in-process et les instances d’hôte isolé.  
  
## <a name="scaling-out-in-process-receiving-hosts"></a>Montée en puissance parallèle In-Process réception héberge  
 L’illustration suivante montre un [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] déploiement qui offre une haute disponibilité pour les instances de l’hôte de réception à un hôte deux chacun sur un autre ordinateur. Notez que dans cette figure l’hôte d’envoi et de traitement n’est pas hautement disponible, étant donné qu’une seule instance d’hôte du traitement des éléments BizTalk affectés à l’hôte.  
  
 ![Plusieurs hôtes de réception de Messages](../core/media/tdi-ha-scalereceive.gif "TDI_HA_ScaleReceive")  
  
 Dans les cas de déploiement à grande échelle, dans des scénarios de partenariats commerciaux multiples ou d'utilisation de protocoles différents, vous avez la possibilité de répartir la fonction de réception entre plusieurs hôtes. Vous pouvez par exemple créer un hôte de réception des messages pour chaque adaptateur ou des hôtes distincts pour la réception des messages provenant de partenaires différents. Lorsque vous mettez en place plusieurs hôtes de réception, vous pouvez créer des limites de sécurité et faciliter la gestion et l'évolutivité de votre environnement sans que ce dernier puisse bénéficier pour autant d'une disponibilité élevée. Pour obtenir un environnement à haute disponibilité, vous devez créer deux instances de l'hôte (ou plus) pour chaque hôte de réception créé. Par exemple, vous pouvez créer trois hôtes de réception différents (A, B et C) pour recevoir des messages à partir de trois sociétés différentes. Pour faire en sorte que tous ces hôtes bénéficient d'une disponibilité élevée, vous devez ensuite créer des instances d'hôte sur deux ordinateurs ou plus pour chaque hôte. Vous pouvez disposer des instances de chaque hôte sur un seul ordinateur sans perdre pour autant les fonctionnalités de limite de sécurité, de gestion ou d'évolutivité.  
  
 La figure suivante illustre une haute disponibilité sur trois ordinateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement avec les hôtes dédié à la réception des messages provenant de différentes sociétés.  
  
 ![Montée en puissance parallèle des hôtes de réception](../technical-guides/media/04bd4234-dc71-49d8-b630-0643390b29f0.gif "04bd4234-dc71-49d8-b630-0643390b29f0")  
  
 Pour fournir une haute disponibilité dans cette configuration, chaque ordinateur exécute les trois instances d’hôte : une instance pour chacune des trois sociétés. Les instances de l'hôte de chaque société contiennent les emplacements de réception et les pipelines permettant la communication avec ces sociétés. Pendant les opérations classiques, tant que vous avez effectué le travail nécessaire pour la montée en puissance parallèle devant les adaptateurs de réception, la charge de messagerie est répartie entre les trois instances pour chaque hôte. Si l'exécution d'une instance de l'hôte échoue sur un ordinateur, les instances de l'hôte exécutées sur les deux autres ordinateurs constituent une redondance permettant de conserver une disponibilité de service.  
  
## <a name="scaling-out-isolated-receiving-hosts"></a>Mise à l’échelle isolé à l’hôte de réception  
 Outre les instances d’hôte, le processus de mise à l’échelle et de fournir une haute disponibilité pour les hôtes de réception dépend également des adaptateurs que vous implémentez dans votre déploiement. Chaque adaptateur possède des caractéristiques de protocole particulières qui rendent la planification et le déploiement différents à chaque fois. Néanmoins, [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] vous permet de mettre en place une solution haute disponibilité identique pour tous les adaptateurs, principalement par l'intermédiaire d'ordinateurs et d'instances d'hôte supplémentaires.  
  
 Selon le protocole utilisé, certains adaptateurs de réception nécessitent un mécanisme supplémentaire pour la distribution des messages entrants sur plusieurs ordinateurs afin de fournir une disponibilité élevée. Par exemple, [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] solutions qui utilisent l’adaptateur HTTP ou SOAP (également appelé l’adaptateur de services Web) nécessitent un équilibreur de charge telles que charger équilibrage réseau (NLB) pour distribuer la charge de réception, comme indiqué dans l’illustration suivante.  
  
 ![Hôte de réception montée en puissance parallèle isolé](../technical-guides/media/cb38ec25-bfb0-4a55-8464-b7918b6fc746.gif "cb38ec25-bfb0-4a55-8464-b7918b6fc746")  
  
 Pour plus d’informations sur les directives de haute disponibilité pour les adaptateurs les plus courants dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], consultez la section « Mise à l’échelle les adaptateurs de réception du serveur BizTalk » [hôtes de réception Scaled-Out](http://go.microsoft.com/fwlink/?LinkId=151283) (http://go.microsoft.com/ fwlink / ? LinkId = 151283) dans [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] aide.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de clusters hôtes de réception](../technical-guides/clustering-receiving-hosts.md)   
 [Mise à l’échelle des hôtes de traitement](../technical-guides/scaling-out-processing-hosts.md)   
 [Montée en charge des hôtes d’envoi](../technical-guides/scaling-out-sending-hosts.md)