---
title: TIBCO Rendezvous Concepts | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certified message delivery
- subjects
- messages, defined
- transports, defined
- events
- virtual circuits
- direct communication
- batch mode
- queue group
- TIBCO Rendezvous, concepts
- distributed queue daemons
ms.assetid: 36060091-57dc-4125-8dca-23058d813deb
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 129fc0a864ac485919090476e153600adf5b4080
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tibco-rendezvous-concepts"></a>Concepts en relation avec TIBCO Rendezvous
Le tableau suivant décrit certaines des fonctionnalités et des concepts dans TIBCO Rendezvous.  
  
|Concept|Définition|  
|-------------|----------------|  
|**Messages**|Transporte des données entre les processus ou les threads du programme. Les messages contiennent des champs de données qui se décrivent lui-même. Les programmes peuvent manipuler les champs de message, envoyer des messages et recevoir des messages.|  
|**Événements**|Crée des objets d'événement pour enregistrer les événements intéressants lorsque cela est important. Par exemple, la distribution d'un événement d'écoute indique au programme qu'un message est arrivé ; la distribution d'un événement de minuteur indique au programme que son intervalle est arrivé à son terme.<br /><br /> Les programmes définissent des fonctions de rappel d'événements pour les traiter.|  
|**Sujets**|Les messages sont associés avec un nom de logiciel (sujet). Les programmes écoutent un sujet particulier, ou publient des messages sous un sujet spécifique.|  
|**Transports**|Les objets qui définissent l'étendue de réception, les mécanismes et les protocoles.|  
|**Mode batch**|Les objets de transport TIBCO Rendezvous prennent en charge le mode Lot pour la publication des messages. <br />Mode par défaut est : envoyer des messages dès que possible. Mode de traitement par lots du minuteur est : accumuler les messages et à envoyer lors de la mémoire tampon est pleine ou intervalle du minuteur expire.|  
|**File d’attente**|Les programmes créent l'événement de mise en file d'attente pour organiser les événements. Une file d'attente une file d'attente contient une séquence d'objets d'événement prêts à être traités.|  
|**Groupe de la file d’attente**|Personnalise le traitement de l'événement en combinant les files d'attentes (à l'aide de différentes priorités).|  
|**Remise des messages certifiés**|Confirme la remise de chaque message à chaque destinataire enregistré. Remet les messages en dépit de l'arrêt et du redémarrage du processus à l'aide de fichiers de comptabilité basés sur un fichier.<br /><br /> La remise certifiée indique aux programmes que chaque message certifié rejoint chaque destinataire prévu, dans l'ordre d'envoi. Quand la remise est impossible, les programmes d'envoi et d'écoute reçoivent des informations explicites sur chaque message non livré.<br /><br /> Les programmes déterminent une limite de temps explicite pour chaque message.<br /><br /> Après qu'un programme envoie un message certifié, le logiciel TIBCO Rendezvous continue ses tentatives de remise jusqu'à la réussite de la remise, ou jusqu'à ce que le délai de remise du message arrive à expiration.<br /><br /> Le logiciel de remise certifiée TIBCO Rendezvous présente des messages d'avertissement pour fournir aux programmes des informations concernant chaque événement important associé à la remise.<br /><br /> Le logiciel de remise certifiée TIBCO Rendezvous enregistre l'état de chaque message dans un fichier de comptabilité. Les programmes nécessitant une certification uniquement durant le processus du programme doivent utiliser un fichier de comptabilité basé sur le processus. Les programmes nécessitant une certification indépendante de l'arrêt du processus et du redémarrage du programme utilisent un fichier de comptabilité basé sur un fichier.<br /><br /> Quand la remise certifiée n'est pas autorisée, les conditions de remise reviennent à la sémantique de fiabilité de la remise TIBCO Rendezvous standard.|  
|**Démons de file d’attente distribuée**|Distribuent un service sur plusieurs processus.<br /><br /> Le démon TIBCO Rendezvous termine le chemin emprunté par les informations entre les processus du programme TIBCO Rendezvous sur le réseau. Les programmes essaient de se connecter à un processus de démon TIBCO Rendezvous. Si un processus de démon local n'est pas encore exécuté, le programme en démarre un automatiquement et s'y connecte. Le démon TIBCO Rendezvous agence les détails du transport de données, des commandes de paquets, la réception des accusés de réceptions, la transmission des demandes, et la distribution des informations aux processus de programme appropriés. Le démon cache tous ces détails dans les programmes TIBCO Rendezvous. Le démon TIBCO Rendezvous est toujours invisible pour les programmes qui dépendent de lui. Les programmes envoient et reçoivent des informations à l'aide des appels de communications TIBCO Rendezvous, et le démon TIBCO Rendezvous transmet les informations aux emplacements appropriés.<br /><br /> La démon effectue les tâches suivantes :<br /><br /> -Transmet les messages sortants à partir de processus du programme pour le réseau.<br />-Remet les messages entrants à partir du réseau dans les processus de programme.<br />: Filtre les messages adressés de sujet.<br />-Protège les programmes à partir des idiosyncrasies du système d’exploitation, tels que les sockets.|  
|**Sécurité**|TIBCO Rendezvous prend en charge l'authentification basée sur un certificat ou par mot de passe.|  
|**Circuits virtuels**|Composants de communication Rendezvous entre deux terminaux à travers une connexion surveillée continue et exclusive.|  
|**Communication directe**|Communications point-à-point sans processus de démon Rendezvous intermédiaire.|  
  
## <a name="see-also"></a>Voir aussi  
 [Messages de l’adaptateur BizTalk pour TIBCO Rendezvous](../core/messages-in-biztalk-adapter-for-tibco-rendezvous.md)   
 [Bien démarrer](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)