---
title: "Étape 6 (sur site) : Créer une transformation pour mapper le Message à partir de la file d’attente vers le schéma Insert | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 30a55f1e-32cc-409a-a814-084026f51b35
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 02b2be9659714beb4b9a52f4c2a9dd1e5b3ea47f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-6-on-premises-create-a-transform-to-map-the-message-from-the-queue-to-the-insert-schema"></a>Étape 6 (sur site) : Créer une transformation pour mapper le Message à partir de la file d’attente vers le schéma Insert
Le message est reçu par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à partir de la file d’attente du Bus de Service sera le **ECommerceSalesOrder.xsd** schéma. Toutefois, pour insérer un message dans le **SalesOrder** table, le message doit être de **insérer** schéma que vous avez généré dans [étape 5 (locaux) : générer le schéma d’insertion d’un Message dans la Table SalesOrder](../core/step-5-generate-the-schema-for-inserting-a-message-into-salesorder-table.md). Par conséquent, dans cette rubrique, nous créons un mappage pour transformer le **ECommerceSalesOrder.xsd** schéma dans le schéma d’opération Insert.  
  
### <a name="to-create-a-map"></a>Pour créer un mappage  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vous avez déjà créé, cliquez sur le projet, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**. Dans le **un nouvel élément** boîte de dialogue, sélectionnez **carte**, entrez le nom de mappage `SalesOrder_SQL.btm`, puis cliquez sur **ajouter**.  
  
2.  Dans le mappage, pour le schéma source, sélectionnez **ECommerceSalesOrder.xsd**. Pour le schéma de destination, sélectionnez **TableOperations.SalesOrder.xsd (Insert)** schéma.  
  
3.  Mappez directement les nœuds suivants dans les schémas source et de destination :  
  
    |Schéma source|Schéma de destination|  
    |-------------------|------------------------|  
    |CompanyCode|CompanyCode|  
    |PartId|PartNum|  
    |Quantité|Qty|  
    |AskPrice|UnitAskPrice|  
    |Commentaires|CustomerComments|  
  
4.  Utilisez le **Date et heure** fonctoid pour mapper les valeurs pour le **DateRequested** et **ShipDate** éléments du schéma de destination. Ces nœuds ne sont pas mappés sur les nœuds respectifs du schéma source. Au lieu de cela, la date et l’heure est transmise à ces nœuds à l’aide du **Date et heure** fonctoid.  
  
    1.  Faites glisser et déposez un **Date et heure** fonctoid à partir de la boîte à outils vers la surface du mappeur.  
  
    2.  Connectez le fonctoid à la **DateRequested** élément dans le schéma de destination.  
  
    3.  Faites glisser une autre **Date et heure** fonctoid et connectez-la à la **ShipDate** élément dans le schéma de destination.  
  
5.  Mappez les nœuds suivants dans les schémas source et de destination à l’aide un **concaténation de chaînes** fonctoid :  
  
    |Schéma source|Schéma de destination|  
    |-------------------|------------------------|  
    |Adresse\Ligne1|SellToAddress<br /><br /> BillToAddress|  
    |Adresse\Ligne2|SellToAddress<br /><br /> BillToAddress|  
    |Adresse\Ville|SellToAddress<br /><br /> BillToAddress|  
    |Adresse\Département|SellToAddress<br /><br /> BillToAddress|  
    |Adresse\Pays|SellToAddress<br /><br /> BillToAddress|  
    |Adresse\CodePostal|SellToAddress<br /><br /> BillToAddress|  
    |Contact\Prénom|PartnerContact|  
    |Contact\NomFamille||  
  
     Effectuez les étapes suivantes pour chaque ensemble de mappage de concaténation de chaîne :  
  
    1.  Faites glisser et déposez un **concaténation de chaînes** fonctoid à partir de la boîte à outils vers la surface du mappeur.  
  
    2.  Ajoutez chaque élément de l’arborescence source en tant qu’entrée à la **concaténation de chaînes** fonctoid.  
  
    3.  Faites glisser et configurez la sortie de la **concaténation de chaînes** fonctoid à l’élément dans le schéma de destination.  
  
         Le mappage terminé ressemble à ceci :  
  
         ![Mappage pour transformer des schémas](../core/media/bts2010r2-tut1-map.jpg "BTS2010R2_Tut1_Map")  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 4 : Création d’une Application hybride à l’aide de BizTalk Server 2013](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)