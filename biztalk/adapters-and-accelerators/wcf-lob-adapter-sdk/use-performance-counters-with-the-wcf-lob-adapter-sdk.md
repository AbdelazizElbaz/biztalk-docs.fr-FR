---
title: Utiliser des compteurs de performance avec WCF LOB Adapter SDK | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b928eaf-2ab6-40a6-a1dd-804d4e89541e
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ead07059cac11f251d35fae18f0e228c4488c07a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="use-performance-counters-with-the-wcf-lob-adapter-sdk"></a>Utiliser des compteurs de performance avec WCF LOB Adapter SDK
Vous pouvez utiliser l’outil performances pour collecter automatiquement des données de performances à partir d’ordinateurs locaux ou distants qui exécutent le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. Vous pouvez définir démarrer et arrêter des heures pour la génération automatique des journaux, gérer plusieurs sessions de connexion à partir d’une fenêtre de console unique et définir une alerte sur un ordinateur qui permet l’envoi d’un message ou un journal doit être démarré lorsque vos critères. Cette rubrique décrit les compteurs de performances pour le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].  
  
## <a name="performance-objects-and-counters"></a>Les compteurs et les objets de performance  
 Lorsque vous installez le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], un objet de performance unique nommé « ServiceModel Adapters » est installé. L’objet de performance contient un nombre de compteurs de performance différents. Un objet de performance mesure l’activité pour une ressource donnée, une application ou un service. Objets de performance et les compteurs obtenir des données de performances à partir de la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], fonctionnalités et des services sur votre ordinateur lorsqu’ils sont utilisés. Ces données de performances sont généralement nommées pour le composant qui génère les données. Compteurs de performances sont utilisés pour la collecte des informations spécifiques ou des données pour un objet de performance donné.  
  
 Lorsque vous sélectionnez les compteurs à partir de l’objet de performance ServiceModel adaptateurs, vous pouvez choisir surveiller uniquement les instances d’adaptateur spécifique d’informations en sélectionnant l’instance à partir de la liste des Instances de sélectionner. Chaque instance d’adaptateur s’afficheront dans le format de \<ProcessId > @\<ConnectionString >. Par exemple, 115@echo:&#124; &#124; hôte &#124; temp ? echoprefix = pre indique l’instance d’adaptateur écho en cours d’exécution dans le processus 115.  
  
 Pour plus d’informations sur les compteurs de performances dans WCF, consultez [compteurs de Performance WCF](https://msdn.microsoft.com/library/ms735098.aspx).
  
### <a name="servicemodel-adapters-metadata-cache-performance-counters"></a>Compteurs de Performance du Cache de métadonnées ServiceModel adaptateurs  
 Le tableau suivant récapitule les compteurs de performance du cache qui peuvent être utilisés pour surveiller la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].  
  
|Compteur| Description|  
|-------------|-----------------|  
|% De cache de lecture présences dans le|Pourcentage de métadonnées en lecture correspondances dans le cache de l’adaptateur.|  
|Métadonnées résolue|Nombre d’éléments de métadonnées résolues par l’adaptateur.|  
|% Cache complet|Pourcentage de la limite de taille du cache en cours d’utilisation.|  
  
### <a name="servicemodel-adapters-connection-performance-counters"></a>Compteurs de Performance ServiceModel adaptateurs connexion  
 Le tableau suivant récapitule les compteurs de performances de connexion qui peuvent être utilisés pour surveiller la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].  
  
|Compteur| Description|  
|-------------|-----------------|  
|Connexions abandonnées|Nombre de connexions du système cible abandonnées.|  
|Connexions en cours d’utilisation|Nombre de connexions du système cible d’actuellement en cours d’utilisation.|  
|Connexions ouvertes|Nombre de connexions du système cible ouverts.|  
|Connexions prêt|Nombre de connexions de système de cibles disponibles.|  
|Demandes de connexion en attente|Nombre d’en attente cible les demandes de connexion système.|  
  
### <a name="servicemodel-adapters-message-exchange-performance-counters"></a>Compteurs de Performance ServiceModel adaptateurs Message Exchange  
 Le tableau suivant récapitule les compteurs de performances exchange message qui peuvent être utilisés pour surveiller la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].  
  
|Compteur| Description|  
|-------------|-----------------|  
|Appels sortants|Nombre d’appels sortants à partir de l’adaptateur au système cible.|  
|Les appels sortants/s|Nombre d’appels sortants par seconde à partir de l’adaptateur au système cible.|  
  
## <a name="see-also"></a>Voir aussi  
 [Résoudre les problèmes d’adaptateur créé à l’aide de WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/troubleshoot-adapter-created-using-the-wcf-lob-adapter-sdk.md)