---
title: "Configurer un EDI et le rapport d’état AS2 | Documents Microsoft"
description: "Créer l’EDI ou expression de requête de rapport d’état AS2 et sélectionner les données que vous souhaitez afficher dans le rapport pour dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6490864d-f1e6-4932-aefb-c332a595aad7
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 833e3c6c26cdac57d7cc57d828b66a66b9eb37f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-an-edi-and-as2-status-report"></a>Configurer un EDI et le rapport d’état AS2
Une fois que vous avez activé EDI ou de rapports d’état AS2, vous affichez le rapport d’état souhaité à partir de la **rapports d’état EDI** ou **rapports d’état EDIINT** section de la **Hub du groupe** onglet de la **vue d’ensemble du groupe** page dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration. Lorsque vous affichez un rapport d'état, vous verrez un ensemble de données par défaut. Vous pouvez configurer les aspects suivants des rapports d'état :  
  
-   L'expression de requête qui est exécutée pour déterminer la plage des données pour lesquelles l'état est rapporté, par exemple, la plage de dates, le sens des données (reçues ou envoyées), ou la valeur d'état (Acceptée, Rejetée, Tout, etc.)  
  
-   Le type de données affichées dans le volet de rapport d'état, comme déterminé par les colonnes de données dans le rapport.  
  
    > [!NOTE]
    >  À chaque fois que les rapports d'état sont activés, tous les états seront enregistrés dans le stockage. En personnalisant l'expression de requête ou les colonnes d'état, vous définissez quelles données enregistrées sont affichées.  
  
 Cinq rapports d’état EDI et AS2 différents sont disponibles (voir [Types de rapports EDI et AS2 état](../core/types-of-edi-and-as2-status-reports.md)). La manière dont vous configurez chaque rapport est la même, même si les données pour chaque rapport sont différentes.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="configure-the-status-report-query-expression"></a>Configurer l’expression de requête du rapport État  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, cliquez sur le **groupe BizTalk** nœud pour afficher les **vue d’ensemble du groupe** volet.  
  
2.  Au bas de la **Hub du groupe** onglet dans le **vue d’ensemble du groupe** volet, cliquez sur le rapport d’état que vous souhaitez configurer, tel que **échange EDI et état ACK corrélé**.  
  
3.  Dans le **Expression de requête** zone du volet de rapport d’état, vérifiez que tous les critères de filtre que vous souhaitez définir pour la requête sont présents. Dans le cas contraire, cliquez sur la flèche vers le bas dans la ligne vide dans le **nom de champ** colonne au bas de l’expression de requête et sélectionnez un critère de filtre que vous souhaitez ajouter à l’expression de requête. Vous pouvez supprimer une ligne de critères de filtre en sélectionnant la ligne en cliquant sur le **supprimer** bouton sur le clavier.  
  
4.  Vérifiez que les valeurs pour les expressions de filtre sont celles désirées. Dans le cas contraire, cliquez sur la flèche bas de la **opérateur** colonne pour sélectionner une opération de requête, entrez la valeur appropriée dans le **valeur** colonne.  
  
    > [!NOTE]
    >  Les opérateurs et les valeurs disponibles pour les critères de filtre dans les expressions de requête sont décrits dans [Types de rapports EDI et AS2 état](../core/types-of-edi-and-as2-status-reports.md) et **l’interface utilisateur de rapports EDI AS2 état** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
5.  Pour exécuter la requête, en affichant le rapport d’état en fonction de critères de filtre, cliquez sur **exécuter la requête**.  
  
6.  Pour enregistrer une expression de requête sous forme de fichier .btq, cliquez sur **enregistrer en tant que**, spécifiez le dossier et entrez un nom de fichier, puis cliquez sur **enregistrer**.  
  
7.  Pour ouvrir un fichier .btq enregistré, cliquez sur **ouvrir une requête**.  
  
## <a name="configure-the-type-of-data-displayed-in-the-status-report-pane"></a>Configurer le type de données affichées dans le volet de rapport d’état  
  
1.  Avec le bouton droit de la zone des résultats du volet de rapport d’état, puis cliquez sur **Ajout/Suppression de colonnes**.  
  
2.  Pour ajouter une catégorie d’état à la liste des colonnes affichées, cliquez sur une colonne dans la **colonnes disponibles** liste, puis cliquez sur **ajouter**.  
  
3.  Pour supprimer une catégorie de statut de la liste des colonnes affichées, cliquez sur une colonne dans la **colonnes affichées** liste, puis cliquez sur **supprimer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Surveillance des Solutions EDI et AS2](../core/monitoring-edi-and-as2-solutions.md)   
 [EDI et AS2 le rapport d’état](../core/edi-and-as2-status-reporting.md)   
 [L’activation des rapports d’état AS2 et EDI](../core/enabling-edi-and-as2-status-reports.md)   
 [Afficher un EDI ou le rapport d’état AS2](../core/displaying-an-edi-or-as2-status-report.md)