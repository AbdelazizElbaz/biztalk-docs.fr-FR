---
title: "Résultats des tests : Indicateurs de Performance clés de la mise en réseau | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9bdbc2df-9d19-4ae8-b540-ec1b9a7cdbe9
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3eb4e10c739178e6cd923f65b51f982e05ab7f56
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="test-results-networking-key-performance-indicators"></a>Résultats des tests : Indicateurs de Performance clés de la mise en réseau
Cette rubrique résume réseau performances indicateurs clés (KPI) observé sur les scénarios de test. Ces tests évaluer les performances du réseau telle que mesurée par le **\Network Interface (\*) \Bytes/s** compteur et par mesure de l’Analyseur de performances le **SQL Network Interface\Bytes Total/s (Moy.)**  retournée par le contrôleur de Test de charge VSTS 2008.  
  
## <a name="summary-of-network-key-performance-indicators"></a>Résumé des indicateurs de Performance clés réseau  
 **Comparaison des indicateurs de Performance de clé de mise en réseau –** débit du réseau pour BizTalk Server s’exécutant sur des ordinateurs virtuels Hyper-V a été observé à la plage d’environ 70 à 96 % du débit du réseau effectué sur les serveurs physiques de BizTalk , en fonction de l’environnement de test particulière. Débit du réseau pour SQL Server s’exécutant sur un ordinateur virtuel Hyper-V a été observé à la plage d’environ 68 à 81 % du débit du réseau effectué sur le serveur SQL physique, à nouveau en fonction de l’environnement de test particulière. Le delta dans le débit observées sur le réseau peut être attribué pour les besoins en ressources de l’hyperviseur Hyper-V.  
  
 Suivez les étapes de [optimisations réseau](../technical-guides/network-optimizations.md) pour optimiser le débit du réseau sur des machines Hyper-V telle que mesurée par **\Network Interface (\*) \Bytes/s**  
  
 Le graphique ci-dessous illustre les performances du réseau sur les différentes plateformes de test :  
  
 ![Mise en réseau des indicateurs de Performance clés](../technical-guides/media/networkkpi.gif "NetworkKPI")  
  
 Le tableau ci-dessous illustre les performances relatives de l’indicateur collectées pour chaque configuration. Chaque jeu de résultats est calculée en pourcentage de la configuration de base indicateur de performance clé  
  
|Indicateur de performance clé|Virtuel BizTalk/physiques SQL|Virtuel BizTalk/virtuel SQL sur des hôtes distincts|Virtuel SQL BizTalk/virtuel dans l’environnement de consolidé|  
|---------|-----------------------------------|----------------------------------------------------|--------------------------------------------------------------|  
|\Network interface (*) \Bytes/s (Moy Total sur tous les serveurs BizTalk)|96%|82.1%|70.2%|  
|SQL Network Interface réseau\Total des octets/s (Moy.)|95.5%|81.2%|68.4%|  
  
 Pour plus d’informations sur la façon d’évaluer les performances du réseau, consultez le **mesure les performances réseau** section de la rubrique [liste de vérification : mesure des performances sur Hyper-V](../technical-guides/checklist-measuring-performance-on-hyper-v.md).