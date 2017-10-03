---
title: "Affichage de la liste, recherche et tri des Messages d’erreur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 850b9682-8eba-4a3f-8508-d3eefcd715b7
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 768dd7f51ff09bad76115f8a7e2a95a11ce47981
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="listing-searching-and-sorting-fault-messages"></a>Affichage de la liste, recherche et tri des Messages d’erreur
Vous pouvez utiliser la page d’accueil du portail de gestion ESB pour obtenir une vue d’ensemble de l’état des applications qui s’exécutent dans Microsoft BizTalk Server. La page d’erreurs peut être utilisée pour rechercher des messages d’erreur, basé sur une plage de critères.  
  
### <a name="to-see-an-overview-of-the-status-of-current-biztalk-server-applications"></a>Pour afficher une vue d’ensemble de l’état des applications de BizTalk Server en cours  
  
1.  Ouvrez le [Page d’accueil du portail](../esb-toolkit/portal-home-page.md). Cette page affiche l’état global d’application, un résumé des erreurs, les demandes récentes pour inscription Universal Description, Discovery and Integration (UDDI) et les graphiques qui montrent une répartition des erreurs par type et par application.  
  
2.  Pour sélectionner les applications pour lesquelles vous souhaitez afficher plus d’informations, cliquez sur le **sélectionner des Applications** ci-dessus le premier graphique, puis activez ou désactivez les cases à cocher dans la liste des applications installées de BizTalk Server qui s’affiche.  
  
3.  Pour modifier la période pour laquelle le portail affiche des informations, sélectionnez **heure, jour, semaine, mois, trimestre, année,** ou **tous les** dans la liste déroulante au-dessus du premier graphique.  
  
4.  Pour modifier les paramètres par défaut utilisés sur la page d’accueil pour obtenir la liste d’applications et de la période d’affichage, modifiez les paramètres sur le [Page Paramètres de portail](../esb-toolkit/portal-my-settings-page.md).  
  
### <a name="to-list-search-for-and-sort-fault-messages-in-the-esb-management-portal"></a>Pour répertorier, rechercher et trier les messages dans le portail de gestion ESB d’erreur  
  
1.  Ouvrez le [Page Paramètres d’erreur](../esb-toolkit/fault-settings-page.md). Cette page affiche la liste de propriétés pour chaque erreur tronquée et prend en charge l’analyse des erreurs par une plage de critères.  
  
2.  Pour filtrer la liste d’erreurs affichés sur la page, utilisez les listes déroulantes et les zones de texte au-dessus de la liste d’erreurs. Vous pouvez filtrer les lignes affichées par application, période, numéro de code d’erreur, nom de catégorie d’erreur, texte du type d’erreur et gravité d’erreur de valeur minimale/maximale. Renseignez les contrôles pour récupérer tous les messages, quel que soit leur valeur pour ce critère.  
  
3.  Cliquez sur **appliquer des filtres** pour afficher la liste des erreurs de mise en correspondance. Le filtrage sur les bases de données des erreurs très volumineux peut prendre de quelques secondes pour afficher les résultats.  
  
4.  Pour afficher plus ou moins de lignes dans la page, sélectionnez la valeur appropriée dans le **enregistrements par Page** liste déroulante.  
  
5.  Pour trier la liste des messages d’erreur, cliquez sur un en-tête de colonne. Pour trier les lignes dans l’ordre inverse, cliquez sur l’en-tête de la même colonne.  
  
6.  Cliquez sur **exporter vers Excel** pour télécharger la liste complète des messages d’erreur dans un format que vous pouvez afficher dans Microsoft Excel.