---
title: Architecture de JD Edwards OneWorld | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: architecture
ms.assetid: 9200a090-a587-4b60-9447-d281580f2078
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1daee7d44152817da1ac536dd98cbaf898e2ac7c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="architecture-of-jd-edwards-oneworld"></a>Architecture de JD Edwards OneWorld
L'adaptateur Microsoft BizTalk pour JD Edwards OneWorld permet d'accéder aux fonctions commerciales de JD Edwards OneWorld. JD Edwards OneWorld communique entre les ordinateurs client et serveur à l'aide d'une architecture de messagerie propriétaire nommée JDENet. Celle-ci est implémentée par les classes de connecteur JD Edwards OneWorld figurant dans les fichiers JAR, Connector.jar et Kernel.jar. La communication est implémentée à l’aide de TCP/IP comme protocole de transport, avec le port par défaut 6009 ou 6010. Pour obtenir une description de l’emplacement où cette valeur est définie, consultez [comment définir les propriétés Transport JD Edwards OneWorld](../core/how-to-set-jd-edwards-oneworld-transport-properties.md).  
  
 **Architecture de l’adaptateur BizTalk pour JD Edwards OneWorld**  
  
 ![](../core/media/jdedadapter-01-architecture.gif "JDEdAdapter_01_Architecture")  
  
 Les appels des fonctions commerciales de JD Edwards OneWorld requièrent deux messages :  
  
-   Le premier message répond avec l'emplacement du serveur qui traite la fonction commerciale. Cela est accompli en effectuant une recherche dans un ensemble de tables appelé *objet configuration le mappage de*.  
  
-   Le second message envoie un tampon de message mis en forme contenant les arguments à transmettre via JD Edwards OneWorld au serveur approprié et attend une réponse. Les tampons sont mis en forme conformément aux définitions de type des structures C++ sous-jacentes.  
  
## <a name="inbound-services-at-design-time"></a>Services entrants au moment de la conception  
  
-   Au moment de la conception, vous créez votre port, sélectionnez l'adaptateur et fournissez les informations d'identification pour la connexion au serveur JD Edwards OneWorld cible. L'environnement de développement Visual Studio appelle l'infrastructure d'adaptateurs pour demander des informations de conception pour ce port. L'adaptateur BizTalk pour JD Edwards OneWorld utilise Browsingagent pour ce port.  
  
-   Au moment de la conception, BizTalk Server demande des informations en appelant l'adaptateur.  
  
-   Browsingagent convertit la demande en code natif JD Edwards OneWorld, puis la transmet à JD Edwards OneWorld via la connexion API ThinNet (établie dans Connector.jar et Kernel.jar).  
  
-   Une fonction commerciale personnalisée est installée via l’installation BTSREL : il expose les principales fonctions commerciales.  
  
-   La liste des modules de JD Edwards OneWorld est initialement renvoyée et transportée vers Visual Studio, dans lequel elle renseigne l'Assistant Adaptateur.  
  
-   Vous pouvez développer la hiérarchie pour afficher le nom de la bibliothèque et le nom du module.  
  
-   Lorsque vous sélectionnez un module spécifique, des schémas pour toutes les fonctions de ce module s'affichent. L'adaptateur obtient les informations requises auprès de JD Edwards OneWorld, et Browsingagent crée les schémas.  
  
-   Les schémas sont ajoutés à l'orchestration du projet BizTalk Server.  
  
## <a name="inbound-services-at-run-time"></a>Services entrants au moment de l'exécution  
  
-   BizTalk Server appelle l'adaptateur BizTalk pour JD Edwards OneWorld pour envoyer un message sur un port spécifique.  
  
-   L'agent d'exécution convertit le code XML en code JD Edwards natif.  
  
-   L'agent d'exécution envoie la demande via ThinNet au système d'entreprise JD Edwards spécifié dans les propriétés de transport du port d'envoi.  
  
-   La fonction commerciale principale est exécutée sur le système JD Edwards, qui génère ensuite un document de réponse, lequel indique si l'opération a réussi ou échoué, ainsi que les paramètres de données renvoyés par la fonction commerciale.  
  
-   Le message envoyé à JD Edwards OneWorld constitue une architecture à message unique et à réponse unique. Il est impossible de traiter plusieurs messages simultanément.  
  
-   Le document de réponse est renvoyé via ThinNet, converti au format XML et retransmis à BizTalk Server.  
  
## <a name="outbound-events-at-design-time"></a>Événements sortants au moment de la conception  
  
-   Aucune création systématique de métadonnées d'événement n'est disponible.  
  
-   Une télécopie du document d'événements doit être fournie à Visual Studio afin qu'un schéma puisse être généré et incorporé au projet avec l'espace de noms cible.  
  
## <a name="outbound-events-at-run-time"></a>Événements sortants au moment de l'exécution  
  
-   Un mécanisme de transport de fichier est mis en place dans le serveur d'entreprise JD Edwards pour transporter le document XML résultant de l'opération, déclenché par la fin de l'événement, vers le répertoire cible de ce serveur.  
  
-   L'ordinateur BizTalk Server possède un lecteur mappé au répertoire figurant sur le serveur d'entreprise.  
  
-   Les propriétés de transport du port de réception sont configurées pour le lecteur mappé. Le port de réception reçoit les messages envoyés au répertoire par le serveur d'entreprise.  
  
-   L'identification de l'espace de noms permet de s'assurer que les messages appropriés sont acheminés vers le port de réception configuré.  
  
-   Le port de réception envoie le document XML à BizTalk Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment définir les propriétés de JD Edwards OneWorld Transport](../core/how-to-set-jd-edwards-oneworld-transport-properties.md)   
 [Planification et Architecture](../core/planning-and-architecture17.md)