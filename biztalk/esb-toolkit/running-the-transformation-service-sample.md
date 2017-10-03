---
title: "Exécution de l’exemple de Service de Transformation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42064d32-5ec5-4219-a338-c5769969b958
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1ac733f3164a319ed0b86e0f609de8ccd03bdbca
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-transformation-service-sample"></a>Exécution de l’exemple de Service de Transformation
Vous pouvez exécuter l’exemple de Service de Transformation à l’aide de n’importe quel outil ou un utilitaire qui peut exécuter des méthodes de service Web. Par exemple, vous pouvez utiliser Storm, disponible à partir de [CodePlex](http://go.microsoft.com/fwlink/?LinkId=187762) ([http://go.microsoft.com/fwlink/?LinkId=187762](http://go.microsoft.com/fwlink/?LinkId=187762)), ou vous pouvez créer votre propre client de test qui appelle le service Web de la Transformation.  
  
 Pour utiliser le Studio de Service Web .NET pour tester l’installation correcte de l’exemple de Service de Transformation, entrez l’URL du service Web de Transformation basés sur ASMX dans le **point de terminaison WSDL** zone de texte, puis cliquez sur le  **Obtenir** bouton. Cela génère une interface frontale client que vous pouvez utiliser pour appeler le Service Web de Transformation ESB, comme indiqué dans la Figure 1.  
  
 ![Service de transformation](../esb-toolkit/media/ch6-transformationservice.gif "§ 6-TransformationService")  
  
 **Figure 1**  
  
 **À l’aide du Studio de Service Web .NET pour tester l’exemple de Service de Transformation**  
  
 L’exemple de Service de Transformation contienne deux mappages Microsoft BizTalk et deux documents de message XML de test. Vous pouvez exécuter le service Web de Transformation avec les messages XML nommés TEST_CanonicalOrder_to_OrderConfirmation.xml et TEST_RetailOrder_to_CanonicalOrder.xml (situé dans le dossier \Source\Samples\TransformServices\Test\Data).  
  
 Le service transforme automatiquement les messages à l’aide de schémas CanonicalOrder.xsd et RetailOrder.xsd et OrderConfirmation.xsd (situé dans le \Source\Samples\TransformServices\Source\ESB. Dossier TransformServices.Schemas), et .NET Web Service Studio affiche les messages transformées résultantes. La procédure suivante montre comment vous pouvez tester le mappage de CanonicalOrder_To_OrderConfirmation.  
  
 **Pour tester le mappage GlobalBank.ESB.TransformServices.Maps.CanonicalOrder_To_OrderConfirmation**  
  
1.  Si l’application GlobalBank.ESB n’est pas en cours d’exécution, utilisez la Console Administration de BizTalk pour le démarrer.  
  
2.  Entrez la représentation sous forme de chaîne suivantes du fichier TEST_CanonicalOrder_to_OrderConfirmation.xml en tant que la valeur de la **message** paramètre dans le **entrée** arborescence de Studio de Service Web .NET. Cette chaîne est conforme au schéma GlobalBank.ESB.TransformServices.Schemas.CanonicalOrder :  
  
    ```  
    <ns0:CanonicalOrder OrderID="OrderID_0" OrderDate="OrderDate_1"   
        Status="Status_2" xmlns:ns0=  
        "http://schemas.globalbank.esb.transformservices.com">  
        <OrderHeader><CustomerName>CustomerName_0</CustomerName>  
        <CustomerID>CustomerID_0</CustomerID><ShipToLine1>  
        ShipToLine1_0</ShipToLine1><ShipToLine2>ShipToLine2_0  
        </ShipToLine2><BillToLine1>BillToLine1_0</BillToLine1>  
        <BillToLine2>BillToLine2_0</BillToLine2><OrderTotal>OrderTotal_0  
        </OrderTotal></OrderHeader><OrderDetails><LineItem Qty="Qty_0"   
        PartNum="PartNum_1" Description="Description_2"   
        UnitPrice="UnitPrice_3" Ext="Ext_4" /></OrderDetails>  
        <B2BPartnerDetails CreditLimit="CreditLimit_0"   
        AccountBalance="AccountBalance_1"   
        LastOrderedData="LastOrderedData_2"   
        DiscountLevel="DiscountLevel_3" /></ns0:CanonicalOrder>  
    ```  
  
3.  Entrez la chaîne suivante en tant que la valeur de la **mapName** paramètre dans le **entrée** arborescence de Studio de Service Web .NET. Il s’agit du nom complet tapé du mappage BizTalk à exécuter sur le message :  
  
    ```  
    GlobalBank.ESB.TransformServices.Maps.CanonicalOrder_To_  
        OrderConfirmation, GlobalBank.ESB.TransformServices.Maps,   
        Version=1.0.0.0, Culture=neutral, PublicKeyToken=<insertYourPublicKeyTokenHere>  
    ```  
  
4.  Cliquez sur le **Invoke** bouton pour exécuter le service Web. Le **sortie** test affiche les résultats.