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
# <a name="step-5-test-the-solution"></a><span data-ttu-id="484d7-102">Étape 5 : Tester la Solution</span><span class="sxs-lookup"><span data-stu-id="484d7-102">Step 5: Test the Solution</span></span>
<span data-ttu-id="484d7-103">Cette solution vise à automatiser le processus d’envoi des notifications à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], chaque fois qu’une nouvelle opportunité est fermée dans Salesforce en définissant le stade de l’opportunité **fermées/gagnées**.</span><span class="sxs-lookup"><span data-stu-id="484d7-103">This solution aims at automating the process of sending notifications to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], every time a new opportunity is closed in Salesforce by setting the stage of the opportunity as **Closed Won**.</span></span> <span data-ttu-id="484d7-104">Une fois que la notification est reçue [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] envoie une requête à Salesforce pour récupérer les détails du produit relatives à l’opportunité, puis insère la réponse de Salesforce dans une table de base de données SQL Server appelée **OrderDetails**.</span><span class="sxs-lookup"><span data-stu-id="484d7-104">After the notification is received [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sends a query to Salesforce to retrieve product details related to the opportunity, and then inserts the response from Salesforce into a SQL Server database table called **OrderDetails**.</span></span> <span data-ttu-id="484d7-105">Par conséquent, pour tester cette solution, nous mettrons à jour l’étape de l’opportunité à **fermées/gagnées** et par conséquent, les enregistrements pertinents doivent être insérés dans la table OrderDetails dans la base de données de commandes.</span><span class="sxs-lookup"><span data-stu-id="484d7-105">So, to test this solution, we will update the stage of an opportunity to **Closed Won** and as a result, relevant records must get inserted in the OrderDetails table in the Orders database.</span></span>  
  
### <a name="to-test-the-solution"></a><span data-ttu-id="484d7-106">Pour tester la solution</span><span class="sxs-lookup"><span data-stu-id="484d7-106">To test the solution</span></span>  
  
1.  <span data-ttu-id="484d7-107">Connectez-vous à `https://login.salesforce.com/?lt=de` à l'aide des informations d'identification développeur Salesforce.</span><span class="sxs-lookup"><span data-stu-id="484d7-107">Log in to `https://login.salesforce.com/?lt=de`, using the Salesforce developer login credentials.</span></span>  
  
2.  <span data-ttu-id="484d7-108">Dans la barre de navigation, cliquez sur **opportunités**, puis cliquez sur **opportunité avec client 1**.</span><span class="sxs-lookup"><span data-stu-id="484d7-108">In the navigation bar, click **Opportunities**, and then click **Opportunity with Customer 1**.</span></span> <span data-ttu-id="484d7-109">Vous avez créé cette opportunité dans [étape 2 : configurer le système Salesforce](../core/step-2-set-up-the-salesforce-system.md).</span><span class="sxs-lookup"><span data-stu-id="484d7-109">You had created this opportunity in [Step 2: Set up the Salesforce System](../core/step-2-set-up-the-salesforce-system.md).</span></span>  
  
3.  <span data-ttu-id="484d7-110">Dans le **détails de l’opportunité** section, notez les produits associés dans le **produits (Standard)** section.</span><span class="sxs-lookup"><span data-stu-id="484d7-110">In the **Opportunity Detail** section, take a note of the associated products in the **Products (Standard)** section.</span></span> <span data-ttu-id="484d7-111">Les valeurs visées dans cette section seront finalement insérées dans la base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="484d7-111">The values you under this section will finally get inserted into the SQL Server database.</span></span> <span data-ttu-id="484d7-112">Sous le **détails de l’opportunité** cliquez ensuite le **modifier** bouton et affectez la valeur **étape** au champ **fermées/gagnées**.</span><span class="sxs-lookup"><span data-stu-id="484d7-112">Under the **Opportunity Detail** section click the **Edit** button and change the value of **Stage** field to **Closed Won**.</span></span> <span data-ttu-id="484d7-113">Cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="484d7-113">Click **Save**.</span></span>  
  
     <span data-ttu-id="484d7-114">![Modifier une opportunité existante](../core/media/bts-sf-edit-opp.jpg "BTS_SF_Edit_Opp")</span><span class="sxs-lookup"><span data-stu-id="484d7-114">![Edit an existing opportunity](../core/media/bts-sf-edit-opp.jpg "BTS_SF_Edit_Opp")</span></span>  
  
4.  <span data-ttu-id="484d7-115">Dans SQL Server Management Studio, exécuter une requête sur le **OrderDetails** table pour sélectionner toutes les lignes.</span><span class="sxs-lookup"><span data-stu-id="484d7-115">In SQL Server Management Studio, run a query on the **OrderDetails** table to select all rows.</span></span>  
  
     <span data-ttu-id="484d7-116">![Sortie de la requête SQL](../core/media/bts-sf-sql-query.jpg "BTS_SF_SQL_Query")</span><span class="sxs-lookup"><span data-stu-id="484d7-116">![SQL Query output](../core/media/bts-sf-sql-query.jpg "BTS_SF_SQL_Query")</span></span>  
  
     <span data-ttu-id="484d7-117">Notez qu'elle énumère les produits qui sont répertoriés dans l'opportunité dont vous avez modifié le stade.</span><span class="sxs-lookup"><span data-stu-id="484d7-117">Notice that it lists the products that are listed in the opportunity for which you changed the stage.</span></span>  
  
     <span data-ttu-id="484d7-118">![Ajouter des produits à une opportunité](../core/media/bts-sf-add-product.gif "BTS_SF_Add_Product")</span><span class="sxs-lookup"><span data-stu-id="484d7-118">![Add products to an opportunity](../core/media/bts-sf-add-product.gif "BTS_SF_Add_Product")</span></span>  
  
 <span data-ttu-id="484d7-119">Vous pouvez voir que les enregistrements entrés dans le **OrderDetails** table correspondent à l’opportunité de vente créée dans Salesforce pour un ensemble donné de produits.</span><span class="sxs-lookup"><span data-stu-id="484d7-119">You can see that the records entered in the **OrderDetails** table correspond to the sales opportunity created in Salesforce for a given set of products.</span></span> <span data-ttu-id="484d7-120">Vous pouvez répéter ces étapes en créant de nouvelles opportunités et en associant de nouveaux produits à l'opportunité.</span><span class="sxs-lookup"><span data-stu-id="484d7-120">You can repeat these steps by creating new opportunities and associating new products with the opportunity.</span></span>