---
title: "Étape 5 : Tester la Solution | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5ca5301-2ee4-4024-a90a-396ed681d12a
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ce7edd1c1f1f8a063e2787cc2acecb3b57cca2c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-5-test-the-solution"></a>Étape 5 : Tester la Solution
Cette solution vise à automatiser le processus d’envoi des notifications à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], chaque fois qu’une nouvelle opportunité est fermée dans Salesforce en définissant le stade de l’opportunité **fermées/gagnées**. Une fois que la notification est reçue [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] envoie une requête à Salesforce pour récupérer les détails du produit relatives à l’opportunité, puis insère la réponse de Salesforce dans une table de base de données SQL Server appelée **OrderDetails**. Par conséquent, pour tester cette solution, nous mettrons à jour l’étape de l’opportunité à **fermées/gagnées** et par conséquent, les enregistrements pertinents doivent être insérés dans la table OrderDetails dans la base de données de commandes.  
  
### <a name="to-test-the-solution"></a>Pour tester la solution  
  
1.  Connectez-vous à `https://login.salesforce.com/?lt=de` à l'aide des informations d'identification développeur Salesforce.  
  
2.  Dans la barre de navigation, cliquez sur **opportunités**, puis cliquez sur **opportunité avec client 1**. Vous avez créé cette opportunité dans [étape 2 : configurer le système Salesforce](../core/step-2-set-up-the-salesforce-system.md).  
  
3.  Dans le **détails de l’opportunité** section, notez les produits associés dans le **produits (Standard)** section. Les valeurs visées dans cette section seront finalement insérées dans la base de données SQL Server. Sous le **détails de l’opportunité** cliquez ensuite le **modifier** bouton et affectez la valeur **étape** au champ **fermées/gagnées**. Cliquez sur **Enregistrer**.  
  
     ![Modifier une opportunité existante](../core/media/bts-sf-edit-opp.jpg "BTS_SF_Edit_Opp")  
  
4.  Dans SQL Server Management Studio, exécuter une requête sur le **OrderDetails** table pour sélectionner toutes les lignes.  
  
     ![Sortie de la requête SQL](../core/media/bts-sf-sql-query.jpg "BTS_SF_SQL_Query")  
  
     Notez qu'elle énumère les produits qui sont répertoriés dans l'opportunité dont vous avez modifié le stade.  
  
     ![Ajouter des produits à une opportunité](../core/media/bts-sf-add-product.gif "BTS_SF_Add_Product")  
  
 Vous pouvez voir que les enregistrements entrés dans le **OrderDetails** table correspondent à l’opportunité de vente créée dans Salesforce pour un ensemble donné de produits. Vous pouvez répéter ces étapes en créant de nouvelles opportunités et en associant de nouveaux produits à l'opportunité.