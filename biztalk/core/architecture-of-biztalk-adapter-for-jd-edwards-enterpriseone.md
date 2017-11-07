---
title: "Architecture de l’adaptateur BizTalk pour JD Edwards EnterpriseOne | Documents Microsoft"
description: "Décrit les services entrants au moment du design et moment de l’exécution, les événements sortants au moment du design et le moment de l’exécution dans l’adaptateur JD Edwards EnterpriseOne dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0441c5d2-6a46-45b6-8ab5-0bdac3590f56
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b495ee9a34cf464bd5cc11caed53c5df54948a49
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="architecture-of-biztalk-adapter-for-jd-edwards-enterpriseone"></a>Architecture de l'adaptateur BizTalk pour JD Edwards EnterpriseOne
L'adaptateur Microsoft BizTalk pour Edwards EnterpriseOne permet d'accéder aux fonctions commerciales de JD Edwards EnterpriseOne. JD Edwards EnterpriseOne communique entre les ordinateurs client et serveur à l'aide d'une architecture de messagerie propriétaire nommée JDENet. Celle-ci est implémentée par les classes de connecteur JD Edwards EnterpriseOne figurant dans les fichiers JAR, Connector.jar et Kernel.jar. La communication est implémentée à l’aide de TCP/IP comme protocole de transport, avec le port par défaut 6009 ou 6010. Pour obtenir une description de l’emplacement où cette valeur est définie, consultez [ajouter les artefacts à l’Administration de BizTalk](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md).  
  
 L'architecture de l'adaptateur BizTalk pour JD Edwards EnterpriseOne est représentée dans la figure suivante.  
  
 ![](../core/media/jd-enterpriseone-arch.gif "JD_EnterpriseOne_arch")  
  
## <a name="inbound-services-at-design-time"></a>Services entrants au moment de la conception  
  
-   Au moment de la conception, vous créez un port, sélectionnez un adaptateur et fournissez les informations d'identification pour la connexion au serveur JD Edwards EnterpriseOne cible. L'environnement de développement Visual Studio appelle l'infrastructure d'adaptateurs pour demander des informations de conception pour ce port. L'adaptateur utilise Browsingagent pour ce port.  
  
-   Au moment de la conception, BizTalk Server demande des informations en appelant l'adaptateur.  
  
-   Browsingagent convertit la demande en code natif JD Edwards EnterpriseOne et la transmet à JD Edwards EnterpriseOne via la connexion API ThinNet (établie dans Connector.jar et Kernel.jar).  
  
-   La liste des modules de JD Edwards EnterpriseOne est initialement renvoyée et transportée vers l'environnement de développement Visual Studio, dans lequel elle renseigne l'Assistant Adaptateur.  
  
-   Vous pouvez développer la hiérarchie en affichant le nom de la bibliothèque puis le nom du module.  
  
-   Lorsque vous sélectionnez un module spécifique, des schémas pour toutes les fonctions de ce module s'affichent. L'adaptateur obtient les informations requises auprès de JD Edwards EnterpriseOne, et Browsingagent crée les schémas.  
  
-   Les schémas sont ajoutés à l'orchestration du projet BizTalk Server.  
  
## <a name="inbound-services-at-run-time"></a>Services entrants au moment de l'exécution  
  
-   BizTalk Server appelle l'adaptateur pour envoyer un message sur un port spécifique.  
  
-   L'agent d'exécution convertit le XML en code JDE natif.  
  
-   L'agent d'exécution envoie la demande via ThinNet au système JD Edwards EnterpriseOne spécifié dans les propriétés de transport du port d'envoi.  
  
-   La fonction commerciale principale est exécutée sur le système JD Edwards EnterpriseOne, qui génère ensuite un document de réponse, lequel indique si l'opération a réussi ou échoué, ainsi que les paramètres de données renvoyés par la fonction commerciale.  
  
-   Le message envoyé à JD Edwards EnterpriseOne constitue une architecture à message unique et à réponse unique. Il est impossible de traiter plusieurs messages simultanément.  
  
-   Le document de réponse est renvoyé via ThinNet, converti au format XML et retransmis à BizTalk Server.  
  
## <a name="outbound-events-at-design-time"></a>Événements sortants au moment de la conception  
  
-   Aucune création systématique de métadonnées d'événement n'est disponible.  
  
-   Une télécopie du document d'événements doit être fournie à Visual Studio afin qu'un schéma puisse être généré et incorporé au projet avec l'espace de noms cible.  
  
## <a name="outbound-events-at-run-time"></a>Événements sortants au moment de l'exécution  
  
-   Un mécanisme de transport de fichier est mis en place dans le serveur JD Edwards EnterpriseOne pour transporter le document XML résultant de l'opération, déclenché par la fin de l'événement, vers le répertoire cible de cet ordinateur.  
  
-   L'ordinateur BizTalk Server possède un lecteur mappé au répertoire figurant sur le serveur EnterpriseOne.  
  
-   Les propriétés de transport du port de réception sont configurées pour le lecteur mappé. Le port de réception reçoit les messages, qui sont envoyés vers un répertoire par le serveur EnterpriseOne.  
  
-   L'identification de l'espace de noms permet de s'assurer que les messages appropriés sont acheminés vers le port de réception configuré  
  
-   Le port de réception envoie le document XML dans BizTalk Server.  
  
## <a name="more-good-stuff"></a>Autre contenu intéressant
[Sécurité de l’adaptateur BizTalk pour JD Edwards EnterpriseOne](../core/security-in-biztalk-adapter-for-jd-edwards-enterpriseone.md)  
[Créer les artefacts de l’application](../core/developing-applications2.md)  
[Importer votre JD Edwards EnterpriseOne application](../core/deploying-biztalk-adapter-for-jd-edwards-enterpriseone.md)  
[Utiliser la gestion des exceptions BizTalk Server](../core/using-biztalk-server-exception-handling3.md)  
[Dépanner](../core/troubleshooting-jd-edwards-enterpriseone.md)  
