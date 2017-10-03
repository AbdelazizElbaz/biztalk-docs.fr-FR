---
title: "Création, affichage et suppression d’erreur des alertes de Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59df2b40-b42c-4167-873c-0819839919da
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e9451ecb9cbeaf2077712f6e6b55a36dab7988c2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-viewing-and-deleting-fault-message-alerts"></a>Création, affichage et suppression d’alertes de Message d’erreur
Le portail de gestion ESB peut générer des alertes lors de l’arrivent de messages d’erreur sur le portail, basée sur une comparaison de valeurs dans le message avec les critères spécifiés pour l’alerte. Le portail peut également conserver une liste des notifications d’alertes liées aux différents utilisateurs, et il informe ces utilisateurs lors de façon proactive, il déclenche des alertes.  
  
### <a name="to-create-and-configure-a-new-alert"></a>Pour créer et configurer une nouvelle alerte  
  
1.  Ouvrez le [Page alertes du portail](../esb-toolkit/portal-alerts-page.md) pour afficher une liste des alertes existantes et vos abonnements en cours pour ces alertes.  
  
2.  Cliquez sur le **créer une alerte** lien pour ouvrir la [ajouter une Page d’alerte](../esb-toolkit/add-alert-page.md).  
  
3.  Dans le **entrer le nom alerte** zone de texte, tapez un nom pour la nouvelle alerte.  
  
4.  Dans le **Conditions** section de la page Ajouter une alerte, sélectionnez un champ (tel que **Application**, **Type d’erreur**, ou **gravité d’erreur**) dans le **Critères** liste déroulante ; Sélectionnez un type de comparaison (tels que +, =, ! =, > =, \<=, ou **comme**) dans le **opérateur** type et liste déroulante ; ou sélectionnez une valeur dans la troisième liste ou zone de texte (nommées **valeur**). Lorsque vous sélectionnez un **critères** valeur, les modifications de la page pour afficher une zone de texte ou d’une liste déroulante pour la valeur correspondante. Toutes les conditions sont combinées à l’aide de la **AND** opérateur.  
  
5.  Cliquez sur le **ajouter** ce lien pour ajouter cette condition à la liste, puis répétez l’étape précédente pour ajouter d’autres conditions si nécessaire.  
  
6.  Cliquez sur le **enregistrer** bouton permettant de créer une nouvelle alerte avec le nom spécifié et les conditions.  
  
### <a name="to-view-details-of-an-existing-alert-or-delete-an-existing-alert"></a>Pour afficher les détails d’une alerte existante ou supprimer une alerte existante  
  
1.  Ouvrez le [Page alertes du portail](../esb-toolkit/portal-alerts-page.md).  
  
2.  Pour supprimer une alerte, cliquez sur le **supprimer l’alerte** icône dans la colonne d’Action d’une alerte existante.  
  
    > [!NOTE]
    >  Utilisateurs non-administrateurs peuvent supprimer uniquement les alertes pour laquelle ils sont propriétaires, et pour lesquels il n’existe actuellement aucun abonné. Vous devez vous connecter au portail en tant qu’administrateur pour supprimer les autres alertes.  
  
3.  Pour afficher les détails d’une alerte, cliquez sur le **vue** icône dans la colonne d’Action d’une alerte existante. Cela ouvre la page Afficheur des alertes.  
  
4.  Cliquez sur **exporter vers Excel** pour télécharger la liste complète des alertes dans un format que vous pouvez afficher dans Microsoft Excel.