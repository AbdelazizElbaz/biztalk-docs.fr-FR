---
title: PIP de RosettaNet | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PIPs, clusters
- RosettaNet, PIPs
- PIPs, PIP specifications
- PIPs, segments
- PIPs, RosettaNet
- DTDs, DTD files
ms.assetid: 2f7e8db3-9ccb-403a-9fe7-58fbba3c4cb1
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1980f7c5e22259dc6c09d4f2d8dba31f3ac04d61
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="rosettanet-pips"></a>PIP de RosettaNet
L’organisation RosettaNet crée et gère les processus d’Interface partenaires (PIP) pour fournir des définitions communes de processus d’entreprise pour tous les échanges de messages RosettaNet.  
  
 Chaque spécification PIP fournit un fichier de définition (DTD) de type de document et un document d’indications de message. Le fichier DTD définit la structure du message de contenu de service. Le document de l’indication de message, qui est un fichier HTML lisible, spécifie les contraintes au niveau de l’élément. Ensemble, ils fournissent une définition complète du processus d’entreprise.  
  
 Pour plus d’informations sur les spécifications PIP, consultez le site Web de RosettaNet [http://go.microsoft.com/FWLink/?LinkID=33859](http://go.microsoft.com/FWLink/?LinkID=33859).  
  
## <a name="pip-contents"></a>Contenu PIP  
 Une spécification PIP effectue les opérations suivantes :  
  
-   Décrit le modèle de processus public il implémente  
  
-   Décrit comment configurer le processus public  
  
-   Fournit des références pour les documents à transmettre au sein du PIP  
  
 Une spécification PIP inclut trois parties principales : une vue opérationnel Business (BOV), affichage du Service fonctionnel (FSV) et une vue de Framework implémentation (IFV). Chacune de ces vues spécifie les contraintes au niveau de l’élément :  
  
-   Le BOV spécifie la sémantique des entités de données d’entreprise et le flux du processus. Il décrit le démarrage et les États de fin et les rôles de partenaire. Elle décrit l’interaction entre les rôles et sécurité des informations d’audit et les contrôles de processus. Il spécifie les documents commerciaux et les entités de données d’entreprise.  
  
-   Le FSV spécifie les interactions, les agents et les services de composants réseau. Il fournit la conception du composant de réseau requise pour exécuter le processus PIP et décrit les interactions entre les composants réseau.  
  
-   Le IFV spécifie les formats de message de protocole de réseau et les spécifications de communication requises pour exécuter le PIP.  
  
## <a name="clusters-and-segments"></a>Les Segments et les clusters  
 Vous classez PIP en une fonction d’entreprise de niveau supérieur (cluster) et une sous-fonction (segment). Les segments et les clusters organisent les messages en catégories reconnaissables. Le tableau suivant répertorie ces segments et les clusters.  
  
|Clusters|Segments|  
|--------------|--------------|  
|0 : prise en charge de RosettaNet|0 : administration<br /><br /> 0C : test|  
|1 : partenaires produit et Service, consultez|1 a : examen du partenaire<br /><br /> 1 b : produit et Service, consultez|  
|2 : informations de produit|2 a : préparation pour la Distribution<br /><br /> 2 b : Notification de modification de produit<br /><br /> 2C : les informations de conception de produit<br /><br /> 2D : conception collaboratif et l’ingénierie|  
|3 : gestion des commandes|3 a : devis & de saisie de commande<br /><br /> 3 b : transport et Distribution<br /><br /> 3c : retourne & Finance<br /><br /> 3D : Configuration du produit|  
|4 : gestion des stocks|4 a : prévision collaboration<br /><br /> 4 b : Allocation de stock<br /><br /> 4c : les rapports d’inventaire<br /><br /> 4D : demande de réapprovisionnement de stock<br /><br /> 4e : déclaration des ventes<br /><br /> 4f : Protection de prix|  
|5 : gestion des informations marketing|5 a : opportunité gestion des prospects<br /><br /> 5 b : gestion de la campagne Marketing|  
|6 : prise en charge et Service|6 a : fournir et d’administrer des garanties, Packages de Service et de contrat de Services<br /><br /> 6 b : fournir et d’administrer la gestion des actifs (fusionnée avec 6 a)<br /><br /> 6C : assistance technique et gestion des services|  
|7 : de fabrication|7 a : transfert de conception<br /><br /> 7 b : gérer WO de fabrication et les travaux en cours<br /><br /> 7C : distribuer les informations d’édition|  
  
 Chaque segment inclut un numéro de message spécifique PIP. Par exemple, le PIP 3 a 4 est une partie du cluster de gestion des commandes (Cluster 3) et du segment apostrophe et Saisie des commandes (un Segment de Cluster 3). Ce segment inclut les autres processus PIP messages connexes, comme suit :  
  
 Cluster 3 : Gestion des commandes  
  
-   Segment A: devis et de saisie de commande  
  
    -   PIP 3A1 : demande de devis  
  
    -   PIP 3A2 : demande de prix et disponibilité  
  
    -   PIP 3A3 : demande de transfert de panier d’achat  
  
    -   3 a 4 PIP : gérer le bon de commande  
  
    -   PIP 3A5 : état de la commande de requête  
  
    -   PIP 3A6 : distribuer l’état de la commande  
  
    -   …  
  
## <a name="see-also"></a>Voir aussi  
 [RosettaNet et CIDX normes de messagerie](../../adapters-and-accelerators/accelerator-rosettanet/rosettanet-and-cidx-messaging-standards.md)   
 [Norme RNIF](../../adapters-and-accelerators/accelerator-rosettanet/rnif-standard.md)