---
title: "Scénarios de test pour mesurer le débit maximal acceptable du moteur de | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e54667b9-7262-43c8-a013-9242eb062daf
caps.latest.revision: "28"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dd5b9a2697cb96bb2d042b9fee6a15317f35971c
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="test-scenarios-for-measuring-mst-of-the-engine"></a>Test des scénarios de mesure du débit maximal acceptable du moteur
Cette section décrit un scénario de test qui a été implémenté pour mesurer l'effet produit par le fait de porter un système BizTalk à trois niveaux de charge différents :  
  
-   [Test de charge maximale](../core/sustainable-load-test.md). Pour ces tests, la charge maximale est décrite dans la rubrique [Nouveautés des performances durables ?](../core/what-is-sustainable-performance.md).  
  
-   [Dépassement de Test de charge](../core/overdrive-load-test.md). Une surcharge se définie comme une charge homogène supérieure au débit maximal acceptable.  
  
-   [Test de charge de saturation](../core/floodgate-load-test.md). Un état de saturation se définit comme une charge faible avec des pics de charge intermittents supérieurs au débit maximal acceptable.  
  
 Cette rubrique décrit la configuration matérielle de test, les scénarios de test, et présente les découvertes effectuées au cours de chaque test.  
  
> [!IMPORTANT]
>  Les lecteurs doivent savoir que les informations contenues dans cette section représentent l'opinion actuelle de Microsoft sur les points cités à la date de publication. Étant donné que l'entreprise doit s'adapter aux conditions fluctuantes du marché et aux nouvelles technologies, Microsoft ne peut pas garantir la véracité de toute information présentée après la date de publication.  
  
## <a name="test-system-configuration"></a>Configuration système de test  
 Le matériel suivant a été utilisé pour ce scénario de test :  
  
-   **Six serveurs BizTalk**. Chacun est équipé de doubles processeurs de 3 GHz et de 2 Go de RAM. Chaque serveur utilise des disques locaux. Deux des serveurs BizTalk Server sont configurés avec une instance de l'hôte de réception, deux sont configurés avec une instance de l'hôte émetteur, et deux autres encore sont configurés avec une instance de l'hôte utilisé pour traiter les orchestrations.  
  
-   **Un serveur SQL Server pour la base de données principale et les bases de données non-MessageBox**. Équipé de huit processeurs de 2 GHz et de 4 Go de RAM. Ce serveur est connecté à un sous-système de disque SAN rapide par une fibre. La publication des messages est désactivée.  
  
-   **Trois serveurs SQL pour les bases de données Messagebox sont publiés dans**. Équipés de quatre processeurs de 2 GHz et de 4 Go de RAM. Ces serveurs sont connectés à un sous-système de disque SAN rapide par une fibre. Les fichiers journaux de données et de transactions des bases de données MessageBox se trouvent sur des numéros d'unité logique (LUN) réseau SAN.  
  
-   **Ordinateur client de pilote charge**. Équipé de doubles processeurs de 3 GHz et de 2 Go de RAM. Ce serveur a été utilisé pour générer la charge de test du système BizTalk.  
  
 La topologie utilisée pour les tests de charge est illustrée ci-dessous.  
  
 **Topologie utilisée pour les tests de charge**  
  
 ![La topologie matérielle pour le test de charge de BizTalk Server](../core/media/bts06-msttopology.gif "BTS06_MSTTopology")  
  
## <a name="the-test-scenario"></a>Scénario de test  
 Le scénario de test est très simple. L'outil de génération de charge, LoadGen 2007, a été installé sur le serveur du gestionnaire de charge et a été utilisé pour envoyer des copies d'un fichier aux partages surveillés par l'adaptateur FILE. L'outil de génération de charge répartit équitablement des copies de l'instance du fichier d'entrée entre les partages de fichiers.  
  
> [!NOTE]
>  Télécharger [LoadGen](https://www.microsoft.com/download/details.aspx?id=14925). La version précédente de cet outil, l’outil de génération de charge de BizTalk Server 2004 est disponible pour téléchargement à l’adresse [http://go.microsoft.com/fwlink/?linkid=108999](http://go.microsoft.com/fwlink/?linkid=108999). Pour plus d’informations sur l’utilisation de LoadGen avec l’adaptateur MSMQ, consultez [à l’aide de LoadGen 2007 avec MSMQ](../core/using-loadgen-2007-with-msmq.md).  
  
 L'adaptateur BizTalk FILE est configuré pour contrôler les partages de fichiers et pour publier les messages dans le MessageBox. Une orchestration simple qui contient seulement une forme Réception et une forme Envoi souscrit au message publié. Les messages qui sont republiés par l'orchestration dans le MessageBox sont récupérés par un port d'envoi de fichier, puis envoyés à un partage commun, défini sur le SAN. Les fichiers arrivant à la sortie du SAN sont supprimés immédiatement pour éviter l'accumulation de fichiers sur le partage pendant des tests longs.  
  
 Quatre hôtes ont été définis pour le scénario : pour l'emplacement de réception, les orchestrations, le port d'envoi et le suivi. Afin d'observer le comportement de journalisation du moteur, le suivi est complètement arrêté pendant les tests. Par défaut, le suivi est activé uniquement pour les pipelines et les orchestrations ; le suivi a donc été désactivé explicitement dans l'Administrateur BizTalk pour l'orchestration et le pipeline utilisés.  
  
 Aucune instance de l'hôte de suivi n'a été créée depuis que le suivi a été désactivé afin d'isoler le comportement principal MessageBox pour ces tests.  
  
 Un schéma simple a été utilisé et les fichiers d'instance utilisés pour le test étaient tous de 10 Ko. Le pipeline XMLReceive a été utilisé pour les documents entrants et aucun composant de mappage ou sortant n'a été utilisé pour conserver le scénario de test simple et pour orienter les observations sur le comportement de MessageBox.  
  
## <a name="parameters-measured-in-the-test"></a>Paramètres mesurés dans le test  
 Les paramètres suivants ont été mesurés au cours de ce test :  
  
 **Paramètres de test principal mesurés**  
  
 Les paramètres suivants sont les principaux indicateurs servant à mesurer le débit maximal acceptable :  
  
-   La file d’attente MessageBox telle que mesurée par le **taille mise en attente** compteur qui est disponible avec le **MessageBox : compteurs généraux** objet de performance. Il s'agit d'un indicateur clé de durabilité. Le nombre de messages accumulés dans le MessageBox ne peut pas augmenter indéfiniment sans que cela entraîne le moindre problème. Le développement de cette accumulation dans la base de données MessageBox, contrôlé en permanence, sert à évaluer la durabilité.  
  
     La table MessageBox intitulée **spool** contient un enregistrement pour chaque message dans le système (actif ou en attente pour l’opération garbage collector). L'analyse du nombre de lignes de cette table et du nombre de messages reçus par seconde, bien qu'entraînant une hausse de la charge système, fournit un moyen facile pour mesurer le débit durable maximal. Cette mesure est également appelée le **table profondeur du spooleur** ou **profondeur du spooleur**.  
  
-   Le nombre de documents reçus par seconde, telle que mesurée par le **Documents reçus/s** compteur qui est disponible avec le **BizTalk : messagerie** objet de performance.  
  
 **Paramètres de test secondaires mesurés**  
  
 Les paramètres suivants sont des indicateurs secondaires qui peuvent être évalués pour mesurer le débit maximal acceptable. Ces paramètres peuvent avoir un impact sur les indicateurs principaux que sont la profondeur du spouleur et le nombre de documents reçus par seconde.  
  
-   MessageBox transaction et données fichier disque telle que mesurée par durée d’inactivité du disque physique du **% durée d’inactivité** compteur disponible avec le **LogicalDisk** objet de performance.  
  
-   L’utilisation du processeur (%) pour le serveur MessageBox telle que mesurée par le **% temps processeur** compteur disponible avec le **processeur** objet de performance.  
  
-   Les délais d’attente de verrous par seconde sur la MessageBox de base de données telle que mesurée par le **des délais d’attente de verrous/s** compteur disponible avec le **SQLServer : verrous** objet de performance.  
  
-   Durée (en secondes) de la dernière exécution du travail d'Agent SQL qui nettoie les tables de zone de message associées aux messages supprimés. Mesuré par le **MsgBox Msg Cleanup(Purge Jobs)** compteur disponible avec le **MessageBox : compteurs généraux** objet de performance.  
  
-   Durée (en secondes) de la dernière exécution du travail d'Agent SQL qui nettoie les tables de zone de message associées aux parties de messages supprimées. Mesuré par le **MsgBox parties Cleanup(Purge Jobs)** compteur disponible avec le **MessageBox : compteurs généraux** objet de performance.  
  
 Lors du test effectué pour déterminer le débit maximal acceptable, la charge en entrée a été augmentée jusqu'au point à partir duquel la table de mise en file d'attente a commencé à croître indéfiniment.  
  
> [!NOTE]
>  Si vous ne parvenez pas à générer assez de charge pour provoquer un tel accroissement, cela signifie simplement que la partie la plus lente de votre système se trouve sur le côté de réception et non sur le côté de traitement/d'envoi.  
  

## <a name="next"></a>Suivant
  
-   [À l’aide de l’outil Microsoft BizTalk LoadGen 2007](../core/using-the-microsoft-biztalk-loadgen-2007-tool.md)  
  
-   [Test de charge maximale](../core/sustainable-load-test.md)  
  
-   [Test de surcharge de dépassement](../core/overdrive-load-test.md)  
  
-   [Test de surcharge de saturation](../core/floodgate-load-test.md)